## Stage

当我们敲下 `gcc test.c -o test` 时，事实上程序经历了 `preprocessor, compilier, assembler, linker` 四个子程序的处理，最终才生成可执行文件。

![[Pasted image 20260121140225.png]]

这个流程应该是 `.cpp --(cpp)--> .i --(cc1)--> .s --(as)--> .o --(ld)--> [executable]`

当一个程序被执行时，system 提供的 `loader` 会被唤醒，把程序和数据拷到内存里，然后把 control flow 转移。

## Object files

这里说的 object file，不仅仅指上面提到的 .o 文件。它可以是以下三种任一：`Relocatable object file`，这也就是我们上面说的 .o；`Executable object file`，其实就是可执行文件；`Shared objefct file`，这是后面会提到的动态运行库。

这三种 object file 都遵循统一的格式，然而在不同 os 上可能不一样。下面基于 x86-64 Linux 的 ELF 讨论。

![[Pasted image 20260121142001.png]]

就长这样。

- ELF header 放一些简单的环境信息，比如大小端、字长一类的
- .text 放代码
- .rodata 放只读数据，比如 switch 的 jump table、字符串字面量
- .data 放初始化了的全局变量
- .bss 放未初始化的全局变量（初始化为 0 的也算未初始化，static local variables 也算全局），所以它们其实并没有真正占用那么大的空间
- .symtab 是 symbol table，记录本程序内 symbol 有关的一些信息
- .rel.text 放 .text 字段内有哪些东西需要 linker 修改，比如调用 external 函数、访问 global variable
- .rel.data 一样，只不过是 .data 字段内，比如某个全局变量的初始值是另一个全局变量的地址之类的
- .debug 是调试相关信息，比如局部变量、c 源码
- .line 存的是 machine code 跟源码之间的映射关系
- .strtab 存 .symtab .debug 里 symbol 的名字
- section header table 放每个 section 的位置、大小。

注意局部变量存放在栈中，并不在 .data/.bss 中。

然而被 static 修饰的局部变量事实上会存在 .data/.bss，因此它更像是 global variable。
## Symbols

可以分成三类：

- `Global symbols`，在本文件定义，也许会被别的文件访问。比如 nonstatic 函数和 global variables。
- `Externals`，在本文件访问，但是在别的文件定义。
- `Local symbols` 在本文件定义，仅在本文件内访问。例如 static 函数/global variables。

每个 symbol 都会在 .symtab 里存下自己的一个 entry。

![[Pasted image 20260121145531.png]]

## Static linking

为了构建可执行文件，linker 需要完成两项任务：标识解析、重定位。

首先，linker 需要把 .o 文件中每次标识访问，对应到某一个对应的标识定义上去。这就是标识解析。之后，linker 需要把标识最后真实的地址填充到标识访问处。这就是重定位。

### Symbol Resolution

对 local symbol 比较好处理。然而对于 global 就有一些棘手，比如多个文件中定义了同一个 symbol。下面介绍一下规则。

在 Linux 中，symbol 被分为 strong/weak。函数/有初始值的 global symbol 是 strong 的，无初始值的 global symbol 是 weak 的。

进行 resolution 时遵循如下规则：如果有多个重名 strong symbols，报错；如果有一个 strong 和多个 weak，那么全都解析到 strong；如果有多个 weak，那么任选其中一个，全解析到这一个。

这样的规则会导致奇怪的问题，所以请确定你明白自己在做什么。

### Static Libraries

在 linux 中一般是 .a 文件，里面包含一系列 .o 文件，以及一个索引。linker 只会把程序用到的 .o 连接进去，可以节省空间。

为了节省空间，linker 整出了一套神秘操作。简单来说，你在命令行中给出文件的顺序会影响最终能否成功 linking。

在 linking 过程中，linker 会按从左到右顺序，依次扫描每个文件，同时维护三个 set： U, D, E。

- U 表示那些被访问，但是还未定义的 symbol
- D 表示那些已被定义的 symbol
- E 表示那些真正被用到的 .o 文件

如果 linker 扫描到一个 .o 文件，一切都很正常。如果扫描到一个 .a 文件，它会扫描其内部的 .o 文件，然后去更新 UDE 三个 set。这意味着，如果后面有文件，使用了当前这个 .a 的某个 .o，但是这个 .o 没有被之前的文件使用过，那么它会被丢弃，导致 linking 错误。

解决办法是把所有 .a 放到命令行参数的最后。

### Relocation

也分两步。

首先要把所有文件的相同 section 合并起来，这样，对于每个 instruction 和 data，我们都有一个确定的地址。

然后要把这里面该填的地址填回去。

怎么知道我们有哪些位置需要填地址呢？之前的 .rel.text & .rel.data 就有用了。这里面的每个 relocation entry 形如：

![[Pasted image 20260121161956.png]]

## Executable files

结构就是这样。

![[Pasted image 20260121165955.png]]

这里 segment header table 就是告诉 os 执行的时候要把哪些数据拷到哪里，并设置对应的权限。

![[Pasted image 20260121170432.png]]

## Dynamic Linking

static 显然存在很多问题，所以我们开发了 dynamic 技术。

shared libraries 以 .so 作为后缀。

在 linking 阶段，我们不会把 .so 直接拷进来，而是把一些 relocation/symbol table 搞进来。

在真正执行的时候，loader 会发现这个程序含有一个 .interp 部分，这个部分包含我们需要的 .so 的路径。loader 会把 control 传递给对应的 .so 让它把自己加载到内存里，然后 relocate 这个程序，最后开始执行。

## Runtime Linking

更进一步地，我们甚至可以在运行时加载 shared library。

具体来说，c 可以通过一些函数，把 .so 加载到内存中，然后获取你想访问的内容的指针，这样就能访问了。

事实上，这不是严格意义上的 linking，更像是加载+指针访问。因为本程序的代码并未被修改。

### PIC(Position Independent Code)

由于 shared library 加载到的位置是不固定的，所以我们希望它具有 PIC 的性质：无论代码加载到内存中的什么位置，都可以正常执行。

为了达到这样的效果，我们存储一个全局 GOT，在程序被 load 确定好位置的那一刻，把每次 symbol reference 的位置跟它实际要访问的 symbol 的地址之差记录在里面，然后程序只需要通过 GOT 就可以访问 symbol 了，我们每次只需要修改 GOT，不需要修改 .text。这样安全性会高很多。

为了我也不知道是什么的原因，对于 function call，我们做得更复杂一点。我们实现了 lazy binding，只在每个函数被调用的第一次，将其加载到内存中，并初始化 GOT；在后续调用中，我们可以直接访问 GOT。这个过程并没有修改 .text，也是只修改了 GOT。是通过如下图所示的方法实现的。

![[Pasted image 20260122171223.png]]

## Interpositioning

允许你把程序调用的库函数篡改为自己的函数。这个过程可以发生在 compile, link or run 阶段。通常用来创建 wrapper 函数收集一些统计信息，当然你也可以用来做破坏。

### Compile-time

设想程序 `int.c` 里使用了库 `malloc.c`，因此需要 `#include <malloc.h>`。

我们自己编写一个 `mymalloc.c`，里面创建 `mymalloc, myfree` 两个函数。

编写一个 `malloc.h`，里面通过宏把 `malloc, free` 替换为 `mymalloc, myfree`，并且给出函数原型。

在编译 `mymalloc.c` 时正常编译，在编译 `int.c` 时使用 `-I.`，这会要求编译器先在 `.` 目录下寻找 `.h` 文件。

### Link-time

Linker 已经提供了很方便的工具。只需要使用 `-Wl,--wrap,f` 参数，就可以让 linker 把 f 解析到 __wrap_f, 把 __real_f 解析到 f。

这样你只需要写一个 `mymalloc.c`，里面声明 `__real_*`，定义 `__wrap_*` 并调用 `__real_*`。编译都正常编，只有 linking 的时候使用参数就行了。

事实上参数里的 `-Wl,` 的意思是把后面的参数传递给 linker，把后面的逗号改成空格。

### Run-time

这意味着我们只需要 exe 就可以完成 interpositioning。

先写一个 `mymalloc.c`，里面定义 `malloc, free`，然后通过运行时链接的方式调用真正的 `malloc, free`。

把 `mymalloc.c` 通过参数 `-shared -fpic -ldl` 编译成 `mymalloc.so`。

然后在运行前，设置环境变量 `LD_PRELOAD` 为 `./mymalloc.so`。

原理是，在进行动态链接时，linker 会先把 LD_PRELOAD 里的所有 symbol 加载进来。这样就达到了目的。

当然，这招对静态链接完全失效。
