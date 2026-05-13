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