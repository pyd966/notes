# Chap 20 曲线积分

## 习题 20.1

> 1. 计算下列第一型曲线积分：
>
> $(2)$ $\int_L(x^2+y^2)^{1/2}ds$，其中 $L$ 是以原点为中心、$R$ 为半径的右半圆周。
>
> $(7)$ $\int_L\sqrt{2y^2+z^2}ds$，其中 $L$ 是 $x^2+y^2+z^2=a^2$ 与 $x=y$ 相交的圆周。

$(2)$

在右半圆周上，$x^2+y^2=L^2$，所以

$$
\int_L(x^2+y^2)^{1/2}ds=L\int_Lds=\pi L^2
$$

$(7)$

在 $L$ 上，有 $2y^2+z^2=a^2$，并且容易发现 $L$ 是以原点为圆心，$a$ 为半径的圆，那么

$$
\int_L\sqrt{2y^2+z^2}ds=a\int_Lds=2\pi a^2
$$

> 2. 求曲线 $x=a,y=at,z=\dfrac12at^2(0\le t\le1,a>0)$ 的质量，设其线密度为 $\rho=\sqrt{\dfrac{2z}a}$

即计算 $\int_L\rho ds$。

$$
\begin{aligned}
\int_L\rho ds&=\int_0^1\sqrt{\dfrac{2z}a}\sqrt{(0)^2+(a)^2+(at)^2}dt\\
&=a\int_0^1t\sqrt{1+t^2}dt\\
&=\dfrac{2\sqrt2-1}{3}a
\end{aligned}
$$

> 4. 若曲线以极坐标 $\rho=\rho(\theta)(\theta_1\le\theta\le\theta_2)$ 表示，试给出计算 $\int_Lf(x,y)ds$ 的公式，并用此公式计算下列曲线积分：
>
> $(1)$ $\int_Le^{\sqrt{x^2+y^2}}ds$，其中 $L$ 为曲线 $\rho=a(0\le\theta\le\dfrac\pi4)$ 的一段

$x=\rho(\theta)\cos\theta,y=\rho(\theta)\sin\theta$

那么 $x'=\rho'\cos\theta-\rho\sin\theta,y='\rho'\sin\theta+\rho\cos\theta$

所以

$$
\int_Lf(x,y)ds=\int_{\theta_1}^{\theta_2}f(\rho\cos\theta,\rho\sin\theta)\sqrt{x'^2+y'^2}d\theta=\int_{\theta_1}^{\theta_2}f(\rho\cos\theta,\rho\sin\theta)\sqrt{\rho^2+\rho'^2}d\theta
$$

$(1)$

$$
\begin{aligned}
\int_Le^{\sqrt{x^2+y^2}}ds&=\int_0^{\frac\pi4}e^a\sqrt{a^2+0^2}d\theta\\
&=\dfrac{\pi ae^a}4
\end{aligned}
$$

## 习题 20.2

> 1. 计算第二型曲线积分：
>
> $(2)$ $\int_L(2a-y)dx+dy$，其中 $L$ 为摆线 $x=a(t-\sin t),y=a(1-\cos t)(0\le t\le2\pi)$ 沿 $t$ 增加方向的一段；
>
> $(3)$ $\oint_L\dfrac{-xdx+ydy}{x^2+y^2}$，其中 $L$ 为圆周 $x^2+y^2=1$，依逆时针方向。

$(2)$

$$
\begin{aligned}
\int_L(2a-y)dx+dy&=\int_0^{2\pi}(a(1+\cos t)a(1-\cos t)+a\sin t)dt\\
&=a\int_0^{2\pi}(a(1-\cos^2t)+\sin t)dt\\
&=a\int_0^{2\pi}(a\sin^2t+\sin t)dt\\
&=a\int_0^{2\pi}(\dfrac{1-\cos2t}2a+\sin t)dt\\
&=\pi a^2
\end{aligned}
$$

$(3)$

取 $x=\cos\theta,y=\sin\theta$，其中 $\theta$ 从 $0\to2\pi$

$$
\begin{aligned}
\oint_L\dfrac{-xdx+ydy}{x^2+y^2}&=\int_0^{2\pi}(\cos\theta\sin\theta+\sin\theta\cos\theta)d\theta\\
&=\int_0^{2\pi}\sin2\theta d\theta\\
&=0
\end{aligned}
$$

> 3. 设一质点受力作用，力的方向指向原点，大小与质点到 $xOy$ 平面的距离成反比。若质点沿直线 $x=at,y=bt,z=ct(c\neq0)$ 从 $M(a,b,c)$ 移动到 $N(2a,2b,2c)$，求力所做的功。

不难发现 $\vec{OM},\vec{ON}$ 共线，并且在质点从 $M\to N$ 的过程中，力的方向始终跟 $\vec{MN}$ 反向。

所以 $\vec F\cdot\vec{\Delta s}=-|\vec F||\vec{\Delta s}|$，我们把第二类曲线积分转化成了第一类曲线积分。

$$
\begin{aligned}
\int_{MN}-|\vec F| ds&=-\int_{MN}\dfrac{k}{|z|}ds\\
&=-\int_1^2\dfrac{k}{|c|t}\sqrt{a^2+b^2+c^2}dt\\
&=-k\dfrac{\sqrt{a^2+b^2+c^2}}{c}\int_1^2\dfrac1tdt\\
&=-k\ln 2\dfrac{\sqrt{a^2+b^2+c^2}}{|c|}
\end{aligned}
$$

其中 $k$ 是力与质点到 $xOy$ 平面距离的乘积常数。

> 5. 计算沿空间曲线的第二型曲线积分：
>
> $(1)$ $\int_Lxyzdz$，其中 $L$ 为 $x^2+y^2+z^2=1$ 与 $y=z$ 相交的圆，其方向按曲线依次经过第一、二、七、八卦限。

$(1)$

由题知，$y=z$，所以等价于求 $\int_{L'}xy^2dy$，其中 $L'$ 为 $x^2+2y^2=1$。

进行参数化，$x=\cos\theta,y=\dfrac{\sin\theta}{\sqrt{2}}$

那么

$$
\begin{aligned}
\int_{L'}xy^2dy&=\int_0^{2\pi}\dfrac1{2\sqrt2}\cos^2\theta\sin^2\theta d\theta\\
&=\int_0^{2\pi}\dfrac1{8\sqrt2}\sin^22\theta d\theta\\
&=\int_0^{2\pi}\dfrac{1-\cos4\theta}{16\sqrt2}d\theta\\
&=\dfrac{\pi}{8\sqrt2}
\end{aligned}
$$