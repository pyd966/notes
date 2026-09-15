
GPU 跟 CPU 都是计算单元，不过 CPU 被设计为尽可能降低 latency，GPU 被设计为尽可能增加 throughput。这就导致 GPU 特别适合进行大规模并行的简单计算。

我们先介绍 GPU 的架构。

一张 GPU 内部有多个流处理器（SM），我们通常从 SM 的层级思考。进一步地，每个 SM 内部有若干（4 个）warp scheduler，并且有同样多的计算分区，每个计算分区内部有很多计算单元（比如 1 个 tensor core，若干 cuda core 等等）。

整个 GPU 共享显存和 L2 cache；每个 SM 内部有 L1 cache/shared memory，它们共享一块物理内存，可以通过配置调整大小占比；整个 SM 有一大块寄存器堆。

接下来，我们介绍为什么 GPU 要设计成这样的架构。换句话说，我们把 GPU 的物理概念跟一些逻辑概念一一对应起来。

我们提交给 GPU 计算的一个任务被成为一个 grid。对于一般的并行计算任务而言，开一堆 threads 直接爆算就好了。但是 GPU 出于性能考虑，在 grid 和 thread 之间加入了 thread block 这一层结构。

简单来说，你在提交给 GPU 计算时，需要告知你需要生成多少个 thread block，以及一个 thread block 中有多少个 thread。之后 GPU 会按照一定顺序把一个 thread block 分配给某一个 SM 处理，也就是说，同一个 block 中的 threads 一定被同一个 SM 处理。

此时还没完，同一个 thread block 中的 threads 会被按照 32 个一组分为若干 warp，而 warp 才是 GPU 调控的最小单元。为了方便理解，你可以把一个 warp 对应于 CPU 并行中的 SIMD 指令，也就是说同一个 warp 共享一个 instruction flow。

那么问题来了：为什么要有 thread block 和 warp 呢？

不同 thread block 之间是不能通信的。通过划分 thread block，GPU 可以减少自己内部通信网络的硬件开销，并且也可以给硬件调度器更大的自由度（比方说，GPU 并不保证你发射的 block 会同步执行，不保证它们按顺序执行，不保证它们在或者不在同一个 SM 上）。

warp 概念的建立，就是纯粹为了把资源利用率打上去。如果你不进行 warp 分区，也就是说整个 SM 是一个计算分区，那么很有可能你的指令数喂不饱所有的计算单元，就会导致资源浪费。

下面，我们通过讲解一个 kernel 从发射到结束的全流程来进一步理解这个过程。

程序员指定 thread block 数以及每个中的 thread 数。GPU 的调度器会看当前哪些 SM 空闲，然后依次把 thread block 分配到空闲的 SM 上执行。

对于每个 SM，它会把 threads 先分成 warp，然后均匀分配 warp 给四个 warp scheduler（scheduler 0 分到 warp 0, 4, 8...）。每个 warp scheduler 都对应一个计算分区，并且维护一个自己的 warp pool。它会检查自己的 warp pool，如果有某个 warp 的下一条指令就绪，就会把它发射到计算分区执行。这里有 superscalar，每个 scheduler 可以同时发射两个指令，它们可以来自同一 warp 也可以来自不同 warp。但是这里没有 out-of-order。这个 scheduler 会尽量公平地分配计算时间给每个 warp。同一个 block 的 warp 之间可以通过 shared memory 彼此通讯，也可以通过 barrier 同步（不同 block 是不行的，因为你无法保证别的 block 什么时候执行）。

当一个 block 的所有 warp 都执行完毕，这个 block 就执行完了。一个 grid 的所有 block 都执行完毕，它就执行完了。

这里有一个跟 CPU 很不一样的小细节：GPU 中 block 占用的 register 以及 shared memory 都是独享的。这样做的好处是上下文切换极快，坏处是资源占用大，并且每个 SM 能驻留的 block 数量会受到这个限制（compiler 会在编译时静态计算 block 所占用的 reg 数量以及 memory 大小，scheduler 会依据这个进行分配）。

