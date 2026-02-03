
简单来说，虚拟内存是一种技术，把在物理内存中可能零乱的地址用有规律的虚拟地址表达出来，并提供从虚拟地址映射回物理地址的接口。

为什么我们需要虚拟内存？

- 为每个进程提供统一的内存结构，使 linker 在大多情况下可以确定真实地址，无需保持程序的 PIC 性质；
- 将不同进程的内存隔离开，提供访问权限保护；
- 可以方便地实现共享内存；
- 虚拟内存不一定非要映射到主存中，事实上，主存更像是一个 cache，这允许我们拥有更大的“内存”空间，而不必担心空间不足导致程序崩溃。

在现代架构中，从虚拟地址映射回物理地址是由独立于 CPU 外的 MMU(memory management unit) 处理的。
## VM Structure

kernel 为每个进程维护一个 page table，存在 kernel 的内存中，用来记录每个 virtual page 是否已 cache，并记录对应的 physical page number。

![[Pasted image 20260202100625.png]]

注意，page table 只能处理已 cache 的部分，无法区分 uncached 和 unallocated。事实上，只要访问的不是 cached 部分，都会触发一次 page fault，由 os 查询另一个数据结构（vm_area_struct）来判断是哪种类型。

实际上，由于内存空间很大，我们不可能为每个进程维护一个这样的 page table。这就是我们接下来要介绍的 multi-level page table。

简单来说，我们对整个 virtual memory 构建了一棵有很多层的多叉树，一旦从某一层开始，某个节点的后代都不存在，我们就直接不建这些点。这样可以节省很多空间。

当然，实际实现还是用多层 page table 来实现的，每个 page table 内存的不是物理地址（除了最后一层外），而是指向对应的下一层 page table 的指针。

![[Pasted image 20260202113648.png]]

为了避免内存访问速度过低，我们给 page table（原本存放于内存中）额外添加一个 cache 硬件（translation lookaside buffer, TLB）。

同时，我们这里所说的主存/物理内存，并不仅仅指 DRAM，而是指 DRAM & SRAM 构成的整体。所以这里也有 cache 技术的应用。（事实上，你可以选择让 SRAM 使用虚拟地址/物理地址，无非是调整地址翻译和查找缓存的顺序罢了。不过大家都选物理地址）

## Address Translation

CPU 内有一个特殊的 reg，叫做 page table base register (PTBR)，指向当前进程对应的 page table 的开始地址。这样，完成上下文切换只需要修改 PTBR 就行了。

当 MMU 接收到一个虚拟地址时，它会先把这个地址分成 virtual page number 和 virtual page offset 两部分。接下来使用 virtual page number 去查询对应的 physical page number，再跟 virtual page offset 拼成真正的物理地址。

![[Pasted image 20260202113659.png]]

## VM as a Tool for Caching

每个进程有自己的一套 VM，被分割成固定大小的 virtual pages 处理。物理内存也被分成同样大小的 physical pages 处理。

虚拟内存中的某个地址有三种可能情况：

- unallocated: 未被分配到 disk 上的某块地址，因而无法被访问；
- uncached: 已被分配，但是仅存在于 disk 上，未缓存到 main memory 中；
- cached: 同时存在于 disk 和 main memory 中。

这里，main memory 更像是 disk 的 cache。

由于一次 miss 带来的 penalty 过大，所以这里的 cache 策略跟此前出现过的不太一致。

- pages 很大；
- fully-associative；
- 使用更复杂的替换策略（由软件算法实现）；
- write-back。

## VM as a Tool for Memory Management

没什么重要的。

## VM as a Tool for Memory Protection

page table 同时保存了每个地址的权限状态（内核/读/写），权限不对会触发 SIGSEGV。

## Linux Virtual Memory

![[Pasted image 20260202115122.png]]

kernel 所对应的 virtual memory 很有趣，它的一块与进程相关，一块与进程无关。

与进程无关的那一块中，有一整个连续的段被映射到整个物理内存，以方便 kernel 直接对真实的物理内存操作。

与进程有关的那一块中存放着一些该进程的信息。

### Areas

Linux 系统将一个 process 的 VM 视为一系列 area，每个 area 就是一段连续的、有关联的 VM。比如 user stack, heap, code, etc.

![[Pasted image 20260202115930.png]]

Linux 系统为每个 process 维护了一个 task_struct，包含关于这个进程的一切信息。其中包含一个元素，指向 mm_struct，包含关于 VM 的信息。其中包含一个元素，指向 vm_area_struct，是一个由 area 组成的链表。

当一次 page fault 被触发时，handler 会利用 vm_area_struct 来检查此次 fault 的类型：

- 地址未分配：触发 segmentation fault；
- 地址已分配，权限不符：触发 protection exception；
- 地址已分配，权限符合：把 disk 上对应的部分交换到内存里。

### Memory Mapping

当一块 VM 被 allocate 时，它需要从 object 初始化。有两种情况：

- 从普通文件初始化。
- 从匿名文件初始化。匿名文件是一种并不实际存在于 disk 中，全 0 的长度任意的特殊文件。

这样的初始化并没有真正把文件内容 copy 过去，而是等待 CPU 某时真正访问对应的地址时才会利用 page fault 机制初始化。

object 可以作为 shared object 或 private object。

如果一个 object 是 shared object，那么所有写操作都将对别的同样映射过来的进程可见，并且最终会被写回到硬盘里的对应文件。（如果是从匿名文件初始化，那么会写入 disk 中的特殊区域，swap area，用来暂时保存被替换出来的 page，等到一切结束，这些内容会被丢弃）

如果一个 object 是 private object，那么写操作对别的进程不可见，并且最终不会写回对应的文件。简单来说，该进程对 object 的写入操作不会影响原数据。

这里有一种叫做 copy-on-write 的策略。具体来说，两个进程可能都把自己的某块 VM 映射到了同一块物理地址，如果这块地址是 private 的，那么任何一个进程修改其中任何一个 page，都会先复制那个 page，修改自己的映射，再修改复制后的 page。（有点像主席树）

事实上，这正是 `fork` 函数实现的方式。它先把当前进程的 `mm_struct` 复制到新的进程，然后把原本的虚拟内存标记为 private copy-on-write。

`execve` 函数实现的方法也很简单，只需要创立对应的 `mm_struct` 就可以了，并不需要真的等所有内容都 copy 到内存里再结束。

在 user-level 也有函数 `mmap`, `munmap` 可以操控 VM。

## Dynamic Memory Allocation

由 allocator 实现，可以分成两种：

- explicit allocator，需要显式申请与释放内存；
- implicit allocator，需要显式申请，可以自动释放内存（garbage collection, GC）。

所谓 implicit allocator，只不过是一个能自动识别该对谁调用 `free` 的机制罢了。我们先通过实现自己的 allocator，把 `malloc` 和 `free` 机制研究清楚。

`void *malloc(size_t size);` 接受一个参数 `size`，返回一个满足对齐要求的、至少 `size` bytes 大的空间的开头指针；失败返回 `NULL`。这里对齐要求指地址必须是 16/8 的倍数，取决于机器是 64/32 位的。

`void free(void *ptr);` 接受一个指针 `ptr`，要求释放对应的空间。保证指针是之前某次用 `malloc` 得到的返回值，并且当前对应空间仍未释放。

这两个函数必须在线正确处理请求，并且不能移动已分配的地址。

我们实现的 allocator 有两个指标：throughput 衡量时间，memory utilization（最大有效载荷比上声明的堆空间大小）衡量空间。

我们实现的基本思路是，将当前可操作的内存划分为一些 block，每个 block 可能是已分配/未分配。每个 block 额外维护一些信息。当需要分配时，我们找到一个大小合适（大于等于需要的大小）的块，（可能会）把块劈成两半，返回其中一块。需要释放时，我们把对应块标记成释放，修改相应的数据结构。

为了方便起见（也是为了减少下文提到的 `external fragmentation` 情况的出现），我们要求时刻保证一个 free block 两侧都是 allocated block。这个合并操作也叫 coalescing。

在实现过程中，我们经常会遇到以下两种降低 memory utilization 的情况：

- `internal fragmentation`，实际占用的空间比申请的空间来得大。这可能是由额外维护的数据结构造成的，也可能是出于对齐要求等。
- `external fragmentation`，空闲 block 的大小之和可以满足要求，但是任一空闲 block 都不行。这是最难处理的情况。

实现一个 allocator 有很多种方法，我们介绍 implicit free lists, explicit free lists 和 segregated free lists。

### Implicit Free Lists

![[Pasted image 20260202161916.png]]

通过在头尾记录 block 大小的方式，支持往前/后跳 block。

剩下只有一个问题：`malloc` 如何选择一个合适的 block。

有多种策略，比如 first fit, best fit 之类的。都是很 trivial 的。

### Explicit Free Lists

![[Pasted image 20260202162549.png]]

好处在于，`pred` 和 `succ` 并不一定指向内存上连续的上一块/下一块。为我们实现更复杂的结构提供了可能。

### Segregated Free Lists

把 free blocks 按 size 分成若干连续组，每个组维护一个 explicit free list。

当 `malloc` 被调用时，我们只需要在一个最接近的 list 里搜索第一个可容纳的 free block 即可。如果没有就去更大的 list 里找。

这里还有很多变种。

## Garbage Collection

怎么识别一块区域是 garbage 呢？我们把整个内存空间看成一个有向图，点表示区域，从 u 到 v 的边表示区域 u 内有一个指向区域 v 的指针。

从一些 root nodes 出发做 dfs，所有不可达点被认为是 garbage。

一次这样的 dfs 相当耗时，所以我们只在 malloc 发现当前堆空间不足时进行垃圾回收。

显然这对 C 这种底层语言是无效的，因为我可以记录区域 B 的指针跟区域 A 的指针的距离，然后只保存区域 A 的指针。这样看起来我失去了对 B 的访问权限，但事实上我仍然可以访问。

此外，我们不知道一个 data 是否是指针，所以我们只能考虑最坏情况，认为它们都是指针。这样的策略是保守的。

