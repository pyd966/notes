## Numpy

numpy 中的核心数据结构是 `ndarray`，也就是 tensor 的一种实现。

相比于 python 原生数据结构，numpy 的优势在于速度快、占地小，同时保持了运算的灵活性。

numpy 提供了一类称作 `ufunc` 的函数，是其高性能计算的核心。ufunc 核心用 C 实现，并且利用了 CPU 的向量化指令，所以很快。几乎所有的标准运算符都有对应的 ufunc。

ufunc 在保持高效的同时也很灵活，支持广播（处理不同形状的数组）、类型转换、设置输出地址等操作，还可以使用 Numba 自定义 ufunc。

## Pandas

底层使用 numpy 的 ndarray 实现，所以效率也比较高；同时支持更灵活的数据类型、标号、对 NaN 的处理等。

简单来说， pandas 更适合用来读取数据、数据清洗与整理，numpy 适合在此之后进行大规模计算。

pandas 提供了三种数据类型，`Series`, `DataFrame`, `Index`

`Series`: 有标签的一维数组，可以通过 `.values` 得到对应的  ndarray，通过 `.index` 得到对应的 `pd.Index` 对象

`DataFrame`：有标签的二维数组。注意访问时先列后行

`Index`：标签对象本身，可以包含几乎任何东西。你可以把它看作是 Ordered Multiset 或者 Immutable Array。此外还有 `MultiIndex`，可以实现高维数组。