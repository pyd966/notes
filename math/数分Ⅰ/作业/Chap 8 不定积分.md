## 习题 8.1

> 3. 验证 $y=\dfrac{x^2}2\text{sgn}x$ 是 $|x|$ 在 $(-\infty,+\infty)$ 上的一个原函数。

$y=\begin{cases}\dfrac{x^2}2&,x>0\\ 0&,x=0\\ -\dfrac{x^2}2&,x<0\\ \end{cases}$

考虑 $y'$。

当 $x>0$ 时，$y'=x$；当 $x<0$ 时，$y'=-x$。

当 $x=0$ 时，$y'_+(0)=\lim\limits_{x\to0}\dfrac{\frac{x^2}2-0}{x}=0$，同理 $y'_-(0)=0$，所以 $y'(0)=0$。

综上，$y'=|x|$，所以 $y$ 是 $|x|$ 在 $(-\infty,+\infty)$ 上的一个原函数。

> 7. 设 $f'(\arctan x)=x^2$，求 $f(x)$。

$f'(x)=\tan^2x$。

$f(x)=\int \tan^2x\mathrm{d}x=\int(\dfrac{1}{\cos^2x}-1)\mathrm{d}x=\tan x-x+C$。

## 习题 8.2

> 1. 应用换元积分法求下列不定积分：
>
> $(4)\int(1+x)^n \mathrm{d}x$
>
> $(9)\int x\sin x^2\mathrm{d}x$

$(4)$

$$
\int(1+x)^n\mathrm{d}x=\int(1+x)^n\mathrm{d}(1+x)=\dfrac1{n+1}(1+x)^{n+1}+C
$$

$(9)$

$$
\int x\sin x^2\mathrm{d}x=\dfrac12\int\sin x^2\mathrm{d}(x^2)=-\dfrac12\cos x^2+C
$$