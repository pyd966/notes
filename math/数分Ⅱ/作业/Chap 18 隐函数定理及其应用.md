# Chap 18 隐函数定理及其应用

## 习题 18.1

> 2. 方程 $xy+z\ln y+e^{xz}=1$ 在点 $(0,1,1)$ 的某邻域上能否确定出某一个变量为另外两个变量的函数？

首先点 $(0,1,1)$ 满足该方程，并且 $F(x,y,z)=xy+z\ln y+e^{xz}-1$ 在该点邻域上连续。

计算 $F_x(x,y,z)=y+ze^{xz},F_y(x,y,z)=x+\dfrac zy,F_z(x,y,z)=\ln y+xe^{xz}$

$F_x(0,1,1)=2,F_y(0,1,1)=1,F_z(0,1,1)=0$。

所以可以确定 $x$ 关于 $y,z$ 和 $y$ 关于 $x,z$ 的函数，不知道能否确定 $z$ 关于 $x,y$ 的函数。

> 3. 求由下列方程所确定的隐函数的导数：
>
> $(5)$ $x^2+y^2+z^2-2x+2y-4z-5=0$，求 $\dfrac{\partial z}{\partial x},\dfrac{\partial z}{\partial y}$

$(5)$

$F_x(x,y,z)=2x-2,F_y(x,y,z)=2y+2,F_z(x,y,z)=2z-4$。

当 $z\neq2$ 时，有 $F_z\neq0$，满足隐函数可微条件。

$\dfrac{\partial z}{\partial x}=-\dfrac{F_x(x,y,z)}{F_z(x,y,z)}=\dfrac{x-1}{2-z}$

$\dfrac{\partial z}{\partial y}=-\dfrac{F_y(x,y,z)}{F_z(x,y,z)}=\dfrac{y+1}{2-z}$

> 4. 设 $z=x^2+y^2$，其中 $y=f(x)$ 为由方程 $x^2-xy+y^2=1$ 所确定的隐函数，求 $\dfrac{dz}{dx}$ 及 $\dfrac{d^2z}{dx^2}$

$F_x(x,y)=2x-y,F_y(x,y)=-x+2y$。

$\dfrac{dy}{dx}=-\dfrac{F_x(x,y)}{F_y(x,y)}=\dfrac{2x-y}{x-2y}$

$\dfrac{d^2y}{dx^2}=\dfrac{(2-\frac{dy}{dx})(x-2y)-(1-2\frac{dy}{dx})(2x-y)}{(x-2y)^2}=\dfrac{6(y^2-x^2)}{(x-2y)^3}$

$\dfrac{dz}{dx}=2x+2y\cdot\dfrac{dy}{dx}=\dfrac{2x^2-2y^2}{x-2y}$

$\dfrac{d^2z}{dx^2}=2+2((\dfrac{dy}{dx})^2+y\cdot\dfrac{d^2y}{dx^2})=\dfrac{10x^3-48x^2y+42xy^2-8y^3}{(x-2y)^3}$

> 7. 求由下列方程所确定的隐函数的偏导数：
>
> $(1)$ $x+y+z=e^{-(x+y+z)}$，求 $z$ 对于 $x,y$ 的一阶与二阶偏导数。

$(1)$

$F(x,y,z)=e^{-(x+y+z)}-(x+y+z)$

$F_x(x,y,z)=-e^{-(x+y+z)}-1$

$F_y(x,y,z)=-e^{-(x+y+z)}-1$

$F_z(x,y,z)=-e^{-(x+y+z)}-1$

$\dfrac{\partial z}{\partial x}=-\dfrac{F_x(x,y,z)}{F_z(x,y,z)}=-1$

$\dfrac{\partial z}{\partial y}=-1$

$\dfrac{\partial^2z}{\partial x^2}=0,\dfrac{\partial^2z}{\partial y^2}=0$