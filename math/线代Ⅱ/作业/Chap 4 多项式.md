## 习题 4

> 6. 设 $p\in P(C)$ 的次数为 $m$。证明 $p$ 有 $m$ 个不同的零点当且仅当 $p$ 与其导式 $p'$ 没有公共零点。

证明逆否命题：$p$ 存在两个相同零点当且仅当 $p$ 与其导式 $p'$ 有公共零点。

充分性：

设公共零点为 $\lambda$，则 $p(x)=(x-\lambda)s(x), p'(x)=(x-\lambda)t(x),p'(\lambda)=0$

而事实上 $p'(x)=s(x)+s'(x)(x-\lambda),p'(\lambda)=s(\lambda)=0$。

所以 $s(\lambda)=(x-\lambda)q(x)$，所以 $p(x)=(x-\lambda)^2q(x)$，所以 $p$ 存在至少两个相同零点。

必要性：

设 $p(x)=(x-\lambda)^2q(x)$，这里不保证 $q(\lambda)\neq0$。

计算 $p'(x)=2(x-\lambda)q(x)+(x-\lambda)^2q'(x)=(x-\lambda)(2q(x)+q'(x))$，所以 $p'(\lambda)=0$，所以 $p$ 和 $p'$ 有公共零点。

> 8. 定义 $T:P(R)\to R^R$ 为
>
> $$
T_p=\begin{cases}
\dfrac{p-p(3)}{x-3}&,x\neq3\\
p'(3)&,x=3
\end{cases}
> $$
>
> 证明对每个多项式 $p\in P(R)$ 均有 $T_p\in P(R)$，且 $T$ 是线性映射。

首先，在 $p(x)-p(3)$ 中代入 $x=3$ 立刻知道它有因式 $x-3$，$p(x)-p(3)=(x-3)q(x)$。

对上式求导，得 $p'(x)=q(x)+(x-3)q'(x)$，代入 $x=3$ 知 $p'(3)=q(3)$

所以 $T_p=q\in P(R)$。

线性映射：

$$
\begin{aligned}
T_{\lambda p+\mu q}&=\begin{cases}
\dfrac{(\lambda p(x)+\mu q(x))-(\lambda p(3)+\mu q(3))}{x-3}&,x\neq3\\
\lambda p'(3)+\mu q'(3)&,x=3\\
\end{cases}\\
&=\begin{cases}
\lambda\dfrac{p(x)-p(3)}{x-3}+\mu\dfrac{q(x)-q(3)}{x-3}&,x\neq3\\
\lambda p'(3)+\mu q'(3)&,x=3
\end{cases}\\
&=\lambda T_p+\mu T_q
\end{aligned}
$$

> 11. 设 $p\in P(F),p\neq0$，令 $U=\{pq\mid q\in P(F)\}$
>
> $(a)$ 证明 $\dim P(F)/U=\deg p$
>
> $(b)$ 求 $P(F)/U$ 的一个基。

记 $n=\deg p$

我们声称 $\{1+U,x+U,\dots,x^{n-1}+U\}$ 是 $P(F)/U$ 的一组基，如果证明了这个 $(a)(b)$ 自然得到结果。

线性无关性：

设 $\lambda_0(1+U)+\dots+\lambda_{n-1}(x^{n-1}+U)=0+U$

则 $(\lambda_0+\lambda_1x+\dots+\lambda_{n-1}x^{n-1})+U=0+U$，

则 $\lambda_0+\lambda_1x+\dots+\lambda_{n-1}x^{n-1}-0\in U$，然而 $U$ 中只有 $0$ 多项式的度数 $<n$（这是因为若 $q\neq0$，那么 $\deg pq=\deg p+\deg q\ge \deg p=n$），所以 $\lambda_0+\lambda_1x+\dots+\lambda_{n-1}x^{n-1}=0$，所以 $\lambda_0=\lambda_1=\dots=\lambda_{n-1}$。

张成整个空间：

考虑 $f+U$ 这个元素，做带余除法，设 $f(x)=p(x)q(x)+r(x)$，显然 $p(x)q(x)\in U,\deg r<\deg p=n-1$

所以 $f+U=pq+r+U=r+U$。

设 $r(x)=\lambda_0+\lambda_1x+\dots+\lambda_{n-1}x^{n-1}$，

则 $f+U=r+U=\lambda_0(1+U)+\lambda_1(x+U)+\dots+\lambda_{n-1}(x^{n-1}+U)$。

证毕。