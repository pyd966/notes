## Basic

指令集：相当于是 C++ 标准一类的东西，只是规定了 CPU 能够做什么，但是没有要求 CPU 到底怎么做到这一点。不同的厂商实现同一种指令集可能有不同实现方法。常见的指令集有 x86 和 ARM。这个也就是我们说的 Architecture（架构，Instruction Set Architecture ISA）。

往下还有 Microarchitecture，指的是架构具体是怎么实现的。

下面这个图描述的是一个 C 程序到底是怎么编译的。

![[Pasted image 20251005114357.png]]

事实上，流程是这样的：预处理（处理 `#include`,`#define`,`#ifdef` 之类的，以及宏展开，得到的还是 C 程序），编译（得到 Asm，这个是跟架构有关的），汇编（得到 Machine Code，仍然是 ISA Level，事实上 Asm 跟机器码绝大多数时候是一一对应的，所以也有反汇编器），链接（把目标文件 .o/.obj 跟库文件链接起来，生成 .exe）

## Disassemble

反汇编：`objdump -d [name]`

gdb 也可以用来反汇编，`disassemble [function name]`

可以使用 `x/[number]xb [function name]` 来展示从某个函数开始 number 个字节的内容
## Asm

下面说的都是 x86-64 架构。

数据类型：对于 Integer，有 1,2,4,8 bytes 的，但是不区分有无符号，也不区分是不是 pointer。对于 Floating point 有 4,8,10 bytes 的，跟 Integer 完全不同。只有这些，没有什么数组之类的。

寄存器：我们有 16 个寄存器，每个都是 8 bytes，使用 `%r` 可以访问完整的，使用 `%e` 访问较低的 4 bytes，事实上你也可以使用较低的 2/1 bytes.

![[Pasted image 20251006181043.png]]

![[Pasted image 20251008140341.png]]

只有 `%rsp` 这个寄存器不太一样，它是栈指针。

事实上，我们还有 %rip 也是寄存器，它存的是当前正在运行的指令的地址。然而，只有通过特殊的技巧才能访问。

事实上，还有额外的八个位（CF,ZF,SF,OF...），叫做 condition codes，它们和 reg 一起构成了 Processor State。CF(Carry Flag，表示你加法的时候最终产生了进位)，ZF(Zero Flag，表示刚才的计算结果是 0)，SF(Sign Flag，提取符号位)，OF(Overflow Flag，其实就是原本操作数符号同，结果跟它们不同)。大多数指令都会根据其结果设置这几个 flag，但是 leaq 不会。

address mode expression:可以为常量（用 `$` 开头，如 `$0x4`）、寄存器、内存地址（`(register)` 表示 register 里存的值对应的那个地址，`D(Regb,Regi,S)` 表示 Regb 对应的地址往后偏移 `Regi*S+D`，其中 `D` 是常数（1/2/4 bytes，没有 `$`），`S` 是值为 `1/2/4/8` 的常数，Regb 不能是 %rsp，可以使用 `(Regb,Regi)/D(Regb,Regi)/(Regb,Regi,S)` 的省略形式）

`movq source,dest`，用途是复制，其中 source dest 都是 address mode expression。不允许从内存直接复制到内存。

`movezbl source,dest`，用途是复制，其中 source 是一个 1byte，指令将这个 byte 填入 dest 的最低 byte，并且把更高的 3bytes 置为 0.（你可能会想，还有 4bytes 啊。事实上，在 x86-64 中，那些 2bytes/1byte 的命令，不会管高位；那些 4bytes 的命令，会把高位置为 0）

算术与逻辑运算：

`leaq source,dest`，用途是，计算 `source` 的地址，放到 `dest` 中，其中 `source` 是 address mode expression，`dest` 是 reg。事实上它常常用来计算算术表达式，比如 `leaq (%rdi,%rdi,2),%rax` 就算了 `%rdi` 的三倍。

![[Pasted image 20251006185247.png]]
![[Pasted image 20251006185434.png]]

cmp：`cmpq src2,src1`，计算 src1-src2，并设置 condition states。

test：`testq src2,src1`，计算 src1&src2，并设置 condition states。

如何读取 condition states？理论上你可以直接读，但是我们更推荐下面这种做法：

![[Pasted image 20251008140215.png]]

流程控制：

条件语句：

传统方式是使用 jump instructions 来实现的。

![[Pasted image 20251008141447.png]]

使用方法是，`jmp position`，其中 position 是 .NAME，叫做 label，需要你在代码的别的地方写一个 .NAME:。只在汇编中可见，在真实的目标代码中是不可见的，目标代码中只有真实的地址。

另一种方法是，我们把两个 branches 都计算一遍，然后最后我们再进行条件判断，决定到底要采用哪一个值。

为什么要这样？因为现代计算机使用 pipeline，会提前运行接下来的指令（遇到条件分支会猜测），如果分支错误会花较多 cycles 挪回来。

这样的风险是什么？如果两个分支耗时很长，或者有 side effects，或者可能进行不合法的操作。

所以，只有简单的、不危险的、无 side effect 的操作，编译器才会这么做（因为确实会变快）。

核心指令是 `cmovle` 家族。

循环：

也是用 jump instructions 实现的。

switch 语句：

case 只能是整数。会先计算 case 的最大值、最小值，然后添加一个 bias 使得最小值变成 0。

如果 V 不大，那么就建一张跳转表。对于 merge case 的处理大致是 goto。

如果 V 很大，那么就构建一个 ifelse tree，可以做到对数复杂度。

函数调用：

参数以值的形式会被存在至多 6 个 reg 中，第一个是 %rdi，第二个是 %rsi，第三个是 `%rdx`.返回值在 `%rax`。


