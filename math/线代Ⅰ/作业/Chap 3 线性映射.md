## 习题

> 5. 求下列线性变换 $\sigma$ 的象（值域）和核以及 $\sigma$ 的秩。
>
> $(1)\sigma(x_1,x_2,x_3)=(x_1+x_2+x_3,-x_1-2x_3,x_2-x_3)$
>
> $(3)\sigma(x_1,x_2,x_3)=(x_1+x_2+x_3,x_2+x_3,x_3)$

$(1)$

$\sigma(x_1,x_2,x_3)=(1,-1,0)x_1+(1,0,1)x_2+(1,-2,-1)x_3$

分别记这三个向量为 $\alpha_1,\alpha_2,\alpha_3$。

容易发现 $\alpha_3=2\alpha_1-\alpha_2$，且 $\alpha_1,\alpha_2$ 线性无关。

所以 $\text{Im}\sigma=L(\alpha_1,\alpha_2),r(\sigma)=2$。

解方程组 $\sigma(x_1,x_2,x_3)=(0,0,0)$ 可得 $\text{Ker}\sigma=L(1,1,-1)$。

$(3)$

$\sigma(x_1,x_2,x_3)=(1,0,0)x_1+(1,1,0)x_2+(1,1,1)x_3$。

分别记三个向量为 $\alpha_1,\alpha_2,\alpha_3$，容易发现它们线性无关。

所以 $\text{Im}\sigma=L(\alpha_1,\alpha_2,\alpha_3),r(\sigma)=3$。

解方程组 $\sigma(x_1,x_2,x_3)=(0,0,0)$ 可得 $\text{Ker}\sigma=\{0\}$。

> 6. 求 $R^3$ 的一个线性变换，使得 $\sigma$ 的象（值域）为 $\sigma(R^3)=L(\alpha_1,\alpha_2)$，其中 $\alpha_1=(1,0,-1),\alpha_2=(1,2,2)$。

取 $\alpha_3=(1,0,0)$，可以发现 $\alpha_1,\alpha_2,\alpha_3$ 线性无关，它们构成一组基。

设 $\alpha=c_1\alpha_1+c_2\alpha_2+c_3\alpha_3$，我们规定 $\sigma(\alpha)=c_1\alpha_1+c_2\alpha_2$，容易发现 $\sigma(R^3)=L(\alpha_1,\alpha_2)$。

设 $\beta=d_1\alpha_1+d_2\alpha_2+d_3\alpha_3$。

则 $\sigma(\lambda\alpha+\mu\beta)=\sigma((\lambda c_1+\mu d_1)\alpha_1+(\lambda c_2+\mu d_2)\alpha_2+(\lambda c_3+\mu d_3)\alpha_3)=(\lambda c_1+\mu d_1)\alpha_1+(\lambda c_2+\mu d_2)\alpha_2=\lambda(c_1\alpha_1+c_2\alpha_2)+\mu(d_1\alpha_1+d_2\alpha_2)=\lambda\sigma(\alpha)+\mu\sigma(\beta)$，所以 $\sigma$ 是线性变换。

综上，$\sigma$ 符合题意。

> 9. 已知 $R^3$ 的两个线性变换 $\sigma,\tau$ 为：
>
> $$
> \sigma(x_1,x_2,x_3)=(x_3,0,0)\\
> \tau(x_1,x_2,x_3)=(x_1+x_2+x_3,x_1-x_2,0)\\
> $$
>
> $(1)$ 求秩$(\sigma)$，秩$(\tau),\text{Im}\sigma,\text{Ker}\sigma$；
>
> $(2)$ 求秩$(\sigma\tau)$，秩$(\tau\sigma)$；
>
> $(3)$ 求秩$(\sigma+\tau)$；
>
> $(4)$ 求 $\text{Im}\tau+\text{Ker}\tau$。

$(1)$

$\sigma(x_1,x_2,x_3)=(1,0,0)x_3$，所以 $\text{Im}\sigma=L((1,0,0)),r(\sigma)=1$。

解方程 $\sigma(x_1,x_2,x_3)=(0,0,0)$，得 $\text{Ker}\sigma=L((1,0,0),(0,1,0))$。

$\tau(x_1,x_2,x_3)=(1,1,0)x_1+(1,-1,0)x_2$，二者线性无关，所以 $r(\tau)=2$。

$(2)$

$\sigma\tau(x_1,x_2,x_3)=(0,0,0)$，所以 $r(\sigma\tau)=0$。

$\tau\sigma(x_1,x_2,x_3)=(x_3,x_3,0)=(1,1,0)x_3$，所以 $r(\tau\sigma)=1$。

$(3)$

$(\sigma+\tau)(x_1,x_2,x_3)=(x_1+x_2+2x_3,x_1-x_2,0)=(1,1,0)x_1+(1,-1,0)x_2+(2,0,0)x_3$。

记三个向量分别为 $\alpha_1,\alpha_2,\alpha_3$，则 $\alpha_1+\alpha_2=\alpha_3$，且 $\alpha_1,\alpha_2$ 线性无关，所以 $r(\sigma+\tau)=2$。

$(4)$

由 $(1)$ 知 $\text{Im}\tau=L((1,1,0),(1,-1,0))$。

令 $\tau(x_1,x_2,x_3)=(0,0,0)$ 解得 $\text{Ker}\tau=L((1,1,-2))$。

分别记这些向量为 $\beta_1,\beta_2,\beta_3$，可以发现它们线性无关。

所以 $\text{Im}\tau+\text{Ker}\tau=L(\beta_1,\beta_2,\beta_3)$。

> 10. 已知
>
> $$
> \alpha_1=(1,-1),\alpha_2=(2,-1),\alpha_3=(-3,2)\\
> \beta_1=(1,0),\beta_2=(0,1),\beta_3=(1,1)
> $$
>
> 问：是否存在 $\sigma\in L(R^2,R^2)$，使得 $\sigma(\alpha_i)=\beta_i(i=1,2,3)$。

假设存在。

$\alpha_3=-\alpha_1-\alpha_2$。

$\sigma(\alpha_3)=\sigma(-\alpha_1-\alpha_2)=-\sigma(\alpha_1)-\sigma(\alpha_2)$

也就是说 $\beta_3=-\beta_1-\beta_2$，即 $(1,1)=(-1,-1)$，矛盾。

所以不存在。