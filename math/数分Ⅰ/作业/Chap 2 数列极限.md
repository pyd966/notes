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

> 10. 设 $a_n\neq0$，证明：$\lim\limits_{n\to\infty}a_n=0$ 的充要条件是 $\lim\limits_{n\to\infty}\dfrac1{a_n}=\infty$。

先证充分性：

由 $\lim\limits_{n\to\infty}\dfrac1{a_n}=\infty$，我们知道 $\forall M>0,\exist N>0,\forall n>N,\dfrac{1}{|a_n|}>M$，也就是 $|a_n|<\dfrac1M$。

所以 $\forall\epsilon>0，取 M=\dfrac1\epsilon$，我们可以得到 $n>N$ 时 $|a_n|<\epsilon$，所以 $\lim\limits_{n\to\infty}a_n=0$。

再证必要性：

懒得写了，上面的过程都是等价的，倒过来写一遍就行了。

## 习题 2.2

> 1. 求下列极限：
> 
> $(2)\lim\limits_{n\to\infty}\dfrac{1+2n}{n^2}$
>
> $(4)\lim\limits_{n\to\infty}(\sqrt{n^2+n}-n)$
>
> $(6)\lim\dfrac{\frac12+\frac1{2^2}+\dots+\frac1{2^n}}{\frac13+\frac1{3^2}+\dots+\frac1{3^n}}$

$(2)$ 由于 $\lim\limits_{n\to\infty}\dfrac1{n^2}=0,\lim\limits_{n\to\infty}\dfrac{2n}{n^2}=2\lim\limits_{n\to\infty}\dfrac1n=2\times0=0$，

故 $\lim\limits_{n\to\infty}\dfrac{1+2n}{n^2}=(\lim\limits_{n\to\infty}\dfrac1{n^2})+(\lim\limits_{n\to\infty}\dfrac{2n}{n^2})=0+0=0$。

$(4)$ $\lim\limits_{n\to\infty}(\sqrt{n^2+n}-n)=\lim\limits_{n\to\infty}\dfrac{(\sqrt{n^2+n}-n)(\sqrt{n^2+n}+n)}{\sqrt{n^2+n}+n}=\lim\limits_{n\to\infty}\dfrac{n}{\sqrt{n^2+n}+n}=\lim\limits_{n\to\infty}\dfrac1{\sqrt{1+\frac1n}+1}$。

而 $\lim\limits_{n\to\infty}(\sqrt{1+\frac1n}+1)=1+\lim\limits_{n\to\infty}\sqrt{1+\frac1n}=1+\sqrt{\lim\limits_{n\to\infty}(1+\frac1n)}=1+\sqrt{1}=2$，

故 $\lim\limits_{n\to\infty}(\sqrt{n^2+n}-n)=\lim\limits_{n\to\infty}\dfrac1{\sqrt{1+\frac1n}+1}=\dfrac12$。

$(6)$ $\lim\limits_{n\to\infty}\dfrac{\frac12+\frac1{2^2}+\dots+\frac1{2^n}}{\frac13+\frac1{3^2}+\dots+\frac1{3^n}}=\lim\limits_{n\to\infty}\dfrac{\dfrac12\times\dfrac{1-(\frac12)^n}{1-\frac12}}{\dfrac13\times\dfrac{1-(\frac13)^n}{1-\frac13}}=\lim\limits_{n\to\infty}2\times\dfrac{1-(\frac12)^n}{1-(\frac13)^n}$。

而 $\lim\limits_{n\to\infty}(1-(\frac12)^n)=1-\lim\limits_{n\to\infty}(\frac12)^n=1-0=1$，同理 $\lim\limits_{n\to\infty}(1-(\frac13)^n)=1$。

故 所求式 $=\lim\limits_{n\to\infty}2\times\dfrac{1-(\frac12)^n}{1-(\frac13)^n}=2\times\dfrac{\lim\limits_{n\to\infty}(1-(\frac12)^n)}{\lim\limits_{n\to\infty}(1-(\frac13)^n)}=2\times\dfrac11=2$。

> 3. 求下列极限：
>
> $(3)\lim\limits_{n\to\infty}(\dfrac12+\dfrac3{2^2}+\dots+\dfrac{2n-1}{2^n})$
>
> $(5)\lim\limits_{n\to\infty}(\dfrac1{n^2}+\dfrac1{(n+1)^2}+\dots+\dfrac1{(2n)^2})$
>
> $(6)\lim\limits_{n\to\infty}(\dfrac1{\sqrt{n^2+1}}+\dfrac1{\sqrt{n^2+2}}+\dots+\dfrac1{\sqrt{n^2+n}})$

$(3)$ 当 $n\ge3$ 时，

$$
\begin{aligned}
原式&=\lim\limits_{n\to\infty}((\dfrac12+\dots+\dfrac1{2^n})+2\times(\dfrac1{2^2}+\dots+\dfrac1{2^n})+2\times(\dfrac1{2^3}+\dots+\dfrac1{2^n})+\dots+2\times(\dfrac1{2^n}))\\
&=\lim\limits_{n\to\infty}((1-\dfrac1{2^n})+2\times(\dfrac12-\dfrac1{2^n})+2\times(\dfrac1{2^2}-\dfrac1{2^n})+\dots+2\times(\dfrac1{2^{n-1}}-\dfrac1{2^n}))\\
&=\lim\limits_{n\to\infty}((1+1+\dfrac12+\dots+\dfrac1{2^{n-2}})-\dfrac{2n-1}{2^n})\\
&=\lim\limits_{n\to\infty}(3-\dfrac1{2^{n-2}}-\dfrac{2n-1}{2^n})\\
&=\lim\limits_{n\to\infty}(3-\dfrac{2n+3}{2^n})
\end{aligned}
$$

当 $n\ge 3$ 时，$2^n=(1+1)^n\ge\binom n0+\binom n1+\binom n2>0+n+\dfrac{n(n-1)}2>\dfrac{n^2}2,2n+3\le 3n$。

故 $\forall\epsilon>0$，取 $N=\lceil\dfrac6\epsilon\rceil+3$，则

$$
|\dfrac{2n+3}{2^n}-0|=\dfrac{2n+3}{2^n}<\dfrac{3n}{\frac{n^2}2}=\dfrac6n<\dfrac6N\le\dfrac6{\frac6\epsilon}=\epsilon
$$

由定义，$\lim\limits_{n\to\infty}\dfrac{2n+3}{2^n}=0$。

故 所求式 $=3-\lim\limits_{n\to\infty}\dfrac{2n+3}{2^n}=3-0=3$。

$(5)$ 当 $n\ge 2$ 时，

$$
\dfrac1{n^2}+\dots+\dfrac1{(2n)^2}<\dfrac1{(n-1)n}+\dots+\dfrac1{(2n-1)(2n)}=\dfrac1{n-1}-\dfrac1{2n}=\dfrac{n+1}{2n(n-1)}\le\dfrac{2n}{2n(n-1)}=\dfrac1{n-1}
$$

$$
\dfrac1{n^2}+\dots+\dfrac1{(2n)^2}>\dfrac1{n(n+1)}+\dots+\dfrac1{(2n)(2n+1)}=\dfrac1n-\dfrac1{2n+1}=\dfrac{n+1}{n(2n+1)}>\dfrac{n+1}{n(2n+2)}=\dfrac1{2n}
$$

而 $\lim\limits_{n\to\infty}\dfrac1{n-1}=0=\lim\limits_{n\to\infty}\dfrac1{2n}$，

由夹逼定理，$\lim\limits_{n\to\infty}(\dfrac1{n^2}+\dots+\dfrac1{(2n)^2})=0$。

$(6)$

$$
\dfrac1{\sqrt{n^2+1}}+\dots+\dfrac1{\sqrt{n^2+n}}<n\cdot\dfrac1{\sqrt{n^2}}=1
$$

$$
\dfrac1{\sqrt{n^2+1}}+\dots+\dfrac1{\sqrt{n^2+n}}>n\cdot\dfrac1{\sqrt{n^2+n}}=\dfrac1{\sqrt{1+\frac1n}}
$$

由于 $\lim\limits_{n\to\infty}(1+\dfrac1n)=1$，所以 $\lim\limits_{n\to\infty}\sqrt{1+\frac1n}=\sqrt{\lim\limits_{n\to\infty}(1+\frac1n)}=1$，所以 $\lim\limits_{n\to\infty}\dfrac1{\sqrt{1+\frac1n}}=1$。

由夹逼定理，$\lim\limits_{n\to\infty}(\dfrac1{\sqrt{n^2+1}}+\dots+\dfrac1{\sqrt{n^2+n}})=1$。

> 5. 证明以下数列发散：
>
> $(1)\ \{(-1)^n\dfrac n{n+1}\}$
>
> $(2)\ \{n^{(-1)^n}\}$

$(1)$

考察这个数列的奇数项构成的子列：$\{(-1)^{2k-1}\dfrac{2k-1}{2k}\}$，即 $\{-1+\dfrac1{2k}\}$。

由于 $\lim\limits_{k\to\infty}\dfrac1{2k}=0$，故 $\lim\limits_{k\to\infty}(-1+\dfrac1{2k})=-1$，这个子列收敛于 $-1$.

考虑偶数项构成的子列：$\{(-1)^{2k}\dfrac{2k}{2k+1}\}$，类似地，可以证明这个子列收敛于 $1$。

$-1\neq1$，所以原数列发散。

$(2)$

考察这个数列的偶数项构成的子列：$\{(2k)^{(-1)^{2k}}\}=\{2k\}=\{b_k\}$。

若这个子列是收敛的，那么我们知道它是有界的，设界为 $M$，则 $|b_k|\le M$。

然而，取 $k=M+1$，我们有 $|b_k|=|2M+2|=2M+2>M$，所以假设不成立，这个子列是发散的。

所以原数列也是发散的。

> 7. 求以下极限：
>
> $(1)\lim\limits_{n\to\infty}\dfrac12\cdot\dfrac34\cdot\dots\cdot\dfrac{2n-1}{2n}$
>
> $(3)\lim\limits_{n\to\infty}((n+1)^\alpha-n^\alpha),0<\alpha<1$

$(1)$


设 $E_n=\dfrac12\cdot\dfrac34\cdot\dots\cdot\dfrac{2n-1}{2n},O_n=\dfrac23\cdot\dfrac45\cdot\dots\cdot\dfrac{2n}{2n+1}$，所以 $O_n\cdot E_n=\dfrac1{2n+1}$。

显然 $0<E_n\le\dfrac12,0<O_n\le\dfrac23$，又 $E_n,O_n$ 都是单调减的，所以 $E_n,O_n$ 的极限存在，不妨记 $\alpha=\lim\limits_{n\to\infty}E_n,\beta=\lim\limits_{n\to\infty}O_n$。

对 $O_n\cdot E_n=\dfrac1{2n+1}$ 两边同时取极限，可以得到 $\lim\limits_{n\to\infty}(O_n\cdot E_n)=0$，即 $\alpha\beta=0$。

而可以发现 $0<E_n<O_n$，由保不等式性，$0\le\alpha\le\beta$。

若 $\alpha\neq0$，则 $\alpha\beta>0$，矛盾，故 $\alpha=0$。

即 $\lim\limits_{n\to\infty}E_n=0$。

$(3)$

使用牛顿二项式定理，
$$
\begin{aligned}
(n+1)^\alpha-n^\alpha&=(\sum_{k\in N}\binom \alpha kn^{\alpha-k})-n^\alpha\\
&=\sum_{k\ge1}\binom{\alpha}{k}n^{\alpha-k}\\
&\le n^\alpha\sum_{k\ge1}\lvert\binom\alpha k\rvert\cdot\dfrac1{n^k}\\
&=n^\alpha\sum_{k\ge1}\dfrac{|\alpha(\alpha-1)\cdots(\alpha-k+1)|}{k!n^k}
\end{aligned}
$$

设 $b_k=\dfrac{|\alpha(\alpha-1)\cdots(\alpha-k+1)|}{k!n^k}>0$，则 $\dfrac{b_{k+1}}{b_k}=\dfrac{|(\alpha-k)|}{(k+1)n}$。

而 $\alpha-k\in(-k,1-k)$，故 $|\alpha-k|<k$。

所以 $\dfrac{b_{k+1}}{b_k}<\dfrac{k}{(k+1)n}<\dfrac1n$，并且 $b_1=\dfrac{|\alpha|}{n}<\dfrac1n$

那么，

$$
\begin{aligned}
|(n+1)^\alpha-n^\alpha-0|&\le n^\alpha\sum_{k\ge1}b_k\\
&<n^\alpha\sum_{k\ge1}b_1(\dfrac{1}{n})^{k-1}\\
&<n^\alpha\sum_{k\ge1}(\dfrac1n)^k\\
&=n^\alpha\times\dfrac1n\times\dfrac{1}{1-\frac1n}\\
&=\dfrac{n^\alpha}{n-1}\\
&=\dfrac{n^{\alpha-1}}{1-\frac1n}
\end{aligned}
$$

而 $\alpha-1<0$，故 $\lim\limits_{n\to\infty}n^{\alpha-1}=0,\lim\limits_{n\to\infty}(1-\frac1n)=1$，所以 $\lim\limits_{n\to\infty}\dfrac{n^{\alpha-1}}{1-\frac1n}=0$。

又，$(n+1)^\alpha-n^\alpha>0$。

所以 $\lim\limits_{n\to\infty}(n+1)^\alpha-n^\alpha=0$。

> 9. 设 $\lim\limits_{n\to\infty}a_n=a$，证明：
>
> $(2)$ 若 $a>0,a_n>0$，则 $\lim\limits_{n\to\infty}\sqrt[n]{a_n}=1$

设 $\sqrt[n]{a_n}-1=t$，则 $a_n=(1+t)^n$。

考虑到，$a_n=(1+t)^n\ge 1+nt$，所以 $t\le\dfrac{a_n-1}{n}$

考虑到 $|a_n|\le M$，也就是说 $0<a_n\le M$，所以 $t\le\dfrac{a_n-1}{n}\le\dfrac{M-1}{n}$

取 $N=\lceil\dfrac{M-1}{\epsilon}\rceil+1$ 即可。

规范写一下。

当 $a>1$ 时，由保号性，$\exist N_0,\forall n>N_0,a_n>1$。下面均在 $n>N_0$ 意义下讨论。

设 $\sqrt[n]{a_n}-1=t>0$，则 $a_n=(1+t)^n$。

考虑到，$a_n=(1+t)^n\ge 1+nt$，故 $t\le\dfrac{a_n-1}n$。

$\forall\epsilon>0$，取 $N_1=\lceil\dfrac{M-1}\epsilon\rceil+1,N=\max\{N_0,N_1\}$。

则当 $n>N$ 时，可以得到

$$
t\le\dfrac{a_n-1}{n}\le\dfrac{M-1}n<\dfrac{M-1}N<\dfrac{M-1}{\frac{M-1}\epsilon}=\epsilon
$$

因此，我们可以得到 $\lim\limits_{n\to\infty}t=0$。

所以 $\lim\limits_{n\to\infty}(\sqrt[n]{a_n})=\lim\limits_{n\to\infty}(t+1)=1+\lim\limits_{n\to\infty}t=1+0=1$。

当 $a=1$ 时，

$\forall\epsilon>0,\exist N_0$，当 $n>N_0$ 时有 $|a_n-1|<\epsilon$。

当 $n>N_0$ 时，$|t|\le\dfrac{|a_n-1|}{n}<\dfrac{\epsilon}{n}<\dfrac\epsilon{N_0}<\epsilon$，所以 $\lim\limits_{n\to\infty}t=0$，则 $\lim\limits_{n\to\infty}\sqrt[n]{a_n}=1$。

当 $0<a<1$ 时，$\lim\limits_{n\to\infty}\dfrac1{a_n}=\dfrac1a>1$。

$$
\lim_{n\to\infty}\sqrt[n]{a_n}=\lim_{n\to\infty}\dfrac1{\sqrt[n]{\frac1{a_n}}}=\dfrac1{\lim\limits_{n\to\infty}\sqrt[n]{\frac1{a_n}}}=\dfrac11=1
$$

综上，$\lim\limits_{n\to\infty}\sqrt[n]{a_n}=1$。

## 习题 2.3

> 1. 利用 $\lim\limits_{n\to\infty}(1+\dfrac1n)^n=e$ 求下列极限。
>
> $(4)\ \lim\limits_{n\to\infty}(1+\dfrac1{2n})^n$
>
> $(5)\ \lim\limits_{n\to\infty}(1+\dfrac1{n^2})^n$

$(4)$

$$
\begin{aligned}
\lim\limits_{n\to\infty}(1+\dfrac1{2n})^n=\lim\limits_{n\to\infty}((1+\dfrac1{2n})^{2n})^{\frac12}=(\lim\limits_{n\to\infty}(1+\dfrac1{2n})^{2n})^\frac12
\end{aligned}
$$

而由 $\lim\limits_{n\to\infty}(1+\frac1n)^n=e$ 可知 $\forall\epsilon>0,\exist N>0,\forall n>N,|(1+\dfrac1n)^n-e|<\epsilon$，所以取 $N_1=\frac N2$，我们有 $n>N_1$ 时，$|(1+\dfrac1{2n})^{2n}-e|<\epsilon$，根据定义，$\lim\limits_{n\to\infty}(1+\dfrac1{2n})^{2n}=e$。

所以 $\lim\limits_{n\to\infty}(1+\dfrac1{2n})^n=\sqrt{e}$。

$(5)$

记 $a_n=(1+\dfrac1n)^n,b_n=(1+\dfrac1{n^2})^n$，所以有 $a_{n^2}=b_n^n$，也就是说 $b_n=\sqrt[n]{a_{n^2}}$。

由于 $\lim\limits_{n\to\infty}a_{n^2}=\lim\limits_{n\to\infty}a_n=e>1$，所以 $\lim\limits_{n\to\infty}\sqrt[n]{a_{n^2}}=1$，我们知道 $\lim\limits_{n\to\infty}b_n=1$。

> 5. 应用柯西收敛准则，证明以下数列 $\{a_n\}$ 收敛：
>
> $(1)\ a_n=\dfrac{\sin 1}2+\dfrac{\sin 2}{2^2}+\dots+\dfrac{\sin n}{2^n}$

$(1)$

$\forall\epsilon>0$，取 $N=\max\{1,\lceil\log_2(\dfrac1\epsilon)\rceil\}+1$

当 $n,m>N$ 时，不妨令 $n\le m$，有 

$$
\begin{aligned}
|a_n-a_m|&=|\dfrac{\sin m}{2^m}+\dfrac{\sin(m-1)}{2^{m-1}}+\dots+\dfrac{\sin (n+1)}{2^{n+1}}|\\
&\le|\dfrac{\sin m}{2^m}|+|\dfrac{\sin(m-1)}{2^{m-1}}|+\dots+|\dfrac{\sin (n+1)}{2^{n+1}}|\\
&\le\dfrac1{2^m}+\dfrac1{2^{m-1}}+\dots+\dfrac1{2^{n+1}}\\
&=\dfrac1{2^n}-\dfrac1{2^m}\\
&<\dfrac1{2^n}\\
&\le\dfrac1{2^N}\\
&<\dfrac1{2^{\log_2(\frac1\epsilon)}}\\
&=\epsilon
\end{aligned}
$$

由柯西收敛准则，该数列收敛。

> 11. 给定两正数 $a_1>b_1$，作出其等差中项 $a_2=\dfrac{a_1+b_1}2$ 与等比中项 $b_2=\sqrt{a_1b_1}$，一般地令 $a_{n+1}=\dfrac{a_n+b_n}2,b_{n+1}=\sqrt{a_nb_n}$。证明：$\lim\limits_{n\to\infty}a_n$ 与 $\lim\limits_{n\to\infty}b_n$ 存在且相等。

由均值不等式直接得到 $a_n\ge b_n$，若 $a_n=b_n$，根据取等条件，需要 $a_{n-1}=b_{n-1}$，由数学归纳法可以证明这是不可能的，所以 $a_n>b_n$。

那么 $a_{n+1}=\dfrac{a_n+b_n}2<\dfrac{a_n+a_n}2=a_n$，$b_{n+1}=\sqrt{a_nb_n}>\sqrt{b_n\cdot b_n}=b_n$。

所以 $\{a_n\}$ 是递减数列，并且 $a_n>b_n>b_{n-1}>\dots>b_1$，所以有下界 $b_1$。根据单调有界定理，$\lim\limits_{n\to\infty}a_n$ 存在，记为 $A$。

同理 $\{b_n\}$ 递增有上界，极限存在记为 $B$。

对 $a_{n+1}=\dfrac{a_n+b_n}2$ 两边同时取极限，得到 $A=\dfrac{A
"+B}2$，化简得到 $A=B$，即 $\lim\limits_{n\to\infty}a_n=\lim\limits_{n\to\infty}b_n$。

## 第二章练习题

> 5. 应用上题的结论证明下列各题：
>
> $(3)\lim\limits_{n\to\infty}\sqrt[n]{n}=1$
>
> $(5)\lim\limits_{n\to\infty}\dfrac n{\sqrt[n]{n!}}=e$
>
> $(7)$ 若 $\lim\limits_{n\to\infty}\dfrac{b_{n+1}}{b_n}=a(b_n>0)$ 则 $\lim\limits_{n\to\infty}\sqrt[n]{b_n}=a$

$(3)$

取 $a_n=\begin{cases}1,n=1\\\dfrac n{n-1},n\ge 2\end{cases}$，则显然 $\lim\limits_{n\to\infty}a_n=1$。

由上题结论，$\lim\limits_{n\to\infty}\sqrt[n]{n}=\lim\limits_{n\to\infty}\sqrt[n]{a_1\cdot a_2\cdot\dots\cdot a_n}=1$。

$(5)$

考虑取对数，记 $a_n=\dfrac{n}{\sqrt[n]{n!}},b_n=\ln a_n=\dfrac{n\ln n-(\ln1+\ln2+\dots+\ln n)}n$。

取 $c_n=n\ln n-(\ln1+\ln2+\dots+\ln n),d_n=n$，应用 Scolt 定理，为计算 $\lim\limits_{n\to\infty}b_n$，只需计算 $\lim\limits_{n\to\infty}\dfrac{c_n-c_{n-1}}{d_n-d_{n-1}}=\lim\limits_{n\to\infty}\dfrac{(n-1)\ln(1+\dfrac1{n-1})}{1}=\lim\limits_{n\to\infty}n\ln(1+\dfrac1n)$。

我们知道 $\lim\limits_{n\to\infty}(1+\dfrac1n)^n=e$，取对数，可以得到 $\lim\limits_{n\to\infty}n(1+\dfrac1n)=1$。

所以 $\lim\limits_{n\to\infty}b_n=1$，$\lim\limits_{n\to\infty}a_n=e$。

$(7)$

取 $a_n=\begin{cases}b_1,n=1\\\dfrac{b_{n}}{b_{n-1}},n\ge2\end{cases}$，则 $\lim\limits_{n\to\infty}a_n=a,b_n=a_1\cdot a_2\cdot\dots\cdot a_n$。

则 $\lim\limits_{n\to\infty}\sqrt[n]{b_n}=\lim\limits_{n\to\infty}\sqrt[n]{a_1\cdot a_2\dots\cdot a_n}=a$。

> 6. 证明：若 $\{a_n\}$ 为递增数列，$\{b_n\}$ 为递减数列，且 $\lim\limits_{n\to\infty}(a_n-b_n)=0$，则 $\lim\limits_{n\to\infty}a_n$ 与 $\lim\limits_{n\to\infty}b_n$ 都存在且相等。

取 $\epsilon_0=1$，则 $\exist N,\forall n>N,|a_n-b_n|<\epsilon_0=1$，即 $a_n-b_n<1$，即 $a_n<b_n+1\le b_{n-1}+1\le\dots\le  b_1+1$，所以 $\{a_n\}$ 递增有上界，极限存在记为 $A$。

同理，$b_n$ 递减有下界，极限存在记为 $B$。

$0=\lim\limits_{n\to\infty}(a_n-b_n)=\lim\limits_{n\to\infty}a_n-\lim\limits_{n\to\infty}b_n=A-B$，所以 $A=B$。