## 习题 13.1

> 1. 讨论下列函数列在所示区间 $D$ 上是否一致连续或内闭一致收敛，并说明理由：
>
> $(2)$ $f_n(x)=\dfrac x{1+n^2x^2}$，$n=1,2,\dots$，$D=(-\infty,+\infty)$
>
> $(4)$ $f_n(x)=\dfrac xn$，$n=1,2,\dots$，$D=[0,+\infty)$

$(2)$

$\forall x,\lim\limits_{n\to\infty}f_n(x)=0$，所以 $\lim\limits_{n\to\infty} f_n=0$。

$f_n'(x)=\dfrac{1-n^2x^2}{(1+n^2x^2)^2}$，令 $f'_n(x)=0$ 知 $f_n(x)\le f_n(\dfrac1n)=\dfrac1{2n}$。

所以 $\lim\limits_{n\to\infty}\sup\limits_{x\in D}|f_n(x)-0|=\lim\limits_{n\to\infty}\dfrac1{2n}=0$，一致收敛。

$(4)$

$\forall x,\lim\limits_{n\to\infty}f_n(x)=0$，所以 $\lim\limits_{n\to\infty}f_n=0$。

取 $\epsilon_0=1$，则 $\forall N>0$，取 $n=N+1>N,x=N+2\in D$，则 $|f_n(x)-0|>\epsilon_0$，故不一致收敛。

在任意闭区间 $[a,b]\subseteq[0,+\infty)$ 上，$|f_n(x)-0|\le \dfrac bn\to0$，所以内闭一致收敛。

> 3. 判别下列函数项级数在所示区间上的一致收敛性：
>
> $(6)$ $\sum\dfrac{x^2}{(1+x^2)^{n-1}},x\in(-\infty,+\infty)$

$(6)$

记 $S_n=\sum\limits_{i=1}^n\dfrac{x^2}{(1+x^2)^{i-1}}=(1+x^2)(1-\dfrac1{(1+x^2)^{n-1}})$

所以对于每个给定的 $x$，考察 $\lim\limits_{n\to\infty}S_n=\begin{cases}1+x^2&,x\neq0\\1&,x=0\\\end{cases}$，记这个函数为 $f$。

考察 $\Delta_n(x)=|S_n(x)-f(x)|=\begin{cases}\dfrac{1}{(1+x^2)^{n-2}}&,x\neq0\\0&,x=0\end{cases}$。

对于任意区间 $[a,b]\subseteq(-\infty,+\infty)$，若 $0\in[a,b]$，

容易发现，取 $\epsilon_0=\dfrac12$，$\forall N>0$，取 $n=N+2>N,x=\min\{|b|,\sqrt{2^{\frac1n-1}}\}$，此时 $\Delta_n(x)\ge\epsilon_0$，所以不一致收敛，并且不内闭一致收敛。

> 4. 设函数项级数 $\sum u_n(x)$ 在 $D$ 上一致收敛于 $S(x)$，函数 $g(x)$ 在 $D$ 上有界。证明：级数 $\sum g(x)u_n(x)$ 在 $D$ 上一致收敛于 $g(x)S(x)$。

设 $|g(x)|\le M$，记 $S_n(x)$ 为 $\sum u_n(x)$ 的部分和，$T_n(x)$ 为 $\sum g(x)u_n(x)$ 的部分和。

由 $S_n(x)\rightrightarrows S(x)$ 知 $\forall\epsilon>0,\exist N>0,\forall n>N,x\in D,|S_n(x)-S(x)|<\epsilon$。

此时，考察 $|T_n(x)-g(x)S(x)|=|g(x)||S_n(x)-S(x)|<M\epsilon$，所以 $\sum g(x)u_n(x)$ 一致收敛于 $g(x)S(x)$。

> 6. 设 $u_n(x)$ $(n=1,2,\dots)$ 是 $[a,b]$ 上的单调函数，证明：若 $\sum u_n(a)$ 与 $\sum u_n(b)$ 都绝对收敛，则 $\sum u_n(x)$ 在 $[a,b]$ 上绝对且一致收敛。

记 $v_n(x)=|u_n(x)|$，记 $c_n=\max\{v_n(a),v_n(b)\}$，则 $0\le v_n(x)\le c_n$，且由题知 $\sum v_n(a),\sum v_n(b)$ 分别收敛，则 $\sum c_n$ 也收敛。

只需证 $\sum v_n(x)$ 一致收敛。

由魏尔斯特拉斯判别法，显然成立。