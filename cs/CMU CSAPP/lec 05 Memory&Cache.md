# Storage Technologies

分类：RAM(SRAM,DRAM)，ROM，disk。

## RAM

RAM：支持随机访问，断电无法保持信息。SRAM 更贵，每个 bit 需要 6 个晶体管，但是更快，并且更稳定，无需刷新，应用于 cache；DRAM 便宜，每个 bit 需要 1 个晶体管，但是慢，并且对扰动敏感，需要 memory system 定期刷新或者使用额外 bit 纠错，应用于主存。

下面我们看下 basic 的 DRAM 是怎么实现的。

先说一个 DRAM chip。chip 由若干个 supercell 组成，每个 supercell 有 $w$ bits（通常而言 $w=8$），一共有 $d$ 个 supercell。而 supercell 会被排列成二维的 $r$ 行 $c$ 列。它跟外界通过 $w$ 个 data pin 跟 $\log_2 \max(r,c)$ 个 address pin 连接。需要访问某个位置时，memory controller 会先把行（RAS）通过 address pin 发过去，chip 会把那一整行都提取到 chip 内部的 row buffer，然后 controller 把列（CAS） 发过去，chip 会从 row buffer 里找出来，通过 data pin 发回去。

若干个（通常而言，8 个） DRAM chip 会组成一个 memory module。当要访问一个 64-bit 的 word 时，memory controller 会向这 8 个 module 发送同一个 RAS、CAS，然后把得到的 8 个 supercell 拼起来，发回去。

很多个 memory module 拼起来，就组成了 main memory。当要访问一个 word 时，memory controller 会算出它该去哪个 module 找，然后把对应的 RAS,CAS 发给那个 module。

DRAM 有很多改进，不再赘述。

## ROM

上述所讲 RAM 都是 volatile 的，因为一旦断电就会丢失信息。断电后仍能保持信息的统一称作 ROM，虽然它们中的大多数如今已经不是只读的了。

ROM 也分很多种，有的只能写一次，有的可以重复写好多次。其中 flash memory 最常用，我们平常用的 U 盘、SSD 都是 flash memory。

写在 ROM 上的程序也叫做固件（firmware）。

### Accessing Main Memory

CPU 是通过 bus 跟 memory 通信的。bus 就是一组线，能传递 address,controll,data。

具体来说，这个过程中有如下几个部分参与：bus interface（在 cpu 内部，负责跟 bus 对接），I/O bridge（中转站，负责把 cpu 的信息翻译成对应地 IO 设备能理解的格式。比如 memory controller 就在这里），main memory， system bus（连接 bus interface 和 I/O bridge），memory bus（连接 I/O bridge 和 memory）。

需要 read 时，cpu 通过 bus interface 把 address 扔到 system bus 上传给 I/O bridge，翻译成对应格式，传给主存；主存读取，扔回 I/O bridge； I/O bridge 翻译完之后扔回 cpu。

需要 write 时，cpu 通过 bus interface 先把 address 传给主存；主存等待，cpu 继续传 data；主存写入。

## Disk

### Geometry

一个 disk 包含一个位于中间的、高速旋转的 spindle， spindle 上有若干个 platter，每个 platter 有两个 surface。每个 surface 被划分成若干个同心圆，叫做 track，每个 track 又分成若干个 sector，每个 sector 存统一数量的 bytes， sector 之间有 gap， gap 并不是空白，而是固定的一组 01 搭配来表示 gap。

所有位于不同 surface 但是在同一位置的 track 叫做一个 cylinder。

disk capacity 就是这一堆东西乘起来的结果。

起初，每个 track 含有的 sector 数量是相同的，因此越往外的 track 的 gap 就越大。后来我们把 tracks 分成若干个 zone，每个 zone 内部的 sector 数量相同。

每个 surface 上都有一个 read/write head，由 arm 连接。所有的 heads 的位置是统一的。

访问一个位置的用时由 seek time, rotational latency, transfer time 共同决定。

一般而言，seek time 最久，transfer time 可以忽略不计。总用时可以用 2 倍的 seek time 来估计。

因为这个 geometry 实在太复杂了，所以 disk 上还有一个 disk controller 来管这个东西，把复杂的内部结构封装成由 logical blocks 构成的数组。当接收到指令时，firmware 将其转化为 $(surface,track,sector)$，然后再由 hardware 去读。

事实上，并非每个 sector 都会被映射为一个 logical block。 disk controller 会留一部分作为损坏的备用。

### Other Devices

![[Pasted image 20251215081428.png]]

别的 IO 设备包括 USB（Universal Serial Bus）、graphics card、host bus adapter 等等。它们通过 IO bus 跟 IO bridge 连接，它们被设计为独立于 CPU 运行的。
### Accessing the Disk

memory-mapped I/O 技术把一些 IO 设备映射到不存在的 memory address。

当需要读的时候，cpu 会通过三次 load 指令把参数加载到对应的 address 去，这些指令实际上被发给 disk 解码，disk 开始执行对应指令，与此同时 cpu 去干自己的事。当 disk 执行完成，把对应 data 加载到 memory 后，会发送一个 interruption 给 cpu，cpu 中止手头的事，调用 os 来解决这个 interruption。

interruption 本质上就是 cpu 上的一些 pin。

## SSDs

Solid State Disk，使用 flash memory 制作，提供 rotating disk 以外的一种选择。

SSD 总是写比读慢的，这是由底层机制决定的。

SSD 可能包含若干个 flash memory chip，每个 chip 包含多个 block，每个 block 包含多个 page。读和写都是以 page 为单位进行的。

然而，SSD 有一个特殊性质：为了写一个 page，我们必须 erase 掉整个 block（把所有 bits 置为 1）。所以一旦有一个写操作，我们必须把整个 block copy 走，把这个 block 置为 1，然后才能去写。

但是 flash memory 写的次数多了就会 wear out。所以厂商开发了复杂的算法尽量平均磨损、延长使用寿命。

# Locality

locality 是一种我们相信大部分程序应该具备的性质。

分成两种：spatial locality & temporal locality。 spatial 指的是访问一个位置后，大概率还会访问它附近的位置；temporal 指的是访问一个位置后，大概率之后还会访问这个位置。

概念比较简单，只有一个经常被忽略的点：instruction 也是存在 memory 中的，所以它也有 locality 的概念。

# Memory Hierarchy

![[Pasted image 20251215090901.png]]

如图。不同层之间总是以 block 为单位进行交换，但是不同层之间的 block 大小可能不一样。一般而言，越靠下越大。

上一层是下一层的 cache，也就是说，它存着下一层的一部分。

当我们要访问第 $k$ 层的某个数据时，如果在第 $k$ 层，直接获取，这叫 cache hit；如果不在，那就要从第 $k+1$ 层中获取到第 $k$ 层，再获取，这叫 cache miss。

cache miss 分成很多种。cold miss/compulsory miss 来自于系统刚启动，cache 还没有被填充。conflict miss 来自于我们 cache 采用的 replacement policy，为了更快的速度，这样的策略通常会对某个 block 能存在 cache 里的位置做出一些限制（比如，取模），所以有时 cache 还有空间，但是我们仍然需要替换一个块。capacity miss 来自于我们当前程序的这一部分 working set 太大了，比 cache 大小还要大。

![[Pasted image 20251215091337.png]]

# Cache

## structure

一个 cache 有若干 set，每个 set 有若干 line，每个 line 里存放一个 block 和1bit 的 valid bit 和若干 bit 的 tag。

不妨假设 block size $B=2^b$，set 个数 $S=2^s$，address 个数 $M=2^m$。

cache 的工作流程是这样的：当要 read 某个 address 时，它会提取出最开始 $s$ bits 作为去寻址的 set 编号。然后提取出中间 $m-b-s$ bits 作为 tag，在对应的 set 里找是否存在一个 line，它是 valid 的，并且 tag 相对应。如果找到了，那就是 cache hit，把 address 的最后 $b$ bits 作为 offset，从对应的 block 里加上相应偏移读出来。如果没找到，那就是 cache miss，从下一级存储中获取，然后按照一定的 policy 替换某个 line。

![[Pasted image 20251215195734.png]]

为什么 set index 是中间的 bit 呢？因为我们希望具有 spatial locality 的值更有可能同时出现在 cache 中，换句话说我们希望它们尽量平均存在于不同的 set 中（否则，一旦超过 capacity 就会有人被替换）。

每个 set 内 line 个数 $E=2^e$，cache capacity $C=SEB$，当 $E=1$ 时，被称为 direct-mapped cache；$E=\dfrac{M}{C}$ 时，被称为 fully associative cache；其余情况被称为 E-way set associative cache。

## writes

写的时候有两种策略。write-back & write-through。

write-through 就是说我把整个 hierarchy 中所有对应于这个位置的值全都改了。

write-back 就是说我只把当前 cache 中的值改了，并且记录 dirty bit；当这一个 line 被从 cache 中替换出去时再一步步向更低层级改回去。

此外，对于 write cache miss 也有两种策略。write-allocate & no-write-allocate。

write-allocate 就是说 miss 时我把值提取到 cache 中再改。

no-write-allocate 就是说 miss 时我直接改这个地址存在的那个层级的值。

通常而言，write-back & write-allocate 组合使用，因为它们都在尝试 exploit write ops 的 spatial & temporal locality；而 write-through & no-write-allocate 组合使用。

## Anatomy of a Real Cache

事实上，cache 分成 i-cache, d-cache, unified cache 这三种。i-cache 只存指令，d-cache 只存数据，unified cache 两者都存。

在现代 cpu 中，每个 core 有自己独享的 L1 d-cache, L1 i-cache, L2 unified cache；所有 core 共享 L3 unified cache。这所有的 cache 都在 cpu chip 上。

![[Pasted image 20251215200920.png]]