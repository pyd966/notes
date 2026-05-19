# Chap 21 重积分

## 习题 21.2

> 1. 设 $f(x,y)$ 在区域 $D$ 上连续，试将二重积分 $\iint_Df(x,y)d\sigma$ 化为不同次序的累次积分：
>
> $(2)$ $D$ 是由不等式 $y\le x,y\ge0,x^2+y^2\le 1$ 所确定的区域
>
> $(4)$ $D=\{(x,y)\mid|x|+|y|\le1\}$

$(2)$

$$
\begin{aligned}
\iint_Df(x,y)d\sigma&=\int_0^{\frac{\sqrt2}2}dx\int_0^xf(x,y)dy+\int_{\frac{\sqrt2}2}^1dx\int_0^{\sqrt{1-x^2}}f(x,y)dy\\
&=\int_0^{\frac{\sqrt2}2}dy\int_y^{\sqrt{1-y^2}}f(x,y)dx
\end{aligned}
$$

$(4)$

$$
\begin{aligned}
\iint_Df(x,y)d\sigma&=\int_{-1}^1dx\int_{-1+|x|}^{1-|x|}f(x,y)dy\\
&=\int_{-1}^1dy\int_{-1+|y|}^{1-|y|}f(x,y)dx\\
\end{aligned}
$$

> 2. 在下列积分中改变累次积分的顺序：
>
> $(1)$ $\int_0^2dx\int_x^{2x}f(x,y)dy$
>
> $(3)$ $\int_0^{2a}dx\int_{\sqrt{2ax-x^2}}^{\sqrt{2ax}}f(x,y)dy$

$(1)$

对应区域 $D=\{(x,y)\mid0\le x\le2,x\le y\le 2x\}$

$$
\begin{aligned}
\int_0^2dx\int_x^{2x}f(x,y)dy&=\int_0^2dy\int_{\frac y2}^yf(x,y)dx+\int_2^4dy\int_{\frac y2}^2f(x,y)dx
\end{aligned}
$$

$(3)$

对应区域 $D=\{(x,y)\mid 0\le x\le2a,\sqrt{2ax-x^2}\le y\le\sqrt{2ax}\}$

$$
\begin{aligned}
\int_0^{2a}dx\int_{\sqrt{2ax-x^2}}^{\sqrt{2ax}}f(x,y)dy&=\int_0^{a}dy\int_{\frac{y^2}{2a}}^{a-\sqrt{a^2-y^2}}f(x,y)dx+\int_0^{a}dy\int_{a+\sqrt{a^2-y^2}}^{2a}f(x,y)dx+\int_a^{2a}dy\int_{\frac{y^2}{2a}}^{2a}f(x,y)dx
\end{aligned}
$$

> 3. 计算下列二重积分：
>
> $(2)$ $\iint_D(x^2+y^2)d\sigma$，其中 $D=\{(x,y)\mid0\le x\le 1,\sqrt{x}\le y\le2\sqrt x\}$
>
> $(4)$ $\iint_D\sqrt xd\sigma$，其中 $D=\{(x,y)\mid x^2+y^2\le x\}$

$(2)$

$$
\begin{aligned}
\iint_D(x^2+y^2)d\sigma&=\int_0^1dx\int_{\sqrt x}^{2\sqrt x}(x^2+y^2)dy\\
&=\int_0^1(x^{5/2}+\dfrac73x^{3/2})dx\\
&=\dfrac{128}{105}
\end{aligned}
$$

$(4)$

$D=\{(x,y)\mid x^2+y^2\le x\}=\{(x,y)\mid (x-\dfrac12)^2+y^2\le\dfrac14\}$

$$
\begin{aligned}
\iint_D\sqrt xd\sigma&=2\int_0^1dx\int_0^{\sqrt{\frac14-(x-\frac12)^2}}\sqrt{x}dy\\
&=2\int_0^1\sqrt{x}\sqrt{\dfrac14-(x-\dfrac12)^2}dx\\
&=2\int_0^1x\sqrt{1-x}dx\\
&=2\int_0^1(1-t)\sqrt tdt\\
&=2\int_0^1(t^{1/2}-t^{3/2})dt\\
&=\dfrac8{15}
\end{aligned}
$$

> 4. 求由坐标平面及 $x=2,y=3,x+y+z=4$ 所围成的角柱体的体积。

$D=\{(x,y)\mid x\in[0,2],y\in[0,3],x+y\le4\}$

$$
\begin{aligned}
\iint_D(4-x-y)d\sigma&=\int_0^1dx\int_0^3(4-x-y)dy+\int_1^2dx\int_0^{4-x}(4-x-y)dy\\
&=\int_0^1(3(4-x)-\dfrac92)dx+\dfrac12\int_1^2(4-x)^2dx\\
&=6+\dfrac{19}6\\
&=\dfrac{55}6
\end{aligned}
$$

> 5. 设 $f(x)$ 在 $[a,b]$ 上连续。证明不等式：
>
> $$
(\int_a^bf(x)dx)^2\le(b-a)\int_a^bf^2(x)dx
> $$
>
> 其中等号仅在 $f(x)$ 为常量函数时成立。

考虑

$$
\begin{aligned}
\iint_{[a,b]\times[a,b]}(f(x)-f(y))^2dxdy&=\iint(f^2(x)-2f(x)f(y)+f^2(y))dxdy\\
&=\iint f^2(x)dxdy+\iint f^2(y)dxdy-2\iint f(x)f(y)dxdy\\
&=2(b-a)\int_a^bf^2(x)dx-2(\int f(x)dx)(\int f(y)dy)\\
&=2((b-a)\int_a^b f^2(x)dx-(\int_a^bf(x)dx)^2)\\
&\ge0
\end{aligned}
$$

所以 $(\int_a^bf(x)dx)^2\le(b-a)\int_a^bf^2(x)dx$

等号成立当且仅当 $f(x)-f(y)\equiv0$，也就是 $f(x)$ 是常量函数。

> 7. 设 $D=[0,1]\times[0,1]$，
>
> $$
f(x,y)=\begin{cases}
\dfrac1{q_x}+\dfrac1{q_y},& (x,y) 为 D 内有理点\\
0,& (x,y) 为 D 内非有理点
\end{cases}
> $$
>
> 其中 $q_x$ 表示有理数化成既约分数后的分母。证明：$f(x,y)$ 在 $D$ 上的二重积分存在而两个累次积分不存在。

容易发现下积分为 $0$，下面计算上积分。

$\forall\epsilon>0$，取 $\delta=\dfrac\epsilon2$

记 $S=\{(x,y)\mid f(x,y)\ge\delta\}$，这说明 $\dfrac1{q_x}+\dfrac1{q_y}\ge\delta$，那么 $\dfrac1{q_x}\ge\dfrac\delta2$ 或者 $\dfrac1{q_y}\ge\dfrac\delta2$，也即 $q_x\le\dfrac2\delta,q_y\le\dfrac2\delta$，也就是说 $S$ 只包含有限元素。

进行划分，考虑对每个 $S$ 中的元素，用一个边长为 $a$ 的正方形包含进去，其中 $a^2<\dfrac{\epsilon}{2|S|(1+\sup f)}$

考虑把 $D$ 划分为 $D_1$ 和 $D_2$ 两部分，其中 $D_1$ 被某个正方形包含，$D_2$ 是其余部分。

在 $D_1$ 中，上达布和 $\overline{D_1}=|S|a^2\sup f<\dfrac\epsilon2$

在 $D_2$ 中，上达布和 $\overline{D_2}<\sigma(D_2)\delta\le\delta=\dfrac\epsilon2$

所以 $\overline{D}=\overline{D_1}+\overline{D_2}<\epsilon$

所以上积分为 $0$，二重积分存在。

考虑累次积分：

对一个固定的 $y$，若 $y\in Q$，那么 $\int_0^1f(x,y)dx=0$

若 $y_0\in R\backslash Q$，

记 $g(x)=f(x,y_0)=\begin{cases}\dfrac1{q_x}+\dfrac1{q_{y_0}},& x\in Q\\ 0,& x\in R\backslash Q\end{cases}$.

那么考虑 $\int_0^1g(x)dx$。

其下积分显然为 $0$，上积分 $\ge\dfrac1{q_{y_0}}$，所以上下积分不相等，累次积分不存在。同理，另一个累次积分也不存在。

> 8. 设 $D=[0,1]\times[0,1]$，
>
> $$
f(x,y)=\begin{cases}
1,& (x,y) 为 D 内有理点，且 q_x=q_y\\
0,& (x,y) 为 D 内其他点
\end{cases}
> $$
>
> 其中 $q_x$ 意义同第 $7$ 题。证明：$f(x,y)$ 在 $D$ 上的二重积分不存在而两个累次积分存在。

二重积分：

考虑任意一个分割 $D$ 中的一个小矩形 $[a,b]\times[c,d]$，下面证明在这个矩形中既有 $0$ 的点也有 $1$ 的点。

显然取一个无理点它的取值就是 $0$.

取 $\Delta=\min\{b-a,d-c\}$，取一个质数 $p$ 满足 $\dfrac1p<\Delta$。

那么显然可以找到 $\dfrac{x}{p}\in[a,b],\dfrac{y}{p}\in[c,d]$，所以点 $f(\dfrac xp,\dfrac yp)=1$。

那么达布上和是 $1$，达布下和是 $0$.所以二重积分不存在。

累次积分：

固定一个 $y_0$，那么考察 $g(x)=f(x,y_0)$，这个函数只有有限个值不为 $0$，所以 $\int_0^1g(x)dx=0$。

那么 $\int_0^1dy\int_0^1f(x,y)dx=\int_0^10=0$，同理另一个累次积分也存在。