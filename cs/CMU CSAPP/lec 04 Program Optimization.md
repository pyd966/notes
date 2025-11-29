## Intro

优化可以在很多不同的层级去做。比如算法、常数、硬件等等。

除了针对一般的机器而言，优化也可以针对某个特定的处理器型号进行。当然，这样做的适用范围会变窄。

在进行优化的过程中，编译器会尽量不改变程序行为。然而，如果你的代码没有遵循规范（UB），仍然可能出现错误。

此外，这还导致，如果编译器不能确定优化是否安全，它就会选择不进行这个优化。

这是由于编译器掌握的信息跟 programmer 是不一样的。programmer 可能知道某个 int 的更精确的实际范围，但是 compiler 不知道。这还有个名字叫 optimization blocker。

## Generally useful optimizations

这些名字完全没用，写下来只是闲的。

### Code Motion

对于重复计算的值，计算一次之后存下来，之后再用。

### Reduction in Strength

把 costly 的操作用更简单的操作代替。比如乘除法。

### Share Common Subexpressions

进行了多次类似的计算，compiler 会提取出相同的部分，然后重复使用。

### Superscalar Processor

CPU 有多个部分，可能负责 Arith,Read,Load 等等，每个部件可能有多个。如果按顺序执行指令，那就很浪费，所以 CPU 一次读取多个指令，拆分成互不影响的若干个部分，分给各个部件去同步执行，尽量让它们别闲着。

此外，对于一些 costly 的指令，我们可以 pipeline 处理。

比方说一次乘法操作需要 3 个 cycle，我们认为每个 cycle 使用的是不同的部分。

那对于很多次不依赖的乘法操作，我不需要等到每个彻底执行完之后再搞下一个，我可以让它们进入流水线。

对于后面那些依赖这些操作的乘法操作，我可以等这些操作进行完之后，清空流水线，然后开始新的流水线。

![[Pasted image 20251015205601.png]]

这就是为什么，循环展开是有用的。不然因为相互依赖，它不敢使用 pipeline。当然还要注意一下运算结合的位置。

你也可以通过使用浮点寄存器的并行计算功能进一步加速。

然而这里有一个下界。读/写是需要时间的，所以得看一下你有几个单元负责这个工作。

### Branch Prediction

如果有条件分支，CPU 会猜一个分支去执行（这样就变成顺序代码了，可以 pipeline 之类的），然后之后真的执行到的时候，再看猜对了没。猜错了就回退。（事实上，每个 reg 有多个副本，回退的时候把值改成确定正确的那个版本）
## Common Optimization Blockers

一旦调用一个 function，compiler 无法对它做出任何假设。所以可以尽量 inline。

在 C 语言中，有可能会有引用别名。这就意味着你写一个循环，然后 `*p += a[i]` 会导致 `*p` 被反复从内存中读取写入，而不是计算完之后再写入。这是因为，编译器无法确定 `p` 是否指向某个 `a[i]`。所以可以使用临时变量 `sum`。

# Addendum

以上内容，都是仅粗略看一遍网课后写下的，难免有疏漏之处。现计划读一遍书，在读的过程中较系统地记录我的学习过程。

理论上来讲，无论 programmer 写了什么代码，一个最好的 compiler 总能将其转化成等价的、最优的 machine code。然而事实上并非如此，很多时候，programmer 能够进行比 compiler 更好的优化。为什么呢？

本质上是因为，programmer 知道更多的运行时信息。compiler 无法对程序外部的输入进行任何假设，所以它的优化策略会比较保守。但是事实上外部输入往往是有一些限制的，programmer 如果利用这些信息，就有可能能做到更好的优化。

所以，为了提升 compiler 的优化能力，一个方向是提升 compiler 分析给定代码的能力，让它做到已知信息下的最优解；另一个方向是给 compiler 提供更多的信息，这需要编程语言的支持。

为了进行优化，compiler 需要对 processor 执行不同指令所需的时间，以及 processor 自己可能采取的优化（parallel、reorder 等）有一定了解。programmer 最好也知道一些。

然而现实中的影响因素实在是太多了，所以事实上我们没有办法解释某个程序为什么有某个特定运行时间。并且，有时看起来很有前途的优化方法，实践中被证明是无效的。因此，尝试多种不同的优化技术组合也是有必要的。

下面我们介绍一些常见的 optimization blocker。

最常见的就是 memory aliasing。compiler 无法假设任何两个指针指向不同的地址，此时很多优化操作无法进行。

另一个是 function call。compiler 无法假设使用相同的参数 call a function 会得到相同的 return value，因为 function 可能有 side-effect。

下面介绍一些常见的优化方法。

最常见的是 code motion，提取重复计算的片段，改为一次计算。事实上这个思想在算法优化中也很常见。

此外还可以减少函数调用，因为这会带来额外开销。优化方式类似于 inline。

如果可能的话，减少内存访问也是有效的，因为内存访问实在是很慢。

在这一层级，我们似乎没有什么很有效的优化手段了。因此，为了进一步优化，我们需要深入到下一层级：processor level。为此，我们需要先对 processor 有一些了解。

此前被我们了解的，仅仅是 pipelined processor。现代的处理器使用更加先进的技术，实现了 superscalar processor。具体来说，superscalar 拥有多套硬件，采用更加复杂的调度系统，可以同时执行多条指令。

更激进地，superscalar 甚至会在 branch 真正确定下来之前，直接进入 execution 阶段。如果出错，它会重置 state。嗯其实不是这样的，事实上在 branch 真正确定下来之前，所有对 reg 和 mem 的修改都不会真正进行。

这个机制部分是由 retirement unit 实现的。现代 processor 执行指令是按照如下方式进行的：fetch unit 和 decode unit 把 instruction 解释成 operation（下一段提及）后，会被扔入 ROB（Reorder Buffer，重排序缓冲区）。一旦某 operation 的操作数就绪，并且有空闲单元，就会被发射执行。此时结果会被暂存入 ROB 中。retirement unit 维护着一个指令原始顺序的队列，它会监控队列头，当检测到这个指令已被执行完毕重新进入 ROB，并且此前的指令没有 exception，没有 mispred，那就会把它标记成 retired，更新 reg 和 mem。如果有 mispred 等，就清空流水线，重新开始执行。

此外，现代处理器可能会把一个复杂的 instruction 解释为若干简单的 operation。比如 `addq %rax,8(%rdx)` 会把 load,add,store 分成 3 operations 进行。然而这样的解释行为是 processor-specific 的，所以我们不管它。

此外，这里的更加 elaborate 的 forwarding mechanism 也值得提及。这里采用的技术，被称为 register renaming。一个会修改 reg r 的 operation 在被 decode 之后，会给 r 分配一个别名 t，并记录 pair(r,t)，表示 t 会修改 r。之后再访问 r 的 operation 会分配别名 s，记录 pair(t,s)。当第一个指令执行结束得到结果 v 后，会记录 pair(v,t)，然后使用 t 作为 operand 的就可以开始执行了。

评判 performance 的指标有如下三个：latency, issue time, capacity。latency 指的是一个指令从开始到结束所需的时间；issue time 指的是两个指令开始执行的时间间隔（在 pipeline 中我们已经知道这两个指标反映的并不是同一回事）；capacity 指的是可以执行这个任务的单元个数。