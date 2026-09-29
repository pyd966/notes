# 第三次作业

## 第5章

> **3.** Consider again the example of a point charge $Q$ located outside a thin spherical conducting shell of radius $R$. The distance from the point charge to the center of the shell is $d$. This time, the spherical shell is not grounded, and instead it has a total charge of $Q_0$. Calculate the force exerted on the point charge by the shell.

When the shell is grounded, by the method of images, we know the image charge sits at $d'=\dfrac{R^2}{d}$, with charge $q'=-\dfrac{RQ}{d}$.

With Gauss' Law, we know the charge on the grounded shell is $q'$.

Construst another case, where charge $Q_0-q'$ uniformly distributed on the shell. This will change the potential of the shell, but it's still equipotential.

Combine the two cases we constructed above, this is a solution to the original problem, so it's the only solution.

For the image charge,

$\vec F_1=\dfrac{1}{4\pi\epsilon_0}\dfrac{Qq'}{(d-d')^2}(-\hat r)=-\dfrac1{4\pi\epsilon_0}\dfrac{Q^2Rd}{(d^2-R^2)^2}\hat r$

For charges uniformly distributed on the shell, they're equivalent to a point charge at centre,

$\vec F_2=\dfrac{1}{4\pi\epsilon_0}\dfrac{Q(Q-q')}{d^2}(-\hat r)=\dfrac{1}{4\pi\epsilon_0}\dfrac{Q(Q_0+\frac RdQ)}{d^2}\hat r$

So $\vec F=\vec F_1+\vec F_2=\dfrac1{4\pi\epsilon_0}(\dfrac{QQ_0}{d^2}+\dfrac{Q^2R}{d^3}-\dfrac{Q^2Rd}{(d^2-R^2)^2})\hat r$

> **4.** A point charge $Q$ is located at $(a,a,0)$, where $a > 0$. A grounded conductor fills the whole region where $x<0$ or $y<0$ (or both), so that the charge lies in the empty region $x>0$, $y>0$. Calculate the force exerted on the point charge by the conductor. (Hint: the two conducting walls meet along the $z$ axis, and more than one image charge is needed — see rule 3 above.)

We place 3 image charges, at $(-a,a,0)$ with $-Q$, at $(-a,-a,0)$ with $Q$, at $(a,-a,0)$ with $-Q$.

It's trivial to verify at $x=0$ or $y=0$ the potential is $0$.

Due to uniqueness theroem of electrostatic, the electric field can be seen as provoked by these $4$ charges.

$\vec F_1=-\dfrac{1}{4\pi\epsilon_0}\dfrac{Q^2}{4a^2}\hat x$

$\vec F_2=\dfrac1{4\pi\epsilon_0}\dfrac{\sqrt2Q^2}{16a^2}(\hat x+\hat y)$

$\vec F_3=-\dfrac1{4\pi\epsilon_0}\dfrac{Q^2}{4a^2}\hat y$

$\vec F=\vec F_1+\vec F_2+\vec F_3=-\dfrac1{4\pi\epsilon_0}\dfrac{(4-\sqrt2)Q^2}{16a^2}(\hat x+\hat y)$

> **8.** Two conducting spheres of radii $R_1$ and $R_2$, where $R_1 > R_2$, are far apart compared with both radii and are joined by a long thin conducting wire. Together they carry a total charge $Q > 0$. Take $V=0$ at infinity, neglect the charge on the wire, and neglect the effect of each sphere on the other, so that the charge on each sphere is spread uniformly.
>
> (a) Find the charges $Q_1$ and $Q_2$ on the two spheres.
>
> (b) Find the ratio $\sigma_1 / \sigma_2$ of their surface charge densities and the ratio $E_1 / E_2$ of the field strengths just outside their surfaces. On which sphere is the field at the surface stronger? What does this suggest about the field near a sharp point of a conductor?

(a)

A sphere with charge $Q_0$, radius $R_0$ has potential $\dfrac{1}{4\pi\epsilon_0}\dfrac{Q_0}{R_0}$.

We know the two spheres are of same potential, $\dfrac1{4\pi\epsilon_0}\dfrac{Q_1}{R_1}=\dfrac1{4\pi\epsilon_0}\dfrac{Q_2}{R_2},Q_1+Q_2=Q$

So $Q_1=\dfrac{R_1Q}{R_1+R_2},Q_2=\dfrac{R_2Q}{R_1+R_2}$

(b)

$\sigma=\dfrac{Q}{4\pi R^2},\sigma_1=\dfrac{Q}{4\pi R_1(R_1+R_2)},\sigma_2=\dfrac{Q}{4\pi R_2(R_1+R_2)}$, so $\dfrac{\sigma_1}{\sigma_2}=\dfrac{R_2}{R_1}$

$E(r)=\dfrac{1}{4\pi\epsilon_0}\dfrac{Q}{r^2}$

$E_1(R_1)=\dfrac{\sigma_1}{\epsilon_0},E_2(R_2)=\dfrac{\sigma_2}{\epsilon_0}$

So $\dfrac{E_1}{E_2}=\dfrac{R_2}{R_1}<1,E_1<E_2$, field 2 is stronger.

So the sharp point of a conductor should provoke higher electric field.

## 第6章

> **5.** Consider a long wire of radius $a$ parallel to an infinite metallic plate. The plate is grounded $(V=0)$. The distance from the axis of the wire to the plate is $h$ $(h \gg a)$, and the space between them is vacuum. Calculate the capacitance per unit length. (Hint: use the method of images of Chapter 5: the image of a line charge $+\lambda$ at height $h$ above a grounded plane is a line charge $-\lambda$ at depth $h$, and the potential of a line charge is $V=-(\lambda/2\pi\epsilon_0)\ln r + \mathrm{const}$.)

Suppose the line carries density $\lambda$.

Construct the image of this line below the plane at distance $h$ with density $-\lambda$.

The total potential $V=-\dfrac{\lambda}{2\pi\epsilon_0}\ln r_++\dfrac{\lambda}{2\pi\epsilon_0}\ln r_-+C$.

The potential of the plate is the same as at infity, so its potential is $0$, $C=0$.

Calculate the potential of the original line, $V=-\dfrac{\lambda}{2\pi\epsilon_0}\ln(a)+\dfrac{\lambda}{2\pi\epsilon_0}\ln (2h)=\dfrac{\lambda}{2\pi\epsilon_0}\ln\dfrac{2h}{a}$

So $\dfrac{C}{L}=\dfrac{\lambda}{V}=\dfrac{2\pi\epsilon_0}{\ln(2h/a)}$

> **7.** Two long rods with the same cross-sectional area $S$, made of materials with conductivities $\sigma_1$ and $\sigma_2$, are joined end to end along the $x$ axis. A steady current $I > 0$ flows in the $+x$ direction, from rod 1 into rod 2. Assume that the current density is uniform over every cross-section of each rod, and take the permittivity of both materials to be $\epsilon_0$.
>
> (a) Find the electric field in each rod. Why can the fields differ when the current is the same?
>
> (b) Find the free charge $Q$ on the interface between the two rods. For which ordering of $\sigma_1$ and $\sigma_2$ is $Q$ positive?

(a)

$R=\rho\dfrac{L}{S},E=\dfrac{U}{L}=\dfrac{IR}{L}=\dfrac{I}{\sigma S}$.

So $E_1=\dfrac{I}{S\sigma_1},E_2=\dfrac{I}{S\sigma_2}$

The current is the same, but the resistance is not the same. To make their current the same, the rod with higher resistance should be put in larger electric field.

(b)

Take a Gauss surface, $\dfrac{Q}{\epsilon_0}=(E_2-E_1)S$

So $Q=\epsilon_0S(E_2-E_1)=\epsilon_0I(\dfrac1\sigma_2-\dfrac1\sigma_1)$. When $\sigma_1>\sigma_2$, $Q$ is positive.

> **8.** A metal hemisphere of radius $a$ is buried in level ground with its flat face in the ground's surface. The ground is a uniform material of conductivity $\sigma$, much smaller than that of the metal, and the air above it does not conduct. A steady current $I$ flows from the hemisphere into the ground and returns through an electrode very far away; in the ground it flows radially outward from the center of the flat face. Let $r$ be the distance from that center, and take the potential to be zero far away.
>
> (a) Find the current density $\mathbf{j}$ and the electric field $\mathbf{E}$ in the ground at a distance $r > a$, and the resistance $R$ between the hemisphere and the distant electrode.
>
> (b) A person stands on the ground with one foot at distance $r$ from the center and the other at distance $r+s$, on the same radial line. Find the potential difference $V(r)-V(r+s)$ between the two feet. Why is it safer to keep the feet close together near such an electrode?

(a)

$\vec j(r)=\dfrac{I}{2\pi r^2}\hat r,\vec E(r)=\dfrac{\vec j(r)}{\sigma}=\dfrac{I}{2\pi\sigma r^2}\hat r$

$V(a)=\int_a^{+\infty}E(r)dr=\dfrac{I}{2\pi\sigma a}$

$R=\dfrac{V(a)}{I}=\dfrac1{2\pi\sigma a}$

(b)

$V(r)=\int_r^{+\infty}E(r')dr'=\dfrac{I}{2\pi\sigma r}$

$V(r)-V(r+s)=\dfrac I{2\pi\sigma}(\dfrac1r-\dfrac1{r+s})$

When $r$ is small, $V(r)-V(r+s)$ increases rapidly with $s$ increasing, so it's safer to keep $s$ small.

## 第7章

> **3.** Consider the Wheatstone bridge as shown in the figure. Take $I$ positive from C to D.
>
> (a) Compute the current $I$ going through the resistor $r_g$.
>
> (b) What is the condition for $I$ to be zero?



> **5.** Consider the RC circuit shown in the figure, with an ideal emf. The capacitor is uncharged when the switch is closed at $t=0$. Let $Q$ be the magnitude of the charge on either plate. Find the time dependence of $Q$ for $t>0$, and its limit as $t \to \infty$.



> **9.** A parallel-plate capacitor in vacuum has plates of area $S$. The lower plate is fixed, and the upper plate can be moved perpendicular to the plates; $x$ is the separation between them. Neglect edge effects. The upper plate is moved slowly, so that its kinetic energy and any heat produced can be neglected. Let $F$ be the electric force on the upper plate, taken positive in the direction of increasing $x$.
>
> (a) The plates are isolated and carry charges $+q$ and $-q$. Find the stored energy $U(x)$, and from the change of $U$ in a small displacement $dx$, find $F$.
>
> (b) The plates are instead connected to an ideal battery that keeps their potential difference at $V$. Find $U(x)$, and the work $dW_b$ done by the battery when $x$ increases by $dx$. Explain why $F=-dU/dx$ now gives the wrong sign, find $F$ from energy conservation, and compare with (a).

