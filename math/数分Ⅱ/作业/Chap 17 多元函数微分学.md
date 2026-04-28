## 习题 17.1

> 1. 求下列函数的偏导数：
>
> $(3)$ $z=\dfrac1{\sqrt{x^2+y^2}}$
>
> $(6)$ $z=\arctan\dfrac yx$
>
> $(9)$ $u=(xy)^z$

$(3)$

$\dfrac{\partial z}{\partial x}=-x(x^2+y^2)^{-3/2}$

$\dfrac{\partial z}{\partial y}=-y(x^2+y^2)^{-3/2}$

$(6)$

$\dfrac{\partial z}{\partial x}=-\dfrac{y}{x^2+y^2}$

$\dfrac{\partial z}{\partial y}=\dfrac{x}{x^2+y^2}$

$(9)$

$\dfrac{\partial u}{\partial x}=zy^zx^{z-1}$

$\dfrac{\partial u}{\partial y}=zx^zy^{z-1}$

$\dfrac{\partial u}{\partial z}=(xy)^z\ln(xy)$

> 3. 设 $f(x,y)=\begin{cases}y\sin\dfrac1{x^2+y^2}&,x^2+y^2\neq0\\ 0&,x^2+y^2=0\\\end{cases}$，考察函数 $f$ 在原点 $(0,0)$ 的偏导数。

$f_x(0,0)=\left.0\right|_{x=0}=0$

$f_y(0,0)=\left.\sin\dfrac1{y^2}-\dfrac2{y^2}\cos\dfrac1{y^2}\right|_{y=0}$ 不存在。

> 5. 考察函数 $f(x,y)=\begin{cases}xy\sin\dfrac1{x^2+y^2}&,x^2+y^2=0\\ 0&,x^2+y^2=0\\\end{cases}$ 在点 $(0,0)$ 的可微性。

$f_x(0,0)=\left.0\right|_{x=0}=0,f_y(0,0)=\left.0\right|_{y=0}=0$

计算 $\lim\limits_{(x,y)\to(0,0)}\dfrac{f(x,y)-f(0,0)-0\times\Delta x-0\times\Delta y}{\sqrt{x^2+y^2}}=\lim\limits_{(x,y)\to(0,0)}xy\dfrac{\sin\frac1{x^2+y^2}}{\sqrt{x^2+y^2}}=\lim\limits_{r\to0}r^2\cos\theta\sin\theta\dfrac{\sin\frac1{r^2}}r=\lim\limits_{r\to0}r\cos\theta\sin\theta\sin\dfrac1{r^2}$，同时 $\cos\theta\sin\theta\sin\dfrac1{r^2}$ 有界，所以极限为 $0$.

因此在 $(0,0)$ 可微。

> 6. 证明：函数 $f(x,y)=\begin{cases}\dfrac{x^2y}{x^2+y^2}&,x^2+y^2\neq0\\ 0&,x^2+y^2=0\\\end{cases}$ 在点 $(0,0)$ 连续且偏导数存在，但在此点不可微。

$\lim\limits_{(x,y)\to(0,0)}f(x,y)=\lim\limits_{r\to0}\dfrac{r^3\cos^2\theta\sin\theta}{r^2}=\lim\limits_{r\to0}r\cos^2\theta\sin\theta=0=f(0,0)$，连续。

$\dfrac{\partial f}{\partial x}=\left.0\right|_{x=0}=0$

$\dfrac{\partial f}{\partial y}=\left.0\right|_{y=0}=0$

计算 $\lim\limits_{(x,y)\to(0,0)}\dfrac{f(x,y)-f(0,0)-0\times\Delta x-0\times\Delta y}{\sqrt{x^2+y^2}}=\lim\limits_{r\to0}\dfrac{r^3\cos^2\theta\sin\theta}{r^3}=\lim\limits_{r\to0}\cos\theta^2\sin\theta$，显然关于 $\theta$ 并不一致收敛，所以极限不存在，因此不可微。

> 7. 证明：函数 $f(x,y)=\begin{cases}(x^2+y^2)\sin\dfrac1{\sqrt{x^2+y^2}}&,x^2+y^2\neq0\\ 0&,x^2+y^2=0\\\end{cases}$ 在点 $(0,0)$ 偏导数存在且可微，但偏导数在点 $(0,0)$ 不连续。

计算偏导数。

$f_x(0,0)=\lim\limits_{\Delta x\to0}\dfrac{f(\Delta x,0)-f(0,0)}{\Delta x}=\lim\limits_{\Delta x\to0}\Delta x\sin\dfrac1{\Delta x}=0$。

而当 $(x_0,y_0)\neq(0,0)$ 时，$f_x(x_0,y_0)=2x_0\sin\dfrac1{\sqrt{x_0^2+y_0^2}}-\dfrac1{\sqrt{x_0^2+y_0^2}}\cos\dfrac1{\sqrt{x_0^2+y_0^2}}$，显然在 $(0,0)$ 处不连续。

同理 $f_y(0,0)=0$，并且也不连续。

计算 $\lim\limits_{(\Delta x,\Delta y)\to(0,0)}\dfrac{f(\Delta x,\Delta y)-f(0,0)-0\times\Delta x-0\times\Delta y}{\sqrt{\Delta x^2+\Delta y^2}}=\lim\limits_{(\Delta x,\Delta y)\to(0,0)}\sqrt{\Delta x^2+\Delta y^2}\sin\dfrac1{\sqrt{\Delta x^2+\Delta y^2}}=0$

所以可微，$df(0,0)=0$

> 11. 求曲面 $3x^2+y^2-z^2=27$ 在点 $(3,1,1)$ 的切平面方程与法线方程。

改写为 $z=f(x,y)=\sqrt{3x^2+y^2-27}$。

求偏导得 $f_x(3,1)=9,f_y(3,1)=1$

切平面方程：$9(x-3)+(y-1)-(z-1)=0$

法线方程：$\dfrac{x-3}{9}=\dfrac{y-1}{1}=\dfrac{z-1}{-1}$

> 12. 在曲面 $z=xy$ 上求一点，使这点的切平面平行于平面 $x+3y+z+9=0$，并写出此切平面方程和法线方程。

设点 $P(x_0,y_0)$。

$f_x(x_0,y_0)=y_0,f_y(x_0,y_0)=x_0$。

所以切平面方程：$y_0(x-x_0)+x_0(y-y_0)-(z-x_0y_0)=0$

由平行条件，$\dfrac{y_0}{1}=\dfrac{x_0}3=\dfrac{-1}{1}$，所以 $(x_0,y_0)=(-3,-1)$。

切平面方程：$(x+3)+3(y+1)+(z-3)=0$，法线方程：$\dfrac{x+3}1=\dfrac{y+1}3=\dfrac{z-3}1$

> 16. 设二元函数 $f$ 在区域 $D=[a,b]\times[c,d]$ 上连续。
>
> $(1)$ 若在 $\text{int} D$ 内有 $f_x\equiv0$，试问 $f$ 在 $D$ 上有何特性？
>
> $(2)$ 若在 $\text{int} D$ 内有 $f_x=f_y\equiv0$，$f$ 又怎样？
>
> $(3)$ 在 $(1)$ 的讨论中，关于 $f$ 在 $D$ 上的连续性假设可否省略？长方形区域可否改为任意区域？

$(1)$

$f$ 的取值与 $x$ 无关，换言之

$$
\forall y\in[c,d],\forall x_1,x_2\in[a,b],f(x_1,y)=f(x_2,y)
$$

证明可以直接由一维情况的拉格朗日中值定理得到。

$(2)$

$f$ 为常数函数。

因为由 $(1)$ 知 $f$ 的取值与 $x$ 无关，也与 $y$ 无关。

$(3)$

可以省略连续性假设，因为只使用了关于 $x$ 方向的连续性，由偏导存在这是显然的。

不可以改为任意区域，比如下图。我们需要要求区域关于 x 连通。

## 习题 17.2

> 1. 求下列复合函数的偏导数或导数：
>
> $(2)$ 设 $z=\dfrac{x^2+y^2}{xy}e^{\frac{x^2+y^2}{xy}}$，求 $\dfrac{\partial z}{\partial x},\dfrac{\partial z}{\partial y}$
>
> $(3)$ 设 $z=x^2+xy+y^2,x=t^2,y=t$，求 $\dfrac{dz}{dt}$
>
> $(5)$ 设 $u=f(x+y,xy)$，求 $\dfrac{\partial u}{\partial x},\dfrac{\partial u}{\partial y}$

$(2)$

$$
\dfrac{\partial z}{\partial x}=\dfrac{\partial}{\partial x}(\dfrac{x^2+y^2}{xy})e^{\frac{x^2+y^2}{xy}}+\dfrac{x^2+y^2}{xy}\cdot\dfrac{\partial}{\partial y}(e^{\frac{x^2+y^2}{xy}})=\dfrac{(x+y)(x^3-y^3)}{x^3y^2}e^{\frac{x^2+y^2}{xy}}
$$

同理

$$
\dfrac{\partial z}{\partial y}=\dfrac{(x+y)(y^3-x^3)}{x^2y^3}e^{\frac{x^2+y^2}{xy}}
$$

$(3)$

$$
\begin{aligned}
\dfrac{dz}{dt}&=\dfrac{\partial z}{\partial x}\dfrac{dx}{dt}+\dfrac{\partial z}{\partial y}\dfrac{dy}{dt}\\
&=(2x+y)\cdot(2t)+(x+2y)\cdot1\\
&=(2t^2+t)\cdot(2t)+(t^2+2t)\cdot1\\
&=4t^3+3t^2+2t
\end{aligned}
$$

$(5)$

记 $s=x+y,t=xy$

$$
\begin{aligned}
\dfrac{\partial u}{\partial x}&=\dfrac{\partial u}{\partial s}\dfrac{\partial s}{\partial x}+\dfrac{\partial u}{\partial t}\dfrac{\partial t}{\partial x}\\
&=f_x(x+y,xy)+yf_y(x+y,xy)
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{\partial u}{\partial y}&=\dfrac{\partial u}{\partial s}\dfrac{\partial s}{\partial y}+\dfrac{\partial u}{\partial t}\dfrac{\partial t}{\partial y}\\
&=f_x(x+y,xy)+xf_y(x+y,xy)
\end{aligned}
$$

> 3. 设 $z=\dfrac{y}{f(x^2-y^2)}$，其中 $f$ 为可微函数，验证：
>
> $$
\dfrac1x\cdot\dfrac{\partial z}{\partial x}+\dfrac1y\cdot\dfrac{\partial z}{\partial y}=\dfrac z{y^2}
> $$

记 $u=f(x^2-y^2),v=y$，则 $z=\dfrac{v}{u}$

$$
\begin{aligned}
\dfrac{\partial z}{\partial x}&=\dfrac{\partial z}{\partial v}\dfrac{\partial v}{\partial x}+\dfrac{\partial z}{\partial u}\dfrac{\partial u}{\partial x}\\
&=\dfrac1u\cdot0-\dfrac{v}{u^2}f'(x^2-y^2)\cdot 2x\\
&=-\dfrac{2xyf'(x^2-y^2)}{f^2(x^2-y^2)}
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{\partial z}{\partial y}&=\dfrac{\partial z}{\partial v}\dfrac{\partial v}{\partial y}+\dfrac{\partial z}{\partial u}\dfrac{\partial u}{\partial y}\\
&=\dfrac1u\cdot1-\dfrac{v}{u^2}f'(x^2-y^2)\cdot(-2y)\\
&=\dfrac{2y^2f'(x^2-y^2)+f(x^2-y^2)}{f^2(x^2-y^2)}
\end{aligned}
$$

代入即可验证。

> 6. 设 $f(u)$ 是可微函数，$F(x,t)=f(x+2t)+f(3x-2t)$。试求 $F_x(0,0)$ 与 $F_t(0,0)$。

$$
\begin{aligned}
\dfrac{\partial F}{\partial x}&=\dfrac{\partial}{\partial x}(f(x+2t))+\dfrac{\partial}{\partial x}(f(3x-2t))\\
&=f'(x+2t)+3f'(3x-2t)
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{\partial F}{\partial t}&=\dfrac{\partial}{\partial t}(f(x+2t))+\dfrac{\partial}{\partial t}(f(3x-2t))\\
&=2f'(x+2t)-2f'(3x-2t)
\end{aligned}
$$

所以 $F_x(0,0)=4f'(0),F_t(0,0)=0$

## 习题 17.3

> 2. 求函数 $u=xyz$ 在沿点 $A(5,1,2)$ 到点 $B(9,4,14)$ 的方向 $\vec{AB}$ 上的方向导数。

$\vec{AB}=(4,3,12),\hat{AB}=(\dfrac4{13},\dfrac3{13},\dfrac{12}{13})$

$u_x(x_0,y_0,z_0)=y_0z_0,u_y(x_0,y_0,z_0)=x_0z_0,u_z(x_0,y_0,z_0)=x_0y_0$。

所以方向导数为 $(y_0z_0,x_0z_0,x_0y_0)\cdot\hat{AB}=\dfrac{98}{13}$

> 3. 求函数 $u=x^2+2y^2+3z^2+xy-4x+2y-4z$ 在 $A(0,0,0)$ 及 $B(5,-3,\dfrac23)$ 的梯度以及它们的模。

$u_x(x_0,y_0,z_0)=2x_0+y_0-4$

$u_y(x_0,y_0,z_0)=4y_0+x_0+2$

$u_z(x_0,y_0,z_0)=6z_0-4$

$\text{grad}f(A)=(-4,2,-4),|\text{grad}f(A)|=6$

$\text{grad}f(B)=(3,-5,0),|\text{grad}f(B)|=\sqrt{34}$

## 习题 17.4

> 1. 求下列函数的高阶偏导数：
>
> $(3)$ $z=x\ln(xy)$，$\dfrac{\partial^3z}{\partial x^2\partial y},\dfrac{\partial^3z}{\partial x\partial y^2}$

$(3)$

容易发现 $z$ 的各阶偏导数都是连续的，所以求偏导顺序可以交换。

$$
\dfrac{\partial z}{\partial x}=\ln(xy)+1
$$

$$
\dfrac{\partial^2z}{\partial x\partial y}=\dfrac1y
$$

$$
\dfrac{\partial^3z}{\partial x^2\partial y}=0
$$

$$
\dfrac{\partial^3z}{\partial x\partial y^2}=-\dfrac1{y^2}
$$

> 2. 设 $u=f(x,y),x=r\cos\theta,y=r\sin\theta$。证明：
>
> $$
\dfrac{\partial^2u}{\partial r^2}+\dfrac1r\cdot\dfrac{\partial u}{\partial r}+\dfrac1{r^2}\cdot\dfrac{\partial^2u}{\partial\theta^2}=\dfrac{\partial^2u}{\partial x^2}+\dfrac{\partial^2u}{\partial y^2}
> $$

$$
\begin{aligned}
\dfrac{\partial u}{\partial r}&=\dfrac{\partial u}{\partial x}\dfrac{\partial x}{\partial r}+\dfrac{\partial u}{\partial y}\dfrac{\partial y}{\partial r}\\
&=\cos\theta\dfrac{\partial u}{\partial x}+\sin\theta\dfrac{\partial u}{\partial y}\\
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{\partial^2u}{\partial r^2}&=\dfrac{\partial}{\partial r}(\dfrac{\partial u}{\partial r})\\
&=\cos^2\theta\dfrac{\partial^2u}{\partial x^2}+\sin^2\theta\dfrac{\partial^2u}{\partial y^2}+\cos\theta\sin\theta(\dfrac{\partial^2u}{\partial x\partial y}+\dfrac{\partial^2u}{\partial y\partial x})
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{\partial u}{\partial\theta}&=\dfrac{\partial u}{\partial x}\dfrac{\partial x}{\partial\theta}+\dfrac{\partial u}{\partial y}\dfrac{\partial y}{\partial\theta}\\
&=-r\sin\theta\dfrac{\partial u}{\partial x}+r\cos\theta\dfrac{\partial u}{\partial y}
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{\partial^2u}{\partial\theta^2}&=\dfrac{\partial}{\partial\theta}(\dfrac{\partial u}{\partial\theta})\\
&=r^2\sin^2\theta\dfrac{\partial^2u}{\partial x^2}+r^2\cos\theta^2\dfrac{\partial^2u}{\partial y^2}-2r^2\cos\theta\sin\theta\dfrac{\partial^2u}{\partial x\partial y}-r\cos\theta\dfrac{\partial u}{\partial x}-r\sin\theta\dfrac{\partial u}{\partial y}
\end{aligned}
$$

代入即可验证。

> 6. 通过对 $F(x,y)=\sin x\cos y$ 使用中值定理，证明：存在 $\theta\in(0,1)$，有
>
> $$
\dfrac34=\dfrac\pi3\cos\dfrac{\pi\theta}{3}\cos\dfrac{\pi\theta}6-\dfrac\pi6\sin\dfrac{\pi\theta}3\sin\dfrac{\pi\theta}6
> $$

对 $(0,0),(\dfrac\pi3,\dfrac\pi6)$ 使用中值定理。

$F_x(x,y)=\cos x\cos y,F_y(x,y)=-\sin x\sin y$。

由中值定理，$\exist\theta\in(0,1),\dfrac34=F(\dfrac\pi3,\dfrac\pi6)-F(0,0)=\dfrac\pi3F_x(\dfrac{\pi\theta}3,\dfrac{\pi\theta}6)+\dfrac\pi6F_y(\dfrac{\pi\theta}3,\dfrac{\pi\theta}6)=\dfrac\pi3\cos\dfrac{\pi\theta}3\cos\dfrac{\pi\theta}6-\dfrac\pi6\sin\dfrac{\pi\theta}3\sin\dfrac{\pi\theta}6$

> 7. 求下列函数在指定点处的泰勒公式：
>
> $(3)$ $f(x,y)=\ln(1+x+y)$ 在点 $(0,0)$

$(3)$

由数学归纳法可以证明，对 $f$ 求 $n$ 阶偏导的结果只与 $n$ 有关，与求偏导的变量无关。

也即 $\dfrac{\partial^nf}{\partial x^i\partial y^{n-i}}=\dfrac{(-1)^{n-1}(n-1)!}{(1+x+y)^n}$

所以由泰勒公式展开到任意 $m$ 阶

$$
\begin{aligned}
f(x,y)&=\sum_{i=0}^{m}\dfrac1{i!}\cdot(x\dfrac{\partial}{\partial x}+y\dfrac{\partial}{\partial y})^if(0,0)+o(\rho^m)\\
&=\sum_{i=0}^m\dfrac1{i!}\sum_{j=0}^i\binom{i}{j}x^jy^{i-j}\dfrac{\partial^if}{\partial x^j\partial y^{i-j}}(0,0)+o(\rho^m)\\
&=\sum_{i=1}^m\dfrac1{i!}\sum_{j=0}^i\binom ijx^jy^{i-j}\dfrac{(-1)^{i-1}(i-1)!}{1^i}+o(\rho^m)\\
&=\sum_{i=1}^m\dfrac{(-1)^{i-1}}{i}\sum_{j=0}^i\binom ijx^jy^{i-j}+o(\rho^m)\\
&=\sum_{i=1}^m\dfrac{(-1)^{i-1}}{i}(x+y)^i+o(\rho^m)
\end{aligned}
$$

> 8. 求下列函数的极值点：
>
> $(3)$ $z=e^{2x}(x+y^2+2y)$

$(3)$

$\dfrac{\partial z}{\partial x}=e^{2x}(2x+2y^2+4y+1)$

$\dfrac{\partial z}{\partial y}=2e^{2x}(y+1)$

$\dfrac{\partial^2z}{\partial x^2}=4e^{2x}(x+y^2+2y+1)$

$\dfrac{\partial^2z}{\partial y^2}=2e^{2x}$

$\dfrac{\partial^2z}{\partial x\partial y}=\dfrac{\partial^2z}{\partial y\partial x}=4e^{2x}(y+1)$

令 $\dfrac{\partial z}{\partial x}=\dfrac{\partial z}{\partial y}=0$，得到 $(x,y)=(\dfrac12,-1)$，$z=-\dfrac e2$

该点处 $z_{xx}=2e>0,z_{yy}=2e>0,z_{xy}=z_{yx}=0$。

所以 $z_{xx}>0,z_{xx}z_{yy}-z_{xy}^2>0$，因此是极小值点。

> 9. 求下列函数的最大值与最小值：
>
> $(2)$ $z=x^2-xy+y^2,\{(x,y)\mid|x|+|y|\le 1\}$

$(2)$

$z_x=2x-y$

$z_y=-x+2y$

令 $z_x=z_y=0$，得稳定点 $(0,0)$，该点处 $z=0$。

在边界 $|x|+|y|=1$ 上，由对称性，可以只考虑 $y\ge0$ 的情况。

当 $x\in[0,1],y=1-x$ 时，$z=3x^2-3x+1\in[\dfrac14,1]$

当 $x\in[-1,0],y=x+1$ 时，$z=x^2+x+1\in[\dfrac34,1]$

所以最小值 $0$，最大值 $1$。

> 11. 在 $xOy$ 平面上求一点，使它到三直线 $x=0,y=0$ 及 $x+2y-16=0$ 的距离平方和最小。

$s=x^2+y^2+\dfrac{(x+2y-16)^2}{1^2+2^2}$

显然，所求点不会在三条直线围成的三角形之外。

$s_x=2x+\dfrac{2}{5}(x+2y-16)$

$s_y=2y+\dfrac45(x+2y-16)$

令 $s_x=s_y=0$，得稳定点 $(\dfrac85,\dfrac{16}5)$。

计算可知这是一个极小值点。

计算边界上的点，都不会比这个点小。

所以 $(\dfrac85,\dfrac{16}5)$ 就是最小值点。