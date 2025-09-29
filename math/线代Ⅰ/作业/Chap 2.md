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