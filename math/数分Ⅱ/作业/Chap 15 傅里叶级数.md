## 习题 15.1

> 1. 在指定区间上求下列函数的傅里叶级数：
>
> $(1)$ $f(x)=x$ $(i)-\pi<x<\pi$ $(ii)0<x<2\pi$

$(1)$

$(i)$

$$
\begin{aligned}
\pi a_n&=\int_{-\pi}^\pi x\cos nxdx\\
&=\int_{-\pi}^\pi x\dfrac{d(\sin nx)}{n}\\
&=\left.\dfrac{x\sin nx}{n}\right|_{-\pi}^\pi-\int_{-\pi}^\pi\dfrac{\sin nx}{n}dx\\
&=\left.\dfrac{\cos nx}{n^2}\right|_{-\pi}^\pi\\
&=0
\end{aligned}
$$

$$
\begin{aligned}
\pi b_n&=\int_{-\pi}^\pi x\sin nxdx\\
&=\int_{-\pi}^\pi-x\dfrac{d(\cos nx)}{n}\\
&=-\left.\dfrac{x\cos nx}{n}\right|_{-\pi}^\pi+\int_{-\pi}^\pi\dfrac{\cos nx}{n}dx\\
&=(-1)^{n+1}\dfrac{2\pi}n+\left.\dfrac{\sin nx}{n^2}\right|_{-\pi}^\pi\\
&=(-1)^{n+1}\dfrac{2\pi}n
\end{aligned}
$$

$$
b_n=(-1)^{n+1}\dfrac2n
$$

$(ii)$

$$
\begin{aligned}
\pi a_n&=\left.\dfrac{x\sin nx}{n}\right|_0^{2\pi}-\int_0^{2\pi}\dfrac{\sin nx}{n}dx\\
&=\left.\dfrac{\cos nx}{n^2}\right|_0^{2\pi}\\
&=0
\end{aligned}
$$

$$
\begin{aligned}
\pi b_n&=-\left.\dfrac{x\cos nx}{n}\right|_0^{2\pi}+\int_0^{2\pi}\dfrac{\cos nx}{n}dx\\
&=-\dfrac{2\pi}n+\left.\dfrac{\sin nx}{n^2}\right|_0^{2\pi}\\
&=-\dfrac{2\pi}n
\end{aligned}
$$

$$
b_n=-\dfrac2n
$$

> 3. 求函数
>
> $$
f(x)=\begin{cases}
-\dfrac\pi4&,-\pi<x<0\\
\dfrac\pi4&,0\le x<\pi
\end{cases}
>$$
>
> 的傅里叶级数，并由它推出
>
> $(1)$ $\dfrac\pi4=1-\dfrac13+\dfrac15-\dfrac17+\dots$

$$
\begin{aligned}
\pi a_n&=\int_{-\pi}^\pi f(x)\cos nxdx\\
&=-\int_{-\pi}^0\dfrac\pi4\cos nxdx+\int_0^\pi\dfrac\pi4\cos nxdx\\
&=0
\end{aligned}
$$

$$
\begin{aligned}
\pi b_n&=\int_{-\pi}^\pi f(x)\sin nxdx\\
&=\dfrac\pi4(\int_0^\pi\sin nxdx-\int_{-\pi}^0\sin nxdx)\\
&=\dfrac\pi2(\int_0^\pi\sin nxdx)\\
&=\dfrac\pi2\left.(-\dfrac{\cos nx}{n})\right|_0^\pi\\
&=\dfrac{\pi(1-(-1)^n)}{2n}
\end{aligned}
$$

$$
b_n=\dfrac{1-(-1)^n}{2n}
$$

$(1)$

取 $x=\dfrac\pi2$ 得到

$$
\begin{aligned}
\dfrac\pi4&=\dfrac{f(x+0)+f(x-0)}{2}\\
&=\sum_{n=1}^\infty\dfrac{1-(-1)^n}{2n}\sin(\dfrac\pi2x)\\
&=1-\dfrac13+\dfrac15-\dfrac17+\dots
\end{aligned}
$$

## 习题 15.3

> 2. 设 $f$ 为 $[-\pi,\pi]$ 上的可积函数，证明：若 $f$ 的傅里叶级数在 $[-\pi,\pi]$ 一致收敛于 $f$，则成立帕塞瓦尔等式
>
> $$
\dfrac1\pi\int_{-\pi}^\pi f^2(x)dx=\dfrac{a_0^2}2+\sum_{n=1}^\infty(a_n^2+b_n^2)
> $$
>
> 这里 $a_n,b_n$ 为 $f$ 的傅里叶系数。

下记 $S_n(x)$ 为傅里叶级数的前缀和。

在贝塞尔不等式的证明过程中，我们知道

$$
\int_{-\pi}^\pi(f(x)-S_m(x))^2dx=\int_{-\pi}^\pi f^2(x)dx-(\dfrac{\pi a_0^2}2+\pi\sum_{n=1}^m(a_n^2+b_n^2))
$$

然而，$\forall\epsilon>0,\exist N>0,\forall n>N,x\in[-\pi,\pi],|f(x)-S_m(x)|<\epsilon$。

这就是说 

$$
\int_{-\pi}^\pi(f(x)-S_m(x))^2dx<2\pi\epsilon^2
$$

所以 左式$=0$，帕塞瓦尔等式成立。

> 3. 帕塞瓦尔等式对于在 $[-\pi,\pi]$ 上满足收敛定理条件的函数也成立（证略）。请应用这个结果证明下列各式：
>
> $(1)$ $\dfrac{\pi^2}8=\sum\limits_{n=1}^\infty\dfrac1{(2n-1)^2}$

$(1)$

对 $f(x)=\begin{cases}-\dfrac\pi4&,-\pi\le x<0\\ \dfrac\pi4&,0\le x\le\pi\end{cases}$ 使用

$$
\begin{aligned}
\dfrac1\pi\int_{-\pi}^\pi f^2(x)dx=\dfrac{\pi^2}8
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{a_0^2}2+\sum_{n=1}^\infty(a_n^2+b_n^2)&=\sum_{n=1}^\infty b_n^2\\
&=\sum_{n=1}^\infty\dfrac1{(2n-1)^2}
\end{aligned}
$$

由帕塞瓦尔等式，两式相等，证毕。