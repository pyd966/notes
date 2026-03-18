## 习题 1.C

> 13. 证明 $V$ 的三个子空间的并是 $V$ 的子空间当且仅当其中一个子空间包含另两个子空间。

充分性显然。下证必要性。

记三个子空间为 $U_1,U_2,U_3$，分类讨论。

$1\degree$，如果 $\exist i\neq j,U_i\subseteq U_j$，记另一个子空间为 $U_k$。

则 $U_1\cup U_2\cup U_3=U_j\cup U_k$ 为子空间。

则 $U_k\subseteq U_j$ 或者 $U_j\subseteq U_k$，无论哪种都能得到结论。

$2\degree$，如果 $\forall i\neq j,U_i\not\subseteq U_j$。，记 $\alpha_{ij}$ 满足 $\alpha_{ij}\in U_i,\alpha_{ij}\not\in U_j$。

考察 $\alpha_{12}+\alpha_{21}\in U_1\cup U_2\cup U_3$，若它属于 $U_1$，则 $\alpha_{21}\in U_1$ 矛盾，同理也不属于 $U_2$。

所以 $\alpha_{12}+\alpha_{21}\in U_3$。

同理，$2\alpha_{12}+\alpha_{21}\in U_3$。

所以 $\alpha_{12}\in U_3$，同理 $\alpha_{21}\in U_3$。

因此不存在独属于某一子空间的向量。

下面记 $\beta_{ij}$ 表示满足 $\beta_{ij}\in U_i,\beta_{ij}\in U_j,\beta_{ij}\not\in U_k$ 的向量。我们证明 $\beta_{12},\beta_{13},\beta_{23}$ 不可能同时存在。

假设同时存在，考察 $\beta_{12}+\beta_{13}+\beta_{23}\in U_1\cup U_2\cup U_3$。

若 $\beta_{12}+\beta_{13}+\beta_{23}\in U_1$，则 $\beta_{23}\in U_1$ 矛盾。

所以不能同时存在。

不妨假设 $\beta_{12}$ 不存在，则独属于 $U_1,U_2,U_3$ 的均不存在，且恰属于 $U_1,U_2$ 的也不存在，也就是说 $\forall x\in U_1$ 有 $x\in U_3$，同理 $\forall x\in U_2$ 有 $x\in U_3$。

所以 $U_1\subseteq U_3,U_2\subseteq U_3$。

> 21. 设 $U=\{(x,y,x+y,x-y,2x)\in F^5\mid x,y\in F\}$，找出 $F^5$ 的一个子空间 $W$ 使得 $F^5=U\oplus W$。

找到 $U$ 的一组基 $B=\{(1,0,1,1,2),(0,1,1,-1,0)\}$，将其扩充为 $F^5$ 的一组基。

对 $\begin{pmatrix}1 & 0 & 1 & 0 & 0 & 0 & 0\\ 0 & 1 & 0 & 1 & 0 & 0 & 0\\ 1 & 1 & 0 & 0 & 1 & 0 & 0\\1 & -1 & 0 & 0 & 0 & 1 & 0\\2 & 0 & 0 & 0 & 0 & 0 & 1\end{pmatrix}$ 求行简化阶梯型，最终得到扩充的基 $B_2=\{(1,0,1,1,2),(0,1,1,-1,0),(1,0,0,0,0),(0,1,0,0,0),(0,0,1,0,0)\}$。

所以取 $W=L(\{(1,0,0,0,0),(0,1,0,0,0),(0,0,1,0,0)\})$ 即可。

> 22. 设 $U=\{(x,y,x+y,x-y,2x)\in F^5\mid x,y\in F\}$，找出 $F^5$ 的三个非 $\{0\}$ 子空间 $W_1,W_2,W_3$ 使得 $F^5=U\oplus W_1\oplus W_2\oplus W_3$。

由 21. 知，只需取 $W_1=L(\{(1,0,0,0,0)\}),W_2=L(\{(0,1,0,0,0)\}),W_e=L(\{(0,0,1,0,0)\})$ 即可。