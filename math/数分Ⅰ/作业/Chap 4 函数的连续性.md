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


## 习题 4.2

> 3. 设 $f,g$ 在区间 $I$ 上连续，记 $F(x)=\max\{f(x),g(x)\},G(x)=\min\{f(x),g(x)\}$。证明：$F,G$ 也在 $I$ 上连续。

$F(x)=\max\{f(x),g(x)\}=\frac12(f(x)+g(x)+|f(x)-g(x)|)$。

由于 $h(x)=|x|,f(x),g(x)$ 都是 $I$ 上连续函数，所以 $F(x)$ 也是 $I$ 上连续函数。

同理，$G(x)=\frac12(f(x)+g(x)-|f(x)-g(x)|)$ 也是 $I$ 上连续函数。

> 4. 设 $f$ 为 $R$ 上连续函数，常数 $c>0$。记
>
> $$
> F(x)=\begin{cases}
> -c&,f(x)<-c\\
> f(x)&,|f(x)|\le c\\
> c&,f(x)>c\\
> \end{cases}
> $$
> 证明：$F$ 在 $R$ 上连续。

事实上，$F(x)=\min\{\max\{f(x),-c\},c\}$。

综合第 $3$ 题结论，我们知道 $F(x)$ 在 $R$ 上连续。

> 6. 设 $f$ 在 $[a,+\infty)$ 上连续，且 $\lim\limits_{x\to+\infty}f(x)$ 存在。证明：$f$ 在 $[a,+\infty)$ 上有界。又问 $f$ 在 $[a,+\infty)$ 上必有最大值或最小值吗？

先证明。

设 $\lim\limits_{x\to+\infty}f(x)=A$，取 $\epsilon_0=1$，则 $\exist M_0,\forall x>M_0,|f(x)-A|<\epsilon_0=1$，也就是说 $f(x)\in(A-1,A+1)$。

而 $f(x)$ 在 $[a,M_0]$ 闭区间上有上下界 $[m,M]$。

取 $m'=\min\{m,A-1\},M'=\max\{M,A+1\}$，那么有 $\forall x\in[a,+\infty),f(x)\in[m',M']$，证毕。

关于最大值最小值：答案是最大值最小值至少存在一个。

$f(x)$ 有界，所以可以记 $m=\inf\limits_{x\ge a}f(x),M=\sup\limits_{x\ge a}f(x)$。

若 $m=M$，那么 $f(x)\equiv m$，最大值最小值都能取到，下面认为 $m\neq M$。

我们证明一个小引理：若 $A\neq m$，那么最小值是 $m$；若 $A\neq M$ 那么最大值是 $M$。

先证前半部分。

取 $\epsilon_0=A-m$，$\exist M_0,\forall x>M_0,|f(x)-A|<\epsilon_0$，也就是说 $f(x)\in(m,2A-m)$，所以 $\inf\limits_{a\le x\le M_0}f(x)=\inf\limits_{x\ge a}f(x)=m$。

所以 $f(x)$ 在 $[a,M_0]$ 上的最小值是 $m$，而在 $(M_0,+\infty)$ 上 $f(x)>m$，所以 $f(x)$ 有最小值 $m$。

后半部分同理。由于 $m\neq M$，所以不可能 $A=m$ 和 $A=M$ 同时成立，所以最大值最小值至少有一个存在。

下面给出一个只存在一个的例子：$f(x)=\dfrac1x,x\in[1,+\infty)$，容易发现 $\lim\limits_{x\to+\infty}f(x)=0$，但是 $f(x)$ 的值域是 $(0,1]$，有最大值，无最小值。

> 9. 证明：若 $f$ 在 $[a,b]$ 上连续，且对任何 $x\in[a,b],f(x)\neq0$，则 $f$ 在 $[a,b]$ 上恒正或恒负。

反证。

假设结论不成立，即 $\exist x_1,x_2\in[a,b],f(x_1)>0,f(x_2)<0$。

容易发现 $x_1\neq x_2$，不妨假设 $x_1<x_2$。

由根的存在性定理，$\exist x_0\in(x_1,x_2),f(x_0)=0$，与题设矛盾。

所以假设不成立，原命题成立。

> 10. 证明：任一实系数奇次方程至少有一个实根。

设 $f(x)=a_{2n-1}x^{2n-1}+a_{2n-2}x^{2n-2}+\dots+a_1x+a_0(a_{2n-1}\neq0)$，方程为 $f(x)=0$，不妨令 $a_{2n-1}>0$（否则可以把方程变成 $-f(x)=0$）。

$\lim\limits_{x\to+\infty}f(x)=\lim\limits_{x\to+\infty}x^{2n-1}(a_{2n-1}+a_{2n-2}x^{-1}+\dots+a_1x^{2-2n}+a_0x^{1-2n})=+\infty$。

所以 $\exist x_1,\forall x>x_1,f(x)>0$。

同理，$\exist x_2,\forall x<x_2,f(x)<0$。

考虑 $f(x_1+1)>0,f(x_2-1)<0$，所以由根的存在性定理，$\exist x_0\in(x_2-1,x_1+1),f(x_0)=0$，证毕。

> 12. 证明：$f(x)=\sqrt{x}$ 在 $[0,+\infty)$ 上一致连续。

先证明，$f(x)$ 在 $[1,+\infty)$ 上一致连续。

$\forall\epsilon>0$，取 $\delta=2\epsilon$，$\forall x',x''\in[1,+\infty)$ 满足 $|x'-x''|<\delta=2\epsilon$，有 $|f(x')-f(x'')|=|\sqrt{x'}-\sqrt{x''}|=\dfrac{|x'-x''|}{\sqrt{x'}+\sqrt{x''}}\le\dfrac{|x'-x''|}2<\epsilon$。

接下来，由于 $f(x)$ 为 $[0,1]$ 上连续函数，所以 $f(x)$ 在 $[0,1]$ 上一致连续。

综上，$f(x)$ 在 $[0,+\infty)$ 上一致连续。

> 16. 设函数 $f$ 满足第 $6$ 题的条件。证明：$f$ 在 $[a,+\infty)$ 上一致连续。

由于 $\lim\limits_{x\to+\infty}f(x)=A$，所以 $\forall\epsilon>0,\exist M_0,\forall x>M_0,|f(x)-A|<\dfrac\epsilon2$。

考虑 $f$ 在 $[a,M_0+1]$ 上连续，所以连续一致，对这个 $\epsilon,\exist\delta,\forall x',x''\in[a,M+1],|x'-x''|<\delta$，有 $|f(x')-f(x'')|<\epsilon$。

为了证明 $f$ 在 $[a,+\infty)$ 上连续一致，我们取 $\delta'=\min\{1,\delta\}$。

$\forall x',x''\in[a,+\infty)$ 且 $|x'-x''|<\delta'$ 容易发现 $x',x''\in[a,M_0+1]$ 和 $x',x''\in(M_0,+\infty)$ 至少有一个成立。

若 $x',x''\in[a,M_0+1]$，那么 $|x'-x''|<\delta'\le\delta$，所以 $|f(x')-f(x'')|<\epsilon$。

若 $x',x''\in(M_0,+\infty)$，那么 $|f(x')-f(x'')|=|(f(x')-A)+(A-f(x''))|\le|f(x')-A|+|A-f(x'')|<\epsilon$。

综上，$\forall x',x''\in[a,+\infty)$ 且 $|x'-x''|<\delta'$ 总有 $|f(x')-f(x'')|<\epsilon$，所以 $f$ 在 $[a,+\infty)$ 上一致连续。