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

