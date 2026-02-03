
## File System

在 Linux 系统中，万物皆**文件**。目录是包含将文件名映射到文件的 map 的文件，硬盘、网络适配器等硬件也被 Linux 映射为文件。

因此，文件可以被分类为：普通文件、目录、socket 等。

有些时候，普通文件还会被分成 文本文件、二进制文件 两类。

无论是哪种文件，在 Linux 视角下都只不过是一连串 bytes 罢了。都可以进行最基本的文件操作：打开/关闭，读/写。此外，大部分文件还有一个 文件位置（file position） 的属性，表示接下来读/写的位置相对于文件开头的偏移量。

Linux（以及绝大多数 os）的文件结构都是一棵树。

## Opening/Closing Reading/Writing a File

自己翻书。

## RIO Package

自己翻书

## File Metadata

file 存储着一些 data，然而还有另一部分描述这些 data 信息的 data，叫做 metadata。

比如文件的大小、权限、时间、所有权等等。

可以通过 `stat` 访问。

## Reading Directory

自己看。

## Sharing Files

这部分很有意思。

![[Pasted image 20260127160035.png]]

kernel 维护着三种与文件有关的数据结构：Descriptor table, Open file table, v-node table。

每个进程都有自己的 descriptor table，它的下标是随着程序不断打开文件而动态分配的（也就是 `open` 函数的返回值，file descriptor），每一项都是一个指向 open file table 的指针。当 `fork` 函数被调用时，子进程会复制父进程的 descriptor table。

open file table 是由所有进程共享的，维护着计算机上所有打开的文件。每一项代表一个文件（但不一定代表不同的文件），包含一个 file position，一个指向 v-node table 的指针，和一个计数器，表示有多少 file descriptor 指向它。

这个计数器的用途是，让操作系统知道什么时候指向该 file 的所有 file descriptor 都关闭了，好让 os 知道此时可以真正关闭这个文件。

v-node table 也是由所有进程共享的，维护的是所有文件的 stat 信息。

值得注意的一点是，open file table 中的不同 file 可能指向 v-node table 中的同一个文件。

## IO Redirection

自己看

## Standard IO

由 terminal 运行的每个程序都会默认设置三个 file descriptor，分别是 stdin, stdout, stderr。





