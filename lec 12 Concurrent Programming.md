从定义上讲，concurrent 指的是两个程序的运行时间彼此重叠。换言之，其中一个程序的开始时间晚于另一个程序的结束时间。定义本身并不一定要求两个程序严格在同一时刻同时执行过，事实上这需要 multi-core 或 hyperthread 技术。

在 exceptional control flow 中，我们见到了很多 concurrent 的例子，主要是由 kernel 介入的 os-level。事实上在 application-level 也有很多 concurrent 的应用。

## Concurrent Programming with Processes

只需要使用之前讲过的知识就能实现，没什么补充的。唯一需要说一句的是，注意回收子进程。

优点：

- 实现简单，只需要 `fork`, `execve`；
- 进程间彼此独立，几乎不共享数据，不容易犯错。

缺点：

- 进程间几乎不共享数据，除非是用特殊机制（IPC, interprocess communications ）；
- process 开销大，运行速度慢。

## Concurrent Programming with I/O Multiplexing

### I/O Multiplexing

核心是 `select` 函数，接受一个 fd 列表，阻塞进程直到 fd 列表中任何一个处于可读状态。这里可读状态的意思是，可以调用 `read` 函数读取至少一个字节而不会阻塞。

### Event-Driven

使用上面说的 `select` 函数，我们可以实现事件驱动的 server。

比如 echo 服务器，我们维护一个 fd pool，里面存放着所有与 client 连接的 fd，以及一个 listen fd。一旦从 `select` 返回，我们检查哪些事件发生并处理即可。

### Pros & Cons

优点：

- 可共享所有数据（不一定是好事）
- 可自行调度事件的处理顺序、分配资源；
- 开销小。

缺点：

- 难写；
- 本质上仍然是顺序执行，如果某一个事件需要很久才能处理完，那么它会阻塞。

其实不用 `select` 函数也能实现类似效果。这个方法的本质是把所有信息交给程序本身来调度，由程序员负责一部分 kernel 的任务。

## Concurrent Programming with Threads

这种方法像是前两种方法的结合。thread 是在同一个 process 的上下文内运行的，因此它们共享 virtual memory, open files, code, heap, shared libraries，但是独有自己的 PC, register, stack, condition codes, thread ID。

thread 的运行方式跟 process 很像，不同的是 thread 之间并不构成树形结构，而是构成一个 thread 池，每次执行从 thread 池里挑选一个执行，每个 thread 都可以 kill 别人。

main thread 特殊一点，它是第一个执行的 thread，同时还有一个特殊之处后面会讲到。

接下来要讲的是 posix thread，是一套实现 thread 的标准函数，在所有 Linux 上都有提供。

### Creating Threads

```c
typedef void *(func)(void *);

int pthread_cread(pthread_t *tid, pthread_attr_t *attr, func *f, void *arg);
```

`f` 指向要调用的 thread 函数，使用 `arg` 调用它。这函数接受一个泛型指针，返回一个泛型指针，这样的配置允许它接受任意多参数，返回任意多参数。

`tid` 指向的值会变成创建的 tid；`attr` 是一些配置，我们不做讨论。

新创建的 thread 可以通过 `pthread_self` 函数来得知自己的 tid。

### Terminating Threads

以下几种方式会导致线程终止：

- 一个线程的 top-level 函数 `return`；
- 一个线程调用 `pthread_exit` 函数，如果 main thread 调用了，那么会等到所有线程结束后再终止整个进程；
- 某个线程调用 `exit` 终止了整个进程；
- 某个线程调用 `pthread_cancel` 把当前线程终止了。

跟 process 类似，thread 终止后占用的空间不会立刻释放，需要被 reap。
### Reaping Terminated Threads

使用 `pthread_join` 可以等待某个特定 pid 线程终止，捕获它的返回值，并 reap。

### Detaching Threads

thread 存在两种状态： joinable, detached。

joinable 是指 thread 可以被其他线程 kill/reap，同时可以 kill/reap 其他线程，自然地，它的资源在 terminate 后不会自动释放。

detached 是指 thread 不能被其他线程 kill/reap，也不能 kill/reap 别人，它的资源会在 terminate 后自动释放。

所有 thread 默认处于 joinable 状态，使用 `pthread_detach` 传入 tid 可以使对应 thread 变为 detached 状态。

### Initializing Threads

如果有一些由所有 thread 共享的 ds 需要初始化，一种直接的办法是由 main thread 初始化。

另一种办法是使用 Pthread 给我们提供的方法。

```c
pthread_once_t once_control = PTHREAD_ONCE_INIT;

int pthread_once(pthread_once_t *once_control, void (*init_routine)(void));
```

在线程中将 `once_control` 设置成 `static`，然后通过 `pthread_once` 调用 `init_routine`，这样它会保证只在第一次执行时调用一次 `init_routine`，其余时候直接忽略。

## Shared Variables in Threaded Programs

threads 之间共享什么上文已有讨论，这里可以说得更具体一点。

- `global variables` 存放在 data 区域，因此是共享的；
- `local automatic variables` 存放在 stack 区域，通常不是共享的；
- `local static variables` 存放在 data 区域，本质上是限制访问权限的 global variables。

从原理上讲，threads 的 stack 仍然存放在 VM 的 stack 区域，这块区域并没有做权限保护，因此如果某个 thread 得到了另一个 thread 的 stack 区域的指针，那么它可以访问这个区域。

所以我们定义一个变量是 shared，当且仅当有多于一个 thread 访问了它，这里的访问指的不是形式上的，而是实际上的。

## Synchronizing Threads with Semaphore

thread 的执行模型跟 process 类似，它只能保证同一个 thread 内部的 logical flow 相对关系不变，对不同 thread 之间的执行顺序不提供任何保证。

因此，如果多个 thread 访问同一个 shared variable，对它进行修改，那么由于实际执行顺序不同，最终结果也可能不同。

这种问题叫做 synchronization error，可能很隐蔽。

如果你把 process graph 画出来（对 $n$ 个线程来说，这就是 $n$ 维笛卡尔积），并把每个 thread 修改 shared variable 的部分称作 critical section 的话，你会发现如果程序执行的轨迹穿过了两个相同 critical section 的相交区域，那么就可能出错。

![[Pasted image 20260207102540.png]]

解决方法有很多，其中一种是 Djikstra 发明的 semaphores。思想是，对每个 shared variable 创建一个辅助变量 $s$ 表示“锁”。

这种方法通过两种函数来避开 unsafe area：

- `P(s)`。如果 $s$ 非零，那么将 $s$ 减一，往后执行；如果 $s$ 是零，那么等待直到 $s$ 不是零，再将 $s$ 减一，继续执行。
- `V(s)`。将 $s$ 加一。如果有（多个）thread 在等待 $s$ 变成非零，那么就由 kernel 挑选一个 thread 继续执行。

在 Pthread 中，这些函数是通过函数 `sem_init, sem_wait, sem_post` 实现的。

最普通的用法就是把 $s$ 初始化为 $1$，谁要用谁就 `P(s)`，用完了就 `V(s)`。

此外还有两种常见模型：producer-consumer model, reader-writer model。不算很难，自己看。

这个解决方案的问题在于，`P(s), V(s)` 都是 syscall，速度很慢。此外对线程进行创建销毁操作也比较慢，不过这个问题可以通过提前创建线程池来解决。

## Using Threads for Parallelism

parallelism 指的是真正意义上同时运行多个指令。

现代计算机有两种方法来实现这一点：multi-core 和 hyperthread。

multi-core 比较简单不做展开。

hyperthread 是一种在一个 core 内执行多个 logical flow 的方法。现代 CPU 都使用 out-of-order 技术，有一套指令 fetch 系统负责在解决 data dependency, control dependency 的前提下，把所有已经就绪可以执行的指令发射给操作单元执行，以实现操作单元的负载最大化。如果我们把一套指令系统改成两套指令系统，就是 hyperthread。

好消息是，不光 process 会自动利用 parallelism， thread 也会。

这里需要注意的是，parallelism 对性能的提升是有上限的，这个上限由程序中不可并行的部分决定。

设想有一个程序，正常运行需要 $T$ 的时间，程序中有 $p$ 这么多部分可以优化，你将这部分优化到了原先的 $\frac 1k$。

那么最终运行时间 $T'=(1-p)T+\frac pk T$。

假设 $k=\infty$，那么 $T'=(1-p)T$，换言之，即使你使用无限核处理器，最终也只能获得 $p$ 的性能提升。

## Other Concurrency Issues

### Thread Safety

如果一个函数能在多个 thread 中被同时、重复调用而给出正确结果，那么它被称作 thread-safe。

以下是 thread-unsafe 函数的充分条件：

- 不保护 shared variable；可以通过设置 semaphore 解决。
- 在多次 invocation 中保持追踪同一状态，比如 `rand` 函数；可以通过要求调用时传入状态解决。
- 返回指针，但是指针总是指向同一位置，只是每次修改内容，比如 `ctime` 函数；可以通过要求调用时传入结果保存的地址解决。
- 调用 thread-unsafe 函数。可以通过把所有函数换成 thread-safe 解决。

### Reentrancy

如果一个函数不访问任何 shared data，换言之，它用到的所有数据都存在自己的栈上，那么它被称作 (explicitly) reentrant 的。

如果我们放宽一些限制，允许传入指针，只要指针指向的位置不是 shared 的就可以。这样我们就得到了 implicitly reentrant 的定义。

通常提到 reentrant，同时包含这两种 reentrant。

![[Pasted image 20260207105258.png]]

Linux 提供了绝大多数函数的 thread-safe 版本。

### Races

race 指的是 kernel 调度方法会影响程序正确性的现象。

### Deadlocks

deadlock 指的是几个线程在彼此等待不可能发生的情况。这在使用 semaphore 时最容易出现。

![[Pasted image 20260207105946.png]]

有一个避免 deadlock 的充分条件：如果我们把所有锁按照一个顺序排列，每当程序需要获得某些锁时，按照这个顺序获取，释放时按照逆序释放，就不会出现 deadlock。

好像不需要逆序释放也能避免 deadlock。