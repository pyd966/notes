# Chap 9 实向量空间上的算子

## 习题 9.A

> 9. 证明没有算子 $T\in L(R^7)$ 使得 $(T^2+T+I)$ 是幂零的。

反证法，如果存在这样的 $T$，那么 $\exist k\in N,(T^2+T+I)^k=0$。

所以极小多项式 $p(T)\mid (T^2+T+I)^k$，说明 $\exist s\in N,p(T)=(T^2+T+I)^s$。

那么 $p(T)$ 没有实特征值，但是 $\dim L(R^7)=7$ 是奇数维实线性空间，所以矛盾。

> 15. 设 $V$ 是实向量空间，$T\in L(V)$ 没有本征值。证明：$V$ 的每个在 $T$ 下不变的子空间都是偶数维的。

假设 $V$ 存在一个奇数维不变子空间 $U\le V$。

考虑 $\left.T\right|_U$，由于这是一个定义在奇数维实线性空间上的算子，所以它有实本征值 $\lambda$，也就是说 $\exist v\in U,v\neq0,\left.T\right|_Uv=\lambda v$，也就是说 $Tv=\lambda v$，与没有本征值矛盾。

> 19. 设 $V$ 是实向量空间，$\dim V=n,T\in L(V)$ 使得 $\text{null}T^{n-2}\neq\text{null}T^{n-1}$。证明：$T$ 最多有两个不同的本征值，$T_C$ 没有非实的本征值。

由于 $\text{null}T^{n-2}\neq\text{null}T^{n-1}$，所以 $\dim\text{null}T^{n-1}\ge n-1$，所以 $\dim\text{range}T^{n-1}\le 1$

假设它有三个不同本征值 $\lambda_1,\lambda_2,\lambda_3$，那么至少 $\lambda_1,\lambda_2\neq0$。

所以存在 $v_1,v_2\neq0$，$Tv_1=\lambda_1v_1,Tv_2=\lambda_2v_2$。

也就是说 $T^{n-1}v_1=\lambda_1^{n-1}v_1,T^{n-1}v_2=\lambda_2^{n-1}v_2$，并且 $\lambda_1v_1,\lambda_2^{n-1}v_2$ 线性无关，与 $\dim\text{range}T^{n-1}\le 1$ 矛盾。

所以 $T$ 有多有两个不同的本征值。

考虑到取 $\lambda_1=0$ 时，我们发现 $\dim\text{null}(T-\lambda_1)^{n-1}\ge n-1$，也就是说 $\lambda_1$ 的代数重数 $\ge n-1$，那么对 $T_C$ 而言 $0$ 的代数重数也 $\ge n-1$。

如果 $T_C$ 有非实本征值，它们一定成对出现，导致 $T_C$ 的本征值数目 $\ge n+1$，不可能。

## 习题 9.B

> 3. 设 $V$ 是实内积空间。对 $u,v,x,y\in V$ 定义
>
> $$
\left<u+iv,x+iy\right>=\left<u,x\right>+\left<v,y\right>+(\left<v,x\right>-\left<u,y\right>)i
> $$
>
> 证明：这是 $V_C$ 上的复内积。

考虑 $V_C$ 上两个向量 $u+iv,x+iy$。

考虑这两个向量的复内积 $\left<u+iv,x+iy\right>=\left<u,x+iy\right>+i\left<v,x+iy\right>=\left<u,x\right>-i\left<u,y\right>+i\left<v,x\right>+\left<v,y\right>=\left<u,x\right>+\left<v,y\right>+i(\left<v,x\right>-\left<u,y\right>)$。

与上述定义一致。

> 8. 设 $D$ 是 7.A 节习题 21 中向量空间 $V$ 上的微分算子。求 $V$ 的一个规范正交基使得正规算子 $D$ 的矩阵具有 9.34 中的形式。

容易发现，记 $U_0=L(1),U_1=L(\sin x,\cos x),\dots,U_n=L(\sin^nx,\cos^nx)$，那么 $V=U_0\oplus\dots\oplus U_n$，并且每个 $U_i$ 都是 $D$ 上的不变子空间。

在 $U_0$ 上选择 $1$，在 $U_k$ 上选择 $\dfrac1{\sqrt\pi}\cos kx,\dfrac1{\sqrt\pi}\sin kx$，容易证明它们合起来构成规范正交基。

并且可以验证这组规范正交基下矩阵满足条件。