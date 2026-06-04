# Chap 22 曲面积分

## 习题 22.1

> 1. 计算下列第一型曲面积分：
>
> $(2)$ $\iint_S(x^2+y^2)dS$，其中 $S$ 为立体 $\sqrt{x^2+y^2}\le z\le 1$ 的边界曲面
>
> $(4)$ $\iint_S xyzdS$，其中 $S$ 为平面 $x+y+z=1$ 在第一卦限中的部分。

$(2)$

边界曲面由两部分构成 $S_1=\{(x,y,z)\mid z=1,x^2+y^2\le 1\},S_2=\{(x,y,z)\mid z=\sqrt{x^2+y^2},x^2+y^2\le 1\}$。

对于 $S_2$，记 $D_2=\{(x,y)\mid x^2+y^2\le 1\}$

$$
\begin{aligned}
\iint_{S_2}(x^2+y^2)dS&=\iint_{D_2}(x^2+y^2)\sqrt{1+z_x^2+z_y^2}dxdy\\
&=\sqrt2\iint_{D_2}(x^2+y^2)dxdy\\
&=\sqrt2\int_0^{2\pi}d\theta\int_0^{1}r^2\cdot rdr\\
&=\dfrac{\sqrt2\pi}{2}
\end{aligned}
$$

对于 $S_1$，积分结果就是 $\dfrac\pi2$

所以最终积分结果为 $\dfrac{1+\sqrt2}{2}\pi$

$(4)$

$S=\{(x,y,z)\mid z=1-x-y,x,y\ge0,x+y\le 1\},D=\{(x,y)\mid x,y\ge0,x+y\le 1\}$

那么

$$
\begin{aligned}
\iint_SxyzdS&=\iint_D xy(1-x-y)\sqrt{1+z_x^2+z_y^2}dxdy\\
&=\sqrt3\iint_D xy(1-x-y)dxdy\\
&=\sqrt3\int_0^1xdx\int_0^{1-x}(1-x-y)ydy\\
&=\dfrac{\sqrt3}6\int_0^1(1-x)^3xdx\\
&=\dfrac{\sqrt3}{120}
\end{aligned}
$$