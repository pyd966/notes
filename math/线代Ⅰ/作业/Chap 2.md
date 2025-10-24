# 习题

> 1. 检验下列集合对指定的加和数量乘法，是否构成实数域上的线性空间。
>
> $(1) \mathbb{R}^2=\{(x,y)\mid x,y\in\mathbb{R}\}$ 对通常的向量加和如下定义的数量乘法：
>
> $$
> \lambda\circ(x,y)=(\lambda x,y);
> $$
>
> $(9)$ 集合 $V$ 为区间 $[a,b]$ 上所有函数值 $\ge 0$ 的实变量函数，即
>
> $$
> V=\{f\mid f(x)\ge 0,\forall x\in[a,b]\}
> $$
>
> 对通常的函数加法与函数的乘法，即：
>
> $$
> (f\oplus g)(x)=f(x)+g(x)\\
> (\lambda\circ f)(x)=\lambda f(x)
> $$
>
> $(11) V=\{f\mid x\in\mathbb{R},f(x)\in \mathbb{C}\land f(-x)=\overline{f(x)}\}$，对 $(9)$ 所定义的加法和数量乘法。

$(1)$ 构成线性空间。

显然，向量加法构成一个 Abel 群，且 $V$ 关于数乘封闭。

接下来，只需要验证向量数乘的四条性质。

$1\degree (\lambda+\mu)(x,y)=((\lambda+\mu)x,y)=(\lambda x+\mu x,y)=\lambda(x,y)+\mu(x,y)$

$2\degree \lambda((x,y)+(s,t))=\lambda(x+s,y+t)=(\lambda(x+s),y+t)=(\lambda x+\lambda s,y+t)=(\lambda x,y)+(\lambda s,t)=\lambda(x,y)+\lambda(s,t)$

$3\degree \lambda(\mu(x,y))=\lambda(\mu x,y)=(\lambda\mu x,y)=((\lambda\mu)x,y)=(\lambda\mu)(x,y)$

$4\degree 1(x,y)=(x,y)$

$(9)$ 不构成线性空间。

容易发现，函数 $f(x)\equiv 0(x\in[a,b])$ 是函数加法的单位元。

考虑函数 $g(x)\equiv 1(x\in[a,b])$，它的逆元是 $h(x)\equiv -1(x\in[a,b])$，但 $h(x)\not\in V$，所以 $V$ 关于函数加法不构成群。

$(11)$ 构成线性空间。

先考虑 $V$ 关于加法是否构成 Abel 群。

首先，验证 $V$ 关于加法封闭。考虑 $f,g\in V$，那么显然 $h=f+g$ 仍是实变量复值函数，然后 $h(-x)=f(-x)+g(-x)=\overline{f(x)}+\overline{g(x)}=\overline{f(x)+g(x)}=\overline{h(x)}$，所以 $h\in V$。

其次，显然 $V$ 有结合律和交换律。

之后，$V$ 中存在单位元 $e(x)\equiv 0$，可以验证 $e(-x)=\overline{e(x)}$，所以 $e\in V$。

然后，对 $V$ 中任一元素 $f$，它的逆元 $f^{-1}(x)=-f(x)$。而 $f^{-1}(-x)=-f(-x)=-\overline{f(x)}=\overline{-f(x)}=\overline{f^{-1}(x)}$，所以 $f^{-1}\in V$。

这证明了 $V$ 关于加法是 Abel 群，显然 $V$ 关于数乘封闭，接下来只需要证明向量数乘的四条性质。

$1\degree (\lambda+\mu)f(x)=\lambda f(x)+\mu f(x)$ 非常显然。

$2\degree \lambda(f(x)+g(x))=\lambda f(x)+\lambda g(x)$ 也很显然。

$3\degree (\lambda\mu)f(x)=\lambda(\mu f(x))$ 也是显然的。

$4\degree 1f(x)=f(x)$ 也是显然的。

> 2. 在向量空间 $V(F)$ 中：
>
> $(1)\forall \lambda,\mu\in F,\bold{\alpha,\beta}\in V$，计算 $(\lambda-\mu)(\bold{\alpha-\beta})$
>
> $(2)$ 设 $\bold{x}\in V$，对 $\forall\bold{\alpha_i}\in V$ 及 $\forall\lambda_i\in F$（但 $\lambda_1+\dots+\lambda_n\neq 0$），求解向量方程（即求解 $\bold{x}$）：$\lambda_1(\bold{\alpha_1+x})+\dots+\lambda_n(\bold{\alpha_n+x})=\bold{0}$。

$(1)$

$$
\begin{aligned}
(\lambda-\mu)(\alpha-\beta)&=\lambda(\alpha-\beta)-\mu(\alpha-\beta)\\
&=\lambda\alpha-\lambda\beta-\mu\alpha+\mu\beta
\end{aligned}
$$

$(2)$

$$
\begin{aligned}
&\iff\lambda_1\alpha_1+\lambda_1\bold{x}+\dots+\lambda_n\alpha_n+\lambda_n\bold{x}=\bold{0}\\
&\iff (\lambda_1\alpha_1+\dots+\lambda_n\alpha_n)+(\lambda_1\bold{x}+\dots+\lambda_n\bold{x})=\bold{0}\\
&\iff(\lambda_1+\dots+\lambda_n)\bold{x}=-(\lambda_1\alpha_1+\dots+\lambda_n\alpha_n)\\
&\iff(\lambda_1+\dots+\lambda_n)^{-1}(\lambda_1+\dots+\lambda_n)\bold{x}=-(\lambda_1+\dots+\lambda_n)^{-1}(\lambda_1\alpha_1+\dots+\lambda_n\alpha_n)\\
&\iff \bold{x}=-(\lambda_1+\dots+\lambda_n)^{-1}(\lambda_1\alpha_1+\dots+\lambda_n\alpha_n)\\
\end{aligned}
$$

其中，$(\lambda_1+\dots+\lambda_n)^{-1}$ 表示 $(\lambda_1+\dots+\lambda_n)$ 在域 $F$ 中的乘法逆元。由于 $\lambda_1+\dots+\lambda_n\neq 0$，所以这是存在的。

> 4. 设 $\alpha_1,\alpha_2,\alpha_3\in R^n,c_1,c_2,c_3\in R$，如果 $c_1\alpha_1+c_2\alpha_2+c_3\alpha_3=\bold{0}$，且 $c_1c_3\neq0$，证明：$L(\alpha_1,\alpha_2)=L(\alpha_2,\alpha_3)$。

$\forall \beta\in L(\alpha_1,\alpha_2)$，设 $\beta=\lambda_1\alpha_1+\lambda_2\alpha_2$。

由于 $c_1c_3\neq0,c_1\alpha_1+c_2\alpha_2+c_3\alpha_3=0$，所以 $\alpha_1=-\dfrac{c_2}{c_1}\alpha_2-\dfrac{c_3}{c_1}\alpha_3$。

那么 $\beta=\lambda_1(-\dfrac{c_2}{c_1}\alpha_2-\dfrac{c_3}{c_1}\alpha_3)+\lambda_2\alpha_2$，所以 $\beta\in L(\alpha_2,\alpha_3)$。

所以，$L(\alpha_1,\alpha_2)\subseteq L(\alpha_2,\alpha_3)$。同理 $L(\alpha_2,\alpha_3)\subseteq L(\alpha_1,\alpha_2)$。

所以，$L(\alpha_1,\alpha_2)=L(\alpha_2,\alpha_3)$。

> 6. 设 $\alpha_1=(1,0,1),\alpha_2=(1,1,0),\alpha_3=(1,-1,2)$，问下列 $\beta_1,\beta_2$ 属于 $L(\alpha_1,\alpha_2,\alpha_3)$ 吗？如属于，它们由 $\alpha_1,\alpha_2,\alpha_3$ 线性表示唯一吗？为什么？
>
> $(1)\beta_1=(1-1,-1);(2)\beta_2=(1,2,-1)$

$(1)$

$\beta_1\not\in L(\alpha_1,\alpha_2,\alpha_3)$。

考虑方程 $\lambda_1\alpha_1+\lambda_2\alpha_2+\lambda_3\alpha_3=\beta_1$，这是一个三元一次方程组。

$$
\begin{pmatrix}
1 & 1 & 1 & 1\\
0 & 1 & -1 & -1\\
1 & 0 & 2 & -1\\
\end{pmatrix}
$$

进行高斯消元得到行简化矩阵

$$
\begin{pmatrix}
1 & 0 & 2 & 2\\
0 & 1 & -1 & -1\\
0 & 0 & 0 & -3\\
\end{pmatrix}
$$

方程组无解，所以 $\beta_1\not\in L(\alpha_1,\alpha_2,\alpha_3)$。

$(2)$

$\beta_2=-\alpha_1+2\alpha_2=3\alpha_1-2\alpha_3$，所以 $\beta_2\in L(\alpha_1,\alpha_2,\alpha_3)$，但是表示方法不唯一。

本质上，这是因为 $\alpha_3=2\alpha_1-\alpha_2$，即 $\alpha_1,\alpha_2,\alpha_3$ 线性相关。

> 7. 判断下列向量组的线性相关性：
>
> $(3)$ $R[x]_3$ 中：$p_1(x)=1,p_2(x)=(x-x_0),p_3(x)=(x-x_0)^2$，其中常数 $x_0\in R$。

线性无关。

令 $\lambda_1p_1+\lambda_2p_2+\lambda_3p_3=0$，下面证明 $\lambda_1=\lambda_2=\lambda_3=0$。

方程转化为 $(\lambda_1-\lambda_2x_0+\lambda_3x_0^2)+(\lambda_2-2\lambda_3x_0)x+\lambda_3x^2=0$。

对比系数，得到

$$
\begin{cases}
\lambda_3=0\\
\lambda_2-2\lambda_3x_0=0\\
\lambda_1-\lambda_2x_0+\lambda_3x_0^2=0\\
\end{cases}
$$

解得 $\lambda_1=\lambda_2=\lambda_3=0$，所以 $p_1,p_2,p_3$ 线性无关。

> 10. 下列命题是否正确？如正确，证明之，如不正确，举反例。

$(1)$ 若 $\alpha_1,\dots,\alpha_m(m>2)$ 线性相关，则其中每一向量都是其余向量的线性组合；

错误。

$m=4,\alpha_1=(1,0,0),\alpha_2=(0,1,0),\alpha_3=(0,0,1),\alpha_4=(0,1,1)$。

其中 $\alpha_1$ 不是其余向量的线性组合。

$(2)$ 若 $\alpha_1,\dots,\alpha_m$ 线性无关，则其中每一向量都不是其余向量的线性组合，这个命题的等价命题应如何叙述？

正确。

反证法，不妨假设 $\alpha_1=\lambda_2\alpha_2+\dots+\lambda_m\alpha_m$，移项得到 $-\alpha_1+\lambda_2\alpha_2+\dots+\lambda_m\alpha_m=0$，与它们线性无关矛盾。

所以任何一个向量都不是其余向量的线性组合。

等价命题：若 $\alpha_1,\dots,\alpha_m$ 中存在一个向量是其余向量的线性组合，那么 $\alpha_1,\dots,\alpha_m$ 线性相关。

$(3)$ $\alpha_1,\dots,\alpha_m(m>2)$ 线性无关的充要条件是任意两个向量都线性无关；

错误。

$m=3,\alpha_1=(1,0),\alpha_2=(0,1),\alpha_3=(1,1)$，任意两个向量都是线性无关的，但是它们是线性相关的。

$(4)$ 若 $\alpha_1,\alpha_2$ 线性相关，$\beta_1,\beta_2$ 线性相关，则 $\alpha_1+\beta_1,\alpha_2+\beta_2$ 也线性相关；

错误。

$\alpha_1=(0,1),\alpha_2=(0,2),\beta_1=(2,0),\beta_2=(1,0)$。

则 $\alpha_1+\beta_1=(2,1),\alpha_2+\beta_2=(1,2)$，它们是线性无关的。

$(5)$ 若 $\alpha_1,\dots,\alpha_n$ 线性无关，则 $\alpha_1+\alpha_2,\alpha_2+\alpha_3,\dots,\alpha_{n-1}+\alpha_n,\alpha_n+\alpha_1$ 也线性无关；

错误。

取 $n=4$，那么四个向量是 $\alpha_1+\alpha_2,\alpha_2+\alpha_3,\alpha_3+\alpha_4,\alpha_4+\alpha_1$。

但是 $(\alpha_1+\alpha_2)+(\alpha_3+\alpha_4)=(\alpha_2+\alpha_3)+(\alpha_4+\alpha_1)$，所以它们线性相关。

$(6)$ 若 $\alpha_1,\alpha_2,\alpha_3$ 线性相关，则 $\alpha_1+\alpha_2,\alpha_2+\alpha_3,\alpha_3+\alpha_1$ 也线性相关；

正确。

记 $\beta_1=\alpha_2+\alpha_3,\beta_2=\alpha_1+\alpha_3,\beta_3=\alpha_1+\alpha_2$。

那么 $\alpha_1=\frac12(\beta_2+\beta_3-\beta_1),\alpha_2=\frac12(\beta_1+\beta_3-\beta_2),\alpha_3=\frac12(\beta_1+\beta_2-\beta_3)$。

由于 $\alpha_1,\alpha_2,\alpha_3$ 线性相关，所以存在 $\lambda_1\alpha_1+\lambda_2\alpha_2+\lambda_3\alpha_3=0$，其中 $\lambda_1,\lambda_2,\lambda_3$ 不全为 0。

把上面的式子代入这个式子，可以得到 $\frac12(-\lambda_1+\lambda_2+\lambda_3)\beta_1+\frac12(\lambda_1-\lambda_2+\lambda_3)\beta_2+\frac12(\lambda_1+\lambda_2-\lambda_3)\beta_3=0$。

可以证明，这三个系数不会全是 0（否则 $\lambda_1=\lambda_2=\lambda_3=0$）。

因此， $\beta_1,\beta_2,\beta_3$ 线性相关。

$(7)$ 设 $B=\{\alpha_1,\alpha_2,\alpha_3\}$ 是 $R^3$ 的一组基，非零向量 $\alpha_0\in R^3$，则 $\{\alpha_0+\alpha_1,\alpha_0+\alpha_2,\alpha_0+\alpha_3\}$（其中三个向量均是非零向量）也是 $R^3$ 的一组基；

错误。

取 $\alpha_0=(-\frac13,-\frac13,-\frac13),\alpha_1=(1,0,0),\alpha_2=(0,1,0),\alpha_3=(0,0,1)$。

那么 $\alpha_0+\alpha_1=(\frac23,-\frac13,-\frac13),\alpha_0+\alpha_2=(-\frac13,\frac23,-\frac13),\alpha_0+\alpha_3=(-\frac13,-\frac13,\frac23)$。

这三个向量的和是 $(0,0,0)$，所以它们线性相关，不可能构成一组基。

$(8)$ 设 $B=\{\alpha_1,\alpha_2\}$ 是 $R^2$ 的一组基，则 $\{\alpha_1+\alpha_2,\alpha_1-\alpha_2\}$ 也是 $R^2$ 的一组基；

正确。

记 $\beta_1=\alpha_1+\alpha_2,\beta_2=\alpha_1-\alpha_2$。

那么 $\alpha_1=\frac12(\beta_1+\beta_2),\alpha_2=\frac12(\beta_1-\beta_2)$。

$\forall \gamma\in R^2$，我们知道存在 $\lambda_1,\lambda_2$，使得 $\lambda_1\alpha_1+\lambda_2\alpha_2=\gamma$。

所以 $\gamma=\frac12(\lambda_1+\lambda_2)\beta_1+\frac12(\lambda_1-\lambda_2)\beta_2$。

所以 $\{\beta_1,\beta_2\}$ 也是 $R^2$ 的一组基。

$(9)$ 一个有限维线性空间只含有有限个子空间；

错误。

考虑线性空间 $R^2$。对于任何 $\lambda\in R$，$\{(x,y)\mid x+\lambda y=0\}$ 构成子空间，然而这样子空间的个数是无限的。

$(10)$ 如果 $W_1,W_2$ 是 $R^n$ 的两个子空间，$B_1,B_2$ 分别是 $W_1,W_2$ 的基，则存在 $R^n$ 的一组基 $B$，使得 $\{B_1 \cup B_2\}\subset B$

错误。

考虑 $n=3$ 时，取 $B_1=\{(1,0,0),(0,1,0)\},B_2=\{(0,1,1),(0,0,-1)\}$，此时 $W_1=\{(x,y,0)\mid x,y\in R\},W_2=\{(0,y,z)\mid y,z\in R\}$。

然而 $B_1\cup B_2=\{(1,0,0),(0,1,0),(0,1,1),(0,0,-1)\}$ 有四个元素，但 $R^3$ 的一组基 $B$ 只能有三个元素，所以不可能有 $B_1\cup B_2\subset B$。

> 19. 求下列子空间的一组基及其维数:
>
> $(2) W_2=\{(x_1,x_2,x_3,x_4)\in R^4\mid x_1+x_2-x_3-x_4=0\}$
>
> $(5) W_5=L(\beta_1,\beta_2,\beta_3)$，其中 $\beta_1=(2,3,-1),\beta_2=(1,2,2),\beta_3=(1,1,-3)$。

$(2)$

可选的一组基是 $B_2=\{(-1,1,0,0),(1,0,1,0),(1,0,0,1)\}$。

解方程

$$
x_1+x_2-x_3-x_4=0
$$

可以得到 $(x_1,x_2,x_3,x_4)=k_2(-1,1,0,0)+k_3(1,0,1,0),k_4=(1,0,0,1)$。

所以，任何能被该方程描述的向量都能由 $B_2$ 表示。

此外，可以验证 $B_2$ 是线性无关的，故 $B_2$ 是 $W_2$ 的一组基，且 $\text{dim}W_2=3$。

$(5)$

可选的一组基是 $B_5=\{\beta_1,\beta_2\}$。

通过计算，可以发现 $\beta_3=\beta_1+\beta_2$，故 $L(\beta_1,\beta_2)=L(\beta_1,\beta_2,\beta_3)$。又可以发现 $\beta_1,\beta_2$ 是线性无关的，所以 $B_5$ 是 $W_5$ 的一组基，且 $\text{dim}W_5=2$。

> 21. 已知 $\{\alpha_1,\dots,\alpha_n\}$ 是线性空间 $V(F)$ 的一组基向量，如何求 $V(F)$ 中任一向量关于这一组基的坐标。

通常而言，当我们知道这组基向量的时候，我们是以知道它们在另一组基下的坐标的方式来知道的。

这是，我们可以解方程 $\bold{x}=c_1\alpha_1+c_2\alpha_2+\dots+c_n\alpha_n$，这个方程可以拆成 $n$ 元 $n$ 次方程组，由于 $\alpha_1,\dots,\alpha_n$ 线性无关，这个方程组有唯一解，此时 $\bold{x}$ 的坐标就是 $(c_1,c_2,\dots,c_n)$。

> 22. 证明：$\alpha_1=(1,0,1),\alpha_2=(1,1,0),\alpha_3=(0,1,1)$ 是 $R^3$ 的一组基，并求 $\beta=(1,-2,4)$ 关于这组基的坐标。

证明：

$\forall \alpha\in R^3$，设 $\alpha=(x_1,x_2,x_3)$，通过计算可以发现 $\alpha=\dfrac{x_1+x_3-x_2}{2}\alpha_1+\dfrac{x_1+x_2-x_3}{2}\alpha_2+\dfrac{x_2+x_3-x_1}{2}\alpha_3$，所以这组向量可以线性表示 $R^3$。

另一方面，解方程组可以验证这组向量是线性无关的。所以它们是 $R^3$ 的一组基。

通过计算，$\beta=\dfrac72\alpha_1-\dfrac52\alpha_2+\dfrac12\alpha_3$，所以 $\beta$ 关于这组基的坐标是 $(\dfrac72,-\dfrac52,\dfrac12)$。

> 31. 已知：$\alpha=(1,2,-1,1),\beta=(2,3,1,-1),\gamma=(-1,-1,-2,2)$；
>
> $(1)$ 求 $\alpha,\beta,\gamma$ 的长度及夹角 $\langle\alpha,\beta\rangle$ 与 $\langle\alpha,\gamma\rangle$ 
>
> $(2)$ 求与 $\alpha,\beta,\gamma$ 都正交的所有向量。

$(1)$

$|\alpha|=\sqrt{1^2+2^2+(-1)^2+1^2}=\sqrt{7}$

$|\beta|=\sqrt{2^2+3^2+1^2+(-1)^2}=\sqrt{15}$

$|\gamma|=\sqrt{(-1)^2+(-1)^2+(-2)^2+2^2}=\sqrt{10}$

$\langle\alpha,\beta\rangle=\arccos\dfrac{\alpha\cdot\beta}{|\alpha||\beta|}=\arccos\dfrac{6}{\sqrt{105}}=\arccos\dfrac{2\sqrt{105}}{35}$

$\langle\alpha,\gamma\rangle=\arccos\dfrac{\alpha\cdot\gamma}{|\alpha||\gamma|}=\arccos\dfrac{1}{\sqrt{70}}=\arccos\dfrac{\sqrt{70}}{70}$

$(2)$

设 $\bold{x}=(x_1,x_2,x_3,x_4)$

由题意知

$$
\begin{cases}
\alpha\cdot\bold{x}=0\\
\beta\cdot\bold{x}=0\\
\gamma\cdot\bold{x}=0\\
\end{cases}
$$

即 

$$
\begin{cases}
x_1+2x_2-x_3+x_4&=0\\
2x_1+3x_2+x_3-x_4&=0\\
-x_1-x_2-2x_3+2x_4&=0\\
\end{cases}
$$

解这个方程组，得到 $(x_1,x_2,x_3,x_4)=\lambda(-5,3,1,0)+\mu(5,-3,0,1)$

所以，与 $\alpha,\beta,\gamma$ 都垂直的向量最终构成 $L((-5,3,1,0),(5,-3,0,1))$。

> 37. 设 $\{\epsilon_1,\epsilon_2,\dots,\epsilon_5\}$ 是欧氏空间 $V$ 的一组单位正交基，$W=L(\alpha_1,\alpha_2,\alpha_3)$，其中 $\alpha_1=\epsilon_1+\epsilon_5,\alpha_2=\epsilon_1-\epsilon_2+\epsilon_4,\alpha_3=2\epsilon_1+\epsilon_2+\epsilon_3$。试求 $W$ 的一组单位正交基。

首先，容易验证 $\alpha_1,\alpha_2,\alpha_3$ 线性无关。

我们使用 Schmitdt 正交化过程。

$\beta_1=\alpha_1=\epsilon_1+\epsilon_5$

$\beta_2=\alpha_2-\dfrac{\beta_1\cdot\alpha_2}{\beta_1^2}\beta_1=\alpha_2-\dfrac12\beta_1=\dfrac12(\epsilon_1-2\epsilon_2+2\epsilon_4-\epsilon_5)$

$\beta_3=\alpha_3-\dfrac{\beta_1\cdot\alpha_3}{\beta_1^2}\beta_1-\dfrac{\beta_2\cdot\alpha_3}{\beta_2^2}\beta_2=\alpha_3-\beta_1=\epsilon_1+\epsilon_2+\epsilon_3-\epsilon_5$

最后单位化。

$\gamma_1=\dfrac{\beta_1}{|\beta_1|}=\dfrac{\sqrt2}{2}(\epsilon_1+\epsilon_5)$

$\gamma_2=\dfrac{\beta_2}{|\beta_2|}=\dfrac{\sqrt{10}}{10}(\epsilon_1-2\epsilon_2+2\epsilon_4-\epsilon_5)$

$\gamma_3=\dfrac{\beta_3}{|\beta_3|}=\dfrac{1}{2}(\epsilon_1+\epsilon_2+\epsilon_3-\epsilon_5)$



> 40. 设 $\{\epsilon_1,\dots,\epsilon_n\}$ 是 $n$ 维欧氏空间 $V$ 的一组单位正交基，证明：
>
> $(1)$ 如果 $\beta\in V$，且 $(\beta,\epsilon_i)=0(i=1,\dots,n)$，则 $\beta=0$；
>
> $(2)$ 如果 $\beta_1,\beta_2\in V$，且 $\forall\alpha\in V$，均有 $(\beta_1,\alpha)=(\beta_2,\alpha)$，则 $\beta_1=\beta_2$。

$(1)$

设 $\beta=\lambda_1\epsilon_1+\dots+\lambda_n\epsilon_n$

由题知，$0=(\beta,\epsilon_i)=(\lambda_1\epsilon_1+\dots+\lambda_n\epsilon_n,\epsilon_i)=(\lambda_1\epsilon_1,\epsilon_i)+\dots+(\lambda_n\epsilon_n,\epsilon_i)=\lambda_i(i=1,\dots,n)$

也就是说，$\beta=0$。

$(2)$

设 $\beta_1=\lambda_1\epsilon_1+\dots+\lambda_n\epsilon_n,\beta_2=\mu_1\epsilon_1+\dots+\mu_n\epsilon_n$。

依次取 $\alpha=\epsilon_i(i=1,\dots,n)$

由 $(\beta_1,\alpha)=(\beta_2,\alpha)$，即 $(\beta_1,\epsilon_i)=(\beta_2,\epsilon_i)$，可以得到 $\lambda_i=\mu_i$。

也就是说，$\beta_1=\beta_2$。