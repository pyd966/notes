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

