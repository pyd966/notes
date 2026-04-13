# Problem set #6

## 1

1. Consider a particle with mass $m$ attached to a massless spring with the force constant $k$ (see the figure below). Now the particle undergoes an oscillating motion around its equilibrium position. The position of the particle measured from the equilibrium position is denoted by $x$ and the momentum of the particle is denoted by $p$.  
   (a) Suppose the total energy of the particle is $E$. Plot the trajectory of the particle on the $x-p$ plane. (Take $x$ for the horizontal axis and $p$ for the vertical axis.) The values at the intersection with $x$- and $p$-axes should also be given in terms of $m, k$, and $E$.  
   (b) Suppose this spring is a special spring whose force constant $k$ can be varied. It is known that, if we change the external parameter sufficiently slowly, the area surrounded by the trajectory of the periodic motion in the $x-p$ plane is unchanged ("adiabatic theorem"). Suppose the particle undergoes an oscillatory motion with the energy $E_{\mathrm{i}}$ at the beginning, and then we change the force constant from $k_{\mathrm{i}}$ to $k_{\mathrm{f}}$ very slowly. Derive the energy of the particle $E_{\mathrm{f}}$ at the final state.

![alt text](fig6-1.png)

(a)

$$
\dfrac12mv^2+\dfrac12kx^2=E\\
\dfrac{p^2}{2m}+\dfrac12kx^2=E\\
$$

(b)

Let $p=0$, we can obtain $x_0=\sqrt{\dfrac{2E}{k}}$

Caculate the area surrounded by the trajectory, $S=2\int_{-x_0}^{x_0}pdx=2\pi E\sqrt{\dfrac mk}$。

By the given theorem, $2\pi E_i\sqrt{\dfrac m{k_i}}=2\pi E_f\sqrt{\dfrac m{k_f}}$, so $E_f=E_i\sqrt{\dfrac{k_f}{k_i}}$

## 2

2. Consider a small cylinder with radius $r$ is having a pure rolling motion in a big hollow cylinder with radius $R$. If the rolling is limited to a small angle $\theta \ll 1$, the small cylinder will be in a harmonic oscillation:  
   (a) Calculate the potential energy of the small cylinder in $\theta$;  
   (b) Calculate the kinetic energy of the small cylinder in $d\theta/dt$;   
   (c) What is the period of the harmonic oscillation?

![alt text](fig6-2.png)

(a)

$$
E_p=(R-r)(1-\cos\theta)mg\approx\dfrac12\theta^2mg(R-r)
$$

(b)

Let $\omega=\dfrac{d\theta}{dt}$

$$
E_k=\dfrac12mv_{CM}^2+\dfrac12I\omega^2=\dfrac34m(R-r)^2\omega^2
$$

(c)

By conservation of energy,

$$
E_p+E_k=\dfrac12mg(R-r)\theta^2+\dfrac34m(R-r)^2\omega^2=C
$$

where $C$ is a constant.

So $T=\dfrac{2\pi}{\sqrt{\frac{3(R-r)}{2g}}}$

## 3

3. (a) Let $x_{1}(t)$ and $x_{2}(t)$ be solutions of $\ddot{x}^{2} + bx = 0$. Show that $x_{1}(t) + x_{2}(t)$ is not a solution to this equation.  
   (b) Consider a physical pendulum formed by a rigid body of mass $m$ with the pivot $P$ around it performs frictionless oscillations and which is at a distance $L$ from the center of mass CM, see the sketch. The moment of inertia of the rigid body is $I_{p}$ with respect to the pivot. Derive the equation obeyed by small oscillations and find their frequency $\omega$.

![alt text](fig6-3.png)

(a)

Suppose $x_1+x_2$ is a solution to this equation. Then

$$
\begin{cases}
\ddot x_1^2+bx_1=0\\
\ddot x_2^2+bx_2=0\\
((x_1+x_2)'')^2+b(x_1+x_2)=0
\end{cases}
$$

So $\ddot x_1^2+2\ddot x_1\ddot x_2+\ddot x_2^2=\ddot x_1^2+\ddot x_2^2$, which means $\ddot x_1\ddot x_2=0$. Normally, this is not true, so $x_1+x_2$ is not a solution.

(b)

$$
E_p=mgL(1-\cos\theta)\approx \dfrac12mgL\theta^2\\
E_k=\dfrac12I_p(\dfrac{d\theta}{dt})^2
$$

By conservation of energy,

$$
E_p+E_k=\dfrac12mgL\theta^2+\dfrac12I_p(\dfrac{d\theta}{dt})^2=C
$$

where $C$ is a constant.

So $\omega=\sqrt{\dfrac{mgL}{I_p}}$

## 4

4. A damped harmonic oscillator consists of a block ( $m = 2.00 \mathrm{kg}$ ), a spring ( $k = 10.0 \mathrm{N/m}$ ), and a damping force $F = bv$. Initially, it oscillates with an amplitude of $25.0 \mathrm{cm}$; because of the damping, the amplitude falls to three‑fourths of this initial value at the completion of four oscillations.  
   (a) What is the value of $b$?  
   (b) How much energy has been "lost" during these four oscillations?

(a)

Underdamped.

$x=A_0e^{-\frac b{2m}t}\cos(\omega't+\varphi)$, where $\omega'=\sqrt{\dfrac km-(\dfrac b{2m})^2}$

By given condition, $A_0e^{-\frac b{2m}4T}=\dfrac34A_0$, so $b=2\ln\dfrac43\cdot\sqrt{\dfrac{km}{64\pi^2+\ln^2\frac43}}$

(b)

$\Delta E=\dfrac12kA_0^2-\dfrac12kA_1^2=\dfrac{35}{256}J=0.137J$

## 5

5. Imagine that we have built a straight tunnel through a planet of mass $M$ and radius $R$. The vertical distance between the tunnel and the planet's center is $a$. At time $t = 0$, we drop a particle of mass $m$ into the tunnel from one end of the tunnel. The initial speed of the particle is zero. Assume the tunnel is frictionless and the density of the planet is uniform. Neglect the missing materials from the tunnel and the planet's rotation. The gravitational constant is $G$.

   (a) Calculate the gravity between the particle and the planet when the displacement of the particle from the middle point $P$ of the tunnel is $x$. The $x$-axis with $P$ as the origin has been given in the figure.  
   (Hint: If a particle is in a uniform spherical shell, it feels zero net gravity from the shell. If a particle is out of a uniform spherical shell, it feels nonzero net gravity from the shell as if the mass of the shell is concentrated at the sphere center.)

   (b) Express $x$ as a function of time $t$. How much time does the particle take to reach the other end of the tunnel?  
   (c) Analyze whether the speed of the particle in the tunnel can reach the first cosmic velocity of the planet if we properly choose $a$ when building the tunnel.

![alt text](fig6-4.png)

(a)

$$
F=G\dfrac{M'm}{x^2+a^2}=G\dfrac{Mm(x^2+a^2)^{\frac12}}{R^3}
$$

(b)

$F_x=F\cos\theta=F\dfrac{x}{(a^2+x^2)^{\frac12}}=\dfrac{GMm}{R^3}x$

So it's a harmonic oscillation.

$x=\sqrt{R^2-a^2}\cos(\sqrt{\dfrac{GM}{R^3}}t)$

$t=\dfrac12T=\pi\sqrt{\dfrac{R^3}{GM}}$

(c)

$m\dfrac{v_1^2}R=G\dfrac{Mm}{R^2}$, so $v_1=\sqrt{\dfrac{GM}{R}}$

Maximal speed $v_m$ satisfies $\dfrac12mv_m^2=\dfrac12(\dfrac{GMm}{R^3})(R^2-a^2)\le \dfrac12(\dfrac{GMm}{R^3})\cdot R^2$

So $v_m\le\sqrt{\dfrac{GM}{R}}=v_1$, the equation is satisfied iff $a=0$, which is impossible.

## 6

6. **Vibrational Modes of a Spring‑Ball System**

   Consider three balls connected by two identical springs, as shown in Figure (a). The two red balls have mass $m_{1}$ and the black ball has mass $m_{2}$. The spring constant of both springs is $k$. The force $F$ in each spring follows the Hooke's law. When the system is in equilibrium, the red balls are located at $x = \pm a_{0}$, and the black ball is located at $x = 0$.

   (a) Calculate three eigenfrequencies for longitudinal vibrational modes along the $x$ direction and illustrate the motion of the three balls in each normal mode.

   (b) For transverse vibrational modes, assume that the two red balls are stationary and fixed at $x = \pm a_{0}$, and the black ball oscillates in the $y$ direction with a small amplitude compared to the equilibrium distance $a_{0}$ [Figure (b)]. Calculate the restoring force acting on the black ball as a function of the perpendicular displacement $y$. Is this vibrational mode a harmonic motion? Explain the reason of your answer.

![alt text](fig6-5.png)

(a)

$$
\begin{cases}
m_1\ddot x_1=-k(x_1-x_2)\\
m_2\ddot x_2=k(x_1-x_2)-k(x_2-x_3)\\
m_1\ddot x_3=k(x_2-x_3)\\
\end{cases}
$$

Try $x_1=A_1\cos(\omega t+\varphi),x_2=A_2\cos(\omega t+\varphi),x_3=A_3\cos(\omega t+\varphi)$

$$
\begin{cases}
m_1\omega^2A_1=k(A_1-A_2)\\
m_2\omega^2A_2=k(2A_2-A_1-A_3)\\
m_1\omega^2A_3=k(A_3-A_2)\\
\end{cases}
$$

So

$$
\begin{pmatrix}
\frac{k}{m_1} & -\frac{k}{m_1} & 0\\
-\frac{k}{m_2} & \frac{2k}{m_2} & -\frac{k}{m_2}\\
0 & -\frac{k}{m_1} & \frac{k}{m_1}\\
\end{pmatrix}
\begin{pmatrix}
A_1\\ A_2\\ A_3
\end{pmatrix}=
\omega^2
\begin{pmatrix}
A_1\\
A_2\\
A_3\\
\end{pmatrix}
$$

So $\omega^2$ is eigenvalue.

$\omega_1=0,\omega_2=\sqrt{\dfrac k{m_1}},\omega_3=\sqrt{\dfrac{k(2m_1+m_2)}{m_1m_2}}$

$\omega_1=0$:

Corresponding $(A_1,A_2,A_3)=\lambda_1(1,1,1)$, which means the 3 balls doing translational motion without vibration.

$\omega_2=\sqrt{\dfrac k{m_1}}$:

Correcsponding $(A_1,A_2,A_3)=\lambda_2(1,0,-1)$, which means the 2nd ball stays still, while the other balls vibrating in the opposite directions.

$\omega_3=\sqrt{\dfrac{k(2m_1+m_2)}{m_1m_2}}$:

Corresponding $(A_1,A_2,A_3)=\lambda_3(1,-\dfrac{2m_1}{m_2},1)$, which means the 1st & 3rd balls vibrate at the same velocity, while the 2nd ball moving in the opposite direction.

(b)

$\Delta y=a_0\sin\theta$

$\Delta l=a_0(\dfrac1{\cos\theta}-1)$

$F_y=2k\Delta l\cdot\sin\theta\approx-\dfrac{k}{a_0^2}(\Delta y)^3$.

Not a harmonic motion.

