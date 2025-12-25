## 习题 10.1

> 1. 求由抛物线 $y=x^2$ 与 $y=2-x^2$ 所围图形的面积。

容易求得两抛物线有两个交点 $(-1,1),(1,1)$。

所求面积 $S=\int_{-1}^1|x^2-(2-x^2)|dx=\dfrac83$

> 5. 求心形线 $r=a(1+\cos\theta)(a>0)$ 所围图形的面积。

所求面积 $S=\dfrac12\int_0^{2\pi}r^2d\theta=\dfrac{a^2}2\int_0^{2\pi}(\cos^2\theta+2\cos\theta+1)d\theta=\dfrac{3\pi a^2}2$

> 6. 求三叶形曲线 $r=a\sin3\theta(a>0)$ 所围图形的面积。

在 $[0,2\pi]$ 中，当 $r\ge0$ 时，$\theta\in[0,\dfrac\pi3]\cup[\dfrac{2\pi}3,\pi]\cup[\dfrac{4\pi}3,\dfrac{5\pi}3]$。

由对称性，所求面积 $S=\dfrac32\int_0^{\frac\pi3}r^2d\theta=\dfrac{3a^2}2\int_0^{\frac\pi3}\sin^23\theta d\theta=\dfrac{3a^2}2\int_0^{\frac\pi3}\dfrac{1-\cos6\theta}2d\theta=\dfrac{\pi a^2}4$

## 习题 10.2

> 2. 求下列平面曲线绕轴旋转所围成立体的体积：
>
> $(1)y=\sin x,0\le x\le\pi$，绕 $x$ 轴；
>
> $(2)x=a(t-\sin t),y=a(1-\cos t)(a>0),0\le t\le2\pi$，绕 $x$ 轴；
>
> $(3)\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}=1$，绕 $y$ 轴。

$(1)$

$$
V=\pi\int_0^\pi\sin^2xdx=\pi\int_0^\pi\dfrac{1-\cos2x}2dx=\dfrac{\pi^2}2
$$

$(2)$

$$
V=\pi\int_0^{2\pi}y^2x'dt=a^3\pi\int_0^{2\pi}(1-\cos t)^3dt=a^3\pi\int_0^{2\pi}(\dfrac52-\dfrac{15}4\cos t+\dfrac32\cos2t-\dfrac14\cos3t)dt=5a^3\pi^2
$$

$(3)$

$x=a\cos t,y=b\sin t,t\in[-\dfrac\pi2,\dfrac\pi2]$

$$
V=\pi\int_{-\frac\pi2}^{\frac\pi2}x^2y'dt=a^2b\pi\int_{-\frac\pi2}^{\frac\pi2}\cos^3tdt=a^2b\pi\int_{-\frac\pi2}^{\frac\pi2}(\dfrac34\cos t+\dfrac14\cos3t)dt=\dfrac{4a^2b\pi}3
$$

## 习题 10.3

> 1. 求下列曲线的弧长：
>
> $(1)y=x^{\frac32},0\le x\le 4$。
>
> $(3)x=a\cos^3t,y=a\sin^3t(a>0),0\le t\le2\pi$。
>
> $(5)r=a\sin^3\dfrac\theta3(a>0),0\le\theta\le3\pi$。

$(1)$

$$
l=\int_0^4\sqrt{1+(y')^2}dx=\int_0^4\sqrt{1+\dfrac94x}dx=\left.(\dfrac8{27}(1+\dfrac94x)^{\frac32})\right|_0^4=\dfrac{80\sqrt{10}-8}{27}
$$

$(3)$

$$
l=\int_0^{2\pi}\sqrt{(x')^2+(y')^2}dt=\int_0^{2\pi}\sqrt{9a^2\sin^2t\cos^4t+9a^2\sin^4t\cos^2t}dt=\dfrac{3a}2\int_0^{2\pi}|\sin2t|dt=6a
$$

$(5)$

$$
l=\int_0^{3\pi}\sqrt{r^2+(r')^2}d\theta=\int_0^{3\pi}\sqrt{a^2\sin^6\dfrac\theta3+a^2\sin^4\dfrac\theta3\cos^2\dfrac\theta3}d\theta=a\int_0^{3\pi}\sin^2\dfrac\theta3d\theta=\dfrac{3\pi a}2
$$