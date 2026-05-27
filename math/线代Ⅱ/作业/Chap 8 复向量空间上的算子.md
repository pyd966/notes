# Chap 8 复向量空间上的算子

## 习题 8.A

> 15. 设 $N\in L(V)$ 使得 $\text{null}N^{\dim V-1}\neq\text{null}N^{\dim V}$。证明：$N$ 是幂零的，并且对每个满足 $0\le j\le\dim V$ 的整数 $j$ 都有 $\dim\text{null}N^j=j$。

假设 $\exist 0\le i<\dim V$ 使得 $\text{null}N^i=\text{null}N^{i+1}$

那么此后零空间停止增长，即 $\text{null}N^{\dim V-1}=\text{null}N^{\dim V}$，矛盾。

所以 $\forall 0\le i<\dim V$，都有 $\text{null}N^i\neq\text{null}N^{i+1}$。

也就是说 $\{0\}=\text{null}N^0\subsetneq\text{null}N^1\subsetneq\dots\subsetneq\text{null}N^{\dim V}$

这是说 $0=\dim\text{null}N^0<\dim\text{null}N^1<\dots<\dim\text{null}N^{\dim V}\le\dim V$。

所以 $\forall 0\le j\le\dim V$，都有 $\dim\text{null}N^j=j$。

因为 $\dim\text{null}N^{\dim V}=\dim V$，所以 $N^{\dim V}=0$，$N$ 是幂零的。

> 19. 设 $T\in L(V)$，$m$ 是非负整数。证明：
>
> $$
\text{null} T^m=\text{null} T^{m+1}\ 当且仅当\ \text{range}T^m=\text{range}T^{m+1}
> $$

容易发现 $\text{null}T^m\subseteq\text{null}T^{m+1},\text{range}T^{m+1}\subseteq\text{range}T^m$。

所以只需证明 $\dim\text{null}T^m=\dim\text{null}T^{m+1}\iff\dim\text{range}T^{m+1}=\dim\text{range}T^m$

而 $\dim\text{null}T^m+\dim\text{range}T^m=\dim V=\dim\text{null}T^{m+1}+\dim\text{range}T^{m+1}$，所以上面的等价式成立，原命题成立。

## 习题 8.B

> 4. 设 $V$ 是 $n$ 维复向量空间，$T$ 是 $V$ 上的算子使得 $\text{null}T^{n-2}\neq\text{null}T^{n-1}$。证明 $T$ 最多有两个不同的本征值。

假设 $T$ 有三个不同的本征值，那么有两个不同且不为零的本征值 $\lambda_1,\lambda_2$，设对应的本征向量为 $v_1,v_2$。

由题知 $\dim\text{null}T^{n-1}\ge n-1$，所以 $\dim\text{range}T^{n-1}\le 1$。

但是 $T^{n-1}v_1=\lambda_1^{n-1}v_1\neq0,T^{n-1}v_2=\lambda_2^{n-1}v_2$，且 $\lambda_1^{n-1}v_1$ 与 $\lambda_2^{n-1}v_2$ 显然线性无关，所以 $\dim\text{range}T^{n-1}\ge 2$，矛盾。

所以最多有两个不同的本征值。

> 10. 设 $F=C,T\in L(V)$。证明：存在 $D,N\in L(V)$ 使得 $T=D+N$，算子 $D$ 是对角化的，$N$ 是幂零的，$DN=ND$。

考虑取出 $T$ 的所有本征值 $\lambda_1,\dots,\lambda_s$，那么 $V=G(\lambda_1,T)\oplus\dots\oplus G(\lambda_s,T)$。

因为 $\left.(T-\lambda_iI)\right|_{G(\lambda_i,T)}$ 是幂零的，所以 $\left.T\right|_{G(\lambda_i,T)}=\lambda_iI+N_i$，其中 $N_i$ 是幂零的。

$\forall v\in V,v=v_1+\dots+v_n,v_i\in G(\lambda_i,T)$。

记 $Dv=\lambda_1v_1+\dots+\lambda_sv_s,Nv=N_1v_1+\dots+N_sv_s$，因为 $G(\lambda_i,T)$ 是 $T$ 不变的，所以 $D$ 仍然是对角化的，$N$ 仍然是幂零的，并且 $T=D+N$。

考虑 $DNv=D(N_1v_1+\dots+N_sv_s)=\lambda_1N_1v_1+\dots+\lambda_sN_sv_s=N(\lambda_1v_1+\dots+\lambda_sv_s)=NDv$，所以 $DN=ND$。

## 习题 8.C

> 10. 设 $V$ 是复向量空间，$T\in L(V)$ 是可逆的。令 $p$ 表示 $T$ 的特征多项式，$q$ 表示 $T^{-1}$ 的特征多项式。证明：对所有非零的 $z\in C$ 都有
>
> $$
q(z)=\dfrac1{p(0)}z^{\dim V}p(\dfrac1z)
> $$

记 $n=\dim V$。

记 $T$ 的矩阵为 $A$。

$q(z)=|zI-A^{-1}|=|-zA^{-1}(\dfrac1zI-A)|=(-z)^n|A^{-1}||\dfrac1zI-A|$

而 $p(\dfrac1z)=|\dfrac1zI-A|$，并且 $|A^{-1}|=|A|^{-1}=(-1)^n\dfrac1{p(0)}$

所以 $q(z)=\dfrac1{p(0)}z^np(\dfrac1z)$

> 18. 设 $a_0,\dots,a_{n-1}\in C$。设 $T\in L(C^n)$（关于标准基）的矩阵是
>
> $$
\begin{pmatrix}
0 & & & & -a_0\\
1 & 0 & & & -a_1\\
& 1 & \dots & & -a_2\\
& & \dots & & \vdots\\
& & & 0 & -a_{n-2}\\
& & & 1 & -a_{n-1}\\
\end{pmatrix}
> $$
>
> 求 $T$ 的极小多项式和特征多项式。

计算 $|\lambda I-M(T)|$ 可以发现特征多项式为 $x^n+a_{n-1}x^{n-2}+\dots+a_0$。

考虑极小多项式。

取标准基 $e_1$，那么 $Ae_1=e_2,A^2e_1=e_3,\dots,A^{n-1}e_1=e_n,A^ne_1=-a_0e_1-a_2e_1-\dots-a_{n-1}e_n$

而 $e_1,Ae_1,\dots,A^{n-1}e_1$ 线性无关，所以极小多项式次数 $\ge n$

所以极小多项式等于特征多项式。

## 习题 8.D

> 6. 设 $N\in L(V)$ 是幂零的，$v_1,\dots,v_n$ 和 $m_1,\dots,m_n$ 如 8.55 中所示。证明 $N^{m_1}v_1,\dots,N^{m_n}v_n$ 是 $\text{null}N$ 的基。

容易发现它们线性无关。

$\forall v\in\text{null}N$，因为 $v\in V$，所以 $v=a_{1,m_1}N^{m_1}v_1+\dots+a_{1,0}v_1+\dots+a_{n,m_n}N^{m_n}v_n+\dots+a_{n,0}v_n$。

计算 $Nv=a_{1,m_1-1}N^{m_1}v_1+\dots+a_{1,0}Nv_1+\dots+a_{n,m_n-1}N^{m_n}v_n+\dots+a_{n,0}Nv_n=0$。

因为这些向量线性无关，所以 $a_{1,m_1-1}=\dots=a_{1,0}=\dots=a_{n,m_n-1}=\dots=a_{n,0}=0$。

所以 $v$ 可由 $N_{m_1}v_1,\dots,N^{m_n}v_n$ 线性表示，也就是说它们是 $\text{null}N$ 的基。

> 8. 设 $V$ 是复向量空间，$T\in L(V)$。证明：$V$ 不能分解成 $V$ 的两个在 $T$ 下不变的子空间的直和当且仅当 $T$ 的极小多项式形如 $(z-\lambda)^{\dim V}$，其中 $\lambda\in C$。

$T$ 的极小多项式形如 $(z-\lambda)^{\dim V}$ 当且仅当其若当矩阵仅包含一个若当块。

下面证明：$V$ 不能分解成两个在 $T$ 下不变的子空间的直和当且仅当其若当矩阵仅包含一个若当块。

先证充分性。

记 $n=\dim V$，若当基是 $v_1,\dots,v_n$。

假设 $V=V_1\oplus V_2$，其中 $V_1,V_2$ 在 $T$ 下不变。

不妨设 $v_n\in V_1$，$Tv_n=\lambda v_n+v_{n-1}$，所以 $v_{n-1}\in V_1$，由数学归纳法，$v_1,\dots,v_n\in V_1$，那么 $V_2=\varnothing$，矛盾。

再证必要性，考虑证明其逆否命题。

考虑矩阵中有 $m$ 个若当块，它们对应的基的集合记作 $B_1,\dots,B_m$，记 $V_i=\text{span}B_i$。

那么显然它们在 $T$ 下都不变，并且 $V=V_1\oplus\dots\oplus V_m$。

所以 $V$ 可以分解。