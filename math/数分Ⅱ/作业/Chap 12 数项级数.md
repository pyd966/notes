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
>
> $(5)$ $\sum(1-\cos\dfrac1n)$
>
> $(8)$ $\sum\limits_{n=2}^\infty\dfrac{n}{(\ln n)^{\ln n}}$

$(1)$

$\sum\dfrac1{n^2+a^2}\le\sum\dfrac1{n^2}$

因为级数为正项级数，并且 $\sum\dfrac1{n^2}$ 收敛，所以原级数也收敛。

$(3)$

$\sum\dfrac1{\sqrt{1+n^2}}\ge\sum\dfrac1{\sqrt{1+2n+n^2}}=\sum\dfrac1{1+n}$

因为级数为正项级数，并且 $\sum\dfrac1{1+n}$ 发散，所以原级数也发散。

$(5)$

$1-\cos\dfrac1n=\dfrac{1}{2n^2}+o(\dfrac1{n^3})$

所以 $\lim\limits_{n\to\infty}\dfrac{1-\cos\frac1n}{\frac1{n^2}}=\dfrac12$，而 $\sum\dfrac1{n^2}$ 收敛，所以原级数收敛。

$(8)$

$$
\dfrac{n}{(\ln n)^{\ln n}}=\dfrac{n}{e^{\ln n\ln\ln n}}=\dfrac{n}{n^{\ln\ln n}}
$$

当 $n\ge e^{e^3}$ 时，$\dfrac{n}{(\ln n)^{\ln n}}\le\dfrac1{n^2}$

而 $\sum\dfrac1{n^2}$ 收敛，所以原级数收敛。

> 2. 用比式判别法或根式判别法讨论下列级数的收敛性：
>
> $(1)$ $\sum\dfrac{1\cdot 3\cdot\dots\cdot(2n-1)}{n!}$
>
> $(3)$ $\sum(\dfrac{n}{2n+1})^n$
>
> $(4)$ $\sum\dfrac{n!}{n^n}$

$(1)$

记通项为 $a_n$，则 $\lim\limits_{n\to\infty}\dfrac{a_{n+1}}{a_n}=\lim\limits_{n\to\infty}\dfrac{2n+1}{n+1}=2>1$，所以原级数发散。

$(3)$

记通项为 $a_n$，则 $\lim\limits_{n\to\infty}\sqrt[n]{a_n}=\lim\limits_{n\to\infty}\dfrac n{2n+1}=\dfrac12<1$，所以原级数收敛。

$(4)$

记通项为 $a_n$，则 $\lim\limits_{n\to\infty}\dfrac{a_{n+1}}{a_n}=\lim\limits_{n\to\infty}(\dfrac{n}{n+1})^n=\dfrac1e<1$，所以原级数收敛。

> 3. 设 $\sum u_n$ 和 $\sum v_n$ 为正项级数，且存在正数 $N_0$，对一切 $n>N_0$，有
>
> $$
> \dfrac{u_{n+1}}{u_n}\le\dfrac{v_{n+1}}{v_n}
> $$
>
> 证明：若级数 $\sum v_n$ 收敛，则级数 $\sum u_n$ 也收敛；若 $\sum u_n$ 发散，则 $\sum v_n$ 也发散。

命题前后部分等价，下证前半部分。

$\forall n>N_0, u_n=u_{N_0+1}\cdot\prod\limits_{i=N_0+1}^{n-1}\dfrac{u_{i+1}}{u_i}\le u_{N_0+1}\cdot\prod\limits_{i=N_0+1}^{n-1}\dfrac{v_{i+1}}{v_i}=\dfrac{u_{N_0+1}}{v_{N_0+1}}\cdot v_n$

记 $u_n$ 前缀和为 $S_n$，$v_n$ 前缀和为 $T_n$，$\sum v_n=T$。

所以 $\forall n>N_0$，$S_n\le S_{N_0}+\dfrac{u_{N_0+1}}{v_{N_0+1}}\cdot(T_n-T_{N_0})\le S_{N_0}+\dfrac{u_{N_0+1}}{v_{N_0+1}}\cdot(T-T_{N_0})$

所以 $S_n$ 有上界且递增，故 $\sum u_n$ 收敛。

> 4. 设正项级数 $\sum a_n$ 收敛，证明 $\sum a_n^2$ 也收敛；试问反之是否成立？

由 $\sum a_n$ 收敛可知 $\lim\limits_{n\to\infty} a_n=0$，因此取 $\epsilon_0=1$，那么 $\exist N>0$，当 $n>N_0$ 时有 $0<a_n<\epsilon_0=1$。

记 $a_n$ 前缀和为 $S_n$，$a_n^2$ 前缀和为 $T_n$，$\sum a_n=S$。

所以当 $n>N_0$ 时，$T_n=T_{N_0}+\sum\limits_{i=N_0+1}^n a_n^2<T_{N_0}+\sum\limits_{i=N_0+1}^na_n=T_{N_0}+S_n-S_{N_0}\le T_{N_0}+S-S_{N_0}$。

所以 $T_n$ 有界且单增，极限存在，$\sum a_n^2$ 收敛。

反之不成立，例如取 $a_n=\dfrac1n$，则 $\sum a_n$ 不收敛，但是 $\sum a_n^2$ 收敛。

> 6. 设级数 $\sum a_n^2$ 收敛，证明： $\sum\dfrac{a_n}n(a_n>0)$ 也收敛。

记 $a_n^2$ 前缀和为 $S_n$，$\dfrac{a_n}{n}$ 前缀和为 $T_n$，$\dfrac1{n^2}$ 前缀和为 $R_n$。易知 $S_n,R_n$ 收敛，设收敛于 $S,R$。

则由柯西不等式，$T_n^2\le S_n\cdot R_n\le S\cdot R$。

所以 $T_n$ 有上界且单增，故 $T_n$ 收敛。

> 9. 用积分判别法讨论的列级的敛散性：
>
> $(3)$ $\sum\limits_{n=1}^\infty\dfrac{n}{e^{\sqrt n}}$

$(3)$

记 $f(x)=\dfrac{x}{e^{\sqrt{x}}}$，则 $f'(x)=\dfrac{1-\frac12\sqrt x}{e^{\sqrt x}}$，当 $x$ 充分大时，$f'(x)<0$，$f(x)$ 单调减。

考察 $\int_1^{+\infty}f(x)dx$。

记 $t=\sqrt{x}$，则

$$
\int_1^{+\infty}f(x)dx=\int_1^{+\infty}\dfrac{2t^3}{e^t}dt=\left.(-\dfrac{2t^3+6t^2+12t+12}{e^t})\right|_1^{+\infty}=\dfrac{32}e
$$

所以原级数收敛。