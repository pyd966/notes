## 习题 6.1

> 1. 试讨论下列函数在指定区间上是否存在一点 $\xi$，使 $f'(\xi)=0$。
>
> $(1)f(x)=\begin{cases}x\sin\dfrac1x&,0<x\le\dfrac1\pi\\0&,x=0\\\end{cases}$

$\lim\limits_{x\to0}f(x)=\lim\limits_{x\to0}x\sin\dfrac1x=0=f(0)=f(\lim\limits_{x\to0}x)$，所以 $f$ 在 $x=0$ 处连续，所以 $f$ 在 $[0,\dfrac1\pi]$ 上连续。

并且显然 $f$ 在 $(0,\dfrac1\pi)$ 上可导，且 $f(0)=f(\dfrac1\pi)=0$。

由罗尔中值定理，$\exist\xi\in(0,\dfrac1\pi),f'(\xi)=0$。

> 2. 证明：
>
> $(2)$ 方程 $x^n+px+q=0(n\in N^+,p,q\in R)$ 当 $n$ 为偶数时至多有两个实根，当 $n$ 为奇数时至多有三个实根。

$(2)$

记 $f(x)=x^n+px+q$，则 $f'(x)=nx^{n-1}+p$。

则 $f'(x)$ 在 $n$ 为偶数时恰好有一个实根，在 $n$ 为奇数时至多有两个实根。

反证法。

当 $n$ 为偶数时，假设有三个不同实根 $x_1<x_2<x_3$。

则 $f(x_1)=f(x_2)=f(x_3)=0$，分别在 $(x_1,x_2),(x_2,x_3)$ 上对 $f$ 使用罗尔中值定理

$\exist\xi_1\in(x_1,x_2),\xi_2\in(x_2,x_3),f'(\xi_1)=f'(\xi_2)=0$，与 $f'(x)=0$ 最多有一个实根矛盾。

当 $n$ 为奇数得时候，假设有四个实根 $x_1<x_2<x_3<x_4$。

同理可得 $\exist\xi_1\in(x_1,x_2),\xi_2\in(x_2,x_3),\xi_3\in(x_3,x_4),f'(\xi_1)=f'(\xi_2)=f'(\xi_3)=0$，与 $f'(x)=0$ 最多有两个实根矛盾。

综上，矛盾，原命题成立。

> 4. 证明：
>
> $(2)$ 若函数 $f$ 在 $[a,b]$ 上可导，且 $|f'(x)|\le M$，则
>
> $$
> |f(b)-f(a)|\le M(b-a)
> $$

$(2)$

在 $[a,b]$ 上对 $f$ 使用拉格朗日中值定理，

$\exist\xi\in(a,b),\dfrac{|f(b)-f(a)|}{b-a}=f'(\xi)\le M$

所以 $|f(b)-f(a)|\le M(b-a)$。

> 5. 应用拉格朗日中值定理证明下列不等式：
>
> $(2)\dfrac h{1+h^2}<\arctan h<h$，其中 $h>0$。

$(2)$

记 $f(x)=\arctan x$，则 $f'(x)=\dfrac1{1+x^2}$。

对 $f$ 在 $[0,h]$ 上使用拉格朗日中值定理，

$\exist\xi\in(0,h),\dfrac{|f(h)-f(0)|}{|h-0|}=\dfrac{\arctan h}{h}=f'(\xi)=\dfrac1{1+\xi^2}\in(\dfrac1{1+h^2},1)$。

所以 $\dfrac h{1+h^2}<\arctan h<h$。

> 6. 确定下列函数的单调区间：
>
> $(3)f(x)=\sqrt{2x-x^2}$

$f$ 的定义域为 $[0,2]$。

$f'(x)=(2x-x^2)^{-\frac12}(1-x)$，定义域为 $(0,2)$。

不难发现，当 $x\in(0,1)$ 时 $f'(x)>0$，当 $x=1$ 时 $f'(x)=0$，当 $x\in(1,2)$ 时 $f'(x)<0$。

所以函数在 $(0,1)$ 严格单调增，在 $(1,2)$ 严格单调增。

又函数在 $x=1$ 处连续，在 $x=0$ 处右连续，在 $x=2$ 处左连续。

进而在 $[0,1]$ 严格单调增，在 $[1,2]$ 严格单调减。

> 7. 应用函数的单调性证明下列不等式：
>
> $(1)\tan x>x-\dfrac{x^3}3,x\in(0,\dfrac\pi2)$
>
> $(2)\dfrac{2x}\pi<\sin x<x,x\in(0,\dfrac\pi2)$

$(1)$

令 $f(x)=\tan x-x+\dfrac{x^3}3$。

$f'(x)=\dfrac1{\cos^2x}-1+x^2,f''(x)=\dfrac{2\sin x}{\cos^3x}+2x$

当 $x\in(0,\dfrac\pi2)$ 时 $f''(x)>0$，所以 $f'$ 在 $(0,\dfrac\pi2)$ 上严格单调增，又 $f'$ 在 $x=0$ 连续，所以 $f'$ 在 $[0,\dfrac\pi2)$ 上严格单调增。

$\forall x\in(0,\dfrac\pi2),f'(x)>f'(0)=0$。

所以 $f$ 在 $(0,\dfrac\pi2)$ 严格单调增，又 $f$ 在 $x=0$ 连续，所以在 $[0,\dfrac\pi2)$ 严格单调增。

所以当 $x\in(0,\dfrac\pi2)$ 时，$f(x)>f(0)=0$，即 $\tan x>x-\dfrac{x^3}3$。

$(2)$

先证右边，记 $f(x)=x-\sin x$，则 $f'(x)=1-\cos x$，当 $x\in(0,\dfrac\pi2)$ 时 $f'(x)>0,f(x)$ 严格增，又 $f$ 在 $x=0$ 连续，故 $f$ 在 $[0,\dfrac\pi2)$ 严格增。

当 $x\in(0,\dfrac\pi2)$ 时，$f(x)>f(0)=0$，即 $x>\sin x$。

再证左边，记 $g(x)=\sin x-\dfrac{2x}\pi$，则 $g'(x)=\cos x-\dfrac2\pi,g''(x)=-\sin x$。

当 $x\in(0,\dfrac\pi2)$ 时，$g''(x)<0$，$g'(x)$ 严格减，又 $g'(x)$ 在 $x=0$ 连续，所以在 $x\in[0,\dfrac\pi2)$ 严格减。

又 $g'(0)=1-\dfrac2\pi>0,g'(\dfrac\pi2)=-\dfrac2\pi<0$，所以存在唯一的 $x_0\in(0,\dfrac\pi2)$，$g'(x_0)=0$。

当 $x\in(0,x_0),g'(x)>g'(x_0)=0$，故 $g(x)$ 增，又 $x=0,x=x_0$ 连续故 $[0,x_0]$ 增，$g(x)>g(0)=0$。

当 $x\in(x_0,\dfrac\pi2),g'(x)<g'(x_0)=0$，故 $g(x)$ 减，又 $x=\dfrac\pi2$ 连续，故 $(x_0,\dfrac\pi2]$ 减，$g(x)>g(\dfrac\pi2)=0$。

综上当 $x\in(0,\dfrac\pi2)$ 时，$g(x)>0$，即 $\sin x>\dfrac{2x}\pi$。

> 13. 设 $a>0$，证明函数 $f(x)=x^3+ax+b$ 存在唯一的零点。

先证零点存在。

$\lim\limits_{x\to+\infty}f(x)=+\infty,\lim\limits_{x\to-\infty}f(x)=-\infty$，所以 $\exist x_1,x_2,f(x_1)<0,f(x_2)>0$。

由连续函数介值定理，$\exist x_0,f(x_0)=0$。

再证零点唯一。

反证，假设至少有两个零点 $\epsilon_1<\epsilon_2$。

对 $f$ 在 $[\epsilon_1,\epsilon_2]$ 使用罗尔中值定理，$\exist\epsilon_0\in(\epsilon_1,\epsilon_2),f'(\epsilon_0)=0$。

然而 $f'(x)=3x^2+a\ge a>0$，所以矛盾。

假设不成立，零点存在且唯一。

> 14. 证明：$\dfrac{\tan x}x>\dfrac x{\sin x},x\in(0,\dfrac\pi2)$

记 $f(x)=\dfrac{\tan x\sin x}{x^2}$，则 $f'(x)=\dfrac{\sin x(\dfrac x{\cos^2x}+x-2\tan x)}{x^3}$。

记 $g(x)=\dfrac x{\cos^2x}+x-2\tan x$

$g'(x)=\dfrac{2x\sin x+\cos^3x-\cos x}{\cos^3 x}$

记 $h(x)=2x\sin x+\cos^3x-\cos x$，则 $h'(x)=2x\cos x+3\sin x(1-\cos^2x)=2x\cos x+3\sin^3x$。

当 $x\in(0,\dfrac\pi2)$ 时，$h'(x)>0$，所以 $h(x)>h(0)=0$。

所以 $g'(x)>0,g(x)>g(0)=0$。

所以 $f'(x)>0,f(x)>f(0+0)=1$。

即 $\dfrac{\tan x}x>\dfrac x{\sin x}$。

## 习题 6.2

> 1. 试问函数 $f(x)=x^2,g(x)=x^3$ 在区间 $[-1,1]$ 上能否应用柯西中值定理得到相应的结论？为什么？

不能，因为当 $f'(x)=2x,g'(x)=3x^2$，当 $x=0$ 时 $f'(x)=g'(x)=0$。

> 2. 设函数 $f$ 在 $[a,b]$ 上连续，在 $(a,b)$ 上可导，证明：存在 $\xi\in(a,b)$，使得
>
> $$
> 2\xi(f(b)-f(a))=(b^2-a^2)f'(\xi)
> $$

取 $g(x)=x^2$。

对 $f,g$ 在 $[a,b]$ 上使用柯西中值定理，得

$$
\exist\xi\in[a,b],\dfrac{f(b)-f(a)}{b^2-a^2}=\dfrac{f(b)-f(a)}{g(b)-g(a)}=\dfrac{f'(\xi)}{g'(\xi)}=\dfrac{f'(\xi)}{2\xi}
$$

即 $2\xi(f(b)-f(a))=(b^2-a^2)f'(\xi)$。

> 3. 设函数 $f$ 在点 $a$ 处具有连续的二阶导数。证明：
>
> $$
> \lim_{h\to0}\dfrac{f(a+h)+f(a-h)-2f(a)}{h^2}=f''(a)
> $$

左式是 $\frac00$ 型

$$
\begin{aligned}
\lim_{h\to0}\dfrac{f(a+h)+f(a-h)-2f(a)}{h^2}&=\lim_{h\to0}\dfrac{f'(a+h)-f'(a-h)}{2h}\\
&=\dfrac12\lim_{h\to0}\dfrac{f'(a+h)-f'(h)}{h}+\dfrac12\lim_{h\to0}\dfrac{f'(h)-f'(a-h)}h\\
&=f''(a)
\end{aligned}
$$

> 5. 求下列不定式极限：
>
> $(6)\lim\limits_{x\to0}(\dfrac1x-\dfrac1{e^x-1})$
>
> $(8)\lim\limits_{x\to1}x^{\frac1{1-x}}$

$(6)$

这是一个 $\infty-\infty$ 型极限，通分后化为 $\frac{0}{0}$ 型。

$$
\begin{aligned}
\lim_{x\to0}(\dfrac1x-\dfrac1{e^x-1})&=\lim_{x\to0}\dfrac{e^x-x-1}{x(e^x-1)}\\
&=\lim_{x\to0}\dfrac{e^x-1}{(x+1)e^x-1}\\
&=\lim_{x\to0}\dfrac{e^x}{(x+2)e^x}\\
&=\lim_{x\to0}\dfrac{1}{x+2}\\
&=\dfrac12
\end{aligned}
$$

$(8)$

$\lim\limits_{x\to1}x^{\frac1{1-x}}=\lim\limits_{x\to1}e^{\frac1{1-x}\ln x}$

而指数是 $\frac00$ 型不定式。

$$
\begin{aligned}
\lim_{x\to1}\dfrac{\ln x}{1-x}&=\lim_{x\to1}-\dfrac{1}{x}\\
&=-1
\end{aligned}
$$

所以 $\lim\limits_{x\to1}x^{\frac1{1-x}}=e^{-1}=\dfrac1e$。

> 6. 设函数 $f$ 在 $a$ 的某个邻域上具有二阶导数。证明：对充分小的 $h$，存在 $\theta,0<\theta<1$，使得
>
> $$
> \dfrac{f(a+h)+f(a-h)-2f(a)}{h^2}=\dfrac{f''(a+\theta h)+f''(a-\theta h)}{2}
> $$

先证明 $\exist h'\in(0,h),s.t. \dfrac{f(a+h)+f(a-h)-2f(a)}{h^2}=\dfrac{f'(a+h')-f'(a-h')}{2h'}$。

构造函数 $F(h)=f(a+h)+f(a-h)-2f(a),G(h)=h^2$。

则 $\exist h'\in(0,h),s.t. \dfrac{f(a+h)+f(a-h)-2f(a)}{h^2}=\dfrac{F(h)-F(0)}{G(h)-G(0)}=\dfrac{F'(h')}{G'(h')}=\dfrac{f'(a+h')-f'(a-h')}{2h'}$。

再构造函数 $\phi(h)=f'(a+h')-f'(a-h'),\psi(h)=2h$。

则 $\exist h''\in(0,h'),s.t. \dfrac{f'(a+h')-f'(a-h')}{2h'}=\dfrac{\phi(h')-\phi(0)}{\psi(h')-\psi(0)}=\dfrac{\phi'(h'')}{\psi'(h'')}=\dfrac{f''(a+h'')+f''(a-h'')}{2}$

由于 $h''\in(0,h')\subseteq(0,h)$，所以 $\exist0<\theta<1,h''=\theta h$，即

$$
\dfrac{f(a+h)+f(a-h)-2f(a)}{h^2}=\dfrac{f''(a+\theta h)+f''(a-\theta h)}{2}
$$

> 7. 求下列不定式极限：
>
> $(7)\lim\limits_{x\to0}\dfrac{(1+x)^{\frac1x}-e}{x}$
>
> $(8)\lim\limits_{x\to+\infty}(\dfrac\pi2-\arctan x)^{\frac1{\ln x}}$

$(7)$

这是 $\frac00$ 型不定式。

$$
\lim_{x\to0}\dfrac{(1+x)^{\frac1x}-e}{x}=\lim_{x\to0}\dfrac{e^{\frac1x\cdot\ln(1+x)}\cdot\dfrac{\frac x{1+x}-\ln(1+x)}{x^2}}{1}
$$

注意到 $\dfrac{\frac{x}{1+x}-\ln(1+x)}{x^2}$ 仍然是 $\frac00$ 型不定式。

$$
\lim\limits_{x\to0}\dfrac{\frac{x}{1+x}-\ln(1+x)}{x^2}=\lim_{x\to0}\dfrac{\frac{1}{(1+x)^2}-\frac1{1+x}}{2x}=\lim_{x\to0}-\dfrac{1}{2(1+x)^2}=-\dfrac12
$$

所以 $\lim\limits_{x\to0}\dfrac{(1+x)^{\frac1x}-e}{x}=\lim\limits_{x\to0}e^{\frac1x\cdot\ln(1+x)}\cdot\lim\limits_{x\to0}\dfrac{\frac{x}{1+x}-\ln(1+x)}{x^2}=-\dfrac e2$。

$(8)$

当 $x>0$ 时，$\dfrac\pi2-\arctan x>0$。

$$
\lim\limits_{x\to+\infty}(\dfrac\pi2-\arctan x)^{\frac1{\ln x}}=\lim_{x\to+\infty}e^{(\dfrac{\ln(\frac\pi2-\arctan x)}{\ln x})}
$$

而指数为 $\frac\infty\infty$ 型

$$
\lim_{x\to+\infty}\dfrac{\ln(\frac\pi2-\arctan x)}{\ln x}=\lim_{x\to+\infty}\dfrac{\frac{1}{\frac\pi2-\arctan x}\cdot(-\frac{1}{1+x^2})}{\frac1x}=\lim_{x\to+\infty}-\dfrac{x}{(1+x^2)(\frac\pi2-\arctan x)}
$$

考察 $\lim\limits_{x\to+\infty}(1+x^2)(\dfrac\pi2-\arctan x)=\lim\limits_{x\to+\infty}\dfrac{\frac\pi2-\arctan x}{\frac1{1+x^2}}=\lim\limits_{x\to+\infty}\dfrac{1+x^2}{2x}=+\infty$。

所以这是 $\frac\infty\infty$ 型

$$
\lim_{x\to+\infty}-\dfrac{x}{(1+x^2)(\frac\pi2-\arctan x)}=\lim_{x\to+\infty}-\dfrac{1}{2x(\frac\pi2-\arctan x)-1}
$$

考察 $\lim\limits_{x\to+\infty}2x(\dfrac\pi2-\arctan x)=\lim\limits_{x\to+\infty}\dfrac{\frac\pi2-\arctan x}{\frac1{2x}}=\lim\limits_{x\to+\infty}\dfrac{2x^2}{1+x^2}=2$

所以 $\lim\limits_{x\to+\infty}-\dfrac{x}{(1+x^2)(\frac\pi2-\arctan x)}=-1$

所以 $\lim\limits_{x\to+\infty}(\dfrac\pi2-\arctan x)^{\frac1{\ln x}}=\dfrac1e$。