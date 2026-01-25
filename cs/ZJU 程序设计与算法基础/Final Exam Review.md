## 输入输出

每个 IO stream 是一个 FILE 文件，可以使用 FILE* 操作。每个 stream 都跟外部的设备（文件，打印机等等）关联。

每个 FILE 文件都包含如下概念：file position indicator, 缓冲区, EOF flag, error flag, open mode。

其中 file position indicator 是下一次操作的偏移量。

默认我们有 stdin, stdout, stderr 这些流。

`FILE *fopen(const char *filename,const char *mode)` 可以使用某种模式打开文件。失败返回 NULL。

mode 可以从下面选。下面漏写了 `b`，这是表示用二进制方式打开。

![[Pasted image 20260104202931.png]]

`int fclose(FILE *stream)` 关闭一个文件，返回 0 表示成功，返回 EOF 表示失败。

`size_t fread(void *buffer, size_t size, size_t count, FILE *stream)` 从 stream 中读取至多 count 个对象到 buffer，其中每个对象的 size 已指定。返回读取成功的对象个数。

`size_t fwrite(const void* buffer, size_t size, size_t count, FILE *stream)` 类似的。

`int fgetc(FILE *stream)` 读一个字符，包括空白。遇到任何错误都会返回 EOF。

`char* fgets(char* str, int count, FILE* stream)` 从 stream 中读，直到遇到换行/EOF/超过 count-1 个字符。注意如果读到换行还不超过 count-1 的话，那么它会把这个换行放到 str 里。成功返回 str，失败 NULL，注意读到 EOF 不算失败，除非一个字符都没读进来。

`int fputc(int ch, FILE* stream)` 输出一个字符，成功返回字符，失败返回 EOF。

`int fputs(const char* str, FILE* stream)` 输出一行，但是不会额外加回车（不加回车是因为 fgets 保留了回车）。成功返回非负，失败返回 EOF。

`long ftell(FILE* stream)` 返回 file position indicator 的位置。注意在文本模式下这个位置值只在给 fseek 使用时才有意义。

`int fseek(FILE* stream, long offset, int origin)` 重定位 indicator 到自 origin 偏移 offset 的位置。origin 可以从宏 `SEEK_SET`,`SEEK_CUR`,`SEEK_END` 中选，分别表示头、当前、尾。注意跟 ftell 同样的问题。成功返回 0，否则返回别的。

`void rewind(FILE* stream)` 一切清空，从头再来。

`int feof(FILE *stream);` 是否已经到 EOF，是返回非 0，否则 0.

`scanf`, `printf`, `fscanf`, `fprintf`,`sscanf`, `sprintf`，重点写一下 format string。

`scanf` 系列返回成功赋值的变量个数。如果在第一个变量成功赋值之前就失败，返回 EOF。

`printf` 系列返回传递给输出流的字符个数，如果出现错误，返回 EOF。

format string 由包括以下几个部分：

- 非空白的非 `%` 字符：要求下一个字符严格是指定的字符，否则读入失败。并不会把读入的字符存到变量里。
- 空白字符：会消耗缓冲区里开头的所有空白字符，也可能不消耗。
- 格式符：形如 `%[flags][width][.prec][length modifier]type`。flags 可为 `-+0` 或其组合，`-` 左对齐，`+` 保留符号，`0` 用 0 填充（跟 width 结合理解）。width 是一个数，表示最小字符数；或者是 `*`，表示下一个参数作为字符数给到函数。.number 表示小数点后保留的位数，`.*` 表示下一个参数作为保留位数给到函数。`length modifier` 可以是 `hh`,`h`,`l`,`ll`,`L` ，分别表示 单个字节，short，long，long long，long double。 type 可以见下图（`%%` 表示 `%` 本身，`%s` 遇到空白就停止了）。 ![[Pasted image 20260104205813.png]]![[Pasted image 20260106205157.png]]
- 格式符还可以是 `%[...]`：![[Pasted image 20260104205931.png]]会在最后放一个 `\0`。

## 内存管理

每个变量有存储位置（stack, heap）、生命周期、作用域。有四种存储类别说明符。

### auto

在函数/代码块内部定义变量默认为 auto。

函数/块开始执行时分配内存，结束释放，作用域仅限于内部。不可外部链接。

存储于栈。

不会初始化。

### static

对全局变量使用，表明作用域仅在此文件，生命周期是程序运行全周期。不可外部链接。

对局部变量使用，表明作用域仅在此函数/代码块，生命周期整个程序，初始化是在第一次执行到这里的时候进行。值会保留。不可外部链接。

对函数使用，表明函数只能在此文件中被调用。

会初始化。

存储于静态存储区。

### register

只是建议编译器把变量放在寄存器中。不能取地址。

### extern

声明不同文件的变量中使用。

或者引用同文件外部的全局变量。（可以覆盖局部变量）

## 指针

`int *p,q;` 中，只有 `p` 是指针。

指针可以加减常数，可以同类指针相减，但是不能相加。

`int * const ptr;` 表示这是一个指针常量，指针指向的位置不能修改。

`const int * ptr;` 和 `int const * ptr;` 表明这是一个常量指针，指向的数据是只读的，不能通过这个指针来修改。

`T a[10]` 的类型是 `T[10]`，必要时可以退化为 `T*`。

`int *p[10]` 表明的是一个类型为 `int*` 长度为 10 的数组。也就是说 `[]` 优先级更高。

函数也有指针。函数名也是指向函数的指针，这个地址是函数在 TEXT 的位置。

可以用 `&a` 来取一个数组的地址，此时地址值与 `a` 所表示的相同，但是二者类型不同。

`void **` 是一个指向 `void *` 的指针，注意必须严格是 `void *`。
## 字符串

注意区分字符串字面常量和字符数组。

`char * strcpy(char *dest, const char *src);`

`char * strcat(char *dest, const char *src);`

`size_t strlen(const char *s);`

`int strcmp(const char *s1, const char* s2);` `s1<s2` 返回负数，相等返回 0，否则返回正数。

`char * strchr(const char *s, int c);` 查找 c 字符第一次出现的位置。未找到返回 NULL。

`char * strstr(const char *haystack, const char *needle);` 在 haystack 里查找子串 needle 第一次出现的位置。找到返回起始位置，否则返回 NULL。

## 结构体

### 内存对齐

- 成员按声明顺序在内存中排列，但是中间可能会插入一些空字节。
- 每个成员的起始地址必须是其对其要求的整数倍。
- 结构体总大小必须是最大对齐要求的整数倍。

## 标准库

`void qsort(void *base, size_t nmemb, size_t size, int (*compar)(const void *, const void *));` base 是首指针，nmemb 是元素个数，size 是每个元素的 size， compar 是指向比较函数的指针，如果第一个元素大于第二个，返回正数，相同返回 0，小于返回负数。

## 杂项

### 变量命名规则

变量名以下划线、大小写字母开头，并且由下划线、数字、大小写字母组成。

不能使用关键字。

![[Pasted image 20260106103814.png]]

![[Pasted image 20260106104051.png]]

此外，关键字不允许被 `#define` 或者 `#undef`。

### 运算符优先级

![[Pasted image 20260106104231.png]]

逗号运算符是从左到右结合。

注意 sizeof 是运算符，并且这是一个在编译期就被计算的运算符，这意味着 `sizeof(a++)` 并不会真的执行 `a++`。

`%`,`<<`,`>>` 不能用到 double 上。

### 复杂类型声明推断

![[Pasted image 20260106104750.png]]

### 宏

![[Pasted image 20260106105135.png]]

### 数据类型

ASCII 的范围是 0~127
### 排序算法

![[Pasted image 20260106105706.png]]

## 一些题目

![[Pasted image 20260106110115.png]]

![[Pasted image 20260106110315.png]]

![[Pasted image 20260106110345.png]]

![[Pasted image 20260106110355.png]]

![[Pasted image 20260106110423.png]]

![[Pasted image 20260106110922.png]]

![[Pasted image 20260106111102.png]]
D

![[Pasted image 20260106111151.png]]

![[Pasted image 20260106111246.png]]

![[Pasted image 20260106111258.png]]

![[Pasted image 20260106111347.png]]

![[Pasted image 20260106111355.png]]

![[Pasted image 20260106111457.png]]

![[Pasted image 20260106111512.png]]

![[Pasted image 20260106111543.png]]

![[Pasted image 20260106111604.png]]

![[Pasted image 20260106111623.png]]

![[Pasted image 20260106111631.png]]

![[Pasted image 20260106111643.png]]

![[Pasted image 20260106111653.png]]

![[Pasted image 20260106111701.png]]

![[Pasted image 20260106111815.png]]

D

![[Pasted image 20260110092945.png]]