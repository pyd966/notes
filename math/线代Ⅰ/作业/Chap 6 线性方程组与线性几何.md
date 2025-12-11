## 习题

> 3. 求一个齐次线性方程组 $AX=0$，使其解空间 $N(A)=L(X_1,X_2)$，其中：
>
> $$
> X_1=(1,2,-1,4)^T,\quad X_2=(1,0,-4,0)^T
> $$

设方程 $a_1x_1+a_2x_2+a_3x_3+a_4x_4=0$ 满足 $X_1,X_2$ 都是它的解。

那么有 $\begin{cases}a_1+2a_2-a_3+4a_4=0\\ a_1-4a_3=0\\\end{cases}$

写出增广矩阵

$$
\begin{pmatrix}
1 & 2 & -1 & 4 & 0\\
1 & 0 & -4 & 0 & 0\\
\end{pmatrix}
$$

解得 $(a_1,a_2,a_3,a_4)^T=k_1(4,-\dfrac32,1,0)^T+k_2(0,-2,0,1)\quad (k_1,k_2\in R)$。

所以取 $A=\begin{pmatrix}4 & -\dfrac32 & 1 & 0\\ 0 & -2 & 0 & 1\\ \end{pmatrix}$，经验证满足条件。

> 6. 设 $A,B$ 分别是 $m\times n$ 和 $n\times s$ 矩阵，证明：
>
> 若方程组 $(AB)X=0$ 与 $BX=0$ 同解，则 $r(AB)=r(B)$。

$r(AB)+\dim\ker(AB)=s$

$r(B)+\dim\ker(B)=s$

由于同解，我们知道 $\ker(AB)=\ker(B)$。

两式相减，可以得到 $r(AB)=r(B)$。

> 9. 证明：若 $A$ 是 $n$ 阶幂等矩阵（即 $A^2=A$），则 $r(A)+r(E-A)=n$。

由 $A^2=A$ 可知 $A(E-A)=O$。

所以 $0=r(A(E-A))\ge r(A)+r(E-A)-n$，即 $r(A)+r(E-A)\le n$。

另一方面，

$\forall X\in N(E-A)$，有 $(E-A)X=O$，即 $AX=X$，说明 $X\in C(A)$。

所以 $N(E-A)\subseteq C(A)$，也就是说 $\dim N(E-A)\le \dim C(A)=r(A)$。

即 $n-r(E-A)\le r(A)$，所以 $r(A)+r(E-A)\ge n$。

综上，$r(A)+r(E-A)=n$。

> 12. 求参数 $t,p$ 的值，使方程组有唯一解，有无穷多数，无解；有解时，求其解：
>
> $(1)$ $\begin{cases}tx_1+x_2+x_3=1\\ x_1+tx_2+x_3=t\\ x_1+x_2+tx_3=t^2\\\end{cases}$
>
> $(2)$ $AX=b$，其中 $A=\begin{pmatrix}1 & 1 & 1 & 1 & 1\\ 3 & 2 & 1 & 1 & -3\\ 0 & 1 & 2 & 2 & 6\\ 5 & 4 & 3 & 3 & -1\\ \end{pmatrix},b=(1,t,3,p)^T$。

$(1)$

增广矩阵

$$
\begin{pmatrix}
t & 1 & 1 & 1\\
1 & t & 1 & t\\
1 & 1 & t & t^2\\
\end{pmatrix}
$$

进行初等行变换，得到

$$
\begin{pmatrix}
1 & 1 & t & t^2\\
0 & t-1 & 1-t & t(1-t)\\
0 & 0 & (1-t)(2+t) & (1+t)^2(1-t)\\
\end{pmatrix}
$$

$1\degree$ 如果 $t=1$，方程只剩下 $x_1+x_2+x_3=1$，解得 $(x_1,x_2,x_3)^T=k_1(-1,1,0)^T+k_2(-1,0,1)^T\quad (k_1,k_2\in R)$。

$2\degree$ 如果 $t=-2$，其中一个方程化为 $0=3$ 矛盾，无解。

$3\degree$ 如果 $t\neq1,-2$，解得 $(x_1,x_2,x_3)^T=(\dfrac{1+t}{2+t},\dfrac1{2+t},\dfrac{(1+t)^2}{2+t})^T$。

$(2)$

增广矩阵

$$
\begin{pmatrix}
1 & 1 & 1 & 1 & 1 & 1\\
3 & 2 & 1 & 1 & -3 & t\\
0 & 1 & 2 & 2 & 6 & 3\\
5 & 4 & 3 & 3 & -1 & p\\
\end{pmatrix}
$$

初等行变换，得到

$$
\begin{pmatrix}
1 & 1 & 1 & 1 & 1 & 1\\
0 & 1 & 2 & 2 & 6 & 3\\
0 & 0 & 0 & 0 & 0 & -t\\
0 & 0 & 0 & 0 & 0 & 2-p\\
\end{pmatrix}
$$

$1\degree$ 如果 $t=0,p=2$，解得 $(x_1,x_2,x_3,x_4,x_5)^T=(-2,3,0,0,0)^T+k_1(1,-2,1,0,0)^T+k_2(1,-2,0,1,0)^T+k_3(5,-6,0,0,1)^T\quad (k_1,k_2,k_3\in R)$。

$2\degree$ 如果 $t\neq0$ 或者 $p\neq 2$，此时方程组无解。