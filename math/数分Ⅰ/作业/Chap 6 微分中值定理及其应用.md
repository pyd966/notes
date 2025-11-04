## 习题 6.1

> 1. 试讨论下列函数在指定区间上是否存在一点 $\xi$，使 $f'(\xi)=0$。
>
> $(1)f(x)=\begin{cases}x\sin\dfrac1x&,0<x\le\dfrac1\pi\\0&,x=0\\\end{cases}$

$\lim\limits_{x\to0}f(x)=\lim\limits_{x\to0}x\sin\dfrac1x=0=f(0)=f(\lim\limits_{x\to0}x)$，所以 $f$ 在 $x=0$ 处连续，所以 $f$ 在 $[0,\dfrac1\pi]$ 上连续。

并且显然 $f$ 在 $(0,\dfrac1\pi)$ 上可导，且 $f(0)=f(\dfrac1\pi)=0$。

由罗尔中值定理，$\exist\xi\in(0,\dfrac1\pi),f'(\xi)=0$。

> 2. 证明：
>
> $(2)$ 方程 $x^n+px+q=0(n\in N^+,p,q\in R)$ 当 $n$ 为偶数时至多有两个实根，当 $n$ 为奇数时至多有三个实根。

$(2)$

记 $f(x)=x^n+px+q$，则 $f'(x)=nx^{n-1}+p$。

则 $f'(x)$ 在 $n$ 为偶数时恰好有一个实根，在 $n$ 为奇数时至多有两个实根。

反证法。

当 $n$ 为偶数时，假设有三个不同实根 $x_1<x_2<x_3$。

则 $f(x_1)=f(x_2)=f(x_3)=0$，分别在 $(x_1,x_2),(x_2,x_3)$ 上对 $f$ 使用罗尔中值定理

$\exist\xi_1\in(x_1,x_2),\xi_2\in(x_2,x_3),f'(\xi_1)=f'(\xi_2)=0$，与 $f'(x)=0$ 最多有一个实根矛盾。

当 $n$ 为奇数得时候，假设有四个实根 $x_1<x_2<x_3<x_4$。

同理可得 $\exist\xi_1\in(x_1,x_2),\xi_2\in(x_2,x_3),\xi_3\in(x_3,x_4),f'(\xi_1)=f'(\xi_2)=f'(\xi_3)=0$，与 $f'(x)=0$ 最多有两个实根矛盾。

综上，矛盾，原命题成立。

> 4. 证明：
>
> $(2)$ 若函数 $f$ 在 $[a,b]$ 上可导，且 $|f'(x)|\le M$，则
>
> $$
> |f(b)-f(a)|\le M(b-a)
> $$

$(2)$

在 $[a,b]$ 上对 $f$ 使用拉格朗日中值定理，

$\exist\xi\in(a,b),\dfrac{|f(b)-f(a)|}{b-a}=f'(\xi)\le M$

所以 $|f(b)-f(a)|\le M(b-a)$。

> 5. 应用拉格朗日中值定理证明下列不等式：
>
> $(2)\dfrac h{1+h^2}<\arctan h<h$，其中 $h>0$。

$(2)$

记 $f(x)=\arctan x$，则 $f'(x)=\dfrac1{1+x^2}$。

对 $f$ 在 $[0,h]$ 上使用拉格朗日中值定理，

$\exist\xi\in(0,h),\dfrac{|f(h)-f(0)|}{|h-0|}=\dfrac{\arctan h}{h}=f'(\xi)=\dfrac1{1+\xi^2}\in(\dfrac1{1+h^2},1)$。

所以 $\dfrac h{1+h^2}<\arctan h<h$。