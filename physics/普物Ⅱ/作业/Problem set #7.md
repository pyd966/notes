# 第7次作业

## Chapter 14

> **1.** A capacitor consists of two parallel circular plates, each of radius $a$. We connect the capacitor to an AC emf such that the charge on the capacitor follows
>
> $$
> Q = Q_{0}\sin \omega t.
> $$
>
> Calculate the displacement current density $j_{d}$, the total displacement current $i_{d}$, and the magnetic field $B$ at a distance $r < a$ from the axis, assuming $\omega a \ll c$. Here we ignore the boundary effect and assume the electric field inside the capacitor to be uniform.

$$
E=\dfrac{\sigma}{\epsilon_0}=\dfrac{Q}{\pi a^2\epsilon_0}=\dfrac{Q_0\sin\omega t}{\pi\epsilon_0a^2}\\
j_d=\epsilon_0\dfrac{\partial E}{\partial t}=\dfrac{Q_0\omega\cos\omega t}{\pi a^2}\\
i_d=\iint j_ddA=Q_0\omega\cos\omega t\\
2\pi rB=\mu_0\oint Bds=\mu_0\iint j_ddA=\mu_0\dfrac{r^2}{a^2}Q_0\omega\cos\omega t
$$

So $B=\dfrac{\mu_0r}{2\pi a^2}Q_0\omega\cos\omega t$

> **3.** A steady current $i$ is flowing through a long cylindrical lead which has a radius $a$ and resistivity $\rho_{e}$, and we assume that the current is uniformly distributed at the cross section and the electric field is also uniform inside the lead. Neglecting the magnetic field of the return circuit, calculate the following quantities:
>
> (a) The magnitudes and directions of $\mathbf{E}$, $\mathbf{B}$ and the Poynting vector $\mathbf{S}$ at a distance $r < a$ from the central axis.
>
> (b) For any point $r$ inside the lead, verify the continuity equation
>
> $$
> \nabla \cdot \mathbf{S} + \frac{\partial u}{\partial t} = -\rho_{e}J^{2} = -\mathbf{j}\cdot \mathbf{E},
> $$
>
> where $J = |\mathbf{j}|$ is the magnitude of the current density.

(a)

Suppose the direction of current to be $+\hat z$, and the radius $+\hat r$, the angular (by right hand rule) $+\hat\phi$

$$
\vec E=\rho_e\vec j=\rho_e\dfrac{i}{\pi a^2}\hat z
$$

Take a circular route at radius $r$, 

$$
2\pi rB=\oint\vec B\cdot d\vec s=\mu_0\iint(\vec j+\epsilon_0\dfrac{\partial\vec E}{\partial t})d\vec A=\dfrac{\mu_0ir^2}{a^2}
$$

So $\vec B=\dfrac{\mu_0ir}{2\pi a^2}\hat\phi$

$$
\vec S=\dfrac1{\mu_0}\vec E\times\vec B=-\dfrac{\rho_ei^2r}{2\pi^2a^4}\hat r
$$

(b)

$u=\dfrac12\epsilon_0E^2+\dfrac1{2\mu_0}B^2$

$\dfrac{\partial u}{\partial t}=0$

$\nabla\cdot\vec S=(\dfrac{\partial}{\partial x}\hat x+\dfrac{\partial}{\partial y}\hat y+\dfrac{\partial}{\partial z}\hat z)(-\dfrac{\rho_ei^2x}{2\pi^2a^4}\hat x-\dfrac{\rho_ei^2y}{2\pi^2a^4}\hat y)=-\dfrac{\rho_ei^2}{\pi^2a^4}=-\rho_eJ^2$


> **4.** A capacitor has a spherical shape, with inner shell radius $r_{1}$ and outer shell radius $r_{2}$. Initially it is at rest and a charge $+Q$ ($-Q$) is uniformly distributed at the inner (outer) shell. A uniform magnetic field $\mathbf{B}$, produced by a long solenoid coaxial with the $z$ axis that encloses the capacitor, points along $+z$ initially, and later it is slowly removed. The two shells are insulating, with the charges fixed on them; they are rigidly joined and can turn freely about the $z$ axis, with moment of inertia $I$. Neglect the magnetic field produced by the rotating shells themselves. Find the final angular velocity, with its sense relative to $+z$.

$$
\begin{aligned}
2\pi rE&=\oint\vec E\cdot d\vec s\\
&=-\dfrac{d\Phi_r}{dt}\\
&=-\pi r^2\dfrac{dB}{dt}
\end{aligned}
$$

So $\vec E=-\dfrac{r}{2}\dfrac{dB}{dt}\hat\phi=-\dfrac{R\sin\theta}{2}\dfrac{dB}{dt}\hat\phi$

$dq=\sigma dS=\dfrac{Q}{4\pi R^2}\cdot R^2\sin\theta d\theta d\phi=\dfrac{Q}{4\pi}\sin\theta d\theta d\phi$

$$
\tau_{in}=\int(r_1\sin\theta)dqE=\int(r_1\sin\theta)(\dfrac{Q}{4\pi}\sin\theta d\theta d\phi)(-\dfrac{r_1\sin\theta}{2}\dfrac{dB}{dt})=-\dfrac{Qr_1^2}{3}\dfrac{dB}{dt}
$$

Similarily, $\tau_{out}=\dfrac{Qr_2^2}{3}\dfrac{dB}{dt}$

$\tau=\tau_{in}+\tau_{out}=\dfrac Q3(R_2^2-R_1^2)\dfrac{dB}{dt}$

$L_z=0+\int_i^{f}\tau dt=-\dfrac{QB_0}{3}(r_2^2-r_1^2)$

$\omega_z=\dfrac{L_z}{I}=-\dfrac{QB_0}{3I}(r_2^2-r_1^2)\hat z$