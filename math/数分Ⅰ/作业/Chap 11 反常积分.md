## 习题 11.1

> 1. 讨论下列无穷积分是否收敛？若收敛，则求其值：
>
> $(1)\int_0^{+\infty}xe^{-x^2}dx$
>
> $(3)\int_0^{+\infty}\dfrac1{\sqrt{e^x}}dx$

$(1)$

$$
\int_0^{+\infty}xe^{-x^2}dx=\lim_{u\to+\infty}\int_0^uxe^{-x^2}dx=\lim_{u\to+\infty}(-\dfrac12e^{-u^2}+\dfrac12)=\dfrac12
$$

$(3)$

$$
\int_0^{+\infty}\dfrac1{\sqrt{e^x}}dx=\lim_{u\to+\infty}\int_0^u\dfrac{dx}{\sqrt{e^x}}=\lim_{u\to+\infty}(-2e^{-\frac u2}+2)=2
$$