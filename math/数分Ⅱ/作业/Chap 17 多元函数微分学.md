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