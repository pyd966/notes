
不得不承认，此前我对 GPU 的理解过于浮于表面。

GPU architecture 也要分成 abstraction 和 implementation 两个层面来理解。abstraction 其实就是 GPU 提供给你的接口，也就是 CUDA 暴露给你的部分；而 implementation 就是除此以外的所有底层细节。

## abstraction

GPU 的 abstraction 跟 ISPC 非常像。其实反过来说才对，是因为先有了 CUDA，之后 intel 说为什么我们不能在 CPU 上有类似的模型呢？才有了 ISPC。

简单来说，这里的并行分成两层，一层是 thread block，另一层是 threads。分别对应于 ISPC 中的 task 和 SIMD。

GPU 不保证不同的 thread block concurrently 执行，但是保证同一个 thread block 的 threads concurrently，这是这两层 abstraction 最大的区别。

此外同一个 thread block 可以使用高速的 shared mem。

## implementation

而相对的，warp 这个概念就是 implementation 层级的，哪怕你完全不知道它的存在，也能写出正确（但可能效率不高）的程序。

