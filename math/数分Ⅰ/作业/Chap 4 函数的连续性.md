## 习题 4.1

> 2. 指出下列函数的间断点并说明其类型：
>
> $(2)f(x)=\dfrac{\sin x}{|x|}$
>
> $(3)f(x)=[|\cos x|]$

$(2)$

$\lim\limits_{x\to0^+}\dfrac{\sin x}{|x|}=\lim\limits_{x\to0^+}\dfrac{\sin x}{x}=1$

$\lim\limits_{x\to0^-}\dfrac{\sin x}{|x|}=\lim\limits_{x\to0^-}-\dfrac{\sin x}{x}=-1$。

左右极限存在且不相等，所以 $x=0$ 是跳跃间断点。

当 $x\neq 0$ 时，若 $x>0,f(x)=\dfrac{\sin x}{x}$；若 $x<0,f(x)=-\dfrac{\sin x}{x}$ 都是连续函数的四则运算，所以仍然是连续的，没有间断点。

$(3)$

先证明 $\forall x_0\in R,\lim\limits_{x\to x_0}f(x)=0$。

由于 $0\le |\cos x|\le 1$，所以 $[|\cos x|]=\{0,1\}$，并且当且仅当 $x=k\pi(k\in Z)$ 时 $f(x)=1$。

$\forall\epsilon>0$，若 $x\neq k\pi(k\in Z)$，取 $\delta=\min\{x_0-\lfloor\frac{x_0}{\pi}\rfloor\pi,(\lfloor\frac{x_0}{\pi}\rfloor+1)\pi-x_0\}$；若 $x=k\pi(k\in Z)$，取 $\delta=\pi$，可以证明 $\forall x\in U^\circ(x_0,\delta),f(x)=0$，所以 $|f(x)-0|=0<\epsilon$，证毕。

所以，对于所有的 $x_0=k\pi(k\in Z)$，$f(x_0)=1\neq\lim\limits_{x\to x_0}f(x)$。对于所有的 $x_0\neq k\pi(k\in Z),f(x_0)=0=\lim\limits_{x\to x_0}f(x)$。

所以，$x=k\pi(k\in Z)$ 为可去间断点。

> 3. 延拓下列函数，使其在 $R$ 上连续：
>
> $(3) f(x)=x\cos\dfrac1x$

当 $x\neq0$ 时，$f(x)$ 有定义，$f(x)$ 是连续函数的复合及四则运算，所以 $f(x)$ 连续。

当 $x=0$ 时，考虑 $x\to0$，$x$ 是此时的无穷小，$\cos\dfrac1x$ 有界，所以 $\lim\limits_{x\to0}x\cos\dfrac1x=0$。

而 $f(0)$ 没有定义，所以延拓为 $g(x)=\begin{cases}f(x)&,x\neq0\\0&,x=0\end{cases}$。

可以验证，$g(x)$ 是连续的。

> 6. 设 $f$ 为区间 $I$ 上的单调函数。证明：若 $x_0\in I$ 为 $f$ 的间断点，则 $x_0$ 必是 $f$ 的第一类间断点。

不妨假设 $f$ 单调增。

我们证明 $\forall x_0\in I,\lim\limits_{x\to x_0^-}f(x)$ 存在。（不考虑 $I$ 的左端点闭且 $x_0$ 是左端点的情况）

考察 $S=\{y=f(x)\mid x\in(U^\circ_-(x_0)\cap I)\}$，显然 $S\neq\varnothing$，且 $\forall y\in S,y\le f(x_0)$ 有上界，可以记 $A=\sup S$。

下面证明 $\lim\limits_{x\to x_0^-}f(x)=A$。

$\forall\epsilon>0$，由于 $A=\sup S$，所以 $\exist y_1\in S,y_1>A-\epsilon$，也就是说 $\exist x_1\in I,x_1<x_0,f(x_1)>A-\epsilon$。

由于单调性，$\forall x\in(x_1,x_0),f(x)>f(x_1)>A-\epsilon$，也就是说 $A-f(x)<\epsilon$。同时有 $f(x)\le A$，所以 $0\le A-f(x)<\epsilon$，也就是 $|A-f(x)|<\epsilon$。

也就是说 $\lim\limits_{x\to x_0^-}f(x)=A$。

同理 $\lim\limits_{x\to x_0^+}f(x)$ 也存在，也就是说如果存在间断点肯定不是第二类间断点，那就是第一类间断点。

> 7. 设函数 $f$ 只有可去间断点，定义 $g(x)=\lim\limits_{y\to x}f(y)$。证明：$g$ 为连续函数。

即证明 $\forall x_0,\lim\limits_{x\to x_0}\lim\limits_{y\to x}f(y)=\lim\limits_{y\to x_0}f(y)$。

反证法，不妨假设二者不相等，前者是 $A$，后者是 $B$。

取 $\epsilon_0=\dfrac{|A-B|}{3}$。

则 $\exist\delta>0,\forall y\in U^\circ(x_0,\delta),|f(y)-B|<\epsilon$。

则 $\exist\delta_0>0,\forall x\in U^\circ(x_0,\delta_0),|g(x)-A|<\epsilon$，并且 $\forall x,\exist\delta_1>0,\forall y\in U^\circ(x,\delta_1),|f(y)-g(x)|<\epsilon$。

那么，$\forall y\in U^\circ(x_0,\delta_0+\delta_1),|f(y)-A|=|(f(y)-g(x))+(g(x)-B)|\le|f(y)-g(x)|+|g(x)-A|<2\epsilon$。

取 $\delta'=\min\{\delta,\delta_0+\delta_1\}$，当 $y\in U^\circ(x_0,\delta')$ 时，$|A-B|=|(A-f(y))+(f(y)-B)|\le|A-f(y)|+|f(y)-B|<3\epsilon=|A-B|$，矛盾。

所以假设不成立，$\lim\limits_{x\to x_0}\lim\limits_{y\to x}f(y)=\lim\limits_{y\to x_0}f(y)$。 