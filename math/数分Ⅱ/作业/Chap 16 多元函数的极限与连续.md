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