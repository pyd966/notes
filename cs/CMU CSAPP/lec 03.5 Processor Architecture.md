
怎么好像没有这个 chap 对应的网课啊？

这一章看起来是从 architecture level 走到了 microarchitecture level。说人话就是我们原本 machine-level programming 就是对着一个提供的 ISA 去编，现在轮到我们来实现一个简化的 ISA 了。换句话说，请你自己搞一个处理器出来。

## ISA

那首先是设计一个 ISA。ISA 由我们 processor state,instruction set,programming conventions,exception handling 组成。

除了 exception handling 之前没提到过，别的区别都不大，我们不说了。

exception handling 就是说，processor 也可能会遇到 runtime-error，比方说访问了非法地址，或者说遇到了一个无法解析的指令之类的，这时它会抛出异常，然后在真实的处理器中通常会由 exception handler 处理。

一些小细节是 `pushq %rsp` 怎么办。那文档规定 push 进去的是原来的值；对应地，pop 出来之后，rsp 是栈顶的值，不会再执行自增。

## HCL

是用来设计硬件的语言，并不难理解。这一部分如果之前玩过类似于图灵完备这种游戏的话非常好理解。

## SEQ

为了帮助我们实现最终的 processor，我们先实现一个比较慢的 processor，以此来了解执行一个 instruction 需要哪些 stage。

那大概需要 fetch,decode,excute,memory,write back,pc update 这些部分。

这里我们把硬件分成了需要时序的部分（内存，PC，CC，reg file）以及不需要时序的 combinational logic。值得一提的是，我们认为内存和 reg file 的 read 部分是不需要时序控制的。

我们能成功的关键就在于，一个指令执行的所有 stage 都不依赖于某一个别的 stage 的更新。换句话说，随着时序一声令下，一个指令的所有 stage 可以仅由开始的 state（内存，PC，CC，reg）计算出最终它们的结果。注意，这并不意味着各个 stage 之间没有互相依赖。这个做法的目的是，保证一个时钟周期内能执行完一条指令。

接下来就是仔细地实现每个 stage 的功能，把它们拼起来就好了。因为我们之前合理地划分了 stage，所以这一部分内容繁杂但并不困难，我们在这里略去。

## Pipeline

整体的思路是，每个 instruction 可以被划分为若干个 stage，这些 stage 是可以顺序执行的，并且不是所有 instruction 都会用到所有 stage。

为了提高 stage 的利用率，我们可以采用流水线模式，让 instruction 按顺序流过 stage，需要执行哪个就执行一次，这样虽然执行单个指令的耗时（latecy）变长了，但是单位时间内可以处理的指令（throughput）变多了。

这样会遇到问题。

最大的问题是，后面的指令可能依赖前面的指令。比如 data dependency 和 control dependency。

关于 data dependency，我们有 stalling 和 forwarding 两种方法。第一个就相当于是插入一个 nop 指令阻塞流水线一会；第二个相当于是一旦我们的需要的值被算出来了就直接转发回来。事实上，大部分时间我们不需要 stalling，只有在 load/use hazard 的时候，因为涉及到内存这个执行顺序很靠后的 stage，可能会需要插入至多一个 bubble。

关于 control denpendency，我们采用 predicting 的方法来解决。具体地，只有 conditional jump 和 ret 指令会有这个问题。对于 conditional jump 我们粗暴地认为 jump 总会成功，对于 ret 指令，我们不做预测，等待 ret 执行完毕后再填充流水线。当然真实的 cpu 要先进得多，不过我们这样简化之后，只需要处理预测出错时复原的情况就可以了。

那怎么处理这个情况呢？很简单，你在 Execute 阶段能检测到错误，此时已经有两个不该被执行的指令被执行了，它们目前在 Fetch,Decode 阶段。好消息是，只有指令进入 Execute 阶段才会对 programmer-visible state 产生影响，所以我们可以简单地在下一个 cycle 把 bubble 插入到 Decode,Execute 阶段，然后给 Fetch 阶段正确的地址即可。这样做是无偏的，只有效率上有损失。

其次，由于各个 stage 耗时不同，而我们的 clock cycle 必须按照最慢的来设置，所以可能造成浪费。

最后，两个 stage 之间我们要插入一个 clocked reg 来控制流程，但是 reg 的读写也是需要时间的，并且这个会成为瓶颈。

除此以外，processor 还要考虑 exceptions。这可以分为两类。对于 internal exception，我们的 processor 需要处理 halt，非法指令，非法读写内存这几种情况。对于 external exception，我们不用管，但是现实中会有用户点击鼠标、网络接到输入等等事件发生。

然而即使是我们的简化 exceptions，还是有一些特殊情况需要考虑：如果 pipeline 里有多个 instructions 同时报错该扔出哪个？如果一个 instruction 先报错但是后来由于 prediction 错误被 cancel 了呢？如果有一个 instruction 在 Memory state 报错，但是它后面的那个 instruction 已经在 Execute stage 修改了我们的 state 该怎么还原？

上面是问题，下面先说说怎么搞一个 pipelined processor。

这个看我 lab 写的 record 吧。

现在我的问题是，我可以理解这种设计的合理性。然而，当我想要自己设计一个功能（比如当 JX 指令的结果已知时，直接跳转到正确位置，而非预测）时，我发现往里面添加 reg 或者修改逻辑是一个很复杂的任务。这应该是由于我没有完全理解它的整个结构。

但是我不太想细抠实现细节，所以暂时先这样吧。

## Performance

这里采用 CPI(Clocks Per Instruction) 来衡量 cpu 的性能。

我认为这是不合适的。

这样的指标忽略了我们把一个指令拆成 5stages 带来的速度提升。在最开始的 SEQ 实现当中，CPI=1，而我们的 PIPE CPI>1，但这并不意味着 PIPE 更差。事实上，受益于 5stages，PIPE 的一个 cycle 用时要比 SEQ 短得多，所以 PIPE 的实际运行速度应当更快。

因此，倘若硬件已给定，我们讨论 CPI 是有意义的。但倘若我们仍可随意修改硬件，那么用 CPI 作为衡量指标就不太有参考价值。

## Things ToBeDone

Multicycle Instructions：

目前为止，我们的所有 instruction 都可以在 1 cycle 内解决。然而很多指令实际上需要多 cycle。比如乘除法，比如浮点运算。你当然可以从软件层面实现这个功能，在编译时把一个指令编译成很多个指令。但是 microarchitecture level 也可以做很多事情。

首先添加为这些运算专门设计的硬件。之后有两条路：直接让指令在 Estage 停留它所需要的时间，或者开一条分支出来，让耗时长的指令独立于主线执行，并且把支路再次 pipelined。

The Memory:

我们假设从内存的读写操作都能在 1cycle 内完成，这是十分不现实的。

我们忽略了自修改代码（这有可能导致 load/use hazard）。

有一个很有意思的点：在实际的 processor 中，short duration（如简单的 cache miss）会通过添加更多 stall 的方式被处理；long duration（如数据根本不在 memory 里而是在 disk 中）会抛出一个 page fault exception，然后由 os 来处理这个问题。

这样做是很合理的，因为 page fault 的 cost 极高，相较之下，唤醒 os 带来的额外开销可以忽略不计。
