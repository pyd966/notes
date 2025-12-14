## Storage Technologies

分类：RAM(SRAM,DRAM)，ROM，disk。

### RAM

RAM：支持随机访问，断电无法保持信息。SRAM 更贵，每个 bit 需要 6 个晶体管，但是更快，并且更稳定，无需刷新，应用于 cache；DRAM 便宜，每个 bit 需要 1 个晶体管，但是慢，并且对扰动敏感，需要 memory system 定期刷新或者使用额外 bit 纠错，应用于主存。

下面我们看下 basic 的 DRAM 是怎么实现的。

先说一个 DRAM chip。chip 由若干个 supercell 组成，每个 supercell 有 $w$ bits（通常而言 $w=8$），一共有 $d$ 个 supercell。而 supercell 会被排列成二维的 $r$ 行 $c$ 列。它跟外界通过 $w$ 个 data pin 跟 $\log_2 \max(r,c)$ 个 address pin 连接。需要访问某个位置时，memory controller 会先把行（RAS）通过 address pin 发过去，chip 会把那一整行都提取到 chip 内部的 row buffer，然后 controller 把列（CAS） 发过去，chip 会从 row buffer 里找出来，通过 data pin 发回去。

若干个（通常而言，8 个） DRAM chip 会组成一个 memory module。当要访问一个 64-bit 的 word 时，memory controller 会向这 8 个 module 发送同一个 RAS、CAS，然后把得到的 8 个 supercell 拼起来，发回去。

很多个 memory module 拼起来，就组成了 main memory。当要访问一个 word 时，memory controller 会算出它该去哪个 module 找，然后把对应的 RAS,CAS 发给那个 module。

DRAM 有很多改进，不再赘述。

### ROM

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