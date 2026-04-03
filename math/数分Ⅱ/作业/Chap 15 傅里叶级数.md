## 习题 15.1

> 1. 在指定区间上求下列函数的傅里叶级数：
>
> $(1)$ $f(x)=x$ $(i)-\pi<x<\pi$ $(ii)0<x<2\pi$

$(1)$

$(i)$

$$
\begin{aligned}
\pi a_n&=\int_{-\pi}^\pi x\cos nxdx\\
&=\int_{-\pi}^\pi x\dfrac{d(\sin nx)}{n}\\
&=\left.\dfrac{x\sin nx}{n}\right|_{-\pi}^\pi-\int_{-\pi}^\pi\dfrac{\sin nx}{n}dx\\
&=\left.\dfrac{\cos nx}{n^2}\right|_{-\pi}^\pi\\
&=0
\end{aligned}
$$

$$
\begin{aligned}
\pi b_n&=\int_{-\pi}^\pi x\sin nxdx\\
&=\int_{-\pi}^\pi-x\dfrac{d(\cos nx)}{n}\\
&=-\left.\dfrac{x\cos nx}{n}\right|_{-\pi}^\pi+\int_{-\pi}^\pi\dfrac{\cos nx}{n}dx\\
&=(-1)^{n+1}\dfrac{2\pi}n+\left.\dfrac{\sin nx}{n^2}\right|_{-\pi}^\pi\\
&=(-1)^{n+1}\dfrac{2\pi}n
\end{aligned}
$$

$$
b_n=(-1)^{n+1}\dfrac2n
$$

$(ii)$

$$
\begin{aligned}
\pi a_n&=\left.\dfrac{x\sin nx}{n}\right|_0^{2\pi}-\int_0^{2\pi}\dfrac{\sin nx}{n}dx\\
&=\left.\dfrac{\cos nx}{n^2}\right|_0^{2\pi}\\
&=0
\end{aligned}
$$

$$
\begin{aligned}
\pi b_n&=-\left.\dfrac{x\cos nx}{n}\right|_0^{2\pi}+\int_0^{2\pi}\dfrac{\cos nx}{n}dx\\
&=-\dfrac{2\pi}n+\left.\dfrac{\sin nx}{n^2}\right|_0^{2\pi}\\
&=-\dfrac{2\pi}n
\end{aligned}
$$

$$
b_n=-\dfrac2n
$$

> 3. 求函数
>
> $$
f(x)=\begin{cases}
-\dfrac\pi4&,-\pi<x<0\\
\dfrac\pi4&,0\le x<\pi
\end{cases}
>$$
>
> 的傅里叶级数，并由它推出
>
> $(1)$ $\dfrac\pi4=1-\dfrac13+\dfrac15-\dfrac17+\dots$

$$
\begin{aligned}
\pi a_n&=\int_{-\pi}^\pi f(x)\cos nxdx\\
&=-\int_{-\pi}^0\dfrac\pi4\cos nxdx+\int_0^\pi\dfrac\pi4\cos nxdx\\
&=0
\end{aligned}
$$

$$
\begin{aligned}
\pi b_n&=\int_{-\pi}^\pi f(x)\sin nxdx\\
&=\dfrac\pi4(\int_0^\pi\sin nxdx-\int_{-\pi}^0\sin nxdx)\\
&=\dfrac\pi2(\int_0^\pi\sin nxdx)\\
&=\dfrac\pi2\left.(-\dfrac{\cos nx}{n})\right|_0^\pi\\
&=\dfrac{\pi(1-(-1)^n)}{2n}
\end{aligned}
$$

$$
b_n=\dfrac{1-(-1)^n}{2n}
$$

$(1)$

取 $x=\dfrac\pi2$ 得到

$$
\begin{aligned}
\dfrac\pi4&=\dfrac{f(x+0)+f(x-0)}{2}\\
&=\sum_{n=1}^\infty\dfrac{1-(-1)^n}{2n}\sin(\dfrac\pi2x)\\
&=1-\dfrac13+\dfrac15-\dfrac17+\dots
\end{aligned}
$$

## 习题 15.2

> 2. 求函数
>
> $$
f(x)=\begin{cases}
x&,0\le x\le 1\\
1&,1<x<2\\
3-x&,2\le x\le 3\\
\end{cases}
> $$
>
> 的傅里叶级数并讨论其收敛性

对其进行偶延拓，可以得到周期为 $3$ 的函数。

套公式积分，

$$
\begin{aligned}
a_n&=\dfrac{2}{3}\int_0^3f(x)\cos\dfrac{n\pi x}{3}dx\\
&=\dfrac23\int_0^3f(x)\cos\dfrac{n\pi x}{3}dx\\
&=\dfrac{6}{n^2\pi^2}(-\cos n\pi+\cos\dfrac{2n\pi}3+\cos\dfrac{n\pi}{3}-1)
\end{aligned}
$$

所以傅里叶级数是 $f(x)=\dfrac23+\sum\limits_{n=1}^\infty\dfrac{6}{n^2\pi^2}(-\cos n\pi+\cos\dfrac{2n\pi}{3}+\cos\dfrac{n\pi}3-1)\cos\dfrac{n\pi x}{3}$

显然函数分段光滑且连续，所以一致收敛于 $f$

> 4. 求函数 $f(x)=\cos\dfrac x2$ 在 $[0,\pi]$ 上的正弦级数。

进行奇延拓。

$$
\begin{aligned}
b_n&=\dfrac2\pi\int_0^\pi f(x)\sin nxdx\\
&=\dfrac1\pi\int_0^\pi(\sin(\dfrac{2n+1}2x)+\sin(\dfrac{2n-1}2x))dx\\
&=\dfrac2\pi(\dfrac1{2n+1}(1-\cos\dfrac\pi2(2n+1))+\dfrac1{2n-1}(1-\cos\dfrac\pi2(2n-1)))\\
&=\dfrac{8n}{\pi(2n+1)(2n-1)}
\end{aligned}
$$

所以

$f(x)=\sum\limits_{n=1}^\infty\dfrac{8n}{\pi(2n+1)(2n-1)}\sin nx$

## 习题 15.3

> 2. 设 $f$ 为 $[-\pi,\pi]$ 上的可积函数，证明：若 $f$ 的傅里叶级数在 $[-\pi,\pi]$ 一致收敛于 $f$，则成立帕塞瓦尔等式
>
> $$
\dfrac1\pi\int_{-\pi}^\pi f^2(x)dx=\dfrac{a_0^2}2+\sum_{n=1}^\infty(a_n^2+b_n^2)
> $$
>
> 这里 $a_n,b_n$ 为 $f$ 的傅里叶系数。

下记 $S_n(x)$ 为傅里叶级数的前缀和。

在贝塞尔不等式的证明过程中，我们知道

$$
\int_{-\pi}^\pi(f(x)-S_m(x))^2dx=\int_{-\pi}^\pi f^2(x)dx-(\dfrac{\pi a_0^2}2+\pi\sum_{n=1}^m(a_n^2+b_n^2))
$$

然而，$\forall\epsilon>0,\exist N>0,\forall n>N,x\in[-\pi,\pi],|f(x)-S_m(x)|<\epsilon$。

这就是说 

$$
\int_{-\pi}^\pi(f(x)-S_m(x))^2dx<2\pi\epsilon^2
$$

所以 左式$=0$，帕塞瓦尔等式成立。

> 3. 帕塞瓦尔等式对于在 $[-\pi,\pi]$ 上满足收敛定理条件的函数也成立（证略）。请应用这个结果证明下列各式：
>
> $(1)$ $\dfrac{\pi^2}8=\sum\limits_{n=1}^\infty\dfrac1{(2n-1)^2}$

$(1)$

对 $f(x)=\begin{cases}-\dfrac\pi4&,-\pi\le x<0\\ \dfrac\pi4&,0\le x\le\pi\end{cases}$ 使用

$$
\begin{aligned}
\dfrac1\pi\int_{-\pi}^\pi f^2(x)dx=\dfrac{\pi^2}8
\end{aligned}
$$

$$
\begin{aligned}
\dfrac{a_0^2}2+\sum_{n=1}^\infty(a_n^2+b_n^2)&=\sum_{n=1}^\infty b_n^2\\
&=\sum_{n=1}^\infty\dfrac1{(2n-1)^2}
\end{aligned}
$$

由帕塞瓦尔等式，两式相等，证毕。

## 第十五章总练习题

> 2. 设 $f$ 为 $[-\pi,\pi]$ 上的可积函数，$a_0,a_k,b_k(k=1,2,\dots,n)$ 为 $f$ 的傅里叶系数。试证明：当
>
> $$
A_0=a_0,A_k=a_k,B_k=b_k(k=1,2,\dots,n)
> $$
>
> 时，积分
>
> $$
\int_{-\pi}^\pi(f(x)-T_n(x))^2dx
> $$
>
> 取最小值，且最小值为
>
> $$
\int_{-\pi}^\pi f^2(x)dx-\pi(\dfrac{a_0^2}2+\sum_{k=1}^n(a_k^2+b_k^2))
> $$
>
> 上述 $T_n(x)$ 是第 1 题中的三角多项式。

$$
\begin{aligned}
\int_{-\pi}^\pi(f(x)-T_n(x))^2dx&=\int_{-\pi}^\pi f^2(x)dx-\int_{-\pi}^\pi2f(x)T_n(x)dx+\int_{-\pi}^\pi T_n^2(x)
\end{aligned}
$$

而

$$
\begin{aligned}
\int_{-\pi}^\pi f(x)T_n(x)dx&=\int_{-\pi}^\pi f(x)dx(\dfrac {A_0}2+\sum_{k=1}^nA_k\cos kx+B_k\sin kx)\\
&=\dfrac {A_0}2\int_{-\pi}^\pi f(x)dx+\sum_{k=1}^nA_k\int_{-\pi}^\pi \cos kxdx+B_k\int_{-\pi}^\pi\sin kxdx\\
&=\pi(\dfrac{A_0}2a_0+\sum_{k=1}^nA_ka_k+B_kb_k)
\end{aligned}
$$

$$
\begin{aligned}
\int_{-\pi}^\pi T_n^2(x)dx&=\int_{-\pi}^\pi(\dfrac{A_0}2+\sum_{k=1}^nA_k\cos kx+B_k\sin kx)^2\\
&=\int_{-\pi}^\pi(\dfrac{A_0^2}4+A_0(\sum_{k=1}^nA_k\cos kx+B_k\sin kx)+(\sum_{k=1}^nA_k\cos kx+B_k\sin kx)^2)dx\\
&=\pi(\dfrac{A_0^2}{2}+\sum_{k=1}^n(A_k^2+B_k^2))
\end{aligned}
$$

所以

$$
\begin{aligned}
R(x)&=\int_{-\pi}^\pi(f(x)-T_n(x))^2dx-(\int_{-\pi}^\pi f^2(x)dx-\pi(\dfrac{a_0}2+\sum_{k=1}^n(a_k^2+b_k^2)))\\
&=\pi(\dfrac12(A_0-a_0)^2+\sum_{k=1}^n(A_k-a_k)^2+(B_k-b_k)^2)\\
&\ge0
\end{aligned}
$$

当且仅当 $A_k=a_k,k=0,1,\dots,n$ 且 $B_k=b_k,k=1,2,\dots,n$ 时成立。 

> 5. 设定义在 $[a,b]$ 上的连续函数列 $\{\varphi_n\}$ 满足关系
>
> $$
\int_a^b\varphi_n(x)\varphi_m(x)dx=\begin{cases}
0&,n\neq m\\
1&,n=m\\
\end{cases}
> $$
>
> 对于在 $[a,b]$ 上的可积函数 $f$，定义
>
> $$
a_n=\int_a^bf(x)\varphi_n(x)dx,\ n=1,2,\dots
> $$
>
> 证明：$\sum\limits_{n=1}^\infty a_n^2$ 收敛，且有不等式
>
> $$
\sum_{n=1}^\infty a_n^2\le\int_a^b f^2(x)dx
> $$

取 $T_n(x)=\sum\limits_{k=1}^na_k\varphi_k(x)$。

考察 $\int_a^b(f(x)-T_n(x))^2dx$，显然 $\ge0$。

然而

$$
\begin{aligned}
\int_a^b(f(x)-T_n(x))^2dx&=\int_a^bf^2(x)dx-2\int_a^bf(x)T_n(x)dx+\int_a^bT_n^2(x)dx\\
&=\int_a^bf^2(x)dx-2\int_a^bf(x)\sum_{k=1}^na_k\varphi_k(x)dx+\sum_{k=1}^n a_k^2\\
&=\int_a^bf^2(x)dx-2\sum_{k=1}^na_k\int_a^bf(x)\varphi_k(x)dx+\sum_{k=1}^n a_k^2\\
&=\int_a^bf^2(x)dx-2\sum_{k=1}^na_k^2+\sum_{k=1}^na_k^2\\
&=\int_a^bf^2(x)dx-\sum_{k=1}^na_k^2
\end{aligned}
$$

所以 $\sum\limits_{k=1}^na_k^2\le\int_a^bf^2(x)dx$。

令 $n\to\infty$，得到 $\sum\limits_{k=1}^\infty a_k^2\le\int_a^bf^2(x)dx$，前者单调递增有上界，所以收敛。