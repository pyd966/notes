# Chap 5 本征向量与上三角矩阵

## 习题 5.A

> 29. 设 $T\in L(V)$ 且 $\dim\text{range}T=k$，证明 $T$ 至多有 $k+1$ 个不同的本征值。

设 $T$ 的本征值为 $\lambda_1,\lambda_2,\dots,\lambda_m$，并且对应的本征向量为 $v_1,v_2,\dots,v_m$。

我们已知 $v_1,v_2,\dots,v_m$ 线性无关。若 $\lambda$ 中有某一个为 $0$，则不妨令 $\lambda_m=0$，否则不变。那么 $Tv_1,Tv_2,\dots,Tv_{m-1}$ 即 $\lambda_1v_1,\lambda_2v_2\dots,\lambda_{m-1}v_{m-1}$ 也线性无关。

所以 $m-1\le k$，即 $m\le k+1$。

> 30. 设 $T\in L(R^3)$ 且 $-4,5,\sqrt7$ 均为 $T$ 的本征值。证明存在 $x\in R^3$ 使得 $Tx-9x=(-4,5,\sqrt7)$

记 $\lambda_1=-4,\lambda_2=5,\lambda_3=\sqrt7$，对应的本征向量为 $v_1,v_2,v_3$，则它们线性无关。

所以设 $x=\mu_1v_1+\mu_2v_2+\mu_3v_3$，则 $Tx-9x=\mu_1(-13v_1)+\mu_2(-4)v_2+\mu_3(\sqrt7-9)v_3$

容易发现 $-13v_1,-4v_2,(\sqrt7-9)v_3$ 也是线性无关的，它们是 $R^3$ 的一组基。

所以一定存在 $\mu_1,\mu_2,\mu_3$ 使得 $Tx-9x=(-4,5,\sqrt7)$。

> 35. 设 $V$ 是有限维的，$T\in L(V)$，$U$ 在 $T$ 下不变。证明 $T/U$ 的每个本征值均为 $T$ 的本征值。

考虑一个 $T/U$ 的本征值 $\lambda$ 以及本征向量 $v+U$，其中 $v\not\in U$

我们有 $(T/U)(v+U)=\lambda(v+U)=\lambda v+U$，同时有 $(T/U)(v+U)=Tv+U$。

所以 $Tv-\lambda v=u\in U$。

再次作用 $T$，得到 $T(Tv)-T(\lambda v)=Tu$。

记 $\dim U=r$，连续作用 $r$ 次，可以得到 $T(T^kv)-\lambda(T^kv)=T^ku,k=0,1,\dots,r$。

所以 $u,Tu,\dots,T^ru$ 线性相关，取最小的 $m$ 使得存在一组 $\lambda$ 满足 $\lambda_0u+\lambda_1Tu+\dots+\lambda_mT^mu=0$。

即 $T(\lambda_0v+\lambda_1Tv+\dots+\lambda_mT^mv)-\lambda(\lambda_0v+\lambda_1Tv+\dots+\lambda_mT^mv)=0$

下证 $\lambda_0v+\lambda_1Tv+\dots+\lambda_mT^mv\neq0$.

假设 $w=\lambda_0v+\lambda_1Tv+\dots+\lambda_mT^mv=0$。

先证明 $v,Tv,\dots,T^{m-1}v$ 线性无关。

假设相关，说明存在多项式 $q$，其中 $\deg q\le m-1$ 满足 $q(T)(v)=0$。

而 $q(T)(u)=q(T)(T-\lambda)(v)=0$，其中 $\deg q<m$，与 $m$ 的最小性矛盾。

所以线性无关，记张成空间 $W$。容易发现 $W$ 是 $T$ 不变子空间。

下面考虑 $u,Tu,\dots,T^{m-1}u$，它们也落在 $W$ 中，并且线性无关，所以构成一组基。

那么 $v=\mu_0u+\mu_1Tu+\dots+\mu_{m-1}T^{m-1}u$，这说明 $v\in U$，矛盾。

所以 $w\neq0$，所以 $Tw-\lambda w=0$，说明 $\lambda$ 是一个本征值。

## 习题 5.B

> 18. 设 $V$ 是有限维的复向量空间，$T\in L(V)$。定义函数 $f:C\to R$ 为
>
> $$
f(\lambda)=\dim\text{range}(T-\lambda I)
> $$
>
> 证明 $f$ 不是连续函数。

事实上 $f$ 的陪域是 $Z$，只需要证明存在 $f(\lambda_1)\neq f(\lambda_2)$

因为 $T\in L(V)$，所以 $T$ 有本征值 $\lambda_1$，这意味着 $\dim\text{null}(T-\lambda_1I)\ge 1$，所以 $f(\lambda_1)\le\dim V-1$。

因为 $V$ 是有限维，所以必然存在 $\lambda_2$ 不是本征值，也就是 $\dim\text{null}(T-\lambda_2I)=0$，所以 $f(\lambda_2)=\dim V$。

所以 $f(\lambda_1)\neq f(\lambda_2)$，$f$ 不是连续函数。

> 19. 设 $V$ 是有限维的，$\dim V>1,T\in L(V)$。证明 $\{p(T)\mid p\in P(F)\}\neq L(V)$

显然 $\exist\sigma_1,\sigma_2\in V$ 满足 $\sigma_1\sigma_2\neq\sigma_2\sigma_1$。

假设 $\{p(T)\mid p\in P(F)\}=L(V)$，那就说明 $\exist p_1,p_2\in P(F)$ 满足 $p_1(T)=\sigma_1,p_2(T)=\sigma_2$。

这说明 $\sigma_1\sigma_2=p_1(T)p_2(T)=p_2(T)p_1(T)=\sigma_2\sigma_1$，矛盾。

所以 $\{p(T)\mid p\in P(F)\}\neq L(V)$

## 习题 5.C

> 5. 设 $V$ 是有限维的复向量空间且 $T\in L(V)$。证明：$T$ 可对角化当且仅当对每个 $\lambda\in C$ 有 $V=\text{null}(T-\lambda I)\oplus\text{range}(T-\lambda I)$

设 $n=\dim V,\lambda_1,\dots,\lambda_m$ 是本征值，对应于本征向量 $v_{1,1},\dots,v_{1,k_1},\dots,v_{m,1},\dots,v_{m,k_m}$。

先证必要性。

由于 $T$ 可对角化，我们知道 $v_{1,1},\dots,v_{1,k_1},\dots,v_{m,1},\dots,v_{m,k_m}$ 是一组基，在这组基下对应的矩阵是对角阵。

下面考虑 $\forall\lambda$，如果 $\lambda$ 不是本征值，那么 $\text{null}(T-\lambda I)=\varnothing$，所以 $V=\text{range}(T-\lambda I)$。

如果 $\lambda$ 是本征值，不妨设 $\lambda=\lambda_p$，那么 $\text{null}(T-\lambda I)=\text{span}(v_{p,1},\dots,v_{p,k_p})$。

考虑其值域 $\text{range}(T-\lambda I)=\text{span}(Tv_{1,1},\dots,Tv_{m,k_m})=\text{span}(\lambda_1v_{1,1},\dots,\lambda_{p-1}v_{p-1,k_{p-1}},\lambda_{p+1}v_{p+1,1},\dots,\lambda_mv_{m,k_m})$，显然 $\text{null}(T-\lambda I)\oplus\text{range}(T-\lambda I)=V$。

再证充分性。

由于 $V$ 是有限维的，所以一定存在本征值 $\lambda_1$。

由题目条件 $V=\text{null}(T-\lambda I)\oplus\text{range}(T-\lambda I)$，其中 $\text{range}(T-\lambda I)$ 是 $T$ 不变的，$\text{null}(T-\lambda I)=\text{span}(v_{1,1},\dots,v_{1,k_1})$。

考虑限制映射 $T_{\text{range}(T-\lambda I)}$，由于 $\text{range}(T-\lambda I)$ 也是有限维复向量空间，并且 $\dim\text{range}(T-\lambda I)<\dim V$，所以由数学归纳法。

$V=\text{null}(T-\lambda_1I)\oplus\text{null}(T-\lambda_2I)\oplus\dots\oplus\text{null}(T-\lambda_mI)$。也就是说 $V=E(\lambda_1,T)\oplus\dots\oplus E(\lambda_m,T)$，所以可以对角化。

> 15. 设 $T\in L(C^3)$ 使得 $6$ 和 $7$ 是 $T$ 的本征值，且 $T$ 关于 $C^3$ 的任意基的矩阵都不是对角矩阵。证明存在 $(x,y,z)\in C^3$ 使得 $T(x,y,z)=(17+8x,\sqrt5+8y,2\pi+8z)$

即要求 $T(x,y,z)-8(x,y,z)=(17,\sqrt5,2\pi)$。

只需要证明 $8$ 不是本征值。

假设 $8$ 是本征值，那么 $T$ 有三个本征值，说明 $T$ 可以被对角化，矛盾。

所以证毕。
