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