## 习题 10.1

> 1. 求由抛物线 $y=x^2$ 与 $y=2-x^2$ 所围图形的面积。

容易求得两抛物线有两个交点 $(-1,1),(1,1)$。

所求面积 $S=\int_{-1}^1|x^2-(2-x^2)|dx=\dfrac83$

> 5. 求心形线 $r=a(1+\cos\theta)(a>0)$ 所围图形的面积。

所求面积 $S=\dfrac12\int_0^{2\pi}r^2d\theta=\dfrac{a^2}2\int_0^{2\pi}(\cos^2\theta+2\cos\theta+1)d\theta=\dfrac{3\pi a^2}2$

> 6. 求三叶形曲线 $r=a\sin3\theta(a>0)$ 所围图形的面积。

所求面积 $S=\dfrac12\int_0^{2\pi}r^2d\theta=\dfrac{a^2}2\int_0^{2\pi}\sin^23\theta d\theta=\dfrac{a^2}2\int_0^{2\pi}\dfrac{1-\cos6\theta}2d\theta=\dfrac{\pi a}4$

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