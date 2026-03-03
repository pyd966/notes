## 习题 12.1

> 1. 证明下列级数收敛，并求其和：
>   
> $(2)$ $(\dfrac12+\dfrac13)+(\dfrac1{2^2}+\dfrac1{3^2})+\dots+(\dfrac1{2^n}+\dfrac1{3^n})+\dots$
> 
> $(4)$ $\sum\limits_{n=1}^{\infty}(\sqrt{n+2}-2\sqrt{n+1}+\sqrt{n})$

$(2)$

考虑数列 $a_n=\dfrac1{2^n}$ 和 $b_n=\dfrac1{3^n}$，容易证明 $\sum a_n=1,\sum b_n=\dfrac12$。

原式 $=\sum(a_n+b_n)=\sum a_n+\sum b_n=\dfrac32$。

$(4)$

考虑其前缀和 $S_n$

$$
\begin{aligned}
S_n&=(\sqrt3-2\sqrt2+\sqrt1)+(\sqrt4-2\sqrt3+\sqrt2)+(\sqrt5-2\sqrt4+\sqrt3)+\dots+(\sqrt{n+2}-2\sqrt{n+1}+\sqrt n)\\
&=\sqrt1-\sqrt2-\sqrt{n+1}+\sqrt{n+2}\\
&=1-\sqrt{2}+\dfrac{1}{\sqrt{n+2}+\sqrt{n+1}}\\
\end{aligned}
$$

则 $\lim\limits_{n\to\infty}S_n=1-\sqrt2$。

> 5. 证明：若数列 $\{b_n\}$ 有 $\lim\limits_{n\to\infty}b_n=\infty$，则：
>
> $(1)$ 级数 $\sum(b_{n+1}-b_n)$ 发散；
>
> $(2)$ 当 $b_n\neq0$ 时，级数 $\sum(\dfrac1{b_n}-\dfrac1{b_{n+1}})=\dfrac1{b_1}$。

$(1)$

考察前缀和 $S_n=(b_2-b_1)+(b_3-b_2)+\dots+(b_{n+1}-b_n)=b_{n+1}-b_1$。

则 $\lim\limits_{n\to\infty}S_n=\infty$，所以该级数发散。

$(2)$

考察前缀和 $T_n=(\dfrac1{b_1}-\dfrac1{b_2})+(\dfrac1{b_2}-\dfrac1{b_3})+\dots+(\dfrac1{b_n}-\dfrac1{b_{n+1}})=\dfrac1{b_1}-\dfrac1{b_{n+1}}$

则 $\lim\limits_{n\to\infty} T_n=\dfrac1{b_1}$，级数收敛。

> 7. 应用柯西准则判别下列级数的敛散性：
>
> $(1)$ $\sum\dfrac{\sin 2^n}{2^n}$
>
> $(2)$ $\sum\dfrac{(-1)^{n-1}n^2}{2n^2+1}$

$(1)$

$\forall\epsilon>0$，取 $N=1+\max\{0,-\log_2\epsilon\}$，当 $m>n>N$ 时，有

$$
\begin{aligned}
|\dfrac{\sin 2^n}{2^n}+\dots+\dfrac{\sin 2^m}{2^m}|&\le|\dfrac{\sin2^n}{2^n}|+\dots+|\dfrac{\sin2^m}{2^m}|\\
&\le\dfrac1{2^n}+\dots+\dfrac1{2^m}\\
&=\dfrac1{2^{n-1}}-\dfrac1{2^m}\\
&<\dfrac1{2^{n-1}}<\dfrac1{2^{N-1}}\le\epsilon
\end{aligned}
$$

由柯西准则，该级数收敛。

$(2)$

取 $\epsilon_0=\dfrac13$，$\forall N>0$，取 $m=n=\max\{N,1\}$

$$
|\dfrac{(-1)^{n-1}n^2}{2n^2+1}|=|\dfrac12-\dfrac{1}{4n^2+2}|\ge|\dfrac12-\dfrac16|=\dfrac13=\epsilon_0
$$

由柯西准则，该级数发散。

## 习题 12.2

> 1. 应用比较原则判别下列级数的敛散性：
>
> $(1)$ $\sum\dfrac1{n^2+a^2}$；
>
> $(3)$ $\sum\dfrac1{\sqrt{1+n^2}}$

$(1)$

$\sum\dfrac1{n^2+a^2}\le\sum\dfrac1{n^2}$

因为级数为正项级数，并且 $\sum\dfrac1{n^2}$ 收敛，所以原级数也收敛。

$(3)$

$\sum\dfrac1{\sqrt{1+n^2}}\ge\sum\dfrac1{\sqrt{1+2n+n^2}}=\sum\dfrac1{1+n}$

因为级数为正项级数，并且 $\sum\dfrac1{1+n}$ 发散，所以原级数也发散。