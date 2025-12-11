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

## 习题 9.4

> 2. 不求出定积分的值，比较下列各对定积分的大小：
>
> $(1)\int_0^1 xdx$ 与 $\int_0^1x^2dx$。

$(1)$

当 $0\le x\le1$ 时，$x^2\le x$。

所以 $\int_0^1xdx\ge\int_0^1x^2dx$。

> 3. 证明下列不等式：
>
> $(1)\dfrac\pi2<\int_0^{\frac\pi2}\dfrac{dx}{\sqrt{1-\frac12\sin^2x}}<\dfrac{\pi}{\sqrt2}$
>
> $(4)3\sqrt{e}<\int_e^{4e}\dfrac{\ln x}{\sqrt{x}}dx<6$

$(1)$

$$
\dfrac1{\sqrt{1-\frac12\sin^2x}}=\dfrac1{\sqrt{\frac{3+\cos2x}4}}\in[1,\sqrt2]
$$

同时积分，得到

$$
\dfrac\pi2<\int_0^{\frac\pi2}\dfrac{dx}{\sqrt{1-\frac12\sin^2x}}<\dfrac\pi{\sqrt{2}}
$$

$(4)$

记 $f(x)=\dfrac{\ln x}{\sqrt x}$，则 $f'(x)=\dfrac{\sqrt{x}(2-\ln x)}{2x^2}$。

当 $x\in(e,e^2)$ 时，$f'(x)>0$；当 $x\in(e^2,4e)$ 时，$f'(x)<0$。

所以 $\min\limits_{x\in[e,4e]}f(x)=\min\{f(e),f(4e)\}=\dfrac1{\sqrt e}$，$\max\limits_{x\in[e,4e]}f(x)=f(e^2)=\dfrac2e$。

所以 $\dfrac1{\sqrt e}\le\dfrac{\ln x}{\sqrt{x}}\le\dfrac2e$。

同时积分，得

$$
3\sqrt e\le\int_e^{4e}\dfrac{\ln x}{\sqrt x}dx\le 6
$$

容易发现等号是取不到的，原不等式成立。

> 6. 试求心形线 $r=a(1+\cos\theta),0\le\theta\le2\pi$ 上各点极径的平均值。

即求 $\dfrac1{2\pi}\int_0^{2\pi}a(1+\cos\theta)d\theta=\dfrac a{2\pi}\left.(\theta+\sin\theta)\right|_0^{2\pi}=a$

> 11. 证明：
>
> $(1)\ln(1+n)<1+\dfrac12+\dots+\dfrac1n<1+\ln n$
>
> $(2)\lim\limits_{n\to\infty}\dfrac{1+\frac12+\dots+\frac1n}{\ln n}=1$

$(1)$

$(1+\dfrac1{n+1})^n<e<(1+\dfrac1n)^{n+1}$

所以，$n\ln(1+\dfrac1{n+1})<1<(n+1)\ln(1+\dfrac1n)$。

所以，$\ln(1+\dfrac1{n+1})<\dfrac1n<\ln(1+\dfrac1{n-1})$

上式求和，即得

$$
\ln(1+n)<1+\dfrac12+\dots+\dfrac1n<1+\ln n
$$

$(2)$

变形得

$$
\dfrac{\ln n+\ln(1+\frac1n)}{\ln n}=\dfrac{\ln(1+n)}{\ln n}<\dfrac{1+\frac12+\dots+\frac1n}{\ln n}<\dfrac{1+\ln n}{\ln n}
$$

同时取极限 $n\to\infty$，由夹逼定理得 $\lim\limits_{n\to\infty}\dfrac{1+\frac12+\dots+\frac1n}{\ln n}=1$