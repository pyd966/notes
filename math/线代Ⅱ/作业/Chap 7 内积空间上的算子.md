# Chap 7 内积空间上的算子

## 习题 7.B

> 4. 设 $F=C$ 且 $T\in L(V)$。证明：$T$ 是正规的当且仅当 $T$ 的对应于不同本征值的任意一对本征向量都是正交的且
>
> $$
V=E(\lambda_1,T)\oplus\dots\oplus E(\lambda_m,T)
> $$
>
> 这里 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的全体互不相同的本征值。

先证必要性。

由于 $T$ 是正规的，由复谱定理，其可对角化，所以 $V=E(\lambda_1,T)\oplus\dots\oplus E(\lambda_m,T)$。

由于 $T$ 是正规的，所以对应于不同本征值的任意一对本征向量都是正交的。

再证充分性。

在 $E(\lambda_1,T),E(\lambda_2,T),\dots,E(\lambda_m,T)$ 中各自取出其中的一组规范正交基，拼起来，因为 $T$ 对应于不同本征值的任意一对本征向量都是正交的，所以可以得到 $V$ 的一组规范正交基。

所以 $V$ 有一组由本征向量组成的规范正交基，由复谱定理，$T$ 是正规的。

> 10. 找出一个实内积空间 $V$ 和 $T\in L(V)$ 以及满足 $b^2<4c$ 的实数 $b,c$ 使得 $T^2+bT+cI$ 不是可逆的。

取 $V=R^2,b=0,c=1$

在自然基下，取 $T=\begin{pmatrix}0 & -1\\ 1 & 0\\\end{pmatrix}$

那么 $T^2+I=\begin{pmatrix}0 & 0\\ 0 & 0\\\end{pmatrix}$，显然不可逆。

## 习题 7.C

> 1. 证明或给出反例：若 $T\in L(V)$ 是自伴的，且 $V$ 有一个规范正交基 $e_1,\dots,e_n$ 使得对每个 $j$ 有 $\left<Te_j,e_j\right>\ge0$，则 $T$ 是正算子。

反例：取 $V=R^2$，在自然基下取 $T=\begin{pmatrix}0 & 1\\ 1 & 0\end{pmatrix}$，不难验证 $T$ 是自伴的。

取规范正交基 $e_1=(1,0),e_2=(0,1)$，则 $\left<Te_1,e_1\right>=\left<Te_2,e_2\right>=0$。

取 $v=(1,-1)$，那么 $\left<Tv,v\right>=-2<0$，所以不是正算子。

> 13. 证明或给出反例：若 $S\in L(V)$ 且存在 $V$ 的规范正交基 $e_1,\dots,e_n$ 使得对每个 $e_j$ 均有 $||Se_j||=1$，则 $S$ 是等距同构。

反例：

考虑一个线性映射 $S(v)=e_1$，显然满足 $||S(e_j)||=||e_1||=1$。

但是 $S(e_1-e_2)=S(e_1)-S_(e_2)=0$，可是 $||e_1-e_2||\neq0$，所以不是等距同构。

## 习题 7.D

> 7. 定义 $T\in L(F^3)$ 为 $T(z_1,z_2,z_3)=(z_3,2z_1,3z_2)$。求一个等距同构 $S\in L(F^3)$ 使得 $T=S\sqrt{T^*T}$

在自然基下 $T=\begin{pmatrix}0 & 0 & 1\\ 2 & 0 & 0\\ 0 & 3 & 0\\\end{pmatrix},T^*=\begin{pmatrix}0 & 2 & 0\\ 0 & 0 & 3\\ 1 & 0 & 0\\\end{pmatrix}$

所以 $T^*T=\begin{pmatrix}4 & 0 & 0\\ 0 & 9 & 0\\ 0 & 0 & 1\\\end{pmatrix},\sqrt{T^*T}=\begin{pmatrix}2 & 0 & 0\\ 0 & 3 & 0\\ 0 & 0 & 1\\\end{pmatrix}$

取 $S=\begin{pmatrix}0 & 0 & 1\\ 1 & 0 & 0\\ 0 & 1 & 0\\\end{pmatrix}$，容易发现 $T=S\sqrt{T^*T}$，并且 $SS^*=I$，所以 $S$ 是等距同构。

> 17. 设 $T\in L(V)$ 有如下奇异值分解：对每个 $v\in V$ 有
>
> $$
Tv=s_1\left<v,e_1\right>f_1+\dots+s_n\left<v,e_n\right>f_n
> $$
>
> 其中 $s_1,\dots,s_n$ 是 $T$ 的奇异值，$e_1,\dots,e_n$ 和 $f_1,\dots,f_n$ 都是 $V$ 的规范正交基。
>
> $(a)$ 证明：若 $v\in V$，则 $T^*v=s_1\left<v,f_1\right>e_1+\dots+s_n\left<v,f_n\right>e_n$
>
> $(b)$ 证明：若 $v\in V$，则 $T^*Tv=s_1^2\left<v,e_1\right>e_1,+\dots+s_n^2\left<v,e_n\right>e_n$
>
> $(c)$ 证明：若 $v\in V$，则 $\sqrt{T^*T}v=s_1\left<v,e_1\right>e_1+\dots+s_n\left<v,e_n\right>e_n$
>
> $(d)$ 设 $T$ 是可逆的，证明：若 $v\in V$，则
>
> $$
T^{-1}v=\dfrac{\left<v,f_1\right>e_1}{s_1}+\dots+\dfrac{\left<v,f_n\right>e_n}{s_n}
> $$

$(a)$

$s_i[i=j]=\left<s_if_i,f_j\right>=\left<Te_i,f_j\right>=\left<e_i,T^*f_j\right>$

所以可知 $T^*f_j=s_je_j$。

设 $v=b_1f_1+\dots+b_nf_n$，那么 $T^*v=s_1b_1f_1+\dots+s_nb_nf_n=s_1\left<v,f_1\right>f_1+\dots+s_n\left<v,f_n\right>f_n$。

$(b)$

$Tv=s_1\left<v,e_1\right>f_1+\dots+s_n\left<v,e_n\right>f_n$

$\left<Tv,f_i\right>=s_i\left<v,e_i\right>$

$T^*Tv=s_1^2\left<v,e_1\right>e_1+\dots+s_n^2\left<v,e_n\right>e_n$

$(c)$

记 $v=v_1+\dots+v_n$，其中 $v_i=\left<v,e_i\right>e_i$。

$T^*Tv_i=s_i^2v_i$，所以 $\sqrt{T^*T}v_i=s_iv_i$。

所以 $\sqrt{T^*T}v=\sum s_i\left<v,e_i\right>e_i$

$(d)$

$\det(T^*T)=\det(T^*)\det(T)=\det(T)^2\neq0$，所以 $T^*T$ 的特征值都不为 $0$，所以 $s_i\neq0$。

$\forall v$，记 $u=\sum\dfrac{\left<v,f_i\right>e_i}{s_i}$，考虑 $Tu=\sum s_i\cdot\dfrac{\left<v,f_i\right>}{s_i}f_i=\sum\left<v,f_i\right>f_i=v$，所以 $u=T^{-1}v$。

所以 $T^{-1}v=u=\sum\dfrac{\left<v,f_i\right>e_i}{s_i}$