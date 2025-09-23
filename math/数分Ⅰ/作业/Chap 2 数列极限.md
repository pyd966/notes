## 习题 2.1

> 2. 按 $\epsilon-N$ 定义证明：
>
> $(2)\ \lim\limits_{n\to\infty}\dfrac{3n^2+n}{2n^2-1}=\dfrac 32$

$\forall \epsilon>0$，取 $N=1+\lceil\dfrac 3{\epsilon}\rceil$，那么有 $N\ge 1$，故 $4n^2-2\ge n^2$，则当 $n>N$ 时，

$$
\begin{aligned}
\lvert\dfrac{2n^2+n}{2n^2-1}-\dfrac32\rvert&=\lvert\dfrac{2n+3}{4n^2-2}\rvert\\
&\le \lvert\dfrac{3n}{n^2}\rvert\\
&=\lvert\dfrac 3n\rvert\\
&=\dfrac 3n\\
&<\dfrac 3N\\
&<\dfrac 3{\frac 3\epsilon}\\
&=\epsilon
\end{aligned}
$$

由定义知，$\lim\limits_{n\to\infty}\dfrac{3n^2+n}{2n^2-1}=\dfrac 32$

> 5. 试用定义 $1'$ 证明：
>
> $(1)$ 数列 $\{\dfrac 1n\}$ 不以 $1$ 为极限。

取 $\epsilon=\dfrac 12>0$，当 $n>2$ 时 $0<\dfrac 1n<\dfrac 12$，则 $\lvert1-\dfrac1n\rvert>\dfrac 12$。

换言之，在 $U(1,\epsilon)$ 外的有无穷项，故 $\{\dfrac 1n\}$ 不以 $1$ 为极限。

> 9. 按 $\epsilon-N$ 定义证明：
>
> $(2)\ \lim\limits_{n\to\infty}\dfrac{1+2+3+\dots+n}{n^3}=0$

$\forall \epsilon>0$，取 $N=1+\lceil\dfrac 1\epsilon\rceil$，则 $N\ge 1$，当 $n>N$ 时，有

$$
\begin{aligned}
\lvert\dfrac{1+2+3+\dots+n}{n^3}-0\rvert&=\dfrac{(1+n)n}{2n^3}\\
&=\dfrac{n+1}{2n^2}\\
&\le\dfrac{2n}{2n^2}\\
&=\dfrac 1n\\
&<\dfrac 1N\\
&<\dfrac{1}{\frac1{\epsilon}}\\
&=\epsilon
\end{aligned}
$$

按定义 $\lim\limits_{n\to\infty}\dfrac{1+2+3+\dots+n}{n^3}=0$。