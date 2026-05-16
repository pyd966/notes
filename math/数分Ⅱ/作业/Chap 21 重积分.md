# Chap 21 重积分

## 习题 21.2

> 5. 设 $f(x)$ 在 $[a,b]$ 上连续。证明不等式：
>
> $$
(\int_a^bf(x)dx)^2\le(b-a)\int_a^bf^2(x)dx
> $$
>
> 其中等号仅在 $f(x)$ 为常量函数时成立。

考虑计算 $$。

$$
\begin{aligned}
\iint_{[a,b]\times[a,b]}(f(x)-f(y))^2dxdy&=\iint(f^2(x)-2f(x)f(y)+f^2(y))dxdy\\
&=\iint f^2(x)dxdy+\iint f^2(y)dxdy-2\iint f(x)f(y)dxdy\\
&=2(b-a)\int_a^bf^2(x)dx-2(\int f(x)dx)(\int f(y)dy)\\
&=2((b-a)\int_a^b f^2(x)dx-(\int_a^bf(x)dx)^2)\\
\ge0
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