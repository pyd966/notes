## 习题 14.1

> 1. 求下列幂级数的收敛半径与收敛域：
>
> $(1)$ $\sum\limits_{n=1}^\infty nx^n$
>
> $(3)$ $\sum\limits_{n=0}^\infty \dfrac{(n!)^2}{(2n)!}x^n$
>
> $(5)$ $\sum\limits_{n=1}^\infty\dfrac{(x-2)^{2n-1}}{(2n-1)!}$
>
> $(8)$ $\sum\limits_{n=0}^\infty\dfrac{x^{n^2}}{2^n}$

$(1)$

$$
\lim_{n\to\infty}\sqrt[n]{n}=1
$$

所以收敛半径为 $\dfrac11=1$。

当 $x=\pm1$ 时由于通项不趋于 $0$，均发散。

所以收敛域为 $(-1,1)$。

$(3)$

$$
\lim_{n\to\infty}\dfrac{a_{n+1}}{a_n}=\lim_{n\to\infty}\dfrac{(n+1)^2}{(2n+2)(2n+1)}=\dfrac14
$$

所以 $\lim\limits_{n\to\infty}\sqrt[n]{a_n}=\dfrac14$

所以收敛半径 $R=\dfrac1{\frac14}=4$。

当 $x=4$ 时，考虑 $\dfrac{a_{n+1}4^{n+1}}{a_n4^n}=\dfrac{4(n+1)^2}{(2n+2)(2n+1)}>1$，所以不可能收敛。

当 $x=-4$ 时，考虑 $\dfrac{a_{n+2}(-4)^{n+2}}{a_n(-4)^n}=\dfrac{16(n+2)^2(n+1)^2}{(2n+4)(2n+3)(2n+2)(2n+1)}>1$，所以不可能收敛。

综上，收敛域为 $(-4,4)$。

$(5)$

先考虑计算 

$$
\begin{aligned}
\lim\limits_{n\to\infty}\dfrac1{\sqrt[2n-1]{(2n-1)!}}&=\lim_{n\to\infty}e^{-\dfrac{\ln(1)+\dots+\ln(2n-1)}{2n-1}}\\
&=\lim_{n\to\infty}e^{-\dfrac{\ln(2n+1)}{2}}\\
&=0
\end{aligned}
$$

所以 $\overline{\lim\limits_{n\to\infty}}a_n=0$

所以收敛半径 $R=+\infty$，收敛域 $(-\infty,+\infty)$。

$(8)$

先考虑计算

$$
\lim_{n\to\infty}\sqrt[n^2]{\dfrac1{2^n}}=0
$$

所以 $\overline{\lim\limits_{n\to\infty}}a_n=1$。

所以收敛半径 $R=1$。

当 $x=1$，显然收敛。所以 $x=-1$ 也收敛。

收敛域 $[-1,1]$

> 2. 应用逐项求导或逐项求积方法求下列幂级数的和函数（应同时指出它们的定义域）：
>
> $(1)$ $x+\dfrac{x^3}3+\dfrac{x^5}5+\dots+\dfrac{x^{2n+1}}{2n+1}+\dots$
>
> $(3)$ $\sum\limits_{n=1}^{\infty}n^2x^n$

$(1)$

设所求和函数为 $S(x)$。

$\lim\limits_{n\to\infty}\dfrac1{\sqrt[2n+1]{2n+1}}=1$，所以收敛半径为 $1$.

当 $x=1$ 时原级数 $>1+\dfrac14+\dfrac16+\dots=\dfrac12(\dfrac12+\dfrac13+\dots)$，后者是调和级数显然发散，所以原级数发散；当 $x=-1$ 时只是改变符号，也发散。

$S(x)$ 定义域为 $(-1,1)$。

对级数在 $(-1,1)$ 上逐项求导得，$S'(x)=\sum x^{2n}=\dfrac1{1-x^2}$。

所以 $S(x)=\int_0^xS'(t)dt=S(0)+\dfrac12\ln\dfrac{1+x}{1-x}=\dfrac12\ln\dfrac{1+x}{1-x}$

$(3)$

设所求和函数为 $S(x)=x\sum\limits_{n=1}^\infty n^2x^{n-1}=xf(x)$。

$\lim\limits_{n\to\infty}\sqrt[n]{n^2}=1$，所以收敛半径为 $1$.

当 $x=\pm 1$ 时显然发散，所以定义域为 $(-1,1)$

$\int_0^xf(t)dt=\sum\limits_{n=1}^{\infty}nx^n=x\sum\limits_{n=1}^\infty nx^{n-1}=xg(x)$

$\int_0^xg(t)dt=\sum\limits_{n=1}^\infty x^n=\dfrac x{1-x}$

所以 $g(x)=(\dfrac{x}{1-x})'=\dfrac1{(1-x)^2}$

$f(x)=(xg(x))'=\dfrac{1+x}{(1-x)^3}$

$S(x)=xf(x)=\dfrac{x+x^2}{(1-x)^3}$

> 3. 证明：设 $f(x)=\sum\limits_{n=0}^\infty a_nx^n$ 当 $|x|<R$ 时收敛，若 $\sum\limits_{n=0}^\infty\dfrac{a_n}{n+1}R^{n+1}$ 也收敛，则
>
> $$
> \int_0^Rf(x)dx=\sum_{n=0}^\infty\dfrac{a_n}{n+1}R^{n+1}
> $$
>
> （注意：这里不管 $\sum\limits_{n=0}^\infty a_nx^n$ 在 $x=R$ 处是否收敛）
>
> 应用这个结果证明：
>
> $$
> \int_0^1\dfrac1{1+x}dx=\ln 2=\sum_{n=1}^\infty(-1)^{n-1}\dfrac1n
> $$

记 $F(x)=\int_0^xf(t)dt,G(x)=\sum\limits_{n=0}^\infty\dfrac{a_n}{n+1}x^{n+1}$。

当 $x\in(-R,R)$ 时，有 $F(x)=G(x)$。

而 $G(x)$ 在 $x=R$ 处收敛，并且 $G(x)$ 在 $x=R$ 处连续，$F(x)$ 也在 $x=R$ 处连续。

所以 $G(R)=\lim\limits_{x\to R^-}G(x)=\lim\limits_{x\to R^-4}F(x)=F(R)$。

取 $a_n=(-1)^n,R=1$，则 $f(x)=\dfrac1{1+x}$，立刻得到所求式子。

> 4. 证明：
>
> $(1)$ $y=\sum\limits_{n=0}^\infty\dfrac{x^{4n}}{(4n)!}$ 满足方程 $y^{(4)}=y$

$(1)$ 

容易发现收敛域为 $(-\infty,+\infty)$。

$y^{(1)}=\sum\limits_{n=1}^{\infty}\dfrac{x^{4n-1}}{(4n-1)!}$

一直计算下去，$y^{(4)}=\sum\limits_{n=4}^{\infty}\dfrac{x^{4n-4}}{(4n-4)!}$，逐项对比系数可以发现，$y^{(4)}=y$。

> 6. 证明：若 $\sum\limits_{n=0}^{\infty}a_nx^n$ 的收敛半径是 $R(0<R<+\infty)$，则 $\sum\limits_{n=0}^{\infty}a_nx^{2n}$ 的收敛半径是 $\sqrt{R}$

由题知，$\overline{\lim\limits_{n\to\infty}}\sqrt[n]{a_n}=\dfrac1R$。

考虑 $\overline{\lim\limits_{n\to\infty}}\sqrt[2n]{a_n}=\dfrac1{\sqrt R}$

所以后者的收敛半径为 $\sqrt R$

> 7. 设 $\sum\limits_{n=0}^\infty a_nx^n$ 的收敛半径是 $R(0<R<+\infty)$。证明：对给定的 $M>\dfrac1R$，存在 $K>0$，使得 $|a_n|\le KM^n,\forall n=1,2,\dots$。

$\dfrac1M<R$，所以 $\sum\limits_{n=0}^\infty\dfrac{a_n}{M^n}$ 收敛。

也就是说 $\lim\limits_{n\to\infty}\dfrac{a_n}{M^n}=0$，所以有界，故 $\exist K>0,|\dfrac{a_n}{M^n}|\le K$，也就是说 $|a_n|\le KM^n$。

> 8. 求下列幂级数的收敛域：
>
> $(1)$ $\sum\limits_{n=0}^{\infty}\dfrac{x^n}{a^n+b^n}$ $(a>0,b>0)$
>
> $(2)$ $\sum\limits_{n=1}^{\infty}(1+\dfrac1n)^{n^2}x^n$

$(1)$

考虑 $\lim\limits_{n\to\infty}\dfrac1{\sqrt[n]{a^n+b^n}}=\dfrac1{\max\{a,b\}}$。

所以收敛半径为 $\max\{a,b\}$，不妨假设 $a\ge b$。

当 $x=\pm a$ 时，$|a_n|=\dfrac1{1+(\frac ba)^n}\not\to 0$，所以不收敛。

所以收敛域为 $(-\max\{a,b\},\max\{a,b\})$。

$(2)$

考虑 $\lim\limits_{n\to\infty}\sqrt[n]{(1+\dfrac1n)^{n^2}}=e$。

所以收敛半径为 $\dfrac1e$。

当 $x=\pm\dfrac1e$ 时，$|a_n|=\large(\dfrac{(1+\dfrac1n)^n}{e^n}\large)^n\not\to 0$，所以不收敛。

> 10. 求下列幂级数的收敛半径及其和函数：
>
> $(1)$ $\sum\limits_{n=1}^\infty\dfrac{x^n}{n(n+1)}$

$(1)$

求 $\lim\limits_{n\to\infty}\sqrt[n]{n(n+1)}=1$，所以收敛半径为 $1$。

考虑当 $x=1$ 时，裂项可知收敛，所以 $x=-1$ 也收敛。

所以收敛域为 $[-1,1]$。

考虑和函数设为 $S(x)$。

则 $S'(x)=\sum\limits_{n=1}^{\infty}\dfrac1{n+1}x^{n-1}=\dfrac1{x^2}\sum\limits_{n=1}^\infty\dfrac{x^{n+1}}{n+1}=\dfrac1{x^2}f(x)$

则 $f'(x)=\sum\limits_{n=1}^{\infty}x^n=\dfrac{x}{1-x}$

所以 $f(x)=f(0)+\int_0^xf'(t)dt=-\ln(1-x)-x$

所以 $S(x)=S(0)+\int_0^x\dfrac1{t^2}f(t)dt=\begin{cases}0&,x=0\\1&,x=1\\1+\dfrac{1-x}{x}\ln(1-x)&,x\in[-1,0)\cup(0,1)\end{cases}$

## 习题 14.2

> 2. 利用已知函数的幂级数展开式，求下列函数在 $x=0$ 处的幂级数展开式，并确定它收敛于该函数的区间：
>
> $(1)$ $e^{x^2}$
>
> $(3)$ $\dfrac{x}{\sqrt{1-2x}}$
>
> $(5)$ $\dfrac{e^x}{1-x}$
>
> $(9)$ $\ln(x+\sqrt{1+x^2})$

$(1)$

$e^x=\sum\limits_{n=0}^{\infty}\dfrac{x^n}{n!}$，在 $(-\infty,+\infty)$ 上成立。

代入 $x^2$，得 $e^{x^2}=\sum\limits_{n=0}^\infty\dfrac{x^{2n}}{n!}$，也在 $(-\infty,+\infty)$ 上成立。

$(3)$

已知 $\dfrac{1}{\sqrt{1+x}}=1+\sum\limits_{n=1}^\infty(-1)^n\dfrac{(2n-1)!!}{(2n)!!}x^n$，在 $x\in(-1,1]$ 上成立。

代入 $-2x$，得 $\dfrac1{\sqrt{1-2x}}=1+\sum\limits_{n=1}^\infty\dfrac{(2n-1)!!2^n}{(2n)!!}x^n$，在 $x\in[-\dfrac12,\dfrac12)$ 上成立。

两边同时乘 $x$，由于 $|x|\le 1$，所以得

$\dfrac{x}{\sqrt{1-2x}}=x+\sum\limits_{n=1}^\infty\dfrac{(2n-1)!!2^n}{(2n)!!}x^{n+1}$，在 $x\in[-\dfrac12,\dfrac12)$ 上成立。

代入 $x=\dfrac12$ 时，由于 $\dfrac{(2n-1)!!}{(2n)!!}=O(\dfrac1{\sqrt{n}})$，所以不收敛。

因此在 $[-\dfrac12,\dfrac12)$ 上成立。

$(5)$

$e^x=\sum\limits_{n=0}^\infty\dfrac{x^n}{n!}$，在 $(-\infty,+\infty)$ 上成立。

$\dfrac1{1-x}=1+\sum\limits_{n=1}^\infty x^n$，在 $(-1,1)$ 上成立。

相乘，通过计算柯西乘积可知

$$
\dfrac{e^x}{1-x}=1+\sum\limits_{n=1}^\infty(\sum\limits_{k=0}^n\dfrac1{k!})x^n
$$

容易发现 $\sum\limits_{k=0}^\infty\dfrac1{k!}=e$，所以收敛半径为 $1$.

代入 $x=\pm1$ 可知均不收敛，所以在 $(-1,1)$ 成立。

$(9)$

记和函数为 $f(x)$，则 $f'(x)=(1+x^2)^{-\frac12}$

展开可得

$$
f'(x)=1+\sum_{n=1}^\infty(-1)^n\dfrac{(2n-1)!!}{(2n)!!}x^{2n}
$$

在 $x\in[-1,1]$ 上成立。

逐项积分，得

$$
f(x)=x+\sum_{n=1}^\infty(-1)^n\dfrac{(2n-1)!!}{(2n)!!(2n+1)}x^{2n+1}
$$

当 $x\in[-1,1]$ 时成立。

> 3. 求下列函数在 $x=1$ 处的泰勒展开式：
>
> $(3)$ $f(x)=\sqrt{x^3}$

$(3)$

$$
\begin{aligned}
f(x)&=\sqrt{x^3}\\
&=(1+(x-1))^{\frac32}\\
&=1+\dfrac32(x-1)+\dfrac38(x-1)^2+\sum_{n=3}^\infty 3\times(-1)^n\dfrac{(2n-5)!!}{(2n)!!}(x-1)^n
\end{aligned}
$$

收敛域 $x-1\in[-1,1]$，即 $x\in[0,2]$

> 4. 求下列函数的麦克劳林级数：
>
> $(2)$ $x\arctan x-\ln\sqrt{1+x^2}$

$(2)$

已知 $\arctan x=\sum\limits_{n=0}^\infty(-1)^n\dfrac{x^{2n+1}}{2n+1},x\in[-1,1]$

并且 $\ln(1+x^2)=\sum\limits_{n=1}^\infty\dfrac{(-1)^{n-1}}{n}x^{2n},x\in[-1,1]$。

所以

$$
\begin{aligned}
x\arctan x-\ln\sqrt{1+x^2}&=x\arctan x-\dfrac12\ln(1+x^2)\\
&=\sum_{n=1}^\infty(-1)^{n-1}\dfrac{x^{2n}}{2n-1}-\dfrac12\sum_{n=1}^\infty\dfrac{(-1)^{n-1}}{n}x^{2n}\\
&=\sum_{n=1}^\infty(-1)^{n-1}\dfrac1{(2n-1)(2n)}x^{2n}
\end{aligned}
$$

$x\in[-1,1]$