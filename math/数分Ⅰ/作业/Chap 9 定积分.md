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

## 习题 9.5

> 1. 设 $f$ 为连续函数，$u,v$ 均为可导函数，且可实行复合 $f\circ u$ 与 $f\circ v$。证明：
>
> $$
> \dfrac{d}{dx}\int_{u(x)}^{v(x)}f(t)dt=f(v(x))v'(x)-f(u(x))u'(x)
> $$

任取在 $f$ 定义域内的一常数 $a$。记 $f(x)$ 的一个原函数是 $F(x)$。

$$
\int_{u(x)}^{v(x)}f(t)dt=\int_{u(x)}^af(t)dt+\int_a^{v(x)}f(t)dt
$$

两边同时对 $x$ 求导。

$$
\begin{aligned}
\dfrac{d}{dx}\int_{u(x)}^{v(x)}f(t)dt&=\dfrac{d}{dx}\int_{u(x)}^af(t)dt+\dfrac{d}{dx}\int_a^{v(x)}f(t)dt\\
&=-\dfrac{d}{dx}\int_a^{u(x)}f(t)dt+\dfrac{d}{dx}\int_a^{v(x)}f(t)dt\\
&=-\dfrac{d}{dx}F(u(x))+\dfrac{d}{dx}F(v(x))\\
&=f(v(x))v'(x)-f(u(x))u'(x)
\end{aligned}
$$

> 3. 求下列极限：
>
> $(1)\lim\limits_{x\to0}\dfrac1x\int_0^x\cos t^2dt$
>
> $(2)\lim\limits_{x\to\infty}\dfrac{(\int_0^xe^{t^2}dt)^2}{\int_0^xe^{2t^2}dt}$

$(1)$

记 $\cos x^2$ 的原函数是 $F(x)$，容易发现极限为 $\dfrac00$ 型。

$$
\begin{aligned}
\lim_{x\to0}\dfrac{F(x)}{x}&=\lim_{x\to0}F'(x)\\
&=\lim_{x\to0}\cos x^2\\
&=1
\end{aligned}
$$

$(2)$

记 $e^{x^2}$ 的原函数为 $F(x)$，$e^{2x^2}$ 的原函数为 $G(x)$。

容易发现极限为 $\dfrac{\infty}{\infty}$ 型。

$$
\begin{aligned}
\lim_{x\to\infty}\dfrac{F^2(x)}{G(x)}&=\lim_{x\to\infty}\dfrac{2F(x)F'(x)}{G'(x)}\\
&=\lim_{x\to\infty}\dfrac{2(\int_0^xe^{t^2}dt)\cdot e^{x^2}}{e^{2x^2}}\\
&=\lim_{x\to\infty}\dfrac{2F(x)}{e^{x^2}}\\
&=\lim_{x\to\infty}\dfrac{2F'(x)}{2xe^{x^2}}\\
&=\lim_{x\to\infty}\dfrac1x\\
&=0
\end{aligned}
$$

> 4. 计算下列定积分：
>
> $(1)\int_0^{\frac\pi2}\cos^5x\sin2xdx$
>
> $(3)\int_0^ax^2\sqrt{a^2-x^2}dx$ $(a>0)$
>
> $(5)\int_0^1\dfrac{dx}{e^x+e^{-x}}$
>
> $(6)\int_0^{\frac\pi2}\dfrac{\cos x}{1+\sin^2x}dx$

$(1)$

$$
\begin{aligned}
\int_0^{\frac\pi2}\cos^5x\sin2xdx&=\int_0^{\frac\pi2}2\sin x\cos^6xdx\\
&=-2\int_0^{\frac\pi2}\cos^6xd(\cos x)\\
&\xlongequal{t=\cos x}-2\int_1^0t^6dt\\
&=\dfrac27
\end{aligned}
$$

$(3)$

记 $x=a\sin t$，则

$$
\begin{aligned}
\int_0^ax^2\sqrt{a^2-x^2}dx&=\int_0^{\frac\pi2}a^4\sin^2t\cos^2tdt\\
&=\int_0^{\frac\pi2}\dfrac{a^4(1-\cos4t)dt}8\\
&=\dfrac{a^4}8\left.(t-\dfrac14\sin4t)\right|_0^\frac\pi2\\
&=\dfrac{\pi a^4}{16}
\end{aligned}
$$

$(5)$

记 $t=e^x$，则 $x=\ln t$。

$$
\int_0^1\dfrac{dx}{e^x+e^{-x}}=\int_1^e\dfrac{dt}{1+t^2}=\arctan e-\dfrac\pi4
$$

$(6)$

记 $t=\sin x$

$$
\int_0^{\frac\pi2}\dfrac{\cos x}{1+\sin^2x}dx=\int_0^{\frac\pi2}\dfrac{d(\sin x)}{1+\sin^2x}=\int_0^{1}\dfrac{dt}{1+t^2}=\dfrac\pi4
$$

> 7. 设 $f$ 为连续函数。证明：
>
> $(2)\int_0^\pi xf(\sin x)dx=\dfrac\pi2\int_0^\pi f(\sin x)dx$

$(2)$

记 $xf(\sin x)$ 的原函数为 $F(x)$，记 $t=\sin x$，记 $u=\pi-x$。

则 $F'(x)=xf(\sin x)$，所以 $F'(x)+F'(\pi-x)=\pi f(x)$。

两边同时积分得

$$
\int_0^{\frac\pi2}F'(x)dx+F'(\pi-x)dx=\pi\int_0^{\frac\pi2}f(x)dx
$$

也即

$$
\begin{aligned}
\dfrac\pi2\int_0^\pi f(\sin x)dx&=\dfrac\pi2(\int_0^{\frac\pi2}f(\sin x)dx+\int_{\frac\pi2}^{\pi}f(\sin x)dx)\\
&=\dfrac\pi2(\int_0^1f(t)d(\arcsin t)+\int_1^0f(t)d(\pi-\arcsin t))\\
&=\pi\int_0^1f(t)d(\arcsin t)\\
&=\pi\int_0^{\frac\pi2}f(\sin x)dx\\
&=\int_0^{\frac\pi2}F'(x)dx+F'(\pi-x)dx\\
&=\int_0^{\frac\pi2}F'(x)dx+\int_\pi^{\frac\pi2}F'(u)d(\pi-u)\\
&=\int_0^{\frac\pi2}F'(x)dx+\int_{\frac\pi2}^\pi F'(u)du\\
&=\int_0^{\pi}F'(x)dx\\
&=\int_0^\pi xf(\sin x)dx
\end{aligned}
$$

> 10. 设 $f$ 为连续可微函数，试求
>
> $$
> \dfrac{d}{dx}\int_a^x(x-t)f'(t)dt
> $$
>
> 并用此结果求 $\dfrac{d}{dx}\int_0^x(x-t)\sin tdt$。

记 $F(x)=\int_a^x(x-t)f'(t)dt$。

则

$$
F(x)=\int_a^xxf'(t)dt-\int_a^xtf'(t)dt=x\int_a^xf'(t)dt-\int_a^xtf'(t)dt
$$

记 $xf'(x)$ 的原函数为 $G(x)$。

则

$$
\dfrac{d}{dx}F(x)=\int_a^xf'(t)dt+xf'(x)-xf'(x)=f(x)-f(a)
$$

在上式中取 $f(t)=-\cos t,a=0$，我们知道

$$
\dfrac{d}{dx}\int_0^x(x-t)\sin tdt=\dfrac{d}{dx}\int_a^x(x-t)f'(t)dt=f(x)-f(a)=1-\cos x
$$