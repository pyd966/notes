## 习题 5.1

> 6. 求下列曲线在指定点 $P$ 的切线方程与法线方程：
>
> $(1)$ $y=\dfrac{x^2}4,P(2,1)$

$(1)$

$f'(x)=y'=\dfrac x2$

切线方程：$y-f(x_0)=f'(x_0)(x-x_0)$，也就是 $y=x-1$。

法线方程：$y-f(x_0)=-\dfrac1{f'(x_0)}(x-x_0)$，也就是 $y=-x+3$。

> 8. 设函数
>
> $$
> f(x)=\begin{cases}
> x^m\sin\dfrac1x&,x\neq0\\
> 0&,x=0\\
> \end{cases}
> (m\in Z^+)
> $$
>
> 试问：$(1)$ 当 $m$ 等于何值时，$f$ 在 $x=0$ 连续？
>
> $(2)$ 当 $m$ 等于何值时，$f$ 在 $x=0$ 可导？

$(1)$

即要求 $\lim\limits_{x\to0}f(x)=f(0)=0$。

由 $m\in Z^+$ 知 $m\ge1$，此时

$\lim\limits_{x\to0}f(x)=\lim\limits_{x\to0}x^m\sin\dfrac1x=0$。这是由于 $x^m$ 是无穷小量，$\sin\dfrac1x$ 有界。

所以，当 $m$ 取任意正整数值时都连续。

$(2)$

即要求 $\lim\limits_{x\to0}\dfrac{f(x)-f(0)}{x-0}=\lim\limits_{x\to0}\dfrac{f(x)}x=\lim\limits_{x\to0}x^{m-1}\sin\dfrac1x$ 存在。

当 $m=1$ 时，$\lim\limits_{x\to0}\sin\dfrac1x$ 显然不存在。

当 $m\ge2$ 时，$\lim\limits_{x\to0}x^{m-1}\sin\dfrac1x=0$。

综上，$m$ 取 $\ge 2$ 的任意值均可。

> 9. 求下列函数的稳定点：
>
> $(1)f(x)=\sin x-\cos x$
>
> $(2)f(x)=x-\ln x$

$(1)$

$f'(x)=\cos x+\sin x$。

令 $f'(x)=0$，得 $\sin x+\cos x=0$，综合 $\sin^2x+\cos^2x=1$ 可以解得 $x=k\pi-\dfrac\pi4(k\in Z)$。

$(2)$

$f'(x)=1-\dfrac1x$。

令 $f'(x)=0$，得 $x=1$。

> 13. 证明：若 $f'(x_0)$ 存在，则
>
> $$
> \lim_{\Delta x\to0}\dfrac{f(x_0+\Delta x)-f(x_0-\Delta x)}{\Delta x}=2f'(x_0)
> $$

$$
\begin{aligned}
\lim_{\Delta x\to0}\dfrac{f(x_0+\Delta x)-f(x_0-\Delta x)}{\Delta x}&=\lim\limits_{\Delta x\to0}\dfrac{f(x_0+\Delta x)-f(x_0)+f(x_0)-f(x_0-\Delta x)}{\Delta x}\\
&=\lim\limits_{\Delta x\to0}\dfrac{f(x_0+\Delta x)-f(x_0)}{\Delta x}+\lim\limits_{\Delta x\to0}\dfrac{f(x_0)-f(x_0-\Delta x)}{\Delta x}\\
&=f'(x_0)+\lim\limits_{-\Delta x\to0}\dfrac{f(x_0)-f(x_0+\Delta x)}{-\Delta x}\\
&=f'(x_0)+\lim\limits_{-\Delta x\to0}\dfrac{f(x_0+\Delta x)-f(x_0)}{\Delta x}\\
&=2f'(x_0)
\end{aligned}
$$

## 习题 5.2

> 1. 求下列函数在指定点的导数：
>
> $(2)$ 设 $f(x)=\dfrac x{\cos x}$，求 $f'(0),f'(\pi)$。

$(2)$

$f'(x)=\dfrac{\cos x+x\sin x}{\cos^2x}$

$f'(0)=1,f'(\pi)=-1$

> 2. 求下列函数的导数：
>
> $(5)y=x^3\log_3x$
>
> $(6)y=e^x\cos x$
>
> $(8)y=\dfrac{\tan x}x$
>
> $(10)y=\dfrac{1+\ln x}{1-\ln x}$

$(5)$

$y'=3x^2\log_3x+\dfrac{x^3}{x\ln3}=3x^2\log_3x+\dfrac{x^2}{\ln3}$

$(6)$

$y'=e^x\cos x-e^x\sin x$

$(8)$

$y'=\dfrac{\dfrac{x}{\cos^2x}-\tan x}{x^2}=\dfrac{x-\sin x\cos x}{x^2\cos^2x}$

$(10)$

$y'=\dfrac{\dfrac1x(1-\ln x)-(-\dfrac1x)(1+\ln x)}{(1-\ln x)^2}=\dfrac{2}{x(1-\ln x)^2}$

> 3. 求下列函数的导数：
>
> $(8)y=\ln\dfrac{\sqrt{1+x}-\sqrt{1-x}}{\sqrt{1+x}+\sqrt{1-x}}$
>
> $(13)y=\arcsin\dfrac1x$
>
> $(20)y=x^{x^x}$

$(8)$

$y=\ln\dfrac{(\sqrt{1+x}-\sqrt{1-x})(\sqrt{1+x}+\sqrt{1-x})}{(\sqrt{1+x}+\sqrt{1-x})^2}=\ln(2x)-2\ln(\sqrt{1+x}+\sqrt{1-x})$

$y'=\dfrac1x-2(\dfrac{1}{\sqrt{1+x}+\sqrt{1-x}})(\dfrac12\cdot\dfrac{1}{\sqrt{1+x}}-\dfrac12\cdot\dfrac1{\sqrt{1-x}})=\dfrac{1}{|x|\sqrt{1-x^2}}$

$(13)$

$y'=\dfrac1{\sqrt{1-(\frac1x)^2}}\cdot(-\dfrac1{x^2})=-\dfrac{1}{x\sqrt{x^2-1}}$

$(20)$

$\ln y=x^x\ln x$

$\ln\ln y=x\ln x+\ln\ln x$

$\dfrac{1}{\ln y}\cdot\dfrac1y\cdot y'=\ln x+1+\dfrac1{\ln x}\cdot\dfrac1x$

最终得到 $y'=x^{x^x}\cdot x^x\ln x(\ln x+1+\dfrac1{x\ln x})$

> 4. 对下列各函数计算 $f'(x),f'(x+1),f'(x-1)$
>
> $(2)f(x+1)=x^3$

$f(x)=(x-1)^3$

$f'(x)=3(x-1)^2$

$f'(x+1)=3x^2$

$f'(x-1)=3(x-2)^2$

## 习题 5.3

> 1. 求下列由参数方程所确定的导数 $\dfrac{\text{d}y}{\text{d}x}$：
>
> $(1)\begin{cases}x=\cos^4t\\y=\sin^4t\end{cases}$，在 $t=\dfrac\pi3$ 处。

$\dfrac{\text{d}y}{\text{d}x}=\dfrac{\frac{\text{d}y}{\text{d}t}}{\frac{\text{d}x}{\text{d}t}}=\dfrac{4\sin^3t\cdot(\cos t)}{4\cos^3t\cdot(-\sin t)}=-\dfrac{\sin^2t}{\cos^2t}$

当 $t=\dfrac\pi3$ 时，结果为 $-3$。

> 3. 设曲线方程为 $\begin{cases}x=1-t^2\\y=t-t^2\end{cases}$，求它在下列点处的切线方程与法线方程：
>
> $(1)t=1$。

$\dfrac{\text{d}y}{\text{d}x}=\dfrac{\frac{\text{d}y}{\text{d}t}}{\frac{\text{d}x}{\text{d}t}}=\dfrac{1-2t}{-2t}=\dfrac12$，这是切线的斜率，记作 $k$。

当 $t=1$ 时，$x_0=0,y_0=0$。

所以切线方程：$y-y_0=k(x-x_0)$，即 $y=\dfrac12x$。

法线方程：$y-y_0=-\dfrac1k(x-x_0)$，即 $y=-2x$。

## 习题 5.4

> 1. 求下列函数在指定点的高阶导数：
>
> $(2)f(x)=\dfrac x{\sqrt{1+x^2}}$，求 $f''(0),f''(1),f''(-1)$

$(2)$

$f'(x)=\dfrac{\sqrt{1+x^2}-\dfrac{x^2}{\sqrt{1+x^2}}}{1+x^2}=(1+x^2)^{-\frac32}$

$f''(x)=-3x(1+x^2)^{-\frac52}$

$f''(0)=0,f''(1)=-\dfrac{3\sqrt2}{8},f''(-1)=\dfrac{3\sqrt2}{8}$

> 3. 求下列函数的高阶导数：
>
> $(2)f(x)=e^{-x^2}$，求 $f'''(x)$
>
> $(4)f(x)=x^3e^x$，求 $f^{(10)}(x)$。

$(2)$

$f'(x)=-2xe^{-x^2}$

$f''(x)=(4x^2-2)e^{-x^2}$

$f'''(x)=(-8x^3+12x)e^{-x^2}$

$(4)$

记 $g(x)=x^3,h(x)=e^x$。

$$
\begin{aligned}
f^{(10)}(x)&=\sum_{k=0}^{10}\binom{10}{k}g^{(k)}(x)h^{(10-k)}(x)\\
&=\sum_{k=0}^3\binom{10}{k}g^{(k)}(x)e^x\\
&=e^x(x^3+30x^2+270x+720)
\end{aligned}
$$

> 5. 求下列函数的 $n$ 阶导数：
>
> $(4)y=\dfrac{\ln x}{x}$

记 $c_n=\sum\limits_{k=1}^n\dfrac1k$

那么 $y^{(n)}=\dfrac{(-1)^nn!(\ln x-c_n)}{x^{n+1}}$

采用归纳法证明，当 $n=0,1$ 时成立。

假设 $n=k$ 成立，下证 $n=k+1$ 成立。

$y^{(k+1)}=(y^{(k)})'=\dfrac{(-1)^nn!(\frac1x\cdot x^{n+1}-(n+1)x^n(\ln x-c_n))}{x^{2n+2}}=\dfrac{(-1)^nn!(-(n+1)\ln x+(n+1)c_n+1)}{x^{n+2}}=\dfrac{(-1)^{n+1}(n+1)!(\ln x-c_n-\frac1{n+1})}{x^{n+2}}=\dfrac{(-1)^{n+1}(n+1)!(\ln x-c_{n+1})}{x^{n+2}}$。

证毕。

> 6. 求由下列参数方程所确定的函数的二阶导数 $\dfrac{\text{d}^2y}{\text{d}x^2}$
>
> $(1)\begin{cases}x=a\cos^3t\\y=a\sin^3t\end{cases}$

$$
\begin{aligned}
\dfrac{\text{d}^2y}{\text{d}x^2}&=\dfrac{\text{d}}{\text{d}x}(\dfrac{\text{d}y}{\text{d}x})\\
&=\dfrac{\text{d}}{\text{d}t}(\dfrac{\text{d}y}{\text{d}x})/\dfrac{\text{d}x}{\text{d}t}\\
\end{aligned}
$$

而我们知道 $\dfrac{\text{d}y}{\text{d}x}=\dfrac{\frac{\text{d}y}{\text{d}t}}{\frac{\text{d}x}{\text{d}t}}=-\dfrac{\sin t}{\cos t},\dfrac{\text{d}}{\text{d}t}(\dfrac{\text{d}y}{\text{d}x})=-\dfrac{1}{\cos^2t}$

所以 $\dfrac{\text{d}^2y}{\text{d}x^2}=\dfrac1{3a\sin t\cos^4 t}$。

## 习题 5.5

> 2. 求下列函数的微分：
>
> $(3)y=x^2\cos2x$

$y'=2x\cos2x-2x^2\sin2x$

所以 $\text{d}y=(2x\cos2x-2x^2\sin2x)\text{d}x$。