## 习题

> 21. 已知：
>
> 平面 $\pi: x-2y-2z+4=0$，直线 $L:\dfrac{x-1}{-1}=\dfrac y2=\dfrac{z+2}n$
>
> $(1)$ 求 $n$，使 $L\perp\pi$；
>
> $(2)$ 求 $n$，使 $L\parallel\pi$
>
> $(3)$ 当 $n=-2$ 时，求 $L$ 与 $\pi$ 之间的夹角
>
> $(4)$ 当 $n=-2$ 时，求 $L$ 与 $\pi$ 的交点，并求 $L$ 在 $\pi$ 上的投影线方程
>
> $(5)$ 求 $L$ 在各坐标平面上的投影线方程
>
> $(6)$ 当 $n=-2$ 时，求直线 $L_1$，使 $L_1$ 与 $L$ 关于平面 $\pi$ 对称；
>
> $(7)$ 求原点关于平面 $\pi$ 的对称点的坐标。

$(1)$

$\pi$ 的法向量 $\vec{n}=(1,-2,-2)$，$L$ 的方向向量 $\vec{l}=(-1,2,n)$。

由 $L\perp\pi$ 可知 $\vec{n}\parallel\vec{l}$，故 $\dfrac1{-1}=\dfrac{-2}2=\dfrac{-2}n$，故 $n=2$。

$(2)$

由 $L\parallel\pi$ 可知 $\vec{n}\perp\vec{l}$，故 $\vec{n}\cdot\vec{l}=0$，解得 $n=-\dfrac52$。

$(3)$

设夹角为 $\theta$，则 $\dfrac\pi2-\theta=\arccos\dfrac{|\vec n\cdot\vec l|}{|\vec n||\vec l|}=\arcsin\dfrac19$

$(4)$

解方程组

$$
\begin{cases}
x-2y-2z+4&=0\\
2x+y-2&=0\\
2x-z-4&=0\\
\end{cases}
$$

得交点为 $P_0=(-8,18,-20)$。

记投影线上另一点为 $P_1$，则 $\begin{cases}\vec{P_0P_1}\cdot\vec n=0\\\vec{P_0P_1}=\vec{l}+\lambda\vec n\end{cases}$

最终解得 $\lambda=\dfrac19,\vec{P_0P_1}=(-\dfrac89,\dfrac{16}9,-\dfrac{20}9)$

所以直线方程：$\dfrac{x+8}{2}=\dfrac{y-18}{-4}=\dfrac{z+20}{5}$

$(5)$

先考虑 $xOy$ 平面。容易发现 $L$ 与之交于 $(-1,2,0)$。

类似 $(4)$ 可以得到直线方程为 $\begin{cases}\dfrac{x-1}{-1}=\dfrac{y}{2}\\z=0\end{cases}$

同理，在 $yOz$ 平面上的投影方程为 $\begin{cases}\dfrac{y}{2}=\dfrac{z+2}{n}\\x=0\end{cases}$

在 $xOz$ 平面上的投影方程为 $\begin{cases}\dfrac{x-1}{-1}=\dfrac{z+2}{n}\\y=0\end{cases}$

$(6)$

在 $(4)$ 中，我们知道 $L$ 与 $\pi$ 交于 $P_0=(-8,18,-20)$，在 $L$ 取一点 $P_2$ 使得 $\vec{P_0P_2}=\vec l$，过 $P_2$ 作 $P_2P_1\perp\pi$ 于 $P_1$，则 $\vec{P_0P_1}=(-\dfrac89,\dfrac{16}9,-\dfrac{20}9)$。

设 $P_2$ 关于 $\pi$ 的对称点为 $P_2'$，则 $\vec{P_0P_2'}=\vec{P_0P_2}+2\vec{P_2P_1}=(-\dfrac79,\dfrac{14}9,-\dfrac{22}9)$。

所以过 $P_0,P_2'$ 的直线即为所求，为 $\dfrac{x+8}{7}=\dfrac{y-18}{-14}=\dfrac{z+20}{22}$

$(7)$

设对称点为 $O'$，记 $OO'$ 与 $\pi$ 交于 $P=(x_1,y_1,z_1)$ 点。

则 $\vec{OP}=k\vec n$，且 $P$ 在 $\pi$ 上，可知

$$
\begin{cases}
x_1=k\\
y_1=-2k\\
z_1=-2k\\
x_1-2y_1-2z_1+4=0\\
\end{cases}
$$

知 $k=-\dfrac49$

所以 $\vec{OO'}=2\vec{OP}$，知 $O'=(-\dfrac89,\dfrac{16}9,\dfrac{16}9)$

> 23. 已知两个平面：
>
> $\pi_1:x-y-2z=2$，$\pi_2:x+2y+z=8$
>
> $(1)$ 求过 $\pi_1,\pi_2$ 的交线，且与 $\pi_3:x+y+z=0$ 垂直的平面的方程；
>
> $(2)$ 求 $\pi_1$ 与 $\pi_2$ 的平分面的方程

$(1)$

设平面为 $\pi_3:\lambda(x-y-2z-2)+\mu(x+2y+z-8)=0$，即 $\pi_3:(\lambda+\mu)x+(-\lambda+2\mu)y+(-2\lambda+\mu)z-2\lambda-8\mu=0$。

$\pi_3$ 法向量 $\vec n_3=(\lambda+\mu,-\lambda+2\mu,-2\lambda+\mu)$。

由题知，$\vec n_3\perp(1,1,1)$，可以取 $(\lambda,\mu)=(2,1)$。

此时 $\pi_3:3x+2y-3z-12=0$

$(2)$

同样可设平面为 $\pi_4:\lambda(x-y-2z-2)+\mu(x+2y+z-8)=0$，即 $\pi_4:(\lambda+\mu)x+(-\lambda+2\mu)y+(-2\lambda+\mu)z-2\lambda-8\mu=0$。

$\vec n_1=(1,-1,-2),\vec n_2=(1,2,1),\vec n_4=(\lambda+\mu,-\lambda+2\mu,-2\lambda+\mu)$。

由平分可知 $<\vec n_1,\vec n_4>=<\vec n_2,\vec n_4>$，

即 $\dfrac{|\vec n_1\cdot\vec n_4|}{|\vec n_1||\vec n_4|}=\dfrac{|\vec n_2\cdot\vec n_4|}{|\vec n_2||\vec n_4|}$，可以取 $(\lambda,\mu)=(1,-1)$ 或 $(1,1)$。

所以 $\pi_4:y+z-2=0$ 或 $\pi_4:2x+y-z-10=0$