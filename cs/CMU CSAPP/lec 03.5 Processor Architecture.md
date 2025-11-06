
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

其次，由于各个 stage 耗时不同，而我们的 clock cycle 必须按照最慢的来设置，所以可能造成浪费。

最后，两个 stage 之间我们要插入一个 clocked reg 来控制流程，但是 reg 的读写也是需要时间的，并且这个会成为瓶颈。

上面是问题，下面先说说怎么搞一个 pipelined processor。