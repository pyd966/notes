# Chap 6 内积空间

## 习题 6.B

> 8. 求多项式 $q\in P_2(R)$ 使得对每个 $p\in P_2(R)$ 均有
>
> $$
\int_0^1 p(x)(\cos\pi x)dx=\int_0^1 p(x)q(x)dx
> $$

取 $P_2(R)$ 的一组基 $1,x,x^2$，定义内积 $\left<p,q\right>=\int_0^1p(x)q(x)dx$。

进行正交化，得到单位正交基 $e_1=1,e_2=2\sqrt3x-\sqrt3,e_3=\sqrt5(6x^2-6x+1)$

记 $T(p)=\int_0^1p(x)(\cos\pi x)dx$。

计算 $T(e_1)=0,T(e_2)=-\dfrac{4\sqrt3}{\pi^2},T(e_3)=0$

因此，取 $q(x)=\overline{T(e_1)}e_1+\overline{T(e_2)}e_2+\overline{T(e_3)}e_3=\dfrac{12}{\pi^2}(1-2x)$

> 14. 设 $e_1,\dots,e_n$ 是 $V$ 的规范正交基，并设 $v_1,\dots,v_n$ 是 $V$ 中的向量使得对每个 $j$ 均有
>
> $$
||e_j-v_j||<\dfrac1{\sqrt n}
> $$
>
> 证明 $v_1,\dots,v_n$ 是 $V$ 的基。

设 $v_j-e_j=u_j=\sum\limits_{i=1}^na_{ji}e_i$，由题知 $||u_j||<\dfrac1{\sqrt n}$

设存在不全为 $0$ 的一组 $k$ 使得 $k_1v_1+\dots+k_nv_n=0$，则 $k_1u_1+\dots+k_nu_n=k_1e_1+\dots+k_ne_n$。

考虑右式的范数，显然为 $\sqrt{k_1^2+\dots+k_n^2}$。

考虑左式的范数，显然 $\le||k_1u_1||+\dots+||k_nu_n||<\dfrac{|k_1|+\dots+|k_n|}{\sqrt n}$

由于左右相等，所以 $\sqrt{k_1^2+\dots+k_n^2}<\dfrac{k_1+\dots+k_n}{\sqrt n}$，也即 $\sqrt{\dfrac{k_1^2+\dots+k_n^2}{n}}<\dfrac{|k_1|+\dots+|k_n|}{n}$。

而由均值不等式，矛盾。所以假设不成立，$v_1,\dots,v_n$ 是 $V$ 的一组基。

## 习题 6.C

> 8. 设 $V$ 是有限维的，$P\in L(V)$ 使得 $P^2=P$ 且对每个 $v\in V$ 均有 $||Pv||\le||v||$。证明存在 $V$ 的子空间 $U$ 使得 $P=P_U$

考察空间 $\text{range}P$ 与 $\text{null}P$，我们声称它们互为正交补。

首先，由于 $P^2=P$，所以 $\forall u\in\text{range}P,Pu=u$，所以 $\text{range}P\cap\text{null}P=\varnothing$，而 $\dim\text{range}P+\dim\text{null}P=\dim V$，所以是直和。取 $U=\text{range}P$

$\forall v\in\text{null}P$，由于 $U\oplus U^\perp=V$，所以可以分解 $v=u+w$，其中 $u\in U,w\in U^\perp$。

若 $\left<u,v\right>\neq0$，考察 $w'=v-ku$，考察 $\left<w',v\right>=\left<v,v\right>-k\left<u,v\right>$，只需取 $k=\dfrac{\left<v,v\right>}{\left<u,v\right>}$ 即可令 $\left<w',v\right>=0$。

此时，考察 $P(w')=P(v-ku)=-ku$，由题知 $|k|^2|u|^2=||Pw'||^2\le||w'||^2=||v-ku||^2=|k|^2|u|^2-||v||^2$，所以 $||v||=0$，矛盾。

所以 $\left<u,v\right>=0$，说明 $\left<u,u\right>=0$，即 $u=0$，即 $v=w\in U^\perp$。

即 $\text{null}P\subseteq U^\perp$，又有维数相等，所以 $\text{null}P=U^\perp$。

下面证明 $P=P_U$。

$\forall v\in V,v=u+w,u\in\text{range}P,w\in\text{null}P$。

所以 $P(v)=u$，而 $P_U(v)=u$，所以证毕。

> 14. 设 $C_R([-1,1])$ 是区间 $[-1,1]$ 上实值连续函数构成的向量空间，且其上的内积为：对 $f,g\in C_R([-1,1])$
>
> $$
\left<f,g\right>=\int_{-1}^1f(x)g(x)dx
> $$
>
> 给定 $C_R([-1,1])$ 的子空间 $U=\{f\in C_R([-1,1])\mid f(0)=0\}$
>
> $(a)$ 证明 $U^{\perp}=\{0\}$
>
> $(b)$ 证明当没有“有限维”这一假设时，6.47 和 6.51 不成立。

$(a)$

取 $g\in U^{\perp}$，假设存在 $x_0\neq0$ 使得 $g(x_0)\neq0$

取 $h(x)=|x|g(x)$。

容易发现 $h\in U,\left<g,h\right>>0$，矛盾。

所以 $\forall x\neq0,g(x)=0,g\in U$，又由连续性可知 $g(0)=0$。

所以 $U^{\perp}=\{0\}$

$(b)$

6.47:

显然 $C_R([-1,1])$ 是无限维空间，$U$ 是其子空间，但是 $V\neq U+U^{\perp}=U$。

6.51:

$(U^\perp)^\perp=V\neq U$，所以 6.51 不成立。