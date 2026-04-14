## 习题 16.1

> 1. 判断下列平面点集中哪些是开集、闭集、有界集，并分别指出它们的聚点与界点。
>
> $(5)$ $\{(x,y)\mid x<2,y<2,x+y>2\}$
>
> $(7)$ $\{(x,y)\mid x^2+y^2\le1 或 y=0,1\le x\le 2\}$
>
> $(9)$ $\{(x,y)\mid y=\sin\dfrac1x,x>0\}$

$(5)$

开集、有界集。

聚点：$\{(x,y)\mid x\le2,y\le2,x+y\ge2\}$

界点：$\{(x,y)\mid x=2,0\le y\le 2或y=2,0\le x\le2或x+y=2,0\le x\le2\}$

$(7)$

闭集，有界集。

聚点：$\{(x,y)\mid x^2+y^2\le1或y=0,1\le x\le2\}$

界点：$\{(x,y)\mid x^2+y^2=1或y=0,1\le x\le2\}$

$(9)$

不开不闭。

聚点：$\{(x,y)\mid x=0,-1\le y\le1或y=\sin\dfrac1x,x>0\}$

界点：$\{(x,y)\mid x=0,-1\le y\le1或y=\sin\dfrac1x,x>0\}$

> 2. 试问集合 $\{(x,y)\mid 0<|x-a|<\delta,0<|y-b|<\delta\}$ 与集合 $\{(x,y)\mid |x-a|<\delta,|y-b|<\delta,(x,y)\neq(a,b)\}$ 是否相同。

并不相同。

例如 $(a,b+\frac\delta2)$ 不在第一个集合里，但是在第二个集合里。

> 9. 求下列各函数的定义域，画出定义域的图像，并说明是何种点集：
>
> $(4)$ $f(x,y)=\sqrt{1-x^2}+\sqrt{y^2-1}$
>
> $(6)$ $f(x,y)=\sqrt{\sin(x^2+y^2)}$

$(4)$

定义域 $\{(x,y)\mid -1\le x\le 1,y\le -1或-1\le x\le1,y\ge1\}$

闭集。

$(6)$

定义域 $\{(x,y)\mid x^2+y^2\in[2k\pi,2k\pi+\pi],k\in Z\}$

闭集。

## 习题 16.2

> 1. 试求下列极限（包括非正常极限）：
>
> $(1)$ $\lim\limits_{(x,y)\to(0,0)}\dfrac{x^2y^2}{x^2+y^2}$
>
> $(3)$ $\lim\limits_{(x,y)\to(0,0)}\dfrac{x^2+y^2}{\sqrt{1+x^2+y^2}-1}$
>
> $(4)$ $\lim\limits_{(x,y)\to(0,0)}\dfrac{xy+1}{x^4+y^4}$
>
> $(5)$ $\lim\limits_{(x,y)\to(1,2)}\dfrac{1}{2x-y}$

$(1)$

极坐标变换。

$$
|f(x,y)-0|=|\dfrac{r^4\cos^2\theta\sin^2\theta}{r^2(\cos^2\theta+\sin^2\theta)}|=r^2|\cos^2\theta\sin^2\theta|\le r^2
$$

因此 $\forall\epsilon>0$，只要取 $\delta=\sqrt{\epsilon}$，当 $0<r<\delta$ 时，无论 $\theta$ 取何值都有 $|f(x,y)-0|<\epsilon$，所以 $\lim\limits_{(x,y)\to(0,0)}\dfrac{x^2y^2}{x^2+y^2}=0$

$(3)$

记 $r=\sqrt{x^2+y^2}$，则

$$
\lim_{r\to0}f(x,y)=\lim_{r\to0}\dfrac{r^2}{\sqrt{1+r^2}-1}=\lim_{r\to0}\dfrac{r^2}{\frac{r^2}2}=2
$$

$(4)$

极坐标变换。

$$
\dfrac{1-r^2}{r^4}\le\dfrac{r^2\sin\theta\cos\theta+1}{r^4}\le\dfrac{1+r^2}{r^4}
$$

而 $\lim\limits_{r\to0}\dfrac{1-r^2}{r^4}=+\infty,\lim\limits_{r\to0}\dfrac{1+r^2}{r^4}=+\infty$。

由夹逼定理，$\lim\limits_{r\to0}\dfrac{r^2\sin\theta\cos\theta+1}{r^4}=+\infty$

$(5)$

$\forall M>0$，取 $\delta=\dfrac1M$，当 $x\in U^\circ(1,\delta),y\in U^\circ(2,\delta)$ 时，$|2x-y|\in[0,4\delta)$，所以 $|\dfrac1{2x-y}|>\dfrac1{4\delta}=\dfrac M4$。

所以 $\lim\limits_{(x,y)\to(1,2)}\dfrac1{2x-y}=\infty$

> 2. 讨论下列函数在点 $(0,0)$ 的重极限与累次极限：
>
> $(3)$ $f(x,y)=\dfrac{x^2y^2}{x^2y^2+(x-y)^2}$
>
> $(6)$ $f(x,y)=\dfrac{x^2y^2}{x^3+y^3}$

$(3)$

重极限:

$\lim\limits_{\substack{(x,y)\to(0,0)\\ y=x}}f(x,y)=1,\lim\limits_{\substack{(x,y)\to(0,0)\\ y=\frac12x}}f(x,y)=0$，所以重极限不存在。

累次极限：

$$
\lim\limits_{x\to0}\lim\limits_{y\to0}f(x,y)=0\\
\lim\limits_{y\to0}\lim\limits_{x\to0}f(x,y)=0
$$

$(6)$

重极限：

$$
\lim\limits_{\substack{(x,y)\to(0,0)\\ y=0}}f(x,y)=0
$$

$$
\lim\limits_{\substack{(x,y)\to(0,0)\\ y=-x-x^2}}f(x,y)=\lim\limits_{\substack{(x,y)\to(0,0)\\ y=-x-x^2}}\dfrac{x^4+2x^5+x^6}{3x^4+3x^5+x^6}=\dfrac13
$$

所以重极限不存在。

累次极限：

$$
\lim\limits_{x\to0}\lim\limits_{y\to0}f(x,y)=0\\
\lim\limits_{y\to0}\lim\limits_{x\to0}f(x,y)=0
$$

> 6. 试写出下列类型极限的精确定义：
>
> $(1)$ $\lim\limits_{(x,y)\to(+\infty,+\infty)}f(x,y)=A$

$\forall\epsilon>0,\exist G>0,\forall x>G,y>G,|f(x,y)-A|<\epsilon$

> 7. 试求下列极限：
>
> $(3)$ $\lim\limits_{(x,y)\to(+\infty,+\infty)}(1+\dfrac1{xy})^{x\sin y}$

$(3)$

先证明 $\lim\limits_{(x,y)\to(+\infty,+\infty)}xy\ln(1+\dfrac1{xy})=1$

令 $t=xy$，容易发现 $\lim\limits_{t\to\infty}t\ln(1+\dfrac1t)=1$。

这说明 $\forall\epsilon>0,\exist M>0,\forall t>M,|t\ln(1+\dfrac1t)-1|<\epsilon$。

只需要取 $x>\sqrt M,y>\sqrt M$ 即可，由定义知 $\lim\limits_{(x,y)\to(+\infty,+\infty)}xy\ln(1+\dfrac1{xy})=1$。

同理 $\lim\limits_{(x,y)\to(+\infty,+\infty)}\dfrac{\sin y}y=0$

所以 $\lim\limits_{(x,y)\to(+\infty,+\infty)}x\sin y\ln(1+\dfrac1{xy})=\lim\limits_{(x,y)\to(+\infty,+\infty)}\dfrac{\sin y}y\cdot xy\ln(1+\dfrac1{xy})=0$。

所以 $\lim\limits_{(x,y)\to(+\infty,+\infty)}(1+\dfrac1{xy})^{x\sin y}=1$。

## 习题 16.3

> 1. 讨论下列函数的连续性：
>
> $(3)$ $f(x,y)=\begin{cases}\dfrac{\sin xy}{y}&,y\neq0\\0&,y=0\end{cases}$
>
> $(5)$ $f(x,y)=\begin{cases}0&,x\in R\backslash Q\\y&,x\in Q\end{cases}$

$(3)$

当 $y\neq0$ 时，由初等函数的连续性可知 $f(x,y)$ 是连续的。

当 $y=0$ 时，

$$
\lim_{(x,y)\to(x_0,0)}f(x,y)=\lim_{(x,y)\to(x_0,0)}\dfrac{\sin xy}{xy}\cdot x=x_0
$$

所以 $x_0=0$ 时，$\lim\limits_{(x,y)\to(x_0,0)}f(x,y)=f(x_0,0)$；

当 $x_0\neq0$ 时，$\lim\limits_{(x,y)\to(x_0,0)}f(x,y)=x_0\neq0=f(x_0,0)$。

所以 $f(x,y)$ 在 $\{(x,y)\mid x=y=0\lor y\neq0\}$ 上连续。

$(5)$

$f(x,y)=yD(x)$。

考虑 $(x,y)\to(x_0,y_0)$。

当 $y_0\neq0$ 时，取 $\epsilon_0=\dfrac{y_0}2$，$0<\forall\delta<\epsilon_0$，取 $x'\in(x_0,x_0+\delta)\cap Q,x''\in(x_0,x_0+\delta)\backslash Q,y'\in(y_0,y_0+\delta)$，此时有 $f(x',y')=y',f(x'',y')=0$，所以 $|f(x',y')-f(x'',y')|\ge\epsilon_0$，极限不存在。

当 $y_0=0$ 时，$\forall\epsilon>0$，取 $\delta=\epsilon$，$\forall x'\in U^\circ(x_0,\delta),y'\in U^\circ(y_0,\delta),f(x',y')=0$ 或 $f(x',y')=y'$，所以 $|f(x',y')|<|y'|<\delta=\epsilon$，由定义 $\lim\limits_{(x,y)\to(x_0,0)}f(x,y)=0$，因此连续。

所以 $f(x,y)$ 在 $\{(x,y)\mid y=0\}$ 上连续。

> 3. 设
>
> $$
f(x,y)=\begin{cases}
\dfrac{x}{(x^2+y^2)^p}&,x^2+y^2\neq0\\
0&,x^2+y^2=0
\end{cases}
\space (p>0)
> $$
>
> 试讨论它在点 $(0,0)$ 处的连续性。

记 $r=\sqrt{x^2+y^2}$。

$$
f(x,y)=\begin{cases}
\dfrac{\cos\theta}{r^{2p-1}}&,r\neq0\\
0&,r=0
\end{cases}
$$

当 $p<\dfrac12$ 时，$\lim\limits_{r\to0^+}|\dfrac{\cos\theta}{r^{2p-1}}|\le\lim\limits_{r\to0^+}\dfrac{1}{r^{2p-1}}=0$，此时连续。

当 $p\ge\dfrac12$ 时，取 $\epsilon_0=2,\theta_1=0,\theta_2=\pi$，则 $\forall0<\delta<1$ $|f(r,\theta_1)-f(r,\theta_2)|=\dfrac{2}{r^{2p-1}}>2\epsilon_0$，所以极限不存在，不连续。

当且仅当 $0<p<\dfrac12$ 时在 $(0,0)$ 连续。

> 4. 设 $f(x,y)$ 定义在闭矩形域 $S=[a,b]\times[c,d]$ 上，且满足：
>
> $(i)$ 任给 $x_0\in[a,b]$，$f(x_0,y)$ 在 $[c,d]$ 上连续；
>
> $(ii)$ 任给 $x_0\in[a,b]$，任给正数 $\epsilon>0$，存在正数 $\delta$，使得当 $|x-x_0|<\delta$ 时，对所有 $y\in[c,d]$，成立 $|f(x,y)-f(x_0,y)|<\epsilon$。
>
> 证明：$f$ 在 $S$ 上连续。

$\forall(x_0,y_0)\in S$，我们证明 $f$ 在 $(x_0,y_0)$ 处连续。

$\forall\epsilon>0$，由条件 $(i)$ 知 $\exist\delta_1>0$，$\forall y\in U(y_0,\delta_1)$，$|f(x_0,y)-f(x_0,y_0)|<\epsilon$。

由条件 $(ii)$ 知 $\exist\delta_2>0$，$\forall x\in U(x_0,\delta_2)$，$|f(x,y)-f(x_0,y)|<\epsilon$。

因此取 $\delta=\min\{\delta_1,\delta_2\}$，则当 $x\in U(x_0,\delta),y\in U(y_0,\delta)$ 时，有 $|f(x,y)-f(x_0,y_0)|<|f(x,y)-f(x_0,y)|+|f(x_0,y)-f(x_0,y_0)|<2\epsilon$。

因此 $\lim\limits_{(x,y)\to(x_0,y_0)}f(x,y)=f(x_0,y_0)$，连续。

> 5. 证明：若 $D\subseteq R^2$ 是有界闭域，$f$ 为 $D$ 上的连续函数，且 $f$ 不是常数函数，则 $f(D)$ 是闭区间。

易知 $f(D)$ 有最大值 $M$ 与最小值 $m$，下证 $[m,M]$ 中每一点都能取到。

由介值性定理，$\forall\mu\in(m,M),\exist x\in D,f(x)=\mu$。

所以证毕。

> 6. 设 $f(x,y)$ 在 $[a,b]\times[c,d]$ 上连续，又有函数列 $\{\varphi_k(x)\}$ 在 $[a,b]$ 上一致收敛，且
>
> $$
c\le\varphi_k(x)\le d,x\in[a,b],k=1,2,\dots
> $$
>
> 试证：$\{F_k(x)\}=\{f(x,\varphi_k(x))\}$ 在 $[a,b]$ 上也一致收敛。

设 $\varphi_k(x)\rightrightarrows\varphi(x)$。

$\forall y\in[c,d],\forall\epsilon>0,\exist\delta>0,\forall y'\in U(y,\delta),|f(x,y)-f(x,y')|<\epsilon$。

$\forall\delta>0,\exist K>0,\forall k>K,x\in[a,b]$，有 $|\varphi_k(x)-\varphi(x)|<\delta$。

所以当 $\forall\epsilon>0$，取同样的 $K$，$\forall k>K,x\in[a,b]$，$|f(x,\varphi_k(x))-f(x,\varphi(x))|<\epsilon$。

所以一致收敛。

> 7. 设 $f(x,y)$ 在区域 $G\subseteq R^2$ 上对 $x$ 连续，对 $y$ 满足利普希茨条件：
>
> $$
|f(x,y')-f(x,y'')|\le L|y'-y''|
> $$
>
> 其中 $(x,y'),(x,y'')\in G,L$ 为常数。试证明：$f$ 在 $G$ 上连续。

$\forall(x,y)\in G$，只需要证明 $f$ 在 $(x,y)$ 处连续。

$\forall\epsilon>0$，由于对 $x$ 连续，所以 $\exist\delta_1>0,\forall x'\in U(x,\delta_1)$，使得 $|f(x',y)-f(x,y)|<\epsilon$。

取 $\delta_2=\dfrac{\epsilon}{L}$，$\forall y'\in U(y,\delta_2),(x',y)\in G$，由利普希茨条件，$|f(x',y')-f(x',y)|\le\epsilon$。

取 $\delta=\min\{\delta_1,\delta_2\}$，则 $\forall x'\in U(x,\delta),y'\in U(y,\delta),(x',y')\in G$，有 $|f(x',y')-f(x,y)|<|f(x',y')-f(x',y)|+|f(x',y)-f(x,y)|<2\epsilon$。

所以连续。