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

> 补充：
>
> 已知 $\lim\limits_{n\to\infty}a_n=a$，求证 $\lim\limits_{n\to\infty}\dfrac{a_1+a_2+\dots+a_n}{n}=a$。

直觉上来讲是挺对的，下面我们形式地证明一下子。

先感受一下整体思路。当我们取一个 $\epsilon$，可以得到一个 $n>N$ 时 $\lvert a_n-a\rvert<\epsilon$。换句话说，对于 $n$ 比较大的时候，我们对 $a_n$ 有估计；而对于 $n$ 比较小的时候，这些 $a_n$ 的和是一个常数，可以通过把 $N$ 调大来让这部分的影响降低。

上面没看懂也无所谓，我们下面写的才是真正的过程。

为了方便，我们记 $b_n=a_n-a$，那么 $\lim\limits_{n\to\infty}b_n=0$，我们要证明的，就是 $\lim\limits_{n\to\infty}\dfrac{b_1+b_2+\dots+b_n}{n}=0$。

$\forall \dfrac{\epsilon}2>0$，$\exist N_0$ 使得当 $n>N_0$ 时，$\lvert b_n\rvert<\dfrac{\epsilon}2$，也就是说

那么当 $n>N_0$ 时，我们把 $b_1+b_2+\dots+b_n$ 分成前 $N_0$ 个，以及剩下的 $n-N_0$ 个这两部分。

$$
\begin{aligned}
\lvert\dfrac{b_1+b_2+\dots+b_n}{n}-0\rvert&=\lvert\dfrac{b_1+b_2+\dots+b_{N_0}}{n}+\dfrac{b_{N_0+1}+\dots+b_n}{n}\rvert\\
&\le\lvert\dfrac{b_1+\dots+b_{N_0}}{n}\rvert+\lvert\dfrac{b_{N_0+1}+\dots+b_n}{n}\rvert\\
&\le\dfrac{\lvert b_1+\dots+b_{N_0}\rvert}{n}+\dfrac{|b_{N_0+1}|+\dots+|b_n|}{n}\\
&<\dfrac{\lvert b_1+\dots+b_{N_0}\rvert}{n}+\dfrac{(n-N_0)\frac{\epsilon}2}{n}
\end{aligned}
$$

我们想让 

$$
\dfrac{\lvert b_1+\dots+b_{N_0}\rvert}{n}+\dfrac{(n-N_0)\epsilon}{2n}\le \epsilon
$$

也就是说

$$
2\lvert b_1+\dots+b_{N_0}\rvert\le(n+N_0)\epsilon
$$

也就是

$$
n\ge \dfrac{2\lvert b_1+\dots+b_{N_0}\rvert}{\epsilon}-N_0
$$

令 $N_1=\lceil\dfrac{2|b_1+\dots+b_{N_0}|}{\epsilon}\rceil$，我们取 $N=\max\{N_0,N_1\}$，那么当 $n>N$ 的时候

$$
\lvert\dfrac{b_1+\dots+b_n-0}{n}\rvert<\epsilon
$$

按照极限的定义，我们证明了 $\lim\limits_{n\to\infty}\dfrac{b_1+\dots+b_n}{n}=0$。