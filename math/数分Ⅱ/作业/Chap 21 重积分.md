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

## 习题 21.4

> 2. 用极坐标计算下列二重积分：
>
> $(3)$ $\iint_D|xy|dxdy$，其中 $D$ 为圆域 $x^2+y^2\le a^2$

$(3)$

记 $x=r\cos\theta,y=r\sin\theta$。

$\Delta=\{(r,\theta)\mid 0\le r\le a,0\le\theta\le2\pi\}$

$$
\begin{aligned}
\iint_D|xy|dxdy&=\iint_\Delta|r^2\cos\theta\sin\theta|rdrd\theta\\
&=\dfrac12\iint_\Delta r^3|\sin2\theta|drd\theta\\
&=\dfrac12\int_0^adr\int_0^{2\pi}r^3|\sin2\theta|d\theta\\
&=\int_0^a2r^3dr\\
&=\dfrac{a^4}2
\end{aligned}
$$

> 3. 在下列积分中引入新变量 $u,v$ 后，试将它化为累次积分：
>
> $(2)$ $\iint_Df(x,y)dxdy$，其中 $D=\{(x,y)\mid\sqrt x+\sqrt y\le\sqrt a,x\ge0,y\ge0\}$，若 $x=u\cos^4v,y=u\sin^4v$

$(2)$

$\sqrt x+\sqrt y\le\sqrt a\iff\sqrt u\cos^2v+\sqrt u\sin^2v=\sqrt u\le\sqrt a\iff 0\le u\le a$

$x\ge 0\iff u\ge0,y\ge0\iff u\ge0$

所以 $\Delta=\{(u,v)\mid 0\le u\le a,0\le v\le \dfrac\pi2\}$

计算 $|\dfrac{\partial(x,y)}{\partial(u,v)}|=4u|\sin^3v\cos^3v|$

$$
\begin{aligned}
\iint_Df(x,y)dxdy&=\iint_\Delta f(u\cos^4v,u\sin^4v)|4u\sin^3v\cos^3v|dudv\\
&=4\int_0^adu\int_0^{\frac\pi2}f(u\cos^4v,u\sin^4v)u|\sin^3v\cos^3v|dudv
\end{aligned}
$$

> 4. 试作适当变换，计算下列积分：
>
> $(1)$ $\iint_D(x+y)\sin(x-y)dxdy$，其中 $D=\{(x,y)\mid0\le x+y\le\pi,0\le x-y\le\pi\}$

$(1)$

记 $u=x+y,v=x-y$，那么 $x=\dfrac{u+v}{2},y=\dfrac{u-v}{2}$

$\Delta=\{(u,v)\mid 0\le u\le \pi,0\le v\le\pi\}$

$|\dfrac{\partial(x,y)}{\partial(u,v)}|=\dfrac12\neq0$

$$
\begin{aligned}
\iint_D(x+y)\sin(x-y)dxdy&=\dfrac12\iint_\Delta u\sin vdudv\\
&=\dfrac12\int_0^\pi du\int_0^\pi u\sin vdv\\
&=\int_0^\pi udu\\
&=\dfrac{\pi^2}2
\end{aligned}
$$

> 5. 求由下列曲面所围立体 $V$ 的体积：
>
> $(1)$ $V$ 是由 $z=x^2+y^2$ 和 $z=x+y$ 所围的立体；
>
> $(2)$ $V$ 是由曲面 $z^2=\dfrac{x^2}{4}+\dfrac{y^2}{9}$ 和 $2z=\dfrac{x^2}{4}+\dfrac{y^2}{9}$ 所围的立体。

$(1)$

令 $x^2+y^2\le x+y$ 得到 $(x-\dfrac12)^2+(y-\dfrac12)^2\le\dfrac12$。

取区域 $D=\{(x,y)\mid(x-\dfrac12)^2+(y-\dfrac12)^2\le\dfrac12\}$。

做变换 $x=r\cos\theta+\dfrac12,y=r\sin\theta+\dfrac12$

那么 $\Delta=\{(r,\theta)\mid 0\le r\le\dfrac{\sqrt2}2,0\le\theta\le2\pi\}$

$|\dfrac{\partial(x,y)}{\partial(u,v)}|=r$

$$
\begin{aligned}
V&=\iint_D(x+y-x^2-y^2)dxdy\\
&=\iint_\Delta(\dfrac12-r^2)rdrd\theta\\
&=\int_0^{\frac{\sqrt2}2}dr\int_0^{2\pi}(\dfrac12-r^2)rd\theta\\
&=2\pi\int_0^{\frac{\sqrt2}2}(\dfrac12-r^2)rdr\\
&=\dfrac{\pi}{8}
\end{aligned}
$$

$(2)$

联立，解得区域 $D=\{(x,y)\mid\dfrac{x^2}{4}+\dfrac{y^2}{9}\le4\}$

做变换 $x=2r\cos\theta,y=3r\sin\theta$

那么 $\Delta=\{(r,\theta)\mid 0\le r\le 2,0\le\theta\le2\pi\}$

$|\dfrac{\partial(x,y)}{\partial(u,v)}|=6r$

$$
\begin{aligned}
V&=\iint_D(\sqrt{\dfrac{x^2}4+\dfrac{y^2}{9}}-\dfrac12(\dfrac{x^2}4+\dfrac{y^2}{9}))dxdy\\
&=\iint_\Delta6r(r-\dfrac12r^2)drd\theta\\
&=3\int_0^2dr\int_0^{2\pi}(2r-r^2)d\theta\\
&=3\int_0^2dr2\pi(2r-r^2)\\
&=8\pi
\end{aligned}
$$

> 6. 求出下列曲线所围的平面图形面积：
>
> $(1)$ $x+y=a,x+y=b,y=\alpha x,y=\beta x$ $(0<a<b,0<\alpha<\beta)$

$(1)$

做变换 $u=x+y,v=\dfrac{y}{x}$，那么 $x=\dfrac u{1+v},y=\dfrac{uv}{1+v}$

$\Delta=\{(u,v)\mid a\le u\le b,\alpha\le v\le\beta\}$

$|\dfrac{\partial(x,y)}{\partial(u,v)}|=\dfrac{u}{(1+v)^2}$

$$
\begin{aligned}
V&=\iint_D1dxdy\\
&=\iint_\Delta\dfrac{u}{(1+v)^2}dudv\\
&=\int_\alpha^\beta dv\int_a^b\dfrac{u}{(1+v)^2}du\\
&=\int_\alpha^\beta dv\dfrac{(b-a)^2}{2(1+v)^2}\\
&=\dfrac{(b-a)^2(\beta-\alpha)}{2(1+\alpha)(1+\beta)}
\end{aligned}
$$

## 习题 21.5

> 1. 计算下列积分：
>
> $(3)$ $\iiint_V\dfrac{dxdydz}{(1+x+y+z)^3}$，其中 $V$ 是由 $x+y+z=1$ 与三个坐标面所围成的区域。
>
> $(4)$ $\iiint_Vy\cos(x+z)dxdydz$，其中 $V$ 是由 $y=\sqrt x,y=0,z=0$ 以及 $x+z=\dfrac\pi2$ 所围成的区域。

$(3)$

$V=\{(x,y,z)\mid 0\le x\le 1,0\le y\le 1-x,0\le z\le 1-x-y\}$

$$
\begin{aligned}
\iiint_V\dfrac{dxdydz}{(1+x+y+z)^3}&=\int_0^1dx\int_0^{1-x}dy\int_0^{1-x-y}(1+x+y+z)^{-3}dz\\
&=\dfrac12\int_0^1dx\int_0^{1-x}((1+x+y)^{-2}-\dfrac14)dy\\
&=\dfrac12\int_0^1((1+x)^{-1}-\dfrac14(1-x)-\dfrac12)dx\\
&=\dfrac12\ln2-\dfrac5{16}
\end{aligned}
$$

$(4)$

$V=\{(x,y,z)\mid 0\le x\le\dfrac\pi2,0\le y\le\sqrt x,0\le z\le\dfrac\pi2-x\}$

$$
\begin{aligned}
\iiint_V y\cos(x+z)dxdydz&=\int_0^{\frac\pi2}dx\int_0^{\sqrt x}dy\int_0^{\frac\pi2-x}y\cos(x+z)dz\\
&=\int_0^{\frac\pi2}dx\int_0^{\sqrt{x}}y(\sin(\dfrac\pi2)-\sin x)dy\\
&=\dfrac12\int_0^{\frac\pi2}x(1-\sin x)dx\\
&=\dfrac{\pi^2-8}{16}
\end{aligned}
$$

> 2. 试改变下列累次积分的顺序：
>
> $(1)$ $\int_0^1dx\int_0^{1-x}dy\int_0^{x+y}f(x,y,z)dz$

$(1)$

$V=\{(x,y,z)\mid 0\le x\le1,0\le y\le 1-x,0\le z\le x+y\}=\{(x,y,z)\mid 0\le y\le 1,0\le x\le 1-y,0\le z\le x+y\}$

$$
\int_0^1dx\int_0^{1-x}dy\int_0^{x+y}f(x,y,z)dz=\int_0^1dy\int_0^{1-y}dx\int_0^{x+y}f(x,y,z)dz
$$

> 3. 计算下列三重积分与累次积分：
>
> $(1)$ $\iiint_Vz^2dxdydz$，其中 $V$ 由 $x^2+y^2+z^2\le r^2$ 和 $x^2+y^2+z^2\le 2rz$ 所确定；
>
> $(2)$ $\int_0^1dx\int_0^{\sqrt{1-x^2}}dy\int_{\sqrt{x^2+y^2}}^{\sqrt{2-x^2-y^2}}z^2dz$

$(1)$

做变换 $\begin{cases}x=R\sin\varphi\cos\theta\\ y=R\sin\varphi\sin\theta\\ z=R\cos\varphi\end{cases}$

那么由 $x^2+y^2+z^2\le r^2$ 知 $0\le R\le r$，由 $x^2+y^2+z^2\le 2rz$ 知 $R\le 2r\cos\varphi$

所以区域 $\Omega=\{(R,\theta,\varphi)\mid 0\le R\le\min\{r,2r\cos\varphi\},0\le\theta\le2\pi,0\le\varphi\le\dfrac\pi2\}$

$$
\begin{aligned}
\iiint_Vz^2dxdydz&=\int_0^{\frac\pi2}d\varphi\int_0^{\min\{r,2r\cos\varphi\}}R^4\cos^2\varphi\sin\varphi dR\int_0^{2\pi}d\theta\\
&=2\pi(\int_0^{\frac\pi3}d\varphi\int_0^{r}R^4\cos^2\varphi\sin\varphi dR+\int_{\frac\pi3}^{\frac\pi2} d\varphi\int_0^{2r\cos\varphi}R^4\cos^2\varphi\sin\varphi dR)\\
&=\dfrac{2\pi}5r^5(\int_0^{\frac\pi3}\cos^2\varphi\sin\varphi d\varphi+\int_{\frac\pi3}^{\frac\pi2}32\cos^7\varphi\sin\varphi d\varphi)\\
&=\dfrac{59\pi r^5}{480}
\end{aligned}
$$

$(2)$

$V=\{(x,y,z)\mid 0\le x\le 1,0\le y\le \sqrt{1-x^2},\sqrt{x^2+y^2}\le z\le\sqrt{2-x^2-y^2}\}$

所以 $x^2+y^2\le 1,x^2+y^2+z^2\le 2,x^2+y^2\le z^2,x,y\ge0$

做变换 $\begin{cases}x=r\cos\theta\\ y=r\sin\theta\\ z=z\end{cases}$

那么 $\Omega=\{(r,\theta,z)\mid 0\le r\le1,0\le\theta\le\dfrac\pi2,r\le z\le\sqrt{2-r^2}\}$

$$
\begin{aligned}
\int_0^1dx\int_0^{\sqrt{1-x^2}}dy\int_{\sqrt{x^2+y^2}}^{\sqrt{2-x^2-y^2}}z^2dz&=\int_0^1dr\int_r^{\sqrt{2-r^2}}dz\int_0^{\frac\pi2} z^2rd\theta\\
&=\dfrac\pi2\int_0^1dr\int_r^{\sqrt{2-r^2}}z^2rdz\\
&=\dfrac\pi6\int_0^1r((2-r^2)^{3/2}-r^3)dr\\
&=\dfrac{\pi(2\sqrt2-1)}{15}
\end{aligned}
$$

> 7. 设 $V=\{(x,y,z)\mid\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}+\dfrac{z^2}{c^2}\le 1\}$，计算下列积分：
>
> $(1)$ $\iiint_V\sqrt{1-\dfrac{x^2}{a^2}-\dfrac{y^2}{b^2}-\dfrac{z^2}{c^2}}dxdydz$

$(1)$

做变换 $\begin{cases}x=ar\sin\varphi\cos\theta\\ y=br\sin\varphi\sin\theta\\ z=cr\cos\varphi\end{cases}$

那么 $\Omega=\{(r,\varphi,\theta)\mid 0\le r\le 1,0\le\varphi\le\pi,0\le\theta\le2\pi\}$

$$
\begin{aligned}
\iiint_V\sqrt{1-\dfrac{x^2}{a^2}-\dfrac{y^2}{b^2}-\dfrac{z^2}{c^2}}dxdydz&=\int_0^1dr\int_0^\pi d\varphi\int_0^{2\pi}r^2abc\sin\varphi\sqrt{1-r^2}d\theta\\
&=2\pi abc\int_0^1dr\int_0^\pi r^2\sqrt{1-r^2}\sin\varphi d\varphi\\
&=4\pi abc\int_0^1r^2\sqrt{1-r^2}dr\\
&=4\pi abc\int_0^{\frac\pi2}\sin^2\alpha\cos^2\alpha d\alpha\\
&=\pi abc\int_0^{\frac\pi2}\sin^22\alpha d\alpha\\
&=\dfrac\pi2abc\int_0^{\frac\pi2}(1-\cos4\alpha)d\alpha\\
&=\dfrac{\pi^2abc}{4}
\end{aligned}
$$