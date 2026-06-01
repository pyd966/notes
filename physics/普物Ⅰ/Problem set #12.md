# Problem set #12

## 1. 
At $20.0^{\circ}\mathrm{C}$, an aluminum ring has an inner diameter of $5.0000\mathrm{cm}$ and a brass rod has a diameter of $5.0500\mathrm{cm}$.  
(a) To what temperature must the ring be heated so that it will just slip over the rod?  
(b) To what common temperature must the two be heated so that the ring just slips over the rod? Would this latter process work?

$\alpha_{al}=2.3\times10^{-5}/\circ C,\alpha_{brass}=1.9\times10^{-5}\circ C$

(a)

$\Delta_{al}L=L_{al}\alpha_{al}(T_1-T_0)=L_{brass}-L_{al}$

So $T_1\approx 454.8\circ C$

(b)

$L_{al}(1+\alpha_{al}(T_2-T_0))=L_{brass}(1+\alpha_{brass}(T_2-T_0))$

So $T_2\approx2645\circ C$, which is higher than their melting point, so it's impossible.

## 2.
In state-of-the-art vacuum systems, pressures as low as $10^{-9}\mathrm{Pa}$ are being attained. Calculate the number of molecules in a $1.00\mathrm{m}^3$ vessel at this pressure if the temperature is $27^{\circ}\mathrm{C}$.

At very low pressure, so $pV=nRT$, $n=\dfrac{pV}{RT}$, $N=\dfrac{pV}{RT}N_A\approx2.41\times10^{11}$

## 3.
At $25.0\mathrm{m}$ below the surface of the sea (density $= 1025\mathrm{kg} / \mathrm{m}^3$), where the temperature is $5.00^{\circ}\mathrm{C}$, a diver exhales an air bubble having a volume of $1.00\mathrm{cm}^3$. If the surface temperature of the sea is $20.0^{\circ}\mathrm{C}$, what is the volume of the bubble right before it breaks the surface?

$p_1V_1=nRT_1,p_2V_2=nRT_2$

$p_1=p_0+\rho gh,p_2=p_0$

So $V_2=V_1\dfrac{(p_0+\rho gh)T_2}{p_0T_1}\approx3.67cm^3$

## 4.
The rms speed of a helium atom at a certain temperature is $1350\mathrm{m / s}$. Find by proportion the rms speed of an oxygen molecule at this temperature. (The molar mass of $\mathrm{O}_2$ is $32.0\mathrm{g / mol}$, and the molar mass of He is $4.00\mathrm{g / mol}$.)

$v_{rms}\propto\sqrt{\dfrac1{Mr}}$

So $v_{rms}(O_2)=v_{rms}(He)\sqrt{\dfrac{Mr(He)}{Mr(O_2)}}\approx477m/s$

## 5.
In class we calculated the root-mean-square speed of the water molecules at room temperature. Following the same line of thinking in Question 4, we realize that the root-mean-square speed of molecules in air (mostly $\mathrm{N}_{2}$) should be comparable to the speed of sound in air (or in an ideal gas). This should not be too surprising to you with the knowledge now you have.  
(a) Using the equation of state of an ideal gas, calculate the bulk modulus (at temperature $T$), which is defined as  

$$B = \frac{\text{volume stress}}{\text{volume strain}} = -\frac{\Delta F / A}{\Delta V / V} = -\frac{\Delta P}{\Delta V / V}$$

(b) Recall that the speed of sound in a fluid $\nu = \sqrt{B / \rho}$ depends on the elastic and inertial properties of the fluid, where $B$ is the bulk modulus and $\rho$ is the density of air. Express the speed of sound waves in terms of molecular mass $m$, temperature $T$, as well as the Boltzmann's constant $k_{\mathrm{B}}$.

(c) Compute the result in (b) at room temperature. The result was first obtained by Isaac Newton, but it is lower than the measured value due to the failure to include the effect of fluctuating temperature.

(d) Pierre-Simon Laplace later pointed out that as a sound wave passes through a gas, the compressions are so rapid or so far apart that energy flow by heat is prevented by lack of time or by insulation. The compressions and rarefactions are adiabatic. As a result, the speed of sound has an additional factor of $\sqrt{\gamma}$, where $\gamma$ is the adiabatic index ($\gamma = 7 / 5 = 1.400$ for diatomic molecules at room temperature). Please evaluate Laplace's result for the speed of sound and compare it to the numerical value that you know or you find elsewhere.

(e) Compare your result with the root-mean-square molecular speed.

(a)

At constant $T$, $pV=$ some constant, so $pdV+Vdp=0$.

So $B=-V\dfrac{dp}{dV}=p$

(b)

$pV=Nk_BT=\dfrac{M}{m}k_BT$, so $\rho=\dfrac{pm}{k_BT}$

So $v=\sqrt{\dfrac{B}{\rho}}=\sqrt{\dfrac{k_BT}{m}}$

(c)

$T_{room}=293K$

$v_{room}=\sqrt{\dfrac{k_BT_{room}}{m}}\approx295m/s$

(d)

$v_{room}'=\sqrt{\gamma\dfrac{k_BT{room}}{m}}\approx349m/s$, is very close to $343m/s$

(e)

$v_{rms}=\sqrt{\dfrac{3k_BT}{m}}\approx511m/s$, this one is larger.

## 6.
The van der Waals Gas  

In class, the van der Waals equation of state  

$$\left(p + \frac{a}{V^2}\right)\left(V - b\right) = nRT,$$

was discussed. In this equation, $T$ is the temperature, $p$ the pressure and $V$ the volume of the gas, $n$ denotes the number of moles and $R$ is the gas constant.

(a) What is the physical interpretation of the constants $a$ and $b$ and what are their dimensions?

(b) Calculate the isothermal compressibility of the van der Waals gas in terms of $(V,T)$ and determine the high-temperature limit. How does this result compare to that for an ideal gas?  

Hint: The isothermal compressibility $\kappa_{T}$ is defined through $\kappa_{T} = -\frac{1}{V}\left(\frac{\partial V}{\partial p}\right)_{T}$.

(c) The van der Waals equation possesses a so-called critical point, where  

$$\left(\frac{\partial p}{\partial V}\right)_{T} = \left(\frac{\partial^{2}p}{\partial V^{2}}\right)_{T} = 0$$

Determine the critical pressure $p_{c}$, the critical volume $V_{c}$ and the critical temperature $T_{c}$. What is the behavior of $\kappa_{T}$ at the critical point?

(d) Use the expressions for $V_{c}$, $p_{c}$, and $T_{c}$ in the van der Waals equation of state and show that it assumes a simple form independent of $a$ and $b$ when $T$, $V$, and $p$ are measured in terms of $T_{c}$, $V_{c}$, $p_{c}$, i.e., when expressing the van der Waals equation in terms of $T / T_{c}$, $V / V_{c}$, $p / p_{c}$.

(a)

a means intermocular attraction, $[a]=m^6\cdot Pa=kg\cdot m^5/s^2$

b means mocular volume, $[b]=m^3\cdot mol$

(b)

By $(p+\dfrac a{V^2})(V-b)=RT$, we know $(1-2\dfrac a{V^3}\dfrac{\partial V}{\partial p})(V-b)+(p+\dfrac a{V^2})(\dfrac{\partial V}{\partial p})$

So $\kappa_T=-\dfrac1V(\dfrac{\partial V}{\partial p})_T=\dfrac1{V(\frac{nRT}{(V-b)^2}-\frac{2a}{V^3})}$

When $T\to+\infty$, $\kappa_T\to\dfrac{V}{nRT}$

That's the same as ideal gas.

(c)

$(\dfrac{\partial p}{\partial V})_T=-\dfrac{RT}{(V-b)^2}+\dfrac{2a}{V^3}=0$

$(\dfrac{\partial^2p}{\partial V^2})_T=\dfrac{2RT}{(V-b)^3}-\dfrac{6a}{V^4}=0$

So $V_c=3b,p_c=\dfrac{a}{27b^3},T_c=\dfrac{8a}{27Rb}$

At this point, $\dfrac{\partial V}{\partial p}\to\infty$, so $\kappa_T\to\infty$

(d)

Let $p'=\dfrac{p}{p_c},V'=\dfrac{V}{V_c},T'=\dfrac{T}{T_c}$

So $(p'p_c+\dfrac{a}{V'^2V_c^2})(V'V_c-b)=nRT'T_c$

So $(p'+\dfrac3{V'^2})(3V'-1)=8T'$