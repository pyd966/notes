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