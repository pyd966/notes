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

## 习题 18.2

> 2. 求下列方程组所确定的隐函数的导数：
>
> $(1)$ $\begin{cases}x^2+y^2+z^2=a^2\\ x^2+y^2=ax\end{cases}$，求 $\dfrac{dy}{dx},\dfrac{dz}{dx}$

不难发现隐函数存在。

方程组对 $x$ 求导。

$$
\begin{cases}
2x+2y\dfrac{dy}{dx}+2\dfrac{dz}{dx}=0\\
2x+2y\dfrac{dy}{dx}=a\\
\end{cases}
$$

解得 $\dfrac{dy}{dx}=\dfrac{a-2x}{2y},\dfrac{dz}{dx}=-\dfrac a{2z}$

> 3. 求下列函数组所确定的反函数组的偏导数：
>
> $(1)$ $\begin{cases}x=e^u+u\sin v\\ y=e^u-u\cos v\end{cases}$，求 $u_x,v_x,u_y,v_y$

$(1)$

$$
\begin{cases}
e^u+u\sin v-x=0\\
e^u-u\cos v-y=0\\
\end{cases}
$$

将 $u,v$ 视为 $u(x,y),v(x,y)$。

对 $x$ 求导

$$
\begin{cases}
e^uu_x+u_x\sin v+uv_x\cos v-1=0\\
e^uu_x-u_x\cos v+uv_x\sin v=0
\end{cases}
$$

对 $y$ 求导

$$
\begin{cases}
e^uu_y+u_y\sin v+uv_y\cos v=0\\
e^uu_y-u_x\cos v+uv_y\sin v-1=0
\end{cases}
$$

解得

$$
u_x=\dfrac{\sin v}{e^u\sin v-e^u\cos v+1}
$$

$$
v_x=\dfrac{\cos v-e^u}{u(e^u\sin v-e^u\cos v+1)}
$$

$$
u_y=\dfrac{-\cos v}{e^u\sin v-e^u\cos v+1}
$$

$$
v_y=\dfrac{e^u+\sin v}{u(e^u\sin v-e^u\cos v+1)}
$$

> 5. 设以 $u,v$ 为新的自变量变换下列方程：
>
> $(1)$ $(x+y)\dfrac{\partial z}{\partial x}-(x-y)\dfrac{\partial z}{\partial y}=0$，设 $u=\ln\sqrt{x^2+y^2},v=\arctan\dfrac yx$

$(1)$

解得 $\begin{cases}x=\pm\dfrac{e^u}{\sqrt{1+\tan^2v}}\\y=\pm\dfrac{e^u\tan v}{\sqrt{1+\tan^2v}}\end{cases}$

而 $x^2+y^2=e^{2u}$

$\dfrac{\partial z}{\partial x}=\dfrac{\partial z}{\partial u}\dfrac{\partial u}{\partial x}+\dfrac{\partial z}{\partial v}\dfrac{\partial v}{\partial x}=\dfrac{x}{x^2+y^2}\dfrac{\partial z}{\partial u}-\dfrac{y}{x^2+y^2}\dfrac{\partial z}{\partial v}=e^{-2u}(x\dfrac{\partial z}{\partial u}-y\dfrac{\partial z}{\partial v})$

$\dfrac{\partial z}{\partial y}=\dfrac{\partial z}{\partial u}\dfrac{\partial u}{\partial y}+\dfrac{\partial z}{\partial v}\dfrac{\partial v}{\partial y}=\dfrac{y}{x^2+y^2}\dfrac{\partial z}{\partial u}+\dfrac{x}{x^2+y^2}\dfrac{\partial z}{\partial v}=e^{-2u}(y\dfrac{\partial z}{\partial u}+x\dfrac{\partial z}{\partial v})$

变换后的方程：

$$
\dfrac{\partial z}{\partial u}-\dfrac{\partial z}{\partial v}=0
$$

## 习题 18.3

> 1. 求平面曲线 $x^{2/3}+y^{2/3}=a^{2/3}(a>0)$ 上任一点处的切线方程，并证明这些切线被坐标轴所截取的线段等长。

$F(x,y)=x^{2/3}+y^{2/3}-a^{2/3}=0$

$F_x(x_0,y_0)=\dfrac23x_0^{-1/3},F_y(x_0,y_0)=\dfrac23y_0^{-1/3}$

切线方程：$F_x(x_0,y_0)(x-x_0)+F_y(x_0,y_0)(y-y_0)=0$，也就是 $x_0^{-1/3}x+y_0^{-1/3}y-a^{2/3}=0$

与坐标轴交于 $(0,y_0^{1/3}a^{2/3}),(x_0^{1/3}a^{2/3},0)$

线段长度 $l^2=a^{4/3}(x_0^{2/3}+y_0^{2/3})=a^2$，所以 $l=a$ 是定值。

> 2. 求下列曲线在所示点处的切线与法平面：
>
> $(2)$ $2x^2+3y^2+z^2=9,z^2=3x^2+y^2$，在点 $(1,-1,2)$

$(2)$

$$
\begin{cases}
4x\dfrac{dx}{dz}+6y\dfrac{dy}{dz}+2z=0\\
2z=6x\dfrac{dx}{dz}+2y\dfrac{dy}{dz}
\end{cases}
$$

所以

$\dfrac{dx}{dz}=\dfrac{4z}{7x},\dfrac{dy}{dz}=-\dfrac{5z}{7y}$

所以切线：$\dfrac{7(x-1)}{8}=\dfrac{7(y+1)}{10}=\dfrac{z-2}{1}$

法平面：$\dfrac{8}{7}(x-1)+\dfrac{10}{7}(y+1)+(z-2)=0$

> 3. 求下列曲面在所示点处的切平面与法线：
>
> $(2)$ $\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}+\dfrac{z^2}{c^2}=1$，在点 $(\dfrac{a}{\sqrt3},\dfrac{b}{\sqrt3},\dfrac{c}{\sqrt3})$

$(2)$

$F(x,y,z)=\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}+\dfrac{z^2}{c^2}-1=0$

$F_x(x_0,y_0,z_0)=\dfrac{2\sqrt3}{3a},F_y(x_0,y_0,z_0)=\dfrac{2\sqrt3}{3b},F_z(x_0,y_0,z_0)=\dfrac{2\sqrt3}{3c}$

切平面：$\dfrac{2}{3a}(\sqrt3x-a)+\dfrac{2}{3b}(\sqrt3x-b)+\dfrac{2}{3c}(\sqrt3x-c)=0$

法线：$a(\sqrt3x-a)=b(\sqrt3x-b)=c(\sqrt3x-c)$

> 5. 求曲面 $x^2+2y^2+3z^2=21$ 的切平面，使它平行于平面
>
> $$
x+4y+6z=0
> $$

考虑点 $P(x_0,y_0,z_0)$

在该点处的切平面为 $x_0(x-x_0)+2y_0(y-y_0)+3z_0(z-z_0)=0$

所以 $\begin{cases}x_0^2+2y_0^2+3z_0^2=21\\ \frac{x_0}1=\frac{2y_0}4=\frac{3z_0}{6}\end{cases}$

所以 $P(1,2,2)$ 或 $(-1,-2,-2)$，平面为 $(x-1)+4(y-2)+6(z-2)=0$ 或 $(x+1)+4(y+2)+6(z+2)=0$

> 6. 在曲线 $x=t,y=t^2,z=t^3$ 上求出一点，使曲线在此点的切线平行于平面 $x+2y+z=4$

切线：$\dfrac{x-t_0}{1}=\dfrac{y-t_0^2}{2t_0}=\dfrac{z-t_0^3}{3t_0^2}$

方向向量 $\vec l=(1,2t_0,3t_0^2)$，平面法向量 $\vec n=(1,2,1)$

由平行条件知 $\vec l\cdot\vec n=0$，所以 $1+4t_0+3t_0^2=0$，解得 $t_0=-1$ 或 $t_0=-\dfrac13$。

所求点为 $(-1,1,-1)$ 或 $(-\dfrac13,\dfrac19,-\dfrac1{27})$

> 7. 求函数
>
> $$
u=\dfrac x{\sqrt{x^2+y^2+z^2}}
> $$
>
> 在点 $M(1,2,-2)$ 沿曲线
>
> $$
x=t,y=2t^2,z=-2t^4
> $$
>
> 在该点切线的方向导数。

在点 $(1,2,-2)$ 处，对应的 $t_0=1$。

所以切线方向向量 $\vec l=(1,4,-8)$。

$u_x=\dfrac{y^2+z^2}{(x^2+y^2+z^2)^{3/2}},u_x(M)=\dfrac8{27}$

$u_y=-\dfrac{xy}{(x^2+y^2+z^2)^{3/2}},u_y(M)=-\dfrac2{27}$

$u_z=-\dfrac{xz}{(x^2+y^2+z^2)^{3/2}},u_z(M)=\dfrac2{27}$

所以方向导数 $f_l(M)=-\dfrac{16}{243}$。