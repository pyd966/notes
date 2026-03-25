## 习题 3.E

> 11. 设 $v_1,\dots v_m\in V$。令
>
> $$
A=\{\lambda_1v_1+\dots+\lambda_mv_m\mid\lambda_1,\dots,\lambda_m\in F,\lambda_1+\dots\lambda_m=1\}
> $$
>
> $(a)$ 证明 $A$ 是 $V$ 的仿射子集。
>
> $(b)$ 证明 $V$ 的每个包含 $v_1,\dots,v_m$ 的仿射子集均包含 $A$。
>
> $(c)$ 证明有某个 $v\in V$ 及 $V$ 的某个子空间 $U$ 使得 $A=v+U$ 且 $\dim U\le m-1$。

$(a)$

$$
\begin{aligned}
\lambda_1v_1+\dots+\lambda_m v_m&=v_1+((\lambda_1-1)v_1+\dots+\lambda_m v_m)\\
&=v_1+(\mu_1v_1+\dots+\mu_m v_m)
\end{aligned}
$$

其中 $\sum\mu_i=0$。我们证明后者是包含零向量的子空间。

包含零向量显然，只要取 $\mu_1=\dots=\mu_m=0$ 即可。

子空间显然，因为对加法和数乘封闭。

因此 $A=v_1+U$，其中 $U$ 是过零向量的子空间，因此 $A$ 是仿射子集。

$(b)$

任取一个包含 $v_1,\dots,v_m$ 的仿射子集 $C=v+U$。

由于 $v_1\in C$，所以 $C=v_1+U$。

因为 $v_1,\dots,v_m\in C$，所以 $v_2-v_1,\dots,v_m-v_1\in U$。

$\forall\vec{x}=\lambda_1v_1+\dots+\lambda_m v_m\in C$，我们可以重写成 $\vec{x}=v_1+((\lambda_1-1)v_1+\dots+\lambda_m v_m)=v_1+(\mu_1v_1+\dots+\mu_m v_m)$。

因为 $\mu_1+\dots+\mu_m=0$，所以 $\mu_1=-(\mu_2+\dots+\mu_m)$。

所以 $\vec{x}=v_1+(\mu_2(v_2-v_1)+\dots+\mu_m(v_m-v_1))$，所以 $\vec{x}\in C$。

所以 $A\subseteq C$。

$(c)$

在 $b$ 中，我们事实上证明了可以取 $v=v_1,U=L(v_2-v_1,\dots,v_m-v_1)$。

容易发现，此时 $\dim U\le m-1$。

> 18. 设 $T\in L(V,W)$，并设 $U$ 是 $V$ 的子空间。用 $\pi$ 表示 $V$ 到 $V/U$ 的商映射。证明：存在 $S\in L(V/U,W)$ 使得 $T=S\circ\pi$ 当且仅当 $U\subseteq\text{null} T$。

充分性：

取 $S(v+U)=T(v)$ 即可。

显然 $S\in L(V/U,W)$。

下证这个定义是合理的。

取 $u,v\in V$，使得 $u+U=v+U$，也即 $u-v\in U$，下面证明 $T(u)=T(v)$。

$u-v\in U\subseteq\text{null}T$，所以 $T(u-v)=0$。

所以 $T(u)=T(u-v+v)=T(u-v)+T(v)=0$。

下面验证这个 $S$ 满足题意。

$(S\circ\pi)(u)=S(\pi(u))=S(u+U)=T(u)$ 满足题意。

必要性：

考虑采用反证法证明逆否命题，$\exist\vec x\in U,\vec x\not\in\text{null} T$，假设此时仍然存在这样的映射 $S$。

那么 $0\neq T(\vec x)=(S\circ\pi)(\vec x)=S(\pi(\vec x))=S(\vec x+U)=S(0+U)=0$，矛盾。

所以假设不成立，所以逆否命题成立，所以原命题成立。

## 习题 3.F

> 6. 设 $V$ 是有限维的，$v_1,\dots,v_m\in V$。定义线性映射 $\Gamma:V'\to F^m$ 如下：
>
> $$
\Gamma(\varphi)=(\varphi(v_1),\dots,\varphi(v_m))
> $$
>
> $(a)$ 证明 $v_1,\dots,v_m$ 张成 $V$ 当且仅当 $\Gamma$ 是单的。
>
> $(b)$ 证明 $v_1,\dots,v_m$ 是线性无关的当且仅当 $\Gamma$ 是满的。

$(a)$

必要性：

$L(v_1,\dots,v_m)=V$，所以任何 $V$ 中元素均可分解。

反证法，假设 $\exist\varphi_1\neq\varphi_2,\Gamma(\varphi_1)=\Gamma(\varphi_2)$。

由 $\varphi_1\neq\varphi_2$，$\exist v,\varphi_1(v)\neq\varphi_2(v)$。

由 $\Gamma(\varphi_1)=\Gamma(\varphi_2)$，$\varphi_1(v_1)=\varphi_2(v_1),\dots,\varphi_1(v_m)=\varphi_2(v_m)$。

设 $v=k_1v_1+\dots k_mv_m$。

$\varphi_1(v)=\sum\limits_{i=1}^mk_1\varphi_1(v_1)=\sum\limits_{i=1}^mk_1\varphi_2(v_1)=\varphi_2(v)$

矛盾。

充分性：

反证，假设 $\exist v$ 不能用 $v_1,\dots,v_m$ 表示，考虑将其扩充为一组基 $v,v_{i_1},\dots,v_{i_k},u_1,\dots,u_p$。

构造这样的映射 $\varphi(v)=1,\varphi(v_{i_*})=\varphi(u_*)=0$。

容易发现 $\Gamma(\varphi)=(0,\dots,0)$，但是 $\varphi\neq 0$，所以 $\Gamma$ 不是单的，矛盾。

$(b)$

必要性：

扩充为一组基 $v_1,\dots,v_m,v_{m+1},\dots,v_n$

$\forall (x_1,\dots,x_m)\in F^m$，构造映射 $\varphi(v_i)=\begin{cases}x_i&,1\le i\le m\\ 0&,m+1\le i\le n\end{cases}$

容易验证 $\Gamma(\varphi)=(x_1,\dots,x_m)$，所以是满射。

充分性：

设 $k_1v_1+\dots+k_mv_m=0$。

则 $k_1\varphi(v_1)+\dots+k_m\varphi(v_m)=0$。

若 $\exist k_i\neq0$，那么 $(0,0,\dots,1,\dots,0)$，其中只有第 $i$ 个位置上是 $1$，因为它不满足上式，所以不能出现在 $\text{range}\Gamma$ 中。

但是 $\Gamma$ 是满射，所以上述情况不存在，也就是说 $k_i=0$，所以线性无关。

> 27. 设 $T\in L(P_5(R),P_5(R))$ 且 $\text{null}T'=\text{span}(\varphi)$，这里 $\varphi$ 是 $P_5(R)$ 上的由 $\varphi(p)=p(8)$ 定义的线性泛函。证明 $\text{range}T=\{p\in P_5(R)\mid p(8)=0\}$

先证 $\text{range}T\subseteq\{p\in P_5(R)\mid p(8)=0\}$。

$\forall q=T(p)\in\text{range}T$，由 $\text{null}T'=\text{span}(\varphi)$ 知 $T'(\varphi)=0$，则 $0=\varphi(T(p))=\varphi(q)=q(8)$，所以 $q\in\{p\in P_5(R)\mid p(8)=0\}$。

容易发现右侧是子空间。再证维数相等。

容易发现 $\dim\{p\in P_5(R)\mid p(8)=0\}=5$。

并且 $\dim\text{null}T'=\dim\text{null}T+\dim P_5(R)-\dim P_5(R)$，所以 $\dim\text{null} T=1$。

此时 $\dim\text{range}T=\dim P_5(R)-\dim\text{null}T=5$。

所以二者维数相等，所以相等。