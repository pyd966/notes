i# Chap 1 实数集与函数

## 习题 1.1

> 6. 设 $a,b,c\in R_+$，证明 $|\sqrt{a^2+b^2}-\sqrt{a^2+c^2}|\le|b-c|$。并说明几何意义。

两边同时平方，即证明 

$$
2a^2+b^2+c^2-2\sqrt{(a^2+b^2)(a^2+c^2)}\le b^2+c^2-2bc
$$


即

$$
2a^2-2\sqrt{a^4+a^2b^2+a^2c^2+b^2c^2}\le-2bc
$$

即

$$
a^2+bc\le\sqrt{a^4+a^2b^2+a^2c^2+b^2c^2}
$$

如果左侧 $\le 0$，那么不等式显然成立。下面不妨设左侧 $>0$。

两边平方，即

$$
a^4+b^2c^2+2a^2bc\le a^4+a^2b^2+a^2c^2+b^2c^2
$$

即

$$
2a^2bc\le a^2b^2+a^2c^2
$$

由于 $a>0$，上式等价于

$$
2bc\le b^2+c^2
$$

$b,c>0$，由熟知的均值不等式，上式成立不等式成立。

考虑几何意义，懒得画图了，总之就是两个直角三角形拼一拼。

> 7. 设 $x>0,b>0,a\neq b$，证明：$\dfrac{a+x}{b+x}$ 介于 $1$ 和 $\dfrac ab$ 之间。

分类讨论。

如果 $a<b$，下面我们证明 $\dfrac ab<\dfrac{a+x}{b+x}<1$。

左半边等价于 $a(b+x)<b(a+x)$，也就是 $ab+ax<ab+bx$，也就是 $ax<bx$。

而 $x>0$，所以也就是 $a<b$，显然成立，故左半边成立。

右半边等价于 $a+x<b+x$，也就是 $a<b$，也显然成立。

如果 $a>b$，下面我们证明 $\dfrac ab>\dfrac{a+x}{b+x}>1$。

左半边等价于 $a(b+x)>b(a+x)$，也就是 $ab+ax>ab+bx$，也就是 $ax>bx$，又 $x>0$，也就是 $a>b$，显然成立。

右半边等价于 $a+x>b+x$，也就是 $a>b$，显然成立。

综上，QED。

> 8. 设 $p$ 为正整数。证明：若 $p$ 不是完全平方数，则 $\sqrt{p}$ 是无理数。

反证法，假设 $\sqrt p$ 是有理数，$\sqrt p=\dfrac ab(a,b\in Z^+,\gcd(a,b)=1)$。

那么 $p=\dfrac{a^2}{b^2}$。

把 $a,b$ 写成唯一分解形式，$a=p_1^{\alpha_1}p_2^{\alpha_2}\dots p_n^{\alpha_n},b=p_1^{\beta_1}p_2^{\beta_2}\dots p_n^{\beta_n}$，其中 $p_1<p_2<\dots<p_n$ 是素数，$\alpha_i,\beta_i\in N$。

那么 $p=p_1^{2(\alpha_1-\beta_1)}p_2^{2(\alpha_2-\beta_2)}\dots p_n^{2(\alpha_n-\beta_n)}=\large(p_1^{\alpha_1-\beta_1}p_2^{\alpha_2-\beta_2}\dots p_n^{\alpha_n-\beta_n}\large)^2$，所以 $p$ 是完全平方数，与条件矛盾，故假设不成立，原命题成立。

## 习题 1.2

> 4. 求下数数集的上、下确界，并依定义加以验证：
> 
> $(3)$ $S=\{x\mid x\in (0,1),x\in R/Q\}$。

$\sup S=1,\inf S=0$，证明如下：

先证明，$\sup S=1$。

$(1) \forall x\in S$，由于 $x\in(0,1)$，所以 $x<1$。

$(2)\forall \alpha<1$，根据实数的稠密性，存在无理数 $\beta\in(\max\{\alpha,0\},1)$，那么 $\beta\in S$，且 $\beta>\alpha$。

再证明，$\inf S=0$。

$(1)\forall x\in S$，由于 $x\in(0,1)$，所以 $x>0$。

$(2)\forall \alpha>0$，根据实数的稠密性，存在无理数 $\beta\in(0,\min\{\alpha,1\})$，那么 $\beta\in S$，且 $\beta<\alpha$。

QED。

> 6. 设 $S$ 为非空数集，定义 $S^-=\{x\mid -x\in S\}$，证明：
>
> $(1) \inf S^-=-\sup S$
>
> $(2) \sup S^-=-\inf S$

先证 $(1)$。

记 $p=\inf S^-$，下面证明 $-p$ 是 $S$ 的上确界。

$(1) \forall x\in S$，我们有 $-x\in S^-$，所以 $p\le -x$，也就是 $-p\ge x$。

$(2) \forall \alpha <-p$，我们有 $-\alpha>p$，根据 $p=\inf S^-$，我们知道 $\exist x\in S^-,s.t.\ x<-\alpha$，也就是说 $-x>\alpha$，而 $-x\in S^-$，所以这部分完。

综上，$-p$ 是 $S$ 的上确界。

$(2)$ 是一样的。

> 设 $A,B$ 皆为非有界数集，定义数集
>
> $A+B=\{z\mid z=x+y,x\in A,y\in B\}$。
>
> 证明：$(2) \inf(A+B)=\inf A+\inf B$。

这个 $(1)$ 上课讲了，$(2)$ 完全没区别，随便写一下。

我们记 $x=\inf A,y=\inf B$，下面分两方面证明 $x+y$ 是 $A+B$ 的下确界。

$(1) \forall z\in A+B$，一定 $\exist a\in A,b\in B,s.t.\ z=a+b$，那么 $a\ge x,b\ge y$，所以 $z=a+b\ge x+y$。

$(2) \forall \epsilon>0$，一定 $\exist a\in A,b\in B,s.t.\ a<x+\dfrac{\epsilon}2,b<y+\dfrac{\epsilon}2$，两式相加，$a+b<x+y+\epsilon$，而 $a+b\in A+B$，所以这部分证毕。

综上，$x+y$ 是 $A+B$ 的下确界。

## 习题 1.3

> 4. 确定下列初等函数的存在域：
> 
>  $(3)\ y=\arcsin(\lg\dfrac x{10})$。

由 $\lg \dfrac x{10}$ 有意义，可知 $\dfrac x{10}>0$，即 $x>0$。

由于 $\arcsin x$ 的定义域是 $[-1,1]$，所以要求 $\lg\dfrac x{10}\in[-1,1]$，也就是说 $\dfrac x{10}\in[\dfrac 1{10},10]$，即 $x\in[1,100]$。

综上 $x\in[1,100]$。

> 7. 试问下列函数是由哪些初等函数复合而成：
>
> $(1)\ y=(1+x)^{20};\ (4)y=2^{\sin^2x}$

$(1)$

$f(x)=x^{20},g(x)=1+x,y=f(g(x))$

$(2)$

$f(x)=2^x,g(x)=x^2,h(x)=\sin x,y=f(g(h(x)))$

> 10. 试问下列等式是否成立：
>
> $(1)\ \tan(\arctan x)=x,x\in R;$
>
> $(2)\ \arctan(\tan x)=x,x\neq k\pi+\dfrac{\pi}2,k=0,\pm1,\dots$

$(1)$ 成立，证明如下：

设 $f(x)=\tan x(x\in(-\dfrac{\pi}2,\dfrac{\pi}2)),g(x)=\arctan x$，则由定义可知，$g$ 为 $f$ 的反函数，故 $f(g(x))=x$。

由于 $\arctan x\in(-\dfrac{\pi}2,\dfrac{\pi}2)$，所以把 $f$ 换成 $h(x)=\tan x$，结果不变。即 $h(g(x))=f(g(x))=x$。

$(2)$ 不成立，证明如下：

取 $x=\dfrac{5\pi}4$，则 $\tan x=1$，$\arctan(\tan x)=\dfrac{\pi}4\neq x$，所以不成立。

> 12. 证明关于函数 $y=[x]$ 的如下不等式：
>
> $(1)$ 当 $x>0$ 时，$1-x<x[\dfrac 1x]\le 1$

由 $x>0$，可得 $[\dfrac 1x]\in(\dfrac 1x-1,\dfrac 1x]$，所以 $x[\dfrac 1x]\in(1-x,1]$。

## 习题 1.4

> 6. 设函数 $f$ 定义在 $[-a,a]$ 上，证明：
>
> $(1)\ F(x)=f(x)+f(-x),x\in[-a,a]$ 为偶函数；
>
> $(2)\ G(x)=f(x)-f(-x),x\in[-a,a]$ 为奇函数；
>
> $(3)\ f$ 可表示某个奇函数和偶函数之和。

$(1)$

$F(-x)=f(-x)+f(x)=f(x)+f(-x)=F(x)$，又定义域 $[-a,a]$ 关于 $0$ 对称，所以 $F(x)$ 是偶函数。

$(2)$

$G(-x)=f(-x)-f(x)=-(f(x)-f(-x))=-G(x)$，又定义域 $[-a,a]$ 关于 $0$ 对称，所以 $G(x)$ 是奇函数。

$(3)$

$f(x)=\dfrac{F(x)}2+\dfrac{G(x)}2$。由于 $F(x),G(x)$ 分别是偶函数、奇函数，所以 $\dfrac{F(x)}2,\dfrac{G(x)}2$ 分别是偶函数、奇函数。证毕。

> 9. 设 $f$ 为定义在 $D$ 上的有界函数，证明：
>
> $(1)\ \sup\limits_{x\in D}\{-f(x)\}=-\inf\limits_{x\in D}f(x)$

记 $S=\{y\mid y=f(x),x\in D\},T=\{y\mid y=-f(x),x\in D\},p=\inf S$。

下面证明 $-p$ 是 $T$ 的上界。

$(1)\ \forall y\in T$，有 $-y\in S$。由于 $p$ 是 $S$ 的下界，故 $-y\ge p$，也就是 $y\le -p$。

$(2) \forall z<-p$，有 $-z>p$。由于 $p$ 是 $S$ 的下界，故 $\exist y\in S,s.t.\ y<-z$，即 $-y>z$，又 $-y\in T$，所以这部分证毕。

综上，$-p$ 是 $T$ 的上界，原命题成立。

## 第一章总练习题

> 13. 设 $f,g$ 为 $D$ 上的非负有界函数，证明：
>
> $(1)\ \inf\limits_{x\in D}f(x)\cdot\inf\limits_{x\in D}g(x)\le\inf\limits_{x\in D}\{f(x)g(x)\}$

设 $p=\inf\limits_{x\in D}f(x),q=\inf\limits_{x\in D}g(x)$。

显然 $\forall x\in D,0\le p\le f(x),0\le q\le g(x)$，两式相乘，得到

$$
\forall x\in D,pq\le f(x)g(x)
$$

那么，$pq$ 是 $f(x)g(x)$ 的一个下界，所以有 $pq\le f(x)g(x)\le\inf\limits_{x\in D}\{f(x)g(x)\}$。