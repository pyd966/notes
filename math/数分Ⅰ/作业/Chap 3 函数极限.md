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

> 2. 求下列极限：
>
> $(1)\lim\limits_{x\to\infty}(1-\dfrac2x)^{-x}$
>
> $(3)\lim\limits_{x\to0}(1+\tan x)^{\cot x}$

$(1)$

记 $t=-\dfrac x2$，则 $x\to\infty$ 时 $t\to\infty,t\neq0$。

$$
\begin{aligned}
\lim_{x\to\infty}(1-\dfrac2x)^{-x}&=\lim_{t\to\infty}(1+\dfrac1t)^{2t}\\
&=\lim_{t\to\infty}((1+\dfrac1t)^t)^2\\
&=(\lim_{t\to\infty}(1+\dfrac1t)^t)^2\\
&=e^2
\end{aligned}
$$

$(3)$

记 $t=\cot x$，则 $x\to0$ 时 $t\to\infty$。

$$
\begin{aligned}
\lim_{x\to0}(1+\tan x)^{\cot x}&=\lim_{t\to\infty}(1+\dfrac1t)^t\\
&=e
\end{aligned}
$$

> 4. 利用归结原则计算下列极限：
>
> $(2)\lim\limits_{n\to\infty}(1+\dfrac1n+\dfrac1{n^2})^n$

一方面，$(1+\dfrac1n+\dfrac1{n^2})^n\ge(1+\dfrac1n)^n$，$\lim\limits_{n\to\infty}(1+\dfrac1n)^n=e$。

另一方面，$(1+\dfrac1n+\dfrac1{n^2})^n=(1+\dfrac{n+1}{n^2})^{\frac{n^2}{n+1}+\frac{n}{n+1}}=(1+\dfrac{n+1}{n^2})^{\frac{n^2}{n+1}}\cdot(1+\dfrac{n+1}{n^2})^{\frac{n}{n+1}}\le(1+\dfrac{n+1}{n^2})^{\frac{n^2}{n+1}}\cdot(1+\dfrac{n+1}{n^2})$。

取 $x_n=\dfrac{n^2}{n+1}$，容易发现 $\lim\limits_{n\to\infty}x_n=\infty$，由 $\lim\limits_{x\to\infty}(1+\dfrac1x)^x=e$ 及归结原则可知，$\lim\limits_{n\to\infty}(1+\dfrac{n+1}{n^2})^{\frac{n^2}{n+1}}=e$。

又有 $\lim\limits_{n\to\infty}(1+\dfrac{n+1}{n^2})^{\frac{n^2}{n+1}}\cdot(1+\dfrac{n+1}{n^2})=e\cdot 1=e$。

由迫敛性，$\lim\limits_{n\to\infty}(1+\dfrac1n+\dfrac1{n^2})^n=e$。

## 习题 3.5

> 1. 证明下列各式：
>
> $(2)x\sin\sqrt{x}=O(x^{\frac32})(x\to0^+)$
>
> $(4)(1+x)^n=1+nx+o(x)(x\to0)(n\in N^+)$

$(2)$

即证 $\exist L>0,\forall x\in U^\circ_+(0),|\dfrac{x\sin\sqrt{x}}{x^{\frac32}}|\le L$。

取 $L=1$，当 $x>0$ 时，有 $|\sin\sqrt{x}|\le|\sqrt{x}|$。

所以 $|x\sin\sqrt{x}|\le |x^{\frac32}|$，也就是 $|\dfrac{x\sin\sqrt{x}}{x^{\frac32}}|\le 1$，证毕。

> 2. 应用定理 3.13 求下列极限：
>
> $(1)\lim\limits_{x\to\infty}\dfrac{x\arctan\dfrac1x}{x-\cos x}$
>
> $(2)\lim\limits_{x\to0}\dfrac{\sqrt{1+x^2}-1}{1-\cos x}$

$(1)$

记 $t=\dfrac1x$，则 $x\to\infty$ 时 $t\to0$，此时 $t\sim\arctan t$。

$$
\begin{aligned}
\lim_{x\to\infty}\dfrac{x\arctan\dfrac1x}{x-\cos x}&=\lim_{t\to0}\dfrac{\dfrac1t\arctan t}{\dfrac1t-\cos\dfrac1t}\\
&=\lim_{t\to0}\dfrac{\arctan t}{1-t\cos\dfrac1t}\\
&=\lim_{t\to0}\dfrac{t}{1-t\cos\dfrac1t}
\end{aligned}
$$

$t\to 0$ 时，$t$ 是无穷小，$|\cos\dfrac1t|\le 1$ 有界，所以 $\lim\limits_{t\to0}t\cos\dfrac1t=0$。

$$
\begin{aligned}
\lim_{t\to0}\dfrac{t}{1-t\cos\dfrac1t}&=\dfrac{\lim\limits_{t\to0}t}{\lim\limits_{t\to0}(1-t\cos\dfrac1t)}\\
&=\dfrac01\\
&=0
\end{aligned}
$$

$(2)$

当 $x\to0$ 时，$\sin x\sim x,1-\cos x\sim \dfrac{x^2}2$

$$
\begin{aligned}
\lim\limits_{x\to0}\dfrac{\sqrt{1+x^2}-1}{1-\cos x}&=\lim\limits_{x\to0}\dfrac{(\sqrt{1+x^2}-1)(\sqrt{1+x^2}+1)}{(1-\cos x)(\sqrt{1+x^2}+1)}\\
&=\lim\limits_{x\to0}\dfrac{x^2}{\dfrac{x^2}2(\sqrt{1+x^2}+1)}\\
&=\lim\limits_{x\to0}\dfrac{2}{\sqrt{1+x^2}+1}\\
&=\dfrac22\\
&=1
\end{aligned}
$$

> 3. 证明定理 3.14。
>
> $(i)$ 设 $f$ 在 $U^\circ(x_0)$ 上有定义且不等于 $0$。若 $f$ 为 $x\to x_0$ 时的无穷小量，则 $\dfrac 1f$ 为 $x\to x_0$ 时的无穷大量。
>
> $(ii)$ 若 $g$ 为 $x\to x_0$ 时的无穷大量，则 $\dfrac 1g$ 为 $x\to x_0$ 时的无穷小量。

$(i)$

由定义知 $\forall\epsilon>0,\exist\delta>0,\forall x\in U^\circ(x_0,\delta),0<|f(x)|<\epsilon$，也就是说 $|\dfrac1{f(x)}|>\dfrac1\epsilon$。

$\forall M>0$，取 $\epsilon=\dfrac1M$，可得 $|\dfrac1{f(x)}|>M$，也就是说 $\dfrac1f$ 是 $x\to x_0$ 时的无穷大。

$(ii)$

由定义知 $\forall M>0,\exist\delta>0,\forall x\in U^\circ(x_0,\delta),|g(x)|>M$，也就是说 $|\dfrac1{g(x)}|<\dfrac1M$。

$\forall\epsilon>0$，取 $M=\dfrac1\epsilon$，可得 $|\dfrac1{g(x)}|<\epsilon$ 也就是说 $\dfrac1g$ 时 $x\to x_0$ 时的无穷小。

> 5. 试确定 $\alpha$ 的值，使下列函数与 $x^\alpha$ 当 $x\to0$ 时为同阶无穷小量：
>
> $(4)\sqrt[5]{3x^2-4x^3}$。

即 $0<K\le|\dfrac{\sqrt[5]{3x^2-4x^3}}{x^\alpha}|\le L$。

也就是 $0<K^5\le|x^{2-5\alpha}||3-4x|\le L^5$

分讨一下。

如果 $\alpha<\dfrac25$，那么 $\lim\limits_{x\to0}|x^{2-5\alpha}||3-4x|=0$，取 $\epsilon_0=K^5$，$\exist x_0\in U^\circ(0),|x_0^{2-5\alpha}||3-4x_0|<K^5$，矛盾，故舍去。

如果 $\alpha>\dfrac25$，那么 $\lim\limits_{x\to0}|x^{2-5\alpha}||3-4x|=+\infty$，取 $M=L^5,\exist x_0\in U^\circ(0),|x_0^{2-5\alpha}||3-4x_0|>K^5$，矛盾，故舍去。

如果 $\alpha=\dfrac25$，那么 $\lim\limits_{x\to0}\dfrac{\sqrt[5]{3x^2-4x^3}}{x^{\frac25}}=\lim\limits_{x\to0}\sqrt[5]{3-4x}=\sqrt[5]{3}\neq0$，此时二者是同阶无穷小。

综上，$\alpha=\dfrac25$。

