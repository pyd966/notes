## 习题

> 5. 利用 Vandermonde 行列式，展开下列行列式：
>
> $(2)\begin{vmatrix}a_1+a_2 & a_2+a_3 & \dots & a_{n-1}+a_n & a_n+a_1\\ a_1^2+a_2^2 & a_2^2+a_3^2 & \dots & a_{n-1}^2+a_n^2 & a_n^2+a_1^2\\ \vdots & & & & \vdots\\ a_1^n+a_2^n & a_2^n+a_3^n & \dots & a_{n-1}^n+a_n^n & a_n^n+a_1^n\\\end{vmatrix}$

记所求行列式为 $D=\det(\alpha_1+\alpha_2,\alpha_2+\alpha_3,\dots,\alpha_{n-1}+\alpha_n,\alpha_n+\alpha_1)$。

展开得 

$$
D=\sum_{\{b_n\},b_i\in\{0,1\}}\det(\alpha_{1+b_1},\alpha_{2+b_2},\dots,\alpha_{n-1+b_{n-1},\alpha_{n-(n-1)b_n}})
$$

下面证明，只有 $b_i$ 全为 $0$ 或 全为 $1$ 时，对应的行列式才不为 $0$.

考虑一个既有 $1$ 又有 $0$ 的 $b_i$，如果存在 $p$ 使得 $b_p=1,b_{p+1}=0$，那么

$$
\det(\alpha_{1+b_1},\alpha_{2+b_2},\dots,\alpha_{n-1+b_{n-1},\alpha_{n-(n-1)b_n}})=\det(\dots,\alpha_{p+1},\alpha_{p+1},\dots)=0
$$

如果不存在这样的 $p$，说明存在一个 $q$ 使得 $b_i=\begin{cases}0&,i\le q\\ 1&,i>q\\\end{cases}$，这表明 $b_1=0,b_n=1$，此时

$$
\det(\alpha_{1+b_1},\alpha_{2+b_2},\dots,\alpha_{n-1+b_{n-1},\alpha_{n-(n-1)b_n}})=\det(\alpha_1,\dots,\alpha_1)=0
$$

所以

$$
D=\det(\alpha_1,\alpha_2,\dots,\alpha_n)+\det(\alpha_2,\alpha_3,\dots,\alpha_n,\alpha_1)=(1+(-1)^{n-1})\det(\alpha_1,\alpha_2,\dots,\alpha_n)
$$

而

$$
\det(\alpha_1,\alpha_2,\dots,\alpha_n)=\begin{vmatrix}a_1 & a_2 & \dots & a_n\\ a_1^2 & a_2^2 & \dots & a_n^2\\ \vdots & & & \vdots\\ a_1^n & a_2^n & \dots & a_n^n\end{vmatrix}=a_1a_2\cdots a_n\begin{vmatrix}1 & 1 & \dots & 1\\ a_1 & a_2 & \dots & a_n\\ \vdots & & & \vdots\\ a_1^{n-1} & a_2^{n-1} & \dots & a_n^{n-1}\end{vmatrix}=\prod_{i=1}^na_i\prod_{1\le i<j\le n}(a_j-a_i)
$$

所以

$$
D=(1+(-1)^{n-1})\prod_{i=1}^na_i\prod_{1\le i<j\le n}(a_j-a_i)
$$

> 8. 利用 5-2 例 4 的结论，计算下列行列式：
>
> $(3)A\in M_3(R),B\in M_4(R)$。已知：$|A|=-6,|B|=4$，计算 $\begin{vmatrix}O & \dfrac12A\\ -B & C\end{vmatrix}$，其中 $C$ 是任意的 $4\times3$ 矩阵。

$$
\begin{vmatrix}O & \dfrac12A\\ -B & C\\\end{vmatrix}=(-1)^{3\times4}\begin{vmatrix}\dfrac12A & O\\ C & -B\end{vmatrix}=|\dfrac12A|\cdot|-B|=(\dfrac12)^3\cdot(-1)^4|A||B|=-3
$$

> 9. 计算下列行列式：
>
> $(2)\begin{vmatrix}1 & 2 & \dots & n-1 & n\\ 2 & 3 & \dots & n & 1\\ 3 & 4 & \dots & 1 & 2\\ \vdots & & & & \vdots\\ n & 1 & \dots & n-2 & n-1\\\end{vmatrix}$

$(2)$

按照 $i=n-1,n-2,\dots,1$ 的顺序，依次从第 $i+1$ 行减去第 $i$ 行，得到的新矩阵行列式不变，即

$$
D=\begin{vmatrix}1 & 2 & \dots & n-1 & n\\ 2 & 3 & \dots & n & 1\\ \vdots & & & & \vdots\\ n & 1 & \dots & n-2 & n-1\\\end{vmatrix}=\begin{vmatrix}1 & 2 & \dots & n-1 & n\\ 1 & 1 & \dots & 1 & 1-n\\ 1 & 1 & \dots & 1-n & 1\\ \vdots & & & & \vdots\\ 1 & 1-n & \dots & 1 & 1\end{vmatrix}
$$

依次将第 $i$ 列加到第 $1$ 列（$i=2,3,\dots,n$），则

$$
D=\begin{vmatrix}\frac{n(n+1)}{2} & 2 & \dots & n-1 & n\\ 0 & 1 & \dots & 1 & 1-n\\ \vdots & & & & \vdots\\ 0 & 1-n & \dots & 1 & 1\end{vmatrix}
$$

按照第一列展开

$$
\begin{aligned}
D&=(-1)^{1+1}\dfrac{n(n+1)}{2}\begin{vmatrix}1 & 1 & \dots & 1 & 1-n\\ 1 & 1 & \dots & 1-n & 1\\ \vdots & & & & \vdots\\ 1-n & 1 & \dots & 1 & 1\end{vmatrix}\\
&=(-1)^{\frac{(n-2)(n-1)}{2}}\dfrac{n(n+1)}{2}\begin{vmatrix}1-n & 1 & \dots & 1 & 1\\ 1 & 1-n & \dots & 1 & 1\\ \vdots & & & & \vdots\\ 1 & 1 & \dots & 1 & 1-n\end{vmatrix}
\end{aligned}
$$

由课本例题 5，我们知道后面这个行列式的值是 $((1-n)+(n-2)\times1)(1-n-1)^{n-2}$

所以 $D=(-1)^{\frac{(n-1)n}2}\dfrac{n^{n-1}(n+1)}{2}$。

> 11. 设 $A$ 是 $n$ 阶可逆对称矩阵，$B$ 是 $n$ 阶反对称矩阵。证明：当 $n$ 为奇数时，齐次线性方程组 $(AB)X=O$ 有非零解。

$|B|=|B^T|=|-B|=(-1)^n|B|$。

当 $n$ 为奇数时，可以得到 $|B|=-|B|$，所以 $|B|=0$。

则 $|AB|=|A||B|=0$，说明 $r(AB)<n$。

所以 $AB$ 的各列线性相关，$(AB)X=O$ 存在非零解。

> 14. 设 $A,B,C,D$ 都是 $n$ 阶矩阵，$|A|\neq0$ 且 $AC=CA$，证明：
>
> $$
> \begin{vmatrix}A & B\\ C & D\\\end{vmatrix}=|AD-CB|
> $$

因为 $|A|\neq0$，所以 $A$ 可逆。

$$
\begin{aligned}
\begin{vmatrix}E & O\\ -CA^{-1} & E\end{vmatrix}\begin{vmatrix}A & B\\ C & D\\\end{vmatrix}&=\begin{vmatrix}A & B\\ O & D-CA^{-1}B\\\end{vmatrix}\\
&=|A||D-CA^{-1}B|\\
&=|AD-ACA^{-1}B|\\
&=|AD-CAA^{-1}B|\\
&=|AD-CB|\\
\end{aligned}
$$