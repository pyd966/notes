## Exception

exception 机制由软硬件结合实现，因此较为复杂。

exception 不一定表明程序出现异常，实际上，exception 指的是跳出预定 control flow 而执行另外的 control flow 的行为。例如，timer 被触发 也会作为一种 exception 被处理。

exception 能实现，本质上还是由于 processor 的硬件设计。processor 有很多 pin，当某个 exception 发生时，对应的 pin 会被置为 1。每有一条指令执行完成，processor 会检查是否有 pin 被置为 1，如果有，它会简单保存当前 state，然后切换到内核态，根据预先设置好的 exception table，跳转到对应的内核函数（exception handler）去处理这个 exception。

这样的过程可以被看作特殊的 function call。从 exception handler 返回时，根据 exception 的种类，可能有以下三种情况发生：

- 回到 exception 发生时正执行的那条指令；
- 回到 exception 发生时的那条指令的下一条要执行的指令；
- 终止程序。

exception 的分类：

![[Pasted image 20260125194041.png]]

### Interrupt

interrupt 是异步的，意味着当前 exception 可能不是由于当前指令所造成的。

有个很有意思的 interrupt： timer。

无论单核还是多核，大部分时候计算机都要“同时”执行比 cpu 数量多的 process。这是通过 kernel 调度实现的。kernel 通过一定算法，决定运行某个 process 一回，然后去运行另一个 process 一回，然后也许再回来运行。

这意味着每隔固定时间，kernel 需要获得 control flow 的控制权。这一功能就是通过 timer 实现的。

### Trap

trap 通常用来进行 syscall。

syscall 是一种特殊的“函数调用”，设计初衷是为了实现权限保护。一些危险功能（例如 `fork, execve, read` 等）程序是不被允许直接使用的，必须通过 syscall 唤醒 kernel，校验权限后由 kernel 在内核态下执行。

syscall 与 函数调用 的区别正在此处。一条 syscall 指令事实上触发了一次 trap，唤醒 kernel 执行，执行完毕后返回下一条指令。

### Faults

faults 是有可能恢复的错误。例如 page fault。

如果 fault handler 成功处理了错误，就会返回原指令再执行一次。

如果处理失败，就会调用 kernel 的 abort 终止产生错误的程序。

### Aborts

不可恢复的错误。（悲）

## Process

按照逻辑认知顺序，应该先介绍进程概念的。但是已经这样了那就这样吧。

process 是在计算机上运行的实例程序，os 会呈现给 process 这样的错觉：process 是在计算机上运行的唯一程序，独占 cpu, memory 等资源。

独占 memory 的错觉是由 virtual memory 实现的；独占 cpu 的错觉是由 kernel 调度实现的。

尽管被映射到的实际内存可能不同，但是每个程序看到的内存结构都是一样的：0x400 开始是 code，往后是 user 的部分，包括 data, stack 等等；顶端是 kernel 的部分，包括 kernel 的 code, data, stack。 kernel 部分会一直加载在内存中，并且映射到每个程序的内存空间中，这种性质叫做 memory-resident。

![[Pasted image 20260126101755.png]]

正如之前提到过的，当某个 process 运行一段时间后，timer 被触发，唤醒 kernel，决定接下来要执行哪个 process。

一旦 kernel 决定，接下来执行另一个 process，那么 kernel 会进行上下文切换，以保证能回到当初离开这个 process 时的状态。上下文包括，当前进程的 register, flag, file, stack, heap 等等。

为了使 process 不彼此干扰，我们势必要限制它们能访问的内存、能执行的指令。换言之，除了 kernel 能访问全部资源外，其余进程都必须在受限状态下执行。

这两种状态分别叫做 kernel mode & user mode。

当 exception handler 被触发时，processor 会从 user mode 转为 kernel mode，处理完之后再转回来。

## Process Control

这部分没什么有意思的，可以直接翻手册。

值得注意的是：

- process 有三个状态：Running, Stopped, Terminated。其中 Running 指的是进程正在进行，或者正在等待被 schedule； Stopped 其实是暂停； Terminated 是终止。
- 当一个子进程被终止时，它并不会被完全释放，仍然会保留一部分信息，直到被它的父亲 reaped。这种已被终止，仍未释放的状态叫 zombie。
- 如果子进程的父亲被终止，那么 kernel 会把这个“孤儿”的父进程设为 init 进程。init 进程是一个特殊的、永不终止的进程，它是所有进程的祖先。此时，一旦子进程终止，init 进程会 reap 它。

## Signals

某种意义上是 software-level 的异常。设计的初衷是允许进程间（以及 kernel 跟进程之间）进行通信，毕竟所有硬件层面的异常都是由 kernel 捕获并处理的，kernel 需要一种手段通知触发异常的程序。

kernel 为每个 process 维护了一个 bit vector，表示对应的 signal 是否被触发。如果 kernel 要向某个 process 发送一个 signal，它会将对应的 bit 置为 1。这被称为 send 了一个 signal。

然而，kernel 不一定会让目标 process 下一个执行。换句话说，目标 process 这里可能堆积了很多 signal，甚至于同样的 signal 堆积了若干个。当目标 process 执行时，它只能看到某些 bit 置为 1，没有办法知道对应的 signal 被触发了几次。这是 signal 机制中最不寻常的一点。

事实上，当 kernel 准备调度一个 process 运行时，它会先检查这个 process 是否有未处理的 signal。如果有，就从最低位开始逐个要求 process 处理。处理完后再正常运行。这时才能说这个 process receive 了一个 signal。

实际上，kernel 为每个 process 维护两个 bit vector。一个 pending 一个 blocked。

出于某些原因，process 有可能会暂时不想处理某些 signal。这可以通过把对应的 signal 置为 blocked 状态来实现。

因为编写 signal handler 涉及到 concurrency，这可能变得相当复杂，相当难以调试。因此有一系列避免错误的建议可以遵守。具体还是去翻教科书吧。

## Nonlocal Jumps

没完全看懂。