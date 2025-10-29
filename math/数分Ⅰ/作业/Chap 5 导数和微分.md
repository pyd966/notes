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

$(2)$

$f'(x)=-2xe^{-x^2}$

$f''(x)=(4x^2-2)e^{-x^2}$

$f'''(x)=(-8x^3+12x)e^{-x^2}$

