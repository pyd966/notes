# Homework #5

## Chapter 10

> **1.** Consider a circular ring of radius $R$ placed in the $xy$-plane and its center located at the origin. The ring carries a current $I$, flowing counterclockwise when viewed from the positive $z$ axis.
>
> (a) For a point $\mathbf{r} = (r\sin \theta ,0,r\cos \theta)$ located in the $xz$-plane, show that for $r\gg R$ the magnetic field has the following form:
>
> $$
> \mathbf{B} = -\frac{\mu_0\mathbf{\mu}}{4\pi r^3} +\frac{3\mu_0(\mu\cdot\mathbf{r})\mathbf{r}}{4\pi r^5},
> $$
>
> where the magnetic dipole moment is
>
> $$
> \mu = I\pi R^2\hat{z}.
> $$
>
> (b) What is the potential energy of a magnetic dipole $\mu '$ if it is placed at $\mathbf{r}(r\gg R)$?

(a)

Consider a differential element at $\vec s=(R\cos\varphi,R\sin\varphi,0)$, then $d\vec s'=(-R\sin\varphi d\varphi,R\cos\varphi d\varphi,0)$.

By $R<<r$, we obtain $|\vec s|<<|\vec r|$, thus

$$
\begin{aligned}
d\vec B&=\dfrac{\mu_0}{4\pi}\cdot\dfrac{I\cdot d\vec s\times(\vec r-\vec s)}{|\vec r-\vec s|^3}\\
&\approx\dfrac{\mu_0I}{4\pi}\cdot(d\vec s\times(\vec r-\vec s))\cdot r^{-3}(1+\dfrac{3\vec r\cdot\vec s}{2r^2})\\
\end{aligned}
$$

So

$$
\begin{aligned}
\vec B&=\oint d\vec B\\
&=\dfrac{\mu_0I}{4\pi r^3}\oint(d\vec s\times(\vec r-\vec s))(1+\dfrac{3\vec r\cdot\vec s}{r^2})\\
&=\dfrac{\mu_0I}{4\pi r^3}[\oint(d\vec s\times(-\vec s))(1+\dfrac{3Rr\sin\theta\cos\varphi}{r^2})+\oint(d\vec s\times\vec r)(\dfrac{3Rr\sin\theta\cos\varphi}{r^2})\\\
&\approx\dfrac{\mu_0I}{4\pi r^3}[\oint R^2d\varphi\hat z+Rr\oint\cos\varphi d\varphi(\cos\theta\hat x-\sin\theta\hat z)\dfrac{3Rr\sin\theta\cos\varphi}{r^2}]\\
&=\dfrac{\mu_0I}{4\pi r^3}\cdot\pi R^2(3\sin\theta\cos\theta\hat x+(2-3\sin^2\theta)\hat z)\\
&=\dfrac{\mu_0}{4\pi r^3}[3(\mu\cdot\hat r)\hat r-\vec\mu]\\
&=-\dfrac{\mu_0\vec\mu}{4\pi r^3}+\dfrac{3\mu_0(\vec\mu\cdot\vec r)\vec r}{4\pi r^5}
\end{aligned}
$$

(b)

$$
\begin{aligned}
U&=-\vec\mu'\cdot\vec B\\
&=\dfrac{\mu_0(\vec\mu\cdot\vec\mu')}{4\pi r^3}-\dfrac{3\mu_0(\vec\mu\cdot\vec r)(\vec r\cdot\vec\mu')}{4\pi r^5}
\end{aligned}
$$

## Chapter 11

> **1.** An infinitely long conducting wire carries a current $I$, and a rectangular loop lies in the same plane as the wire and moves away from it perpendicular to the wire at constant speed $v$, as shown in Fig. 11.6. The loop has side $a$ parallel to the wire, width $b$, and its near side is a distance $c$ from the wire. Calculate the induced emf in the rectangle.

By Ampere's Law, consider a ring outside the wire with radius $r$

$$
2\pi rB=\oint\vec B\cdot d\vec s=\mu_0I
$$

So $B=\dfrac{\mu_0I}{2\pi r}$

In time $dt$, we calculate corresponding $d\Phi$

$$
\begin{aligned}
d\Phi&=\int_{c+b}^{c+b+vdt}\dfrac{\mu_0I}{2\pi r}dr\cdot a-\int_c^{c+vdt}\dfrac{\mu_0I}{2\pi r}dr\cdot a\\
&=\dfrac{\mu_0Ia}{2\pi}(\ln(1+\dfrac{vdt}{c+b})-\ln(1+\dfrac{vdt}{c}))\\
&\approx\dfrac{\mu_0Ia}{2\pi}(\dfrac{vdt}{c+b}-\dfrac{vdt}{c})
\end{aligned}
$$

So $\mathcal{E}=\dfrac{d\Phi}{dt}=\dfrac{abv\mu_0I}{2\pi c(b+c)}$, clock-wise.

> **3.** A long solenoid with radius $r_1 = 5 \mathrm{cm}$ and $n = 1000$ turns per meter is oriented with its axis along the $\hat{z}$-direction. A current through the solenoid varies with time according to:
>
> $$
> I(t) = I_0\sin (\omega t),
> $$
>
> where $I_0 = 2 \mathrm{A}$, $\omega = 100\pi$ rad/s, and we define the counter-clockwise direction, as viewed from the $+z$ end of the axis, to be positive for the solenoid current, and likewise for the emf induced in the loop and for the current it carries.
>
> A circular conducting loop of radius $r_2 = 3 \mathrm{cm}$ and resistance $R = 0.5 \Omega$ is placed inside the solenoid, with its plane perpendicular to the solenoid's axis.
>
> (a) Find the magnetic field $B(t)$ inside the solenoid as a function of time.
>
> (b) Calculate the induced emf in the loop as a function of time.
>
> (c) Calculate the maximum induced current in the loop.
>
> (d) Sketch a graph showing $I(t)$ in the solenoid and the induced current in the loop over one complete period.

(a)

$B(t)=\mu_0I(t)n=\mu_0nI_0\sin(\omega t)=8\pi\times10^{-4}\sin(100\pi t)$

(b)

$\mathcal{E}=-\dfrac{d\Phi}{dt}=-\pi r_2^2\dfrac{dB}{dt}=-72\pi^3\times10^{-6}\cos(100\pi t)$

(c)

$i=\dfrac{\mathcal{E}}{R}=-144\pi^3\times10^{-6}\cos(100\pi t)$

So $i_{max}=1.44\pi^3\times10^{-4}A$

(d)

Ignored.

> **4.** A uniform magnetic field is confined to a long cylindrical region of radius $R$. The field points out of the page and varies with time according to
>
> $$
> B(t) = B_{0}e^{-t / \tau},
> $$
>
> where $B_{0}$ and $\tau$ are positive constants. There are no charges nearby, so the only electric field is the one induced by the changing $\mathbf{B}$.
>
> (a) Find the magnitude of the induced electric field $E(r,t)$ at a distance $r$ from the axis for both $r< R$ (inside the magnetic field region) and $r > R$ (outside the magnetic field region).
>
> (b) Sketch the spatial dependence of $E(r)$ at a fixed time $t$. At what radius is the electric field maximized?
>
> (c) A charged particle with charge $q$ and mass $m$ is released from rest at $t = 0$ at a distance $r_{0}$ from the axis, and is held in a frictionless insulating circular tube of radius $r_{0}$ so that its motion is confined to the $r = r_{0}$ orbit. Find the speed of the particle as $t\to \infty$ and the sense in which it then circulates as seen on the page (discuss both $r_{0}< R$ and $r_{0} > R$ cases).

(a)

Take a ring with radius $r$, by symmetry the magnitude of induced electric field is the same.

$$
2\pi rE=\oint\vec E\cdot d\vec s=\mathcal{E}=-\dfrac{d\Phi}{dt}=\begin{cases}
\pi r^2\cdot\dfrac1\tau B_0e^{-t/\tau},&r<R\\
\pi R^2\cdot\dfrac1\tau B_0e^{-t/\tau},&r>R
\end{cases}
$$

So

$$
E(r,t)=\begin{cases}
\dfrac{B_0}{2\tau}re^{-t/\tau},&r<R\\
\dfrac{B_0R^2}{2\tau r}e^{-t/\tau},&r>R
\end{cases}
$$

(b)

Ignored.

It's obvious for fixed $t$, $E_{max}=E(R,t)=\dfrac{B_0R}{2\tau}e^{-t/\tau}$

(c)

When $t\to\infty$,

$$
v=\int_0^{+\infty}\dfrac1mE(r_0,t)qdt=\begin{cases}
\dfrac{B_0qr_)}{2m},&r_0<R\\
\dfrac{B_0qR^2}{2mr_0},&r_0>R
\end{cases}
$$

counter-clockwise is positive.

> **7.** A thin conducting disk of radius $a$ turns with constant angular speed $\omega$ about its axis, the $z$ axis, counterclockwise as seen from $+z$, in a uniform magnetic field $\mathbf{B} = B\hat{z}$ with $B > 0$. One sliding contact touches the axle at the center of the disk and another touches its rim; the two are joined by a stationary external wire through a resistor $R$. Neglect all other resistance, all friction, and the self-inductance of the circuit.
>
> (a) Using the magnetic force on a positive charge carried round with the disk, find the emf between the center and the rim, and say which of the two is at the higher potential.
>
> (b) Find the current, the torque that the magnetic field exerts on the disk, and the torque that must be applied to keep $\omega$ constant. Show that the mechanical power supplied equals the power dissipated in $R$.
>
> (c) The magnetic flux through the disk does not change as it turns. Consider instead, for $0< t< 2\pi /\omega$, the closed path made of the external circuit, a radius drawn on the disk that passed the rim contact at $t = 0$ and turns with the disk, and the arc of the rim that this radius has swept since then, from the contact to the end of the radius. Find the rate at which the flux through this path changes, and compare it with your answer to (a).

(a)

Consider a charge $+q$ at raidus $r$, its magnetic force $F_B=Bq\omega r$.

So $\mathcal{E}=\int_0^aF_Bdr=\dfrac{B\omega a^2}{2}$, and the rim is higher.

(b)

Current $I=\dfrac{\mathcal{E}}{R}=\dfrac{B\omega a^2}{2R}$.

Torque

$$
\begin{aligned}
\tau&=\int_0^a\int_0^{2\pi}\vec r\times(\dfrac{d\theta}{2\pi}BIdr\hat r)\\
&=-\dfrac{BIa^2}{2}\hat z\\
&=-\dfrac{B^2\omega a^4}{4R}\hat z
\end{aligned}
$$

So $\tau'=-\tau=\dfrac{B^2\omega a^4}{4R}\hat z$ must be applied.

$P_{F}=\tau\dfrac{d\theta}{dt}=\dfrac{B^2\omega^2a^4}{4R}$

$P_R=I^2R=\dfrac{B^2\omega^2a^4}{4R}$

So $P_F=P_R$

(c)

$$
\dfrac{d\Phi}{dt}=B\dfrac{dS}{dt}=\dfrac{B\omega a^2}{2}
$$

This is the same as (a).
