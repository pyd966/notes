## Binary logic and gates

### buffer

输出跟输入保持相同，目的是放大电流、或者信号延迟、或者电平转换、防反灌等。

### 3-state buffer

三个端口 `IN, OUT, EN`，其中 `EN` 控制是否输出。如果 `EN` 是 0，那么 `OUOT` 会处于一种特殊的高阻态（High-Z），它处于某种断开状态，不会给输出赋值。

用途是做总线系统（如果多个东西会向一条线输出，只要它们不同时输出，就可以用三态缓冲器）等。

### 正逻辑与负逻辑

用 高/低电平 表示 1？

正逻辑下的与门会变成负逻辑下的或门。

### 传输延迟

门电路不是没有代价的，从输入变化到输出变化有延迟。有两种模型：延迟模型、惯性模型。惯性的意思是，如果两次改变间隔过短（rejection time），那这一个 pulse 会被忽略。惯性模型更符合实际。

### 跃迁时间

即使门电路决定把输出改变，改变也是需要一小段时间的。

### Fan-in & Fan-out

Fan-in: 一个逻辑门能接收的输入。如果 fan-in 过大会很复杂，

Fan-out: 一个逻辑门的输出，在其跃迁时间不超过一个阈值的前提下，最多能驱动后面的几个逻辑门（标准负载，以一个 inv 门为基准）。信号每经过一个逻辑门会衰减，可通过增加 buffer 来解决。

## Boolean Algebra

![[Pasted image 20260309081918.png]]

![[Pasted image 20260309081931.png]]
### Dual

变成对偶式，就是与或交换，10 交换。为了保证优先级不变，可能要加入必要的括号。

## Simplification of logic functions

### Cost Criterion

Literal cost: 数一下函数表达式中有多少个 literal（命题变量以及其反）

Gate input cost: 数一下除非门外的所有门，它们的 input 总数是多少。注意某个 term 中只含一个 literal 的情况。

Gate input cost with NOTs: 数一下含非门的所有门 input 总数。注意，同一个命题变量的反只计一次。

## Karnaugh Maps

最多只适用于 4 variables

注意几个名词：Implicant（蕴含项）、Prime Implicant（质蕴含项）、Essential  Prime Implicant（必要质蕴含项）

## XOR

我们说 XOR 是奇函数，这里奇函数的定义是，input 中有奇数个 1 时才为 1.

同或是 XNOR