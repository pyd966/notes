# Problem set #1

## chap01

> **3.** An electric dipole $\mathbf{p}_2$ is located at position $\mathbf{r}$ relative to a second dipole $\mathbf{p}_1$, with $r$ much larger than the size of either dipole. Find the force exerted on $\mathbf{p}_2$ by $\mathbf{p}_1$, expressed in terms of $\mathbf{p}_1$, $\mathbf{p}_2$ and $\mathbf{r}$. (Hint: write $\mathbf{p}_2$ as a pair of charges $\pm q_2$ at $\mathbf{r}\pm \mathbf{d}_2 / 2$, and expand the field of $\mathbf{p}_1$ to first order in $\mathbf{d}_2$, as was done for the dipole field itself in Section 1.4.)

Let's first compute electric field.

$$
\begin{aligned}
E(\vec r\pm\dfrac12\vec d_2)&=\dfrac1{4\pi\epsilon_0}[3(\vec r\pm\dfrac12\vec d_2)^{-5}(\vec p_1\vec r\pm\dfrac12\vec p_1\vec d_2)(\vec r\pm\dfrac12\vec d_2)-(\vec r\pm\dfrac12\vec d_2)^{-3}\vec p_1]\\
\end{aligned}
$$

where $(\vec r\pm\dfrac12\vec d_2)^{-5}\approx r^{-5}(1\mp\dfrac{5\vec r\vec d_2}{2r^2}),(\vec r\pm\dfrac12\vec d_2)^{-3}\approx r^{-3}(1\mp\dfrac{3\vec r\vec d_2}{2r^2})$

so

$$
\begin{aligned}
E(\vec r\pm\dfrac12\vec d_2)&\approx\dfrac1{4\pi\epsilon_0r^5}[3(\vec p_1\vec r\pm\dfrac12\vec p_1\vec d_2\mp\dfrac{5\vec r\vec d_2}{2r^2}\vec p_1\vec r)(\vec r\pm\dfrac12\vec d_2)-r^2(1\mp\dfrac{3\vec r\vec d_2}{2r^2}\vec p_1)]\\
\end{aligned}
$$

so

$$
E(\vec r+\dfrac12\vec d_2)-E(\vec r-\dfrac12\vec d_2)=\dfrac3{4\pi\epsilon_0r^5}[(\vec p_1\vec d_2)\vec r-\dfrac{5(\vec p_1\vec r)(\vec r\vec d_2)}{r^2}\vec r+(\vec p_1\vec r)\vec d_2+(\vec r\vec d_2)\vec p_1]
$$

so

$$
\begin{aligned}
F_{tot}&=q_2(E(\vec r+\dfrac12\vec d_2)-E(\vec r-\dfrac12\vec d_2))\\
&=\dfrac{3}{4\pi\epsilon_0r^4}[(\vec p_1\vec p_2)\hat r-5(\vec p_1\hat r)(\vec p_2\hat r)\hat r+(\vec p_1\hat r)\vec p_2+(\vec p_2\hat r)\vec p_1]
\end{aligned}
$$

> **7.** A thin rod occupies the half-line $z\geq 0$ and carries a uniform linear charge density $\lambda >0$; such a rod is called semi-infinite. The point $P$ lies in the plane $z = 0$, at a perpendicular distance $d$ from the end of the rod.
>
> (a) Calculate both the component of $\mathbf{E}$ perpendicular to the rod and the component parallel to it at $P$, taking $\hat{z}$ as positive for the parallel one, and show that $\mathbf{E}$ makes an angle of $45^{\circ}$ with the axis of the rod no matter how large or small $d$ is.
>
> (b) Without evaluating any new integral, use the result of (a) to obtain the electric field at a perpendicular distance $d$ from an infinitely long rod carrying the same $\lambda$.

(a)

Suppose point $P$ sits on the positive half of $x$-axis.

Take one point $A$ on the rod, suppose $\angle APO=\theta$, then $dz=\dfrac{d}{\cos^2\theta}d\theta$

Then

$$
\begin{aligned}
\vec E_P&=\int_0^{\pi/2}\dfrac{1}{4\pi\epsilon_0}\dfrac{\lambda dz}{(d/\cos\theta)^2}(-\sin\theta\hat z+\cos\theta\hat x)\\
&=\dfrac{\lambda}{4\pi\epsilon_0d}\int_0^{\pi/2}d\theta(-\sin\theta\hat z+\cos\theta\hat x)\\
&=\dfrac{\lambda}{4\pi\epsilon_0d}\hat x-\dfrac{\lambda}{4\pi\epsilon_0d}\hat z
\end{aligned}
$$

Because the magnitude of the two components are equal, so the angle of $E$ with repect to the $z$-axis will be $45^\circ$.

(b)

An infinitely long rod can be considered as 2 semi-inifinite rods.

$\vec E=\dfrac{\lambda}{4\pi\epsilon_0d}((\hat x-\hat z)+(\hat x+\hat z))=\dfrac{\lambda}{2\pi\epsilon_0d}\hat x$

> **10.** The atoms of Feynman's quote are held together by the electric force, and they are neutral to an astonishing accuracy. This exercise estimates both statements. Use $e = 1.60 \times 10^{-19}\ \mathrm{C}$, $\frac{1}{4 \pi \epsilon_0} = 8.99 \times 10^9\ \mathrm{N} \cdot \mathrm{m}^2 / \mathrm{C}^2$, $G = 6.67 \times 10^{-11}\ \mathrm{N} \cdot \mathrm{m}^2 / \mathrm{kg}^2$, $m_e = 9.11 \times 10^{-31}\ \mathrm{kg}$, $m_p = 1.673 \times 10^{-27}\ \mathrm{kg}$ and $m_H = 1.674 \times 10^{-27}\ \mathrm{kg}$.
>
> (a) Calculate the ratio of the electrostatic force to the gravitational force between one electron and one proton, and explain why this ratio does not depend on how far apart they are.
>
> (b) Suppose the two charges did not cancel exactly, the electron carrying $-e(1 + \delta)$ while the proton carries $+e$, so that a hydrogen atom would carry a net charge $-\delta e$. Find the value of $|\delta |$ for which the electrostatic repulsion between two hydrogen atoms would exactly cancel their gravitational attraction, and show that this value is also independent of their separation.

(a)

$F_E=\dfrac{1}{4\pi\epsilon_0}\dfrac{e^2}{d^2},F_G=G\dfrac{m_em_p}{d^2}$

So their ratio $\dfrac{F_E}{F_G}=\dfrac{e^2}{4\pi\epsilon_0Gm_em_p}=2.264\times10^{39}$ is independent of $d$.

(b)

$F_E=\dfrac1{4\pi\epsilon_0}\dfrac{\delta^2e^2}{d^2},F_G=G\dfrac{m_H^2}{d^2}$

Let $F_E=F_G$, $\dfrac{1}{4\pi\epsilon_0}\delta^2e^2=Gm_H^2$, so $|\delta|=\dfrac{\sqrt{4\pi\epsilon_0Gm_H^2}}{e}=9.01\times10^{-19}$

## chap02

> **4.** Two uniformly charged spherical shells are both centered at the origin, whose radii are $R_1$ and $R_2$ $(R_1 < R_2)$. Given that the surface charge density is $+\sigma$ $(\sigma > 0)$ for the outer shell, and that the electric field is zero for any point located outside the outer shell, please calculate the following quantities:
>
> (a) The surface charge density of the inner shell
>
> (b) The magnitude of the electric field for a point located in between the two shells $(R_1 < r < R_2)$
>
> (c) The magnitude of the electric field inside the inner shell $(r < R_1)$

(a)

Suppose the density of the inner shell is $\sigma'$。

Take a shell outside the outer shell as the Gauss surface, $\dfrac{\sigma(4\pi R_2^2)+\sigma'(4\pi R_1^2)}{\epsilon_0}=\oint0dS=0$, so $\sigma'=-\dfrac{R_2^2}{R_1^2}\sigma$

(b)

Due to symmetry, the magnitude is the same at radius $r$, and the direction is $\hat r$.

Take a shell with radius $r$ as the Gauss surface, $\dfrac{\sigma'(4\pi R_1^2)}{\epsilon_0}=\oint\vec E\cdot dS=E\cdot\oint \hat E\cdot dS=4\pi r^2E$, so $E=-\dfrac{R_2^2}{r^2\epsilon_0}\sigma$, its magnitude is $|E|=\dfrac{R_2^2}{r^2\epsilon_0}\sigma$

(c)

Similarily, 

$\dfrac{0}{\epsilon_0}=\oint\vec E\cdot dS=E\oint\hat E\cdot dS$, so $E=0$

> **6.** A point charge $q > 0$ and an imaginary cube of side $a$ are given. The normal of every face of the cube points out of the cube.
>
> (a) The charge sits at the center of the cube. Find the electric flux through each face.
>
> (b) The charge now sits at one corner of the cube. Find the electric flux through each of the six faces. (Hint: consider the eight identical cubes that share this corner.)

(a)

Due to symmetry, the electric flux through each face is the same.

First, we compute the total flux.

$\Phi_{tot}=\oint\vec E\cdot dS=\dfrac{q}{\epsilon_0}$

So through each face $\Phi_{each}=\dfrac16\Phi_{tot}=\dfrac{q}{6\epsilon_0}$

(b)

Consider the eight idential cubes sharing this corner, take its outer surface as our Gauss surface, $\Phi_{tot}=\dfrac{q}{\epsilon_0}$

Then for the three faces that do not share this corner, $\Phi_1=\dfrac1{24}\Phi_{tot}=\dfrac{q}{24\epsilon_0}$.

For the three faces that share this corner, it's obvious $\Phi_2=0$.



> **9.** In a simple model of a p-n junction, the charge density depends only on $z$: $\rho (z) = -\rho_0$ for $-a< z< 0$, $\rho (z) = +\rho_0$ for $0< z< a$, and $\rho (z) = 0$ for $|z| > a$, where $\rho_0 > 0$. The charged layers extend infinitely in the $x$ and $y$ directions, and there is no other charge.
>
> (a) Treat the charge as a stack of thin charged plates, and use the field of an infinitely large charged plate to show that $\mathbf{E} = 0$ for $|z| > a$. Explain why a pillbox placed symmetrically about $z = 0$, as used for a single plate, gives no information here.
>
> (b) Using a pillbox with one end in the region $z< -a$, find $\mathbf{E}(z)$ for $-a< z< a$. Where is the magnitude of the field largest, and what is its value there?

(a)

An infinitely large plate of density $\sigma$ provokes an electric field $E=\dfrac{\sigma}{2\epsilon_0}$.

For a point $A$ sits at $|z|>a$, $\vec E=\int_0^a\dfrac{\rho_0dz}{2\epsilon_0}+\int_{-a}^0\dfrac{-\rho_0dz}{2\epsilon_0}=0$

Explain:

Due to symmetry, we know the direction of electric field is along (or against) $\hat z$, but we don't know exactly which direction.

If they happen to be in the opposite direction, they will cancel each other in our pillbox example, so this gives no information.

(b)

Suppose the area of its bottom is $S$, and the top sits at $z$.

We first calculate $-a<z<0$.

$\dfrac{-\rho_0(z+a)S}{\epsilon_0}=\oint\vec E\cdot dS=0+ES$, so $\vec E(z)=\dfrac{-\rho_0(z+a)}{\epsilon_0}$

Similarity, if $0<z<a$, then $\vec E(z)=-\dfrac{\rho_0(a-z)}{\epsilon_0}$

Together, $\vec E(z)=-\dfrac{\rho_0}{\epsilon_0}(a-|z|)$.

So $|E(0)|$ is largest, $|E(0)|=\dfrac{\rho_0a}{\epsilon_0}$.