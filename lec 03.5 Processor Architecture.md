
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