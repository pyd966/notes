## 习题 3.1

> 1. 按定义证明下列极限：
>
> $(3)\lim\limits_{x\to\infty}\dfrac{x^2-5}{x^2-1}=1$

$\forall\epsilon>0$，取 $\delta=\max\{2,\dfrac4\epsilon\}$，则 $\delta\ge 2$，当 $|x|>\delta$ 时，$|x^2-1|\ge|x^2|-1\ge 2|x|-1\ge |x|$
$$
\begin{aligned}
|\dfrac{x^2-5}{x^2-1}-1|&=|\dfrac{-4}{x^2-1}|\\
&=\dfrac4{|x^2-1|}\\
&\le\dfrac4{|x|}\\
&<\dfrac4\delta\\
&<\epsilon
\end{aligned}
$$

由定义，$\lim\limits_{x\to\infty}\dfrac{x^2-5}{x^2-1}=1$。

> 3. 设 $\lim\limits_{x\to x_0}f(x)=A$，证明：$\lim\limits_{h\to0}f(x_0+h)=A$

由 $\lim\limits_{x\to x_0}f(x)=A$ 可知 $\forall\epsilon>0,\exist\delta>0$，当 $0<|x-x_0|<\delta$ 时，$|f(x)-A|<\epsilon$。

记 $h=x-x_0$，则 $x=x_0+h,f(x)=f(x_0+h)$。

由 $0<|x-x_0|<\delta$ 可知 $0<|h|<\delta$，此时 $|f(x_0+h)-A|=|f(x)-A|<\epsilon$。

由定义，$\lim\limits_{h\to0}f(x_0+h)=A$。

> 6. 讨论下列函数在 $x\to0$ 时的极限或左、右极限：
>
> $(1) f(x)=\dfrac{|x|}x$

$f(x)=\begin{cases}1&,x>0,\\-1&,x<0\end{cases}$。

考虑 $\lim\limits_{x\to0^-}f(x)$。

$\forall\epsilon>0$，取 $\delta=1>0$，当 $x<0-\delta=-\delta<0$ 时，有 $|f(x)-(-1)|=|(-1)-(-1)|=0<\epsilon$。

由定义，$\lim\limits_{x\to0^-}f(x)=-1$。

同理 $\lim\limits_{x\to0^+}f(x)=1$。

由于 $\lim\limits_{x\to0^-}f(x)\neq\lim\limits_{x\to0^+}f(x)$，所以 $x\to 0$ 时 $f(x)$ 极限不存在。

## 习题 3.2

> 1. 求下列极限：
>
> $(5)\lim\limits_{x\to1}\dfrac{x^n-1}{x^m-1}(n,m\in Z^+)$
>
> $(7)\lim\limits_{x\to0}\dfrac{\sqrt{a^2+x}-a}x(a>0)$

$(5)$

$x^n-1=(x-1)(x^{n-1}+\dots+x+1),x^m-1=(x-1)(x^{m-1}+\dots+x+1)$

所以 $\lim\limits_{x\to1}\dfrac{x^n-1}{x^m-1}=\dfrac{\lim\limits_{x\to1}(x^{n-1}+\dots+1)}{\lim\limits_{x\to1}(x^{m-1}+\dots+1)}=\dfrac nm$。

$(7)$

$$
\begin{aligned}
\lim\limits_{x\to0}\dfrac{\sqrt{a^2+x}-a}x&=\lim\limits_{x\to0}\dfrac{(\sqrt{a^2+x}-a)(\sqrt{a^2+x}+a)}{x(\sqrt{a^2+x}+a)}\\
&=\lim\limits_{x\to0}\dfrac{1}{\sqrt{a^2+x}+a}\\
&=\dfrac1{2a}
\end{aligned}
$$

> 5. 设 $f(x)>0,\lim\limits_{x\to x_0}f(x)=A$，证明：
>
> $$
> \lim_{x\to x_0}\sqrt[n]{f(x)}=\sqrt[n]{A}
> $$
>
> 其中 $n\ge 2$ 为正整数。

记 $g(x)=\sqrt[n]{x}(x>0)$，我们先证明引理：$\lim\limits_{x\to x_1}g(x)=\sqrt[n]{x_1}$。

$\forall\epsilon>0$，我们希望取 $\delta$，使得 $x\in U^\circ(x_1,\delta)$ 时，$|\sqrt[n]{x}-\sqrt[n]{x_1}|<\epsilon$，这需要 $\sqrt[n]{x_1}-\epsilon<\sqrt[n]{x}<\sqrt[n]{x_1}+\epsilon$。

记 $s=(\sqrt[n]{x_1}-\epsilon)^n-x_1,t=(\sqrt{x_1}+\epsilon)^n-x_1$。不难证明 $s,t\neq0$。

取 $\delta=\min\{|s|,|t|\}$ 即可证明。

而

$$
\begin{aligned}
\lim\limits_{x\to x_0}\sqrt[n]{f(x)}&=\lim\limits_{x\to x_0}g(f(x))\\
&=\lim\limits_{x\to A}g(x)\\
&=\sqrt[n]{A}
\end{aligned}
$$

> 8. 求下列极限（其中 $n\in Z^+$）
>
> $(3)\lim\limits_{x\to-1}(\dfrac 1{x+1}-\dfrac3{x^3+1})$
>
> $(4)\lim\limits_{x\to0}\dfrac{\sqrt[n]{1+x}-1}x$

$(3)$

$$
\begin{aligned}
\lim\limits_{x\to-1}(\dfrac1{x+1}-\dfrac3{x^3+1})&=\lim\limits_{x\to-1}\dfrac{x^2-x-2}{(x+1)(x^2-x+1)}\\
&=\lim\limits_{x\to-1}\dfrac{x-2}{x^2-x+1}\\
&=\dfrac{-3}{3}\\
&=-1
\end{aligned}
$$

$(4)$

记 $t=\sqrt[n]{1+x}$，则 $t^n=1+x$，那么 $x=t^n-1=(t-1)(t^{n-1}+\dots+t+1)$。

当 $x\to0$ 时，$t\to1,t\neq1$。

$$
\begin{aligned}
\lim\limits_{x\to0}\dfrac{\sqrt[n]{1+x}-1}x&=\lim\limits_{t\to1}\dfrac{t-1}{(t-1)(t^{n-1}+\dots+t+1)}\\
&=\lim\limits_{t\to1}\dfrac{1}{t^{n-1}+\dots+t+1}\\
&=\dfrac1n
\end{aligned}
$$

## 习题 3.3

> 1. 叙述函数极限 $\lim\limits_{x\to+\infty}f(x)$ 的归结原则，并应用它证明 $\lim\limits_{x\to+\infty}\cos x$ 不存在。

叙述：

函数 $f(x)$ 在 $U(+\infty)$ 上有定义。此时，$\lim\limits_{x\to+\infty}f(x)=A$ 的充要条件是，对任何满足 $x_n\to+\infty$ 的递增数列 $\{x_n\}\subset U(+\infty)$，有 $\lim\limits_{n\to\infty}f(x_n)=A$。

证明：

取序列 $x_n=2n\pi,y_n=2n\pi+\dfrac\pi2$，那么显然 $\lim\limits_{n\to\infty}f(x_n)=0\neq1=\lim\limits_{n\to\infty}f(y_n)$。

所以原极限不存在。

> 3. $(1)$ 叙述极限 $\lim\limits_{x\to-\infty}f(x)$ 的柯西准则。
>
> $(2)$ 根据柯西准则叙述 $\lim\limits_{x\to-\infty}f(x)$ 不存在的充要条件，并应用它证明 $\lim\limits_{x\to-\infty}\sin x$ 不存在。

$(1)$

$\forall\epsilon>0,\exist M>0,\forall x',x''<-M,|f(x')-f(x'')|<\epsilon$。

$(2)$

不存在的充要条件：

$\exist\epsilon_0>0,\forall M>0,\exist x',x''<-M,|f(x')-f(x'')|\ge\epsilon_0$。

证明：

取 $\epsilon_0=1$，对于任意的 $M>0$，取 $x'=-2\lceil M\rceil\pi-\dfrac{3\pi}2,x''=-2\lceil M\rceil\pi-\dfrac\pi2$，显然有 $x',x''<-M$，并且 $|f(x')-f(x'')|=2>\epsilon_0$。

> 5. 设 $f$ 为 $U^\circ(x_0)$ 上的递增函数。证明：$f(x_0-0)$ 和 $f(x_0+0)$ 都存在，且
>
> $$
> f(x_0-0)=\sup_{x\in U^\circ_-(x_0)}f(x),f(x_0+0)=\inf_{x\in U^\circ_+(x_0)}f(x)
> $$

由于 $f$ 是 $U^\circ(x_0)$ 的递增函数，所以在 $U^\circ_+(x_0),U^\circ_-(x_0)$ 上都是递增函数。

记 $A=\sup\limits_{x\in U^\circ_-(x_0)}f(x),S=U^\circ_-(x_0)$，则 $\forall x\in S,A\ge f(x)$

$\forall\epsilon>0,\exist x_1\in S,f(x_1)>A-\epsilon$，即 $A-f(x_1)<\epsilon$。

由于 $f(x)$ 增，取 $\delta=x_0-x_1$，当 $x\in U^\circ_-(x_0,\delta)$ 时，有 $|A-f(x)|=A-f(x)<A-f(x_1)<\epsilon$。

由定义，我们知道 $f(x_0-0)=A$，同理可证另外一部分。

## 习题 3.4

> 1. 求下列极限：
>
> $(5)\lim\limits_{x\to0}\dfrac{\tan x-\sin x}{x^3}$
>
> $(7)\lim\limits_{x\to+\infty}x\sin\dfrac1x$

$(5)$

$$
\begin{aligned}
\lim\limits_{x\to0}\dfrac{\tan x-\sin x}{x^3}&=\lim\limits_{x\to0}\dfrac{\sin x}x\cdot\dfrac{1-\cos x}{x^2\cos x}\\
&=\lim\limits_{x\to0}\dfrac{\sin x}x\cdot\dfrac{2\sin^2\frac x2}{4\cdot(\frac x2)^2}\cdot\dfrac1{\cos x}\\
&=1\times\dfrac24\times\dfrac11\\
&=\dfrac12
\end{aligned}
$$

$(7)$

记 $t=\dfrac1x$，当 $x\to+\infty$ 时，$t\to0,t\neq0$。

$$
\begin{aligned}
\lim\limits_{x\to+\infty}x\sin\dfrac1x&=\lim\limits_{x\to+\infty}\dfrac{\sin\frac1x}{\frac1x}\\
&=\lim\limits_{t\to0}\dfrac{\sin t}t\\
&=1
\end{aligned}
$$