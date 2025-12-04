## 习题 9.1

> 2. 通过对积分区间作等分分割，并取适当的点集 $\{\xi_i\}$，把定积分看作是对应的积分和的极限，来计算下列定积分：
>
> $(1)\int_0^1x^3dx$

$(1)$

进行等分，取 $x_i=\dfrac in(i=0,1,\dots n)$，再取 $\xi_i=x_i(i=1,2,\dots n)$。

则由题意

$$
\begin{aligned}
\int_0^1 x^3dx&=\lim_{n\to\infty}\sum_{i=1}^n\xi_i^3\dfrac1n\\
&=\lim_{n\to\infty}\dfrac1{n^4}\cdot(\dfrac14n^2(n+1)^2)\\
&=\lim_{n\to\infty}\dfrac{(n+1)^2}{4n^2}\\
&=\dfrac14
\end{aligned}
$$