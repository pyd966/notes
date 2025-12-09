## 习题 9.1

> 2. 通过对积分区间作等分分割，并取适当的点集 $\{\xi_i\}$，把定积分看作是对应的积分和的极限，来计算下列定积分：
>
> $(1)\int_0^1x^3dx$

$(1)$

进行等分，取 $x_i=\dfrac in(i=0,1,\dots n)$，再取 $\xi_i=x_i(i=1,2,\dots n)$。

则由题意

$$
\begin{aligned}
\int_0^1 x^3dx&=\lim_{n\to\infty}\sum_{i=1}^n\xi_i^3\dfrac1n\\
&=\lim_{n\to\infty}\dfrac1{n^4}\cdot(\dfrac14n^2(n+1)^2)\\
&=\lim_{n\to\infty}\dfrac{(n+1)^2}{4n^2}\\
&=\dfrac14
\end{aligned}
$$

## 习题 9.2

> 1. 计算下列定积分：
>
> $(3)\int_e^{e^2}\dfrac{dx}{x\ln x}$
>
> $(5)\int_0^{\frac\pi3}\tan^2x dx$

$(3)$

记 $x=e^t$，则 $t=\ln x$

$$
\int\dfrac{dx}{x\ln x}=\int\dfrac{d(e^t)}{e^t\ln(e^t)}=\int\dfrac{dt}{t}=\ln|t|+C=\ln|\ln x|+C
$$

所以

$$
\int_e^{e^2}\dfrac{dx}{x\ln x}=\left.\ln|\ln x|\right|_e^{e^2}=\ln2
$$

$(5)$

$$
\int\tan^2xdx=\int(1-\sec^2x)dx=x-\tan x+C=F(x)
$$

所以

$$
\int_0^{\frac\pi3}\tan^2xdx=F(\dfrac\pi3)-F(0)=\dfrac\pi3-\sqrt3
$$

> 2. 利用定积分求极限：
>
> $(2)\lim\limits_{n\to\infty}n(\dfrac1{(n+1)^2}+\dfrac1{(n+2)^2}+\dots+\dfrac1{(n+n)^2})$
>
> $(3)\lim\limits_{x\to\infty}n(\dfrac1{n^2+1}+\dfrac1{n^2+2^2}+\dots+\dfrac1{n^2+n^2})$
>
> $(4)\lim\limits_{n\to\infty}\dfrac1n(\sin\dfrac\pi n+\sin\dfrac{2\pi}n+\dots+\sin\dfrac{n-1}n\pi)$

$(2)$

$$
n(\dfrac1{(n+1)^2}+\dfrac1{(n+2)^2}+\dots+\dfrac1{(n+n)^2})=\sum_{i=1}^n\dfrac1{(1+\frac in)^2}\cdot\dfrac1n
$$

这是函数 $f(x)=\dfrac1{(1+x)^2}$ 在 $[0,1]$ 上的一个积分和。

$$
\lim_{n\to\infty}n\sum_{i=1}^n\dfrac1{(n+i)^2}=\int_0^1\dfrac{dx}{(1+x)^2}=\left.-\dfrac1{1+x}\right|_0^1=\dfrac12
$$

$(3)$

$$
\sum_{i=1}^n\dfrac n{n^2+i^2}=\sum_{i=1}^n\dfrac1n\cdot\dfrac1{1+(\frac in)^2}
$$

这是函数 $f(x)=\dfrac1{1+x^2}$ 在 $[0,1]$ 上的一个积分和。

$$
\lim_{n\to\infty}\sum_{i=1}^n\dfrac n{n^2+i^2}=\int_0^1\dfrac{dx}{1+x^2}=\left.\arctan x\right|_0^1=\dfrac\pi4
$$

$(4)$

$$
\sum_{i=1}^n\dfrac1n\cdot\sin\dfrac in\pi
$$

这是函数 $f(x)=\sin\pi x$ 在 $[0,1]$ 上的一个积分和。

$$
\lim_{n\to\infty}\sum_{i=1}^n\dfrac1n\cdot\sin\dfrac in\pi=\int_0^1\sin\pi xdx=\left.-\dfrac1\pi\cos\pi x\right|_0^1=\dfrac2\pi
$$

## 习题 9.3

> 3. 设 $f,g$ 均为定义在 $[a,b]$ 上的有界函数，仅在有限个点处 $f(x)\neq g(x)$。证明：若 $f$ 在 $[a,b]$ 上可积，则 $g$ 在 $[a,b]$ 上也可积，且 $\int_a^b f(x)dx=\int_a^b g(x)dx$。

记 $S=\{x_1,x_2,\dots,x_k\}$ 为 $f(x)\neq g(x)$ 的位置，$x_1<x_2<\dots<x_k$。

记 $F(x)=f(x)-g(x)$，由题知，$F(x)$ 仅在 $S$ 上可能不为 $0$.

记 $M=\max|F(x)|$。

$\forall\epsilon>0$，取 $\delta=\dfrac\epsilon{2kM}$，对任何一个划分 $T$ 满足 $||T||<\delta$ 以及其中任何一组分点 $\{\xi_i\}$，都有

$$
|\sum_{i=1}^{|T|}f(\xi_i)\Delta x_i-0|=|\sum_{\substack{1\le i\le|T|\\ \exist j,x_j\in\Delta_i}}f(\xi_i)\Delta x_i|\le 2kM||T||<\epsilon
$$

从而 $\int_a^bF(x)dx=0$。

进而 $\int_a^bg(x)dx=\int_a^bf(x)dx-\int_a^bF(x)dx=\int_a^bf(x)dx$。