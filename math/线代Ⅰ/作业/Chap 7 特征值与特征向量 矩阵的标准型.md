## 习题

> 12. 已知三维线性空间 $V$ 的线性变换 $\sigma$ 关于基 $\{\alpha_1,\alpha_2,\alpha_3\}$ 所对应的矩阵为
>
> $$
> A=\begin{pmatrix}
> 1 & 2 & -1\\
> 2 & 1 & 0\\
> 3 & 0 & 1\\
> \end{pmatrix}
> $$
>
> $(1)$ 求 $\sigma$ 在基 $\{\beta_1,\beta_2,\beta_3\}$ 下对应的矩阵 $B$，其中：
>
> $$
> \beta_1=2\alpha_1+\alpha_2+3\alpha_3\\
> \beta_2=\alpha_1+\alpha_2+2\alpha_3\\
> \beta_3=-\alpha_1+\alpha_2+\alpha_3\\
> $$
>
> $(2)$ 求 $\sigma$ 的值域 $\sigma(V)$ 和核 $\ker\sigma$。
>
> $(3)$ 把 $\sigma(V)$ 的基扩充为 $V$ 的基，并求 $\sigma$ 在这个基下对应的矩阵。
>
> $(4)$ 把 $\ker\sigma$ 的基扩充为 $V$ 的基，并求 $\sigma$ 在这个基下对应的矩阵。

$(1)$

$$
(\beta_1,\beta_2,\beta_3)=(\alpha_1,\alpha_2,\alpha_3)\begin{pmatrix}2 & 1 & -1\\ 1 & 1 & 1\\ 3 & 2 & 1\\\end{pmatrix}
$$

记过渡矩阵为 $P$，则 $B=P^{-1}AP$。

$$
B=\begin{pmatrix}2 & 1 & -1\\1 & 1 & 1\\ 3 & 2 & 1\\\end{pmatrix}^{-1}\begin{pmatrix}1 & 2 & -1\\ 2 & 1 & 0\\ 3 & 0 & 1\\\end{pmatrix}\begin{pmatrix}2 & 1 & -1\\ 1 & 1 & 1\\ 3 & 2 & 1\\\end{pmatrix}=\begin{pmatrix}2 & 0 & -1\\ 0 & 2 & 1\\ 3 & 1 & -1\\\end{pmatrix}
$$

$(2)$

记 $A=(\beta_1,\beta_2,\beta_3)$，可以发现 $\beta_1=2\beta_2+3\beta_3$，并且 $\beta_2,\beta_3$ 线性无关。

所以 $\sigma(V)=L(2\alpha_1+\alpha_2,-\alpha_1+\alpha_3)$。

$\forall\bold{x}\in\ker\sigma$，记它的坐标为 $\bold{y}$，则 $A\bold{y}=0$。

解方程，得到 $\bold{y}=\lambda(1,-2,-3)^T$，所以 $\bold{x}=\lambda(\alpha_1-2\alpha_2-3\alpha_3)$，其中 $\lambda\in R$。

也即 $\ker\sigma=L(\alpha_1-2\alpha_2-3\alpha_3)$。

$(3)$

记 $\eta_1=2\alpha_1+\alpha_2,\eta_2=-\alpha_1+\alpha_3$。

求 $\{\eta_1,\eta_2,\epsilon_1,\epsilon_2,\epsilon_3\}$ 的极大线性无关组，得到 $\{\epsilon_1,\eta_1,\eta_2\}$，这也是 $V$ 的一组基。

过渡矩阵 $P'=\begin{pmatrix}1 & 2 & -1\\ 0 & 1 & 0\\ 0 & 0 & 1\\\end{pmatrix}$

$\sigma$ 对应的矩阵 $C=(P')^{-1}AP'=\begin{pmatrix}0 & 0 & 0\\ 2 & 5 & -2\\ 3 & 6 & -2\\\end{pmatrix}$

$(4)$

记 $\gamma_1=\alpha_1-2\alpha_2-3\alpha_3$。

求 $\{\epsilon_1,\epsilon_2,\epsilon_3,\gamma_1\}$ 的极大线性无关组，得到 $\{\epsilon_1,\epsilon_2,\gamma_1\}$，这也是 $V$ 的一组基。

过渡矩阵 $Q=\begin{pmatrix}1 & 0 & 1\\ 0 & 1 & -2\\ 0 & 0 & -3\\\end{pmatrix}$

$\sigma$ 对应的矩阵 $D=\begin{pmatrix}2 & 2 & 0\\ 0 & 1 & 0\\ -1 & 0 & 0\\\end{pmatrix}$

> 16. 设 $V(C)$ 是一个线性空间，$B=\{\alpha_1,\alpha_2,\dots,\alpha_n\}$ 是 $V$ 的基；$\sigma\in L(V,V)$，已知 $\sigma$ 在基 $B$ 下对应的矩阵 $A$ 如下，试求 $\sigma$ 的特征值与特征向量（只要求特征子空间的基）：
>
> $(3)\begin{pmatrix}4 & 5 & -2\\ -2 & -2 & 1\\ -1 & -1 & 1\\\end{pmatrix}$

$(3)$

$$
\begin{aligned}
|\lambda E-A|&=\begin{vmatrix}
\lambda-4 & -5 & 2\\
2 & \lambda+2 & -1\\
1 & 1 & \lambda-1
\end{vmatrix}
\\
&=\begin{vmatrix}
\lambda & 2\lambda-1 & 0\\
2 & \lambda+2 & -1\\
1 & 1 & \lambda-1\\
\end{vmatrix}\\
&=\lambda\begin{vmatrix}\lambda+2 & -1\\ 1 & \lambda-1\\\end{vmatrix}-(2\lambda-1)\begin{vmatrix}2 & -1\\ 1 & \lambda-1\end{vmatrix}\\
&=\lambda^3-3\lambda^2+3\lambda-1\\
&=(\lambda-1)^3
\end{aligned}
$$

令 $|\lambda E-A|=0$ 得特征值 $\lambda_1=1$。

求特征向量：$(\lambda_1E-A)X=0$，解得 $X=k(-1,1,1)^T,k\in R$。

所以特征子空间的一组基为 $\{(-1,1,1)\}$。

> 17. 设
>
> $$
> A=\begin{pmatrix}
> 7 & 4 & -1\\
> 4 & 7 & -1\\
> -4 & -4 & x\\
> \end{pmatrix}
> $$
>
> 试求 $x$ 的值，使 $\lambda_1=3$ 是 $A$ 的二重特征值，并求另一个特征值 $\lambda_2$ 及两个特征子空间的基。

求特征多项式

$$
\begin{aligned}
|\lambda E-A|&=\begin{vmatrix}\lambda-7 & -4 & 1\\ -4 & \lambda-7 & 1\\ 4 & 4 & \lambda-x\end{vmatrix}\\
&=\begin{vmatrix}\lambda-3 & 3-\lambda & 0\\ -4 & \lambda-7 & 1\\ 4 & 4 & \lambda-x\end{vmatrix}\\
&=\begin{vmatrix}\lambda-3 & 0 & 0\\ -4 & \lambda-11 & 1\\ 4 & 8 & \lambda-x\\\end{vmatrix}\\
&=(\lambda-3)\begin{vmatrix}\lambda-11 & 1\\ 8 & \lambda-x\\\end{vmatrix}\\
&=(\lambda-3)(\lambda^2-(11+x)\lambda+11x-8)
\end{aligned}
$$

由题知，$\lambda_1^2-(11+x)\lambda_1+11x-8=0$，所以 $x=4$。

所以特征多项式 $f(\lambda)=(\lambda-3)^2(\lambda-12)$。

因此另一个特征值 $\lambda_2=12$。

解方程 $(\lambda_1 E-A)X=0$，得 $V_{\lambda_1}=L((1,0,4),(0,1,4))$。

解方程 $(\lambda_2 E-A)X=0$，得 $V_{\lambda_2}=L((1,1,-1))$。

> 23. 已知：三阶矩阵 $A$ 的特征值 $\lambda_1=1$（二重），$\lambda_2=-2$；属于 $\lambda_1$ 的特征向量有 $X_1=(1,-1,0)^T,X_2=(1,0,-1)^T$；属于 $\lambda_2$ 的特征向量有 $X_3=(1,1,1)^T$。问 $A$ 可否对角化？如果能对角化，求出 $A$ 及 $A^k$（$k$ 为正整数）。

$2+1=3$，所以 $A$ 可以对角化。

已知 $(\lambda_1 E-A)X_1=(\lambda_1E-A)X_2=(\lambda_2E-A)X_3=0$。

将 $A$ 的元素视为未知数，解方程可得 $A=\begin{pmatrix}0 & -1 & -1\\ -1 & 0 & -1\\ -1 & -1 & 0\\\end{pmatrix}$。

取 $P=\begin{pmatrix}1 & 1 & 1\\ -1 & 0 & 1\\ 0 & -1 & 1\\\end{pmatrix}$。

我们知道 $P^{-1}AP=\begin{pmatrix}1\\ & 1\\ & & -2\end{pmatrix}$。

所以 $P^{-1}A^kP=(P^{-1}AP)^k=\text{diag}(1,1,-2)^k=\text{diag}(1^k,1^k,(-2)^k)$

所以 $A^k=P\text{diag}(1,1,(-2)^k)P^{-1}=\begin{pmatrix}\dfrac{2+(-2)^k}3 & \dfrac{-1+(-2)^k}3 & \dfrac{-1+(-2)^k}3\\ \dfrac{-1+(-2)^k}3 & \dfrac{2+(-2)^k}3 & \dfrac{-1+(-2)^k}3\\ \dfrac{-1+(-2)^k}3 & \dfrac{-1+(-2)^k}3 & \dfrac{2+(-2)^k}3\end{pmatrix}$

> 37. 用配方法将下列二次型 $X^TAX$ 化为标准型，并给出坐标变换 $X=CY$ 的变换矩阵 $C$。
>
> $(4)A=\begin{pmatrix}1 & 3 & -2 & 0\\ 3 & 7 & 0 & -2\\ -2 & 0 & -4 & -4\\ 0 & -2 & -4 & -1\\\end{pmatrix}$

$(4)$

$$
\begin{aligned}
f(X)=X^TAX&=x_1^2+7x_2^2-4x_3^2-x_4^2+6x_1x_2-4x_1x_3-4x_2x_4-8x_3x_4\\
&=(x_1+3x_2-2x_3)^2-2x_2^2-8x_3^2-x_4^2-4x_2x_4+12x_2x_3-8x_3x_4\\
&=(x_1+3x_2-2x_3)^2-2(x_2-3x_3+x_4)^2+10x_3^2-20x_3x_4+x_4^2\\
&=(x_1+3x_2-2x_3)^2-2(x_2-3x_3+x_4)^2+10(x_3-x_4)^2-9x_4^2\\
\end{aligned}
$$

记 

$$
\begin{pmatrix}y_1\\ y_2\\ y_3\\ y_4\end{pmatrix}=\begin{pmatrix}1 & 0 & 0 & 0\\ 3 & 1 & 0 & 0\\ -2 & -3 & 1 & 0\\ 0 & 1 & -1 & 1\\\end{pmatrix}\begin{pmatrix}x_1\\ x_2\\ x_3\\ x_4\\\end{pmatrix}
$$

所以

$$
X=\begin{pmatrix}1 & 0 & 0 & 0\\ 3 & 1 & 0 & 0\\ -2 & -3 & 1 & 0\\ 0 & 1 & -1 & 1\\\end{pmatrix}^{-1}Y=\begin{pmatrix}1 & 0 & 0 & 0\\ -3 & 1 & 0 & 0\\ -7 & 3 & 1 & 0\\ -4 & 2 & 1 & 1\\\end{pmatrix}Y
$$

> 43. 求下列二次型中的参数 $t$，使二次型正定：
>
> $(1)5x_1^2+x_2^2+tx_3^2+4x_1x_2-2x_1x_3-2x_2x_3$
>
> $(2)x_1^2+x_2^2+3x_3^2+2tx_1x_2+2x_1x_3$

$(1)$

对应的矩阵 $A=\begin{pmatrix}5 & 2 & -1\\ 2 & 1 & -1\\ -1 & -1 & t\\\end{pmatrix}$。

为了使二次型正定，需要三个顺序主子式为正。

$$
S_1=\begin{vmatrix}5\end{vmatrix}=5\\
S_2=\begin{vmatrix}5 & 2\\ 2 & 1\end{vmatrix}=1\\
S_3=\begin{vmatrix}5 & 2 & -1\\ 2 & 1 & -1\\ -1 & -1 & t\\\end{vmatrix}=2-t\\
$$

令 $S_3>0$，解得 $t<2$。

$(2)$

对应的矩阵 $A=\begin{pmatrix}1 & t & 1\\ t & 1 & 0\\ 1 & 0 & 3\\\end{pmatrix}$。

$$
S_1=\begin{vmatrix}1\end{vmatrix}=1\\
S_2=\begin{vmatrix}1 & t\\ t & 1\\\end{vmatrix}=1-t^2\\
S_3=\begin{vmatrix}1 & t & 1\\ t & 1 & 0\\ 1 & 0 & 3\\\end{vmatrix}=2-3t^2\\
$$

令 $S_2,S_3>0$，得 $t\in(-\dfrac{\sqrt6}3,\dfrac{\sqrt6}3)$

> 48. 设 $A,B$ 皆是 $n$ 阶正定矩阵；$k,l$ 都是正数，用定义证明 $kA+tB$ 也是正定矩阵。

$\forall X\neq0$，

$$
X^T(kA+tB)X=kX^TAX+tX^TBX>0
$$

所以 $kA+tB$ 也是正定矩阵。

> 53. 设 $A$ 是 $n$ 阶正定矩阵，$X=(x_1,x_2,\dots,x_n)^T$，证明：
>
> $$
> f(x)=\det\begin{pmatrix}0 & X^T\\ X & A\\ \end{pmatrix}
> $$
>
> 是一个负定二次型。

$$
f(x)=\det\begin{pmatrix}0 & X^T\\ X & A\\\end{pmatrix}=\det A\det(-XA^{-1}X^T)=-(\det A)(XA^{-1}X^T)
$$

因为 $A$ 是正定矩阵，所以 $A^{-1}$ 也是正定矩阵。

$\forall X\neq0$，$XA^{-1}X^T>0$，所以 $f(x)<0$。

