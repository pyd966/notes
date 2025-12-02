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
>
> $(23)\int\dfrac{dx}{e^x+e^{-x}}$
>
> $(29)\int\dfrac{\sqrt{x}}{1-\sqrt[3]{x}}dx$
>
> $(30)\int\dfrac{\sqrt{x+1}-1}{\sqrt{x+1}+1}dx$
>
> $(32)\int\dfrac{dx}{x(1+x^n)}(n\in N)$
>
> $(36)\int\dfrac{dx}{x^4\sqrt{x^2-1}}$

$(4)$

$$
\int(1+x)^n\mathrm{d}x=\int(1+x)^n\mathrm{d}(1+x)=\dfrac1{n+1}(1+x)^{n+1}+C
$$

$(9)$

$$
\int x\sin x^2\mathrm{d}x=\dfrac12\int\sin x^2\mathrm{d}(x^2)=-\dfrac12\cos x^2+C
$$

$(23)$

$$
\int\dfrac{dx}{e^x+e^{-x}}=\int\dfrac{e^xdx}{e^{2x}+1}=\int\dfrac{d(e^x)}{(e^x)^2+1}=\int\dfrac{du}{1+u^2}=\arctan u+C=\arctan(e^x)+C
$$

$(29)$

$x\in[0,1)\cup(1,+\infty)$

令 $x=t^6,t\in[0,1)\cup(1,+\infty)$。

$$
\int\dfrac{\sqrt{x}}{1-\sqrt[3]{x}}dx=\int\dfrac{t^3}{1-t^2}(6t^5)dt=-6\int(t^6+t^4+t^2+1-\dfrac1{1-t^2})dt
$$

$$
\int\dfrac1{1-t^2}dt=\dfrac12\int(\dfrac{1}{1-t}+\dfrac1{1+t})dt=\dfrac12\int(-\dfrac{d(1-t)}{1-t}+\dfrac{d(1+t)}{1+t})=\dfrac12\ln|\dfrac{1-t}{1+t}|+C
$$

所以 

$$
\int\dfrac{\sqrt{x}}{1-\sqrt[3]{x}}dx=-6(\dfrac17t^7+\dfrac15t^5+\dfrac13t^3+t-\dfrac12\ln|\dfrac{1-t}{1+t}|)+C=-\dfrac67t^7-\dfrac65t^5-2t^3-6t+3\ln|\dfrac{1-t}{1+t}|+C
$$

代入 $t=x^{\frac16}$，

$$
\int\dfrac{\sqrt{x}}{1-\sqrt[3]{x}}dx=-\dfrac67x^{\frac76}-\dfrac65x^{\frac56}-2x^{\frac12}-6x^{\frac16}+3\ln|\dfrac{1-x^{\frac16}}{1+x^{\frac16}}|+C
$$

经验证，答案正确。

$(30)$

令 $t=\sqrt{1+x}$，则 $x=t^2-1$

$$
\int\dfrac{\sqrt{x+1}-1}{\sqrt{x+1}+1}dx=\int(1-2\dfrac{1}{\sqrt{x+1}+1})dx=\int(1-2\dfrac1{t+1})d(t^2-1)=\int(2t-\dfrac{4t}{t+1})dt=\int(2t-4+\dfrac{4}{t+1})dt
$$

$$
\int(2t-4+\dfrac4{t+1})dt=t^2-4t+4\ln|t+1|+C=x+1-4\sqrt{1+x}+4\ln|\sqrt{1+x}+1|+C
$$

经验证，答案正确。

$(32)$

$$
\int\dfrac{dx}{x(1+x^n)}=\int(\dfrac1x-\dfrac{x^{n-1}}{1+x^n})dx=\int\dfrac{dx}x-\dfrac1n\int\dfrac{d(1+x^n)}{1+x^n}=\ln|x|-\dfrac1n\ln|1+x^n|+C
$$

$(36)$

记 $x=\sec t$

$$
\int\cos^3tdt=\int\dfrac{1+\cos2t}2\cos tdt=\dfrac12\int\cos tdt+\dfrac12\int\cos2t\cos tdt
$$

$$
\int\cos^3tdt=\dfrac12\sin t+C+\dfrac12\int\dfrac12(\cos t+\cos3t)=\dfrac34\sin t+\dfrac1{12}\sin3t+C
$$

当 $x>1$ 时，取 $t\in(0,\dfrac\pi2)$

$$
\int\dfrac{dx}{x^4\sqrt{x^2-1}}=\int\cos^3tdt=\sqrt{1-\frac1{x^2}}-\dfrac13(1-\dfrac1{x^2})^{\frac32}+C=\dfrac1x\sqrt{x^2-1}-\dfrac13(\dfrac1x-\dfrac1{x^3})\sqrt{x^2-1}+C
$$

当 $x<-1$ 时，取 $t\in(\dfrac\pi2,\pi)$

$$
\int\dfrac{dx}{x^4\sqrt{x^2-1}}=-\int\cos^3tdt=-\sqrt{1-\dfrac1{x^2}}-\dfrac13(1-\dfrac1{x^2})^{\frac32}+C=\dfrac1x\sqrt{x^2-1}-\dfrac13(\dfrac1x-\dfrac1{x^3})\sqrt{x^2-1}+C
$$

综上，

$$
\int\dfrac{dx}{x^4\sqrt{x^2-1}}=\dfrac1x\sqrt{x^2-1}(\dfrac23+\dfrac1{3x^2})+C
$$

经验证，答案正确。

> 2. 应用分部积分法求下列不定积分：
>
> $(3)\int x^2\cos xdx$
>
> $(7)\int(\ln(\ln x)+\dfrac1{\ln x})dx$
>
> $(9)\int\sec^3xdx$
>
> $(10)\int\sqrt{x^2\pm a^2}dx(a>0)$

$(3)$

$$
\int x^2\cos xdx=\int x^2d(\sin x)=x^2\sin x-2\int x\sin xdx
$$

$$
\int x\sin xdx=-\int xd(\cos x)=-(x\cos x-\int\cos xdx)=-x\cos x+\sin x+C
$$

所以

$$
\int x^2\cos xdx=x^2\sin x+2x\cos x-2\sin x+C
$$

$(7)$

记 $t=\ln x$，则 $x=e^t$。

$$
\int(\ln(\ln x)+\dfrac1{\ln x})dx=\int(e^t\ln t+\dfrac{e^t}t)dt
$$

而

$$
\int e^t\ln tdt=\int\ln td(e^t)=e^t\ln t-\int\dfrac{e^t}tdt
$$

（多神奇的巧合！）

所以

$$
\int(\ln(\ln x)+\dfrac1{\ln x})dx=e^t\ln t+C=x\ln(\ln x)+C
$$

$(9)$

$$
\int\sec^3xdx=\int\sec x\cdot\sec^2 xdx=\int\sec xd(\tan x)=\sec x\tan x-\int\tan^2 x\sec xdx
$$

而

$$
\int\tan^2x\sec xdx=\int\dfrac{1-\cos^2x}{\cos^3x}dx=\int\sec^3xdx-\int\sec xdx=\int\sec^3xdx-\dfrac12\ln|\dfrac{1+\sin x}{1-\sin x}|+C
$$

代回上式，移项得到

$$
2\int\sec^3xdx=\sec x\tan x+\dfrac12\ln|\dfrac{1+\sin x}{1-\sin x}|+C
$$

$$
\int\sec^3xdx=\dfrac12\sec x\tan x+\dfrac14\ln|\dfrac{1+\sin x}{1-\sin x}|+C
$$

$(10)$

$$
\int a\sqrt{(\frac xa)^2\pm1}dx=a^2\int\sqrt{u^2\pm1}du
$$

我们对 $\pm1$ 分开计算。

先算 $+1$，记 $u=\tan t,t\in(-\dfrac\pi2,\dfrac\pi2)$

$$
a^2\int\sqrt{u^2+1}du=a^2\int\sqrt{\tan^2t+1}\sec^2tdt=a^2\int\sec^3tdt=a^2(\dfrac12\sec t\tan t+\dfrac12\ln|\sec t+\tan t|)+C
$$

$$
a^2\int\sqrt{u^2+1}du=\dfrac{a^2}2(\sqrt{1+(\frac xa)^2}\dfrac xa+\ln|\dfrac xa+\sqrt{1+(\frac xa)^2}|)+C
$$

再算 $-1$，记 $u=\sec t$。

当 $u\ge 1$ 时，取 $t\in[0,\dfrac\pi2)$。

$$
a^2\int\sqrt{u^2-1}du=a^2\int\tan^2t\sec tdt=a^2(\dfrac12\sec t\tan t-\dfrac12\ln|\sec t+\tan t|)+C
$$

$$
a^2\int\sqrt{u^2-1}du=\dfrac{a^2}2(\dfrac xa\sqrt{(\frac xa)^2-1}-\ln|\dfrac xa+\sqrt{(\frac xa)^2-1}|)+C
$$

当 $u\le-1$ 时，取 $t\in(\dfrac\pi2,\pi]$

$$
a^2\int\sqrt{u^2-1}du=-a^2\int\tan^2t\sec tdt=-\dfrac{a^2}2(\sec t\tan t-\ln|\sec t+\tan t|)+C
$$

$$
a^2\int\sqrt{u^2-1}du=\dfrac{a^2}2(\sqrt{(\frac xa)^2-1}\dfrac xa+\ln|\dfrac xa-\sqrt{(\frac xa)^2-1}|)+C=\dfrac{a^2}2(\dfrac xa\sqrt{(\frac xa)^2-1}-\ln|\dfrac xa-\sqrt{(\frac xa)^2-1}|)+C
$$

所以

$$
\int\sqrt{x^2+a^2}dx=\dfrac x2\sqrt{x^2+a^2}+\dfrac{a^2}2\ln|x+\sqrt{x^2+a^2}|+C\\
\int\sqrt{x^2-a^2}dx=\dfrac x2\sqrt{x^2-a^2}-\dfrac{a^2}2\ln|x-\sqrt{x^2-a^2}|+C\\
$$

## 习题 8.3

> 1. 求下列不定积分：
>
> $(5)\int\dfrac{dx}{(x-1)(x^2+1)^2}$

$(5)$

通过待定系数法，可以得到

$$
\dfrac{1}{(x-1)(x^2+1)^2}=\dfrac1{4(x-1)}-\dfrac{x+1}{4(x^2+1)}-\dfrac{x+1}{2(x^2+1)^2}
$$

而

$$
\int\dfrac1{4(x-1)}dx=\dfrac14\ln|x-1|+C
$$

$$
\int(-\dfrac{x+1}{4(x^2+1)})dx=-\dfrac14\int(\dfrac12\cdot\dfrac{d(x^2+1)}{x^2+1}+\dfrac{dx}{x^2+1})=-\dfrac18\ln|x^2+1|-\dfrac14\arctan x+C
$$

另外一边，

$$
\int(-\dfrac{x+1}{2(x^2+1)^2})dx=-\dfrac12\int(\dfrac12\cdot\dfrac{d(x^2+1)}{(x^2+1)^2}+\dfrac{dx}{(x^2+1)^2})=\dfrac1{4(x^2+1)}-\dfrac12\int\dfrac{dx}{(x^2+1)^2}
$$

其中

$$
\int\dfrac{dx}{(x^2+1)^2}=\int\dfrac{x^2+1-x^2}{(x^2+1)^2}dx=\int\dfrac{dx}{x^2+1}-\int\dfrac{x^2}{(x^2+1)^2}dx=\arctan x+\dfrac12\int x\cdot d(\dfrac1{x^2+1})
$$

$$
\int\dfrac{dx}{(x^2+1)^2}=\arctan x+\dfrac12(\dfrac x{x^2+1}-\int \dfrac{dx}{x^2+1})=\dfrac12\arctan x+\dfrac{x}{2(x^2+1)}+C
$$

代回原式得到

$$
\int\dfrac{dx}{(x-1)(x^2+1)^2}=\dfrac14\ln|x-1|-\dfrac18\ln|x^2+1|-\dfrac12\arctan x+\dfrac{1-x}{4(x^2+1)}+C
$$

> 2. 求下列不定积分：
>
> $(1)\int \dfrac{dx}{5-3\cos x}$
>
> $(2)\int\dfrac{dx}{2+\sin^2x}$
>
> $(4)\int\dfrac{x^2}{\sqrt{1+x-x^2}}dx$
>
> $(6)\int\dfrac1{x^2}\sqrt{\dfrac{1-x}{1+x}}dx$

$(1)$

记 $t=\tan\dfrac x2$，则 $x=2\arctan t,\cos x=\dfrac{1-t^2}{1+t^2}$

所以

$$
\int\dfrac{dx}{5-3\cos x}=\int\dfrac{1+t^2}{2+8t^2}\cdot(\dfrac2{1+t^2})dt=\int\dfrac{dt}{1+4t^2}=\dfrac12\int\dfrac{d(2t)}{1+(2t)^2}=\dfrac12\arctan(2t)+C
$$

答案为 $\dfrac12\arctan(2\tan\dfrac x2)+C$

$(2)$

记 $t=\tan x$，则 $x=\arctan t$

$$
\int\dfrac{dx}{2+\sin^2x}=\int\dfrac{\sin^2x+\cos^2x}{3\sin^2x+2\cos^2x}dx=\int\dfrac{t^2+1}{3t^2+2}\cdot(\dfrac{dt}{t^2+1})=\dfrac{1}{2\sqrt{\frac32}}\int\dfrac{d(\sqrt{\frac32}t)}{(\sqrt{\frac32}t)^2+1}=\dfrac{\sqrt{6}}6\arctan(\dfrac{\sqrt{6}}{2}t)+C
$$

答案为 $\dfrac{\sqrt{6}}6\arctan(\dfrac{\sqrt6}2\tan x)+C$

$(4)$

$1+x-x^2=-(x-\dfrac12)^2+\dfrac54$，记 $u=x-\dfrac12$。

$$
\int\dfrac{x^2}{\sqrt{1+x-x^2}}dx=\int\dfrac{(u+\frac12)^2}{\sqrt{\frac54-u^2}}du
$$

记 $u=\dfrac{\sqrt5}2\sin t$，其中 $t\in(-\dfrac\pi2,\dfrac\pi2)$。

则

$$
\int\dfrac{(u+\frac12)^2}{\sqrt{\frac54-u^2}}du=\int\dfrac{(\frac{\sqrt5}2\sin t+\frac12)^2}{\frac{\sqrt{5}}2\cos t}d(\dfrac{\sqrt{5}}2\sin t)=\int(\dfrac54\sin^2t+\dfrac{\sqrt5}2\sin t+\dfrac14)dt=-\dfrac5{16}\sin2t-\dfrac{\sqrt{5}}2\cos t+\dfrac78t+C
$$

答案为 $-\dfrac5{16}\sin(2\arcsin\dfrac{2x-1}{\sqrt{5}})-\dfrac{\sqrt{5}}2\cos(\arcsin\dfrac{2x-1}{\sqrt{5}})+\dfrac78\arcsin\dfrac{2x-1}{\sqrt{5}}+C$

$(6)$

记 $t=\sqrt{\dfrac{1-x}{1+x}}$，则 $x=\dfrac{1-t^2}{1+t^2}$。

$$
\int\dfrac1{x^2}\sqrt{\dfrac{1-x}{1+x}}dx=\int(\dfrac{1+t^2}{1-t^2})^2t\cdot d(\dfrac{1-t^2}{1+t^2})=-4\int\dfrac{t^2dt}{(1-t^2)^2}
$$

而

$$
\int\dfrac{t^2}{(1-t^2)^2}dt=\int\dfrac t2d(\dfrac1{1-t^2})dt=\dfrac{t}{2(1-t^2)}-\int\dfrac{dt}{2(1-t^2)}
$$

记 $t=\sin u$，则

$$
\int\dfrac{dt}{2(1-t^2)}=\dfrac12\int\dfrac{\cos udu}{\cos^2u}=\dfrac12\int\sec udu=\dfrac12\ln|\sec u+\tan u|+C=\dfrac12\ln|t+1|-\dfrac14\ln(1-t^2)+C
$$

所以

$$
\int\dfrac{t^2}{(1-t^2)^2}dt=\dfrac{t}{2(1-t^2)}-\dfrac12\ln|t+1|+\dfrac14\ln(1-t^2)+C
$$

答案是 $-\dfrac{\sqrt{1-x^2}}{x}+2\ln|\sqrt{\dfrac{1-x}{1+x}}+1|-\ln(\dfrac{2x}{1+x})+C$

## 第八章总练习题

> 1. 求下列不定积分：
>
> $(5)\int e^{\sqrt{x}}dx$
>
> $(15)\int\dfrac{x^2}{(1-x)^{100}}dx$
>
> $(18)\int\dfrac{dx}{\sqrt{\sin x\cos^7x}}$
>
> $(19)\int e^x(\dfrac{1-x}{1+x^2})^2dx$

$(5)$

记 $x=t^2$，则 $t=\sqrt{x}$

$$
\int e^{\sqrt{x}}dx=\int 2te^tdt=2\int td(e^t)=2(te^t-\int e^tdt)=2(t-1)e^t+C=2(\sqrt{x}-1)e^{\sqrt{x}}+C
$$

$(15)$

记 $t=1-x$，则 $x=1-t$。

$$
\int\dfrac{x^2}{(1-x)^{100}}dx=\int\dfrac{(1-t)^2}{t^{100}}d(1-t)=-\int(\dfrac{dt}{t^{100}}-\dfrac{2dt}{t^{99}}+\dfrac{dt}{t^{98}})=\dfrac1{99}t^{-99}-\dfrac1{49}t^{-98}+\dfrac1{97}t^{-97}+C
$$

答案为 $\dfrac1{99}(1-x)^{-99}-\dfrac1{49}(1-x)^{-98}+\dfrac1{97}(1-x)^{-97}+C$

$(18)$

记 $t=\tan x$，则 $x=\arctan t$。

$$
\int\dfrac{dx}{\sqrt{\sin x\cos^7x}}=\int\dfrac{(\sin^2x+\cos^2x)^2}{\sqrt{\sin x\cos^7x}}dx=\int\dfrac{(t^2+1)^2}{\sqrt{t}}\cdot(\dfrac{dt}{1+t^2})=\int\dfrac{1+t^2}{\sqrt{t}}dt
$$

记 $\sqrt{t}=u$，则 $t=u^2$。

$$
\int\dfrac{1+t^2}{\sqrt{t}}dt=\int\dfrac{u^4+1}{u}\cdot(2udu)=2\int(u^4+1)du=\dfrac25u^5+2u+C
$$

答案为 $\dfrac25 \tan^{\frac52}x+2\tan^{\frac12}x+C$。

$(19)$

$$
\int e^x\dfrac{(1-x)^2}{(1+x^2)^2}dx=\int\dfrac{e^xdx}{1+x^2}-\int\dfrac{2xe^xdx}{(1+x^2)^2}
$$

而

$$
\int\dfrac{e^xdx}{1+x^2}=\int\dfrac{d(e^x)}{1+x^2}=\dfrac{e^x}{1+x^2}+\int\dfrac{2xe^x}{(1+x^2)^2}
$$

所以

$$
\int e^x\dfrac{(1-x)^2}{(1+x^2)^2}dx=\dfrac{e^x}{1+x^2}+C
$$

