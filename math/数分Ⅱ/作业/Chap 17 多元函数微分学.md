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
