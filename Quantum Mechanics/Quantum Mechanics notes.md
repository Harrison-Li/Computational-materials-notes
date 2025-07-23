# **Quantum Mechanics Overview**

## **Linear and Nonlinear Theories: Schrödinger’s Equation**





For motion in 1D:


$$
m \frac{d^2x(t)}{dt^2} = -V’(x(t))
$$




Quantum Mechanics is **linear**:


$$
i\hbar \frac{d\Psi}{dt} = \hat{H}\Psi
$$




Hamiltonian is a **linear operator**, so:


$$
L\Psi = 0 \quad \text{where} \quad L \equiv i\hbar\frac{d}{dt} - \hat{H}
$$



$$
\Psi \in \mathbb{C}
$$


> Nonlinear systems are complicated to solve.



------





## **Necessity of Complex Numbers**





- $i = \sqrt{-1}$
- $z = a + ib \in \mathbb{C}, \quad a, b \in \mathbb{R}$
- $|z|^2 = (\sqrt{a^2 + b^2})^2 = zz^*$





------





## **Determinism in Quantum Mechanics**





Electromagnetic field after polarizer:


$$
\vec{E}_a = E_0 \cos\alpha , \hat{x} + E_0 \sin\alpha ,\quad \hat{y} \rightarrow E_0 \cos\alpha , \hat{x}
$$




Fraction of energy transmitted:


$$
(\cos\alpha)^2
$$
Photon polarization states:



- $|photon;x\rangle$: x-polarized
- $|photon;y\rangle$: y-polarized





Superposition state:



$$
|photon;\alpha\rangle = \cos\alpha , |photon;x\rangle + \sin\alpha , |photon;y\rangle
$$



------





## **Nature of Superposition**





Quantum states allow linear combinations, enabling probability-based outcomes.



------





## **The Photoelectric Effect**





1. Light on polished metal emits **photoelectrons**.
2. There’s a **threshold frequency** $\nu_0$: emission only if $\nu > \nu_0$.
3. $\nu_0$ depends on the metal and its atomic configuration.
4. Current magnitude ∝ light intensity.
5. Electron energy is **independent** of light intensity.





Kinetic energy of photoelectron:


$$
E_{e^-} \approx \frac{1}{2}mv^2 = h\nu - W
$$




------





## **Compton Scattering**





Scattering of photons on nearly free electrons.



Photon loses energy:




$$
\lambda_f = \lambda_i + \frac{h}{m_e c}(1 - \cos\theta)
$$




Energy-momentum relation:




$$
E^2 - p^2c^2 = m^2c^4 \quad \text{For photon: } m=0 \Rightarrow E_\gamma = p_\gamma c = \frac{h}{\lambda_\gamma}
$$




------





## **de Broglie’s Proposal**





Wave-particle duality:




$$
\lambda = \frac{h}{p}
$$




Wavefunction: $\Psi(\vec{x}, t) \in \mathbb{C}$



------





## **de Broglie Wavelength in Different Frames**





In different frames:



- p = \frac{h}{\lambda} = \hbar k
- \omega = 2\pi\nu





In frame S’ (moving at velocity v):



$$
p’ = p - mv \Rightarrow \lambda’ = \frac{h}{p - mv} \neq \lambda
$$



> de Broglie wavelength is **not** invariant under Galilean transformation.



------





## **Galilean Transformation of Ordinary Waves**





Wave phase:



$$
\phi = kx - \omega t = \frac{2\pi}{\lambda}(x - v_{\text{phase}} t)
$$



Transformation:



- \phi’ = \phi \Rightarrow k’ = k, \lambda’ = \lambda for **classical waves**
- Not true for \Psi: **not Galilean invariant**





------





## **Frequency of a Matter Wave**





Given:



- p = \hbar k
- E = \hbar\omega \Rightarrow \omega = E/\hbar





Then:



$$
v_{\text{phase}} = \frac{\omega}{k} = \frac{E}{p} = \frac{\frac{1}{2}mv^2}{mv} = \frac{v}{2}
$$



> **Phase velocity ≠ particle velocity**



Group velocity:



$$
V_{\text{group}} = \frac{d\omega}{dk} = \frac{dE}{dp} = \frac{p}{m} = v
$$



------





## **Group Velocity and Stationary Phase Approximation**





Wave packet:



$$
\Psi(x,t) = \int dk , \Phi(k) , e^{i(kx - \omega(k)t)}
$$





### **Stationary Phase Principle**





Non-zero integral only when:



$$
\frac{d\phi(k)}{dk}\bigg|*{k_0} = x - \frac{d\omega}{dk}\bigg|*{k_0} t = 0 \Rightarrow x = v_{\text{group}} t
$$





### **Motion of a Wave Packet**





Using Taylor expansion around k_0:



$$
\Psi(x,t) \approx e^{-i\omega(k_0)t} \cdot \int dk , \Phi(k) , e^{ik(x - v_{\text{group}} t)}
$$



Magnitude:



$$
|\Psi(x,t)| = |\Psi(x - v_{\text{group}} t, 0)|
$$



------





## **Operators in Quantum Mechanics**







### **Momentum and Energy Operators**





Wavefunction:



$$
\Psi(x,t) \sim e^{i(kx - \omega t)}
$$



Momentum:



$$
\hat{p} = \frac{\hbar}{i} \frac{\partial}{\partial x}, \quad \hat{p} \Psi = p \Psi
$$



Energy:



$$
\hat{E} = i\hbar \frac{\partial}{\partial t}, \quad \hat{E} \Psi = E \Psi
$$



Kinetic energy from momentum:



$$
\hat{E} = -\frac{\hbar^2}{2m} \frac{\partial^2}{\partial x^2}
$$



------





## **Free Schrödinger Equation**





$$
i\hbar\frac{\partial \Psi}{\partial t} = -\frac{\hbar^2}{2m} \frac{\partial^2 \Psi}{\partial x^2}
$$



> Not the classical wave equation.



------





## **General Schrödinger Equation and Commutators**





Total Hamiltonian with potential V(x,t):



$$
\hat{H} = \frac{\hat{p}^2}{2m} + V(x,t)
$$



Full time-dependent Schrödinger equation:



$$
i\hbar\frac{\partial\Psi(x,t)}{\partial t} = \left(-\frac{\hbar^2}{2m} \frac{\partial^2}{\partial x^2} + V(x,t)\right)\Psi(x,t)
$$



Position operator:



$$
\hat{x}f(x) = x f(x)
$$



**Commutator**        $[\hat{x}, \hat{p}]$

Proof:



$$
[\hat{x}, \hat{p}] \phi = \hat{x}(\hat{p} \phi) - \hat{p}(\hat{x} \phi) = i\hbar \phi
$$



Thus:



$$
[\hat{x}, \hat{p}] = i\hbar
$$



------





## **Superposition of States**





State:



$$
|\Psi\rangle = \alpha |A\rangle + \beta |B\rangle
$$



Measurement outcomes:



- Prob(a) \sim |\alpha|^2: collapse to |A\rangle
- Prob(b) \sim |\beta|^2: collapse to |B\rangle





**Assumption**: multiplying by scalar doesn’t change state:

|A\rangle \sim \lambda |A\rangle \sim i |A\rangle \sim -|A\rangle



------





## **Spin**





Spin state:


$$
|\Psi\rangle = |\uparrow; z\rangle + |\downarrow; z\rangle
$$


Measurement along z:



- 50% $|\uparrow; z\rangle$
- 50% $|\downarrow; z\rangle$







## **Entanglement**





Entangled states cannot be written as simple products:


$$
|\Psi\rangle \neq |\phi\rangle_A \otimes |\chi\rangle_B
$$




Measurement on one part **affects** the other instantly—correlation beyond classical probability.



------


