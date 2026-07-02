# Introduction to Quantum Mechanics

## Postulates of Quantum Mechanics

**Postulate No. 1.**

The wave functions can be represented by probability depends on the coordinates of the particle(s) $r$ and on time $t$.
$$
\int^{+\infty}_{-\infty}\Psi^\star(r,t)\Psi(r,t)d\tau = \int^{+\infty}_{-\infty}|\Psi(r,t)|^2 =1
$$

- $\tau$ is the volume element and $t$ is the precise instant of time.



**Postulate No. 2.**

To every observable in classical mechanics there corresponds a linear, Hermitian operator in quantum mechanics. If we require that the expectation value of an operator $\hat{A}$  is real, then  $\hat{A}$ must be a real operator. 

**Postulate No.3.**

In any measurement of the observable associated with operator $\hat{A}$, the only values that will ever be observed are the eigenvalues $a$:
$$
\hat{A}\Psi = a\Psi
$$


> [!NOTE]
>
> Although measurements must always yield an eigenvalue, the state does not have to be an eigenstate of $\hat{A}$ initially. An arbitrary state can be expanded in the complete set of eigenvectors of $\hat{A}: \quad (\hat{A}\Psi_i=a_i\Psi_i )$

$$
\Psi = \sum_i^{n=\infty}c_i\Psi_i
$$

So, a single measurement of $A$ will give one exact number, which is one of the $a_i$, but we do not know which one, However, we do know the probability that eigenvalue $a_i$ will occur —it is the absolute value squared of the coefficient, $\abs{c_i}^2$.

After measurement of Ψ yields some eigenvalue $a_i$, the wave-function immediately “collapses” into the corresponding eigenstate $\Psi_i$. 

**Postulate No.4.**

If a system is in a state described by a normalized wave-function $\Psi$, then the average value of the observable corresponding to $\hat{A}$ is:
$$
\langle A \rangle= \int\Psi^\star\hat{A}\Psi d\tau
$$
**Postulate No.5.**

The wave-function or state function of a system evolves in time according to the time- dependent $\text{Schr\"odinger}$ equation as described
$$
\hat{H}\Psi(r,t) = i\bar{h}\frac{\partial \Psi(r,t)}{dt}
$$
**Postulate No.6.**

The total wave function must be antisymmetric with respect to the interchange of all coordinates of one electron (fermion) with those of another electron (fermion). The electronic spin must be included in this set of coordinates.

$\left\{\begin{aligned}&\alpha \,\text{for spin up}\\&\beta\,\text{for spin down}\end{aligned}\right.$

$\int\alpha\alpha^\star=\int\beta\beta^\star=1$

$\int\alpha\beta=\int\alpha^\star\beta^\star=0$

And the spin orbital can be defined by $\chi_i = \alpha \cdot \phi_i$

> [!NOTE]
>
> A **fermion** is a type of particle that follows the **Pauli exclusion principle** — meaning **no two identical fermions can occupy the same quantum state simultaneously**.
>
> Can be explained by Slater determinant: 
> $$
> \Psi(x_1,x_2)
> =
> \frac{1}{\sqrt2}
> \begin{vmatrix}
> \chi_a(x_1) & \chi_b(x_1)\\
> \chi_a(x_2) & \chi_b(x_2)
> \end{vmatrix}\\
> 
> \Psi
> =
> \frac{1}{\sqrt2}
> \left[
> \chi_a(x_1)\chi_b(x_2)
> -
> \chi_a(x_2)\chi_b(x_1)
> \right]
> $$
> And if we swap the electrons/fermions, antisymmetric:
> $$
> \Psi(x_2,x_1)=-\Psi(x_1,x_2)
> $$
> 



## The Schrödinger Equation For The Hydrogen-like Systems

Start form the Schrödinger equation, the $\hat{H}\Psi = \hat{E}+\hat{V} = (-\frac{\bar{h^2}}{2m}\nabla^2 + V)\Psi$

The potential $V$ experienced by two charges separated by some distance $r$ is best described by a Coulomb term
$$
V(r) = -\frac{Ze^2}{4\pi \epsilon_0 r}
$$

- where $Ze$ is the charge of the nucleus, (Z = 1 being the hydrogen case, Z = 2 helium, etc.)
- $\epsilon_0$ is the permittivity of vacuum

While the system contains multi-particles motion for the kinetic energy $-\frac{\hbar}{2m}\frac{\partial^2 \phi}{\partial r^2}$, because the original coordinates ($\mathbf r_1,\mathbf r_2$) mix together two different kinds of motion:

1. the whole system moving through space $\mathbf r_1 \to \mathbf r_1 + \mathbf a, \quad \mathbf r_2 \to \mathbf r_2 + \mathbf a$
2. the particles moving relative to each other, defined by coulomb potential: $|\mathbf r_1-\mathbf r_2|$

So, the equivalent mass a point located at the center of mass of the system would have:
$$
\mu = \frac{m_1m_2}{m_1+m_2}\\
\mathbf R
=
\frac{m_1\mathbf r_1+m_2\mathbf r_2}{m_1+m_2}
$$
And the wave function can be separated by: 
$$
\Psi(\mathbf r_1,\mathbf r_2)
=
\psi_{\rm CM}(\mathbf R)\psi_{\rm rel}(\mathbf r)
$$
While in the real system, according to Born-Oppenheimer approximation: the motion of electrons can be separated from nuclei. Then 
$$
\mu = \frac{mM}{M+m}
$$
And the center of mass kinetic energy could be treated as 0:
$$
\hat{H}=-\frac{\hbar}{2\mu}\nabla^2-\frac{Ze^2}{4\pi \epsilon_0 \mathbf{r}}
$$


The Schrödinger equation in Cartesian coordinates is:
$$
\hat{H}\Psi=[-\frac{h^2}{2m}(\frac{\partial^2}{\partial x^2}+\frac{\partial^2}{\partial y^2}+\frac{\partial^2}{\partial z^2})-\frac{Ze^2}{4\pi\epsilon_0r}]\Psi
$$
The potential part has spherical symmetry. One could write $r = x^2 + y^2 + z^2$ and solve Eq. 2 in Cartesian coordinates. This would work but it would be very tedious, as the mathematics does not display the **symmetry of the physics.** Accordingly, we rather exploit the spherical symmetry of the electrostatic potential and perform a coordinate transformation from Cartesian Coordinates (efficient for rectangle shapes) to Spherical Polar Coordinates (efficient for spherical shapes).

<img src="assets/image-20250929142957857.png" alt="image-20250929142957857" style="zoom:50%;" />
$$
(x,y,z) = (r, \theta, \phi)\\
x = r\sin\theta\cos\phi\\
y = r\sin\theta\sin\phi\\
z = r\cos\theta
$$

$$
\hat{H}\Psi =  -\frac{\hbar^2}{2\mu}
\left[
\frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial}{\partial r}\right)
+\frac{1}{r^2\sin\theta}\frac{\partial}{\partial \theta}\left(\sin\theta\frac{\partial}{\partial \theta}\right)
+\frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial \phi^2}
\right]\Psi
-\frac{Ze^2}{4\pi\epsilon_0 r}\Psi 
$$





**Proof**

Define the scale factor

In cartesian coordinates:
$$
ds^2=dx^2+dy^2+dz^2
$$
In spherical coordinates:
$$
ds^2=(1\cdot dr)^2+ (r\cdot d\theta)^2 +(r\sin\theta\cdot d\phi)^2
$$
So, $h_1 =1$, $h_2=r$, $h_3=r\sin\theta$.

The General Laplacian Formula in *any* orthogonal curvilinear coordinate system $(u_1,u_2,u_3)$ with scale factors $(h_1,h_2,h_3)$ is:
$$
\nabla^2\Psi=\frac{1}{h_1h_2h_3}[\frac{\partial }{\partial u_1}(\frac{h_2h_3}{h_1}\frac{\partial \Psi}{\partial u_1})\, + \, \frac{\partial }{\partial u_2}(\frac{h_1h_3}{h_2}\frac{\partial \Psi}{\partial u_2})\, + \, \frac{\partial }{\partial u_3}(\frac{h_1h_2}{h_3}\frac{\partial \Psi}{\partial u_3})]
$$
Here we substitute $u_1=r$, $u_2=\theta$, $u_3=\phi$. And the pre-factor is: $\frac{1}{h_1h_2h_3}=\frac{1}{r^2\sin\theta}{}$
$$
\nabla^2=\frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial}{\partial r}\right)
+\frac{1}{r^2\sin\theta}\frac{\partial}{\partial \theta}\left(\sin\theta\frac{\partial}{\partial \theta}\right)
+\frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial \phi^2}
$$

$$
\hat{H}\Psi = E\Psi = -\frac{\hbar^2}{2\mu}
\left[
\frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial}{\partial r}\right)
+\frac{1}{r^2\sin\theta}\frac{\partial}{\partial \theta}\left(\sin\theta\frac{\partial}{\partial \theta}\right)
+\frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial \phi^2}
\right]\Psi
-\frac{Ze^2}{4\pi\epsilon_0 r}\Psi = E\Psi
$$

### Separating The Radial From The Angular Part

Since the potential part only depends on $r$, which is symmetric, Using the Separation of Variables, we assume a product solution of a radial and an angular function as in:
$$
\Psi(r,\theta, \phi) = R(r)\cdot Y(\theta,\phi)
$$
Since Y (spherical harmonics) is independent of $r$
$$
\frac{\partial \Psi}{\partial r} = Y \frac{\partial R(r)}{\partial r}
$$
and, similarly, since $R$ does not depend on the angular variables. Thus replace $\Psi$ and the differentials:


$$
\frac{Y}{r^2}\frac{\partial}{\partial r}(r^2\frac{\partial R}{\partial r})\, +\, \frac{R}{r^2\sin\theta}\frac{\partial}{\partial\theta}(\sin\theta\frac{\partial Y}{\partial \theta})\,+\,\frac{R}{r^2\sin^2\theta}\frac{\partial^2Y}{\partial \phi^2}\,+\, \frac{2\mu}{\bar{h}^2}(E+\frac{Ze^2}{4\pi\epsilon_0r})RY=0\\
%
\\
\Downarrow{\text{multiply } r^2 \text{ and divide by } RY}\\
\\
%after transformation
\frac{1}{R}\frac{\partial}{\partial r}(r^2\frac{\partial R}{\partial r})\, +\, \frac{1}{Y\sin\theta}\frac{\partial}{\partial\theta}(\sin\theta\frac{\partial Y}{\partial \theta})\,+\,\frac{1}{Y\sin^2\theta}\frac{\partial^2Y}{\partial \phi^2}\,+\, \frac{2\mu r^2}{\bar{h}^2}(E+\frac{Ze^2}{4\pi\epsilon_0r})=0
$$


Now, the first term and the last term only relies on $r$, and the middle part depends on angles only. They can only balance each other for all points in space if the radial and angular terms are the same constant but with opposite signs.

So, we setting $A$ as the separation constant (e.g. $\hat{R}=-\hat{Y}=A$), we can split a **radial function**:
$$
\frac{\partial}{\partial r}(r^2\frac{\partial R}{\partial r})+\frac{2\mu r^2}{\bar{h}^2}(E+\frac{Ze^2}{4\pi\epsilon_0r})R-AR=0\label{eq:radial func}
$$
And also for the **angular function**:
$$
\frac{1}{\sin\theta}\frac{\partial}{\partial \theta}(\sin\theta\frac{\partial Y}{\partial\theta})+\frac{1}{\sin^2\theta}\frac{\partial^2Y}{\partial\phi^2}+AY=0
$$

### Separating The Angular Part Into Polar And Azimuth Parts

Since the angular function $Y(\theta,\phi)$ also contains the parameters of $\theta,\phi$, Hence, another separation of variables is needed.
$$
Y(\theta,\phi)=\Theta(\theta)\cdot\Phi(\phi)
$$

$$
\frac{\Phi}{\sin\theta}\frac{\partial}{\partial \theta}(\sin\theta\frac{\partial \Theta}{\partial\theta})+\frac{\Theta}{\sin^2\theta}\frac{\partial^2\Phi}{\partial\phi^2}+A\Theta\Phi=0
\\
%
\Downarrow\text{Divided by }\Phi\Theta ,\text{ and multiply by }\sin\theta^2\\
%
\frac{\sin\theta}{\Theta}\frac{\partial}{\partial \theta}(\sin\theta\frac{\partial \Theta}{\partial\theta})+\frac{1}{\Phi}\frac{\partial^2\Phi}{\partial\phi^2}+A\sin^2\theta=0
$$

Same way setting constant B as another separation parameter.

For **polar function**:
$$
\frac{\sin\theta}{\Theta}\frac{\partial}{\partial \theta}(\sin\theta\frac{\partial \Theta}{\partial\theta})+A\sin^2\theta-B=0
$$
For **azimuth function**:
$$
\frac{1}{\Phi}\frac{\partial^2\Phi}{\partial\phi^2}+B=0
$$

### Solving the Azimuth equation

The azimuthal equation obtained after separation of variables is:
$$
\frac{d^2\Phi}{d\phi^2}+m_l^2\Phi=0
$$
which is a second-order differential equation with constant coefficients, and for azimuth function in equation 30. A trial solution to $2^{rd}$  differential equation has the form $\Phi(\phi)=e^{\lambda \phi}$, which gives a characteristic solution $\lambda^2+m_l^2=0$, with roots $\pm im_l$, and the general solution is 
$$
\Phi_m(\phi) = c_1\cdot e^{im_l\phi}+c_2\cdot e^{-im_n\phi}
$$
The normalized azimuthal solution is therefore written as:
$$
\Rightarrow \Phi_{m_l}(\phi)=\frac{1}{\sqrt{2\pi}} e^{im_l\phi}
$$
Since the wavefunction is periodic, so the azimuthal function must also satisfy the periodic boundary condition:
$$
\Phi(\phi)=\Phi(2\pi+\phi)\\
e^{im_l(\phi+2\pi)}
=
e^{im_l\phi}
$$

$$
e^{i2\pi m_l}=1
$$

And $m_l$ should be the integer number which satisfies:
$$
m_l = 0,\pm1,\pm2,\ldots, \pm l
$$

- $l$ is the angular momentum
- $m$ is the magnetic quantum number



### Solving the polar equation

Setting $B=m_l^2$:
$$
\begin{aligned}
\frac{\sin\theta}{\Theta}\frac{\partial}{\partial \theta}(\sin\theta\frac{\partial \Theta}{\partial\theta})+A\sin^2\theta-m_l^2&=0\Rightarrow \text{multiply }\frac{\Theta}{\sin^2\theta}\\
\frac{1}{\sin\theta}\frac{\partial}{\partial \theta}(\sin\theta\frac{\partial \Theta}{\partial\theta})+&\Big(A-\frac{m_l^2}{\sin^2\theta}\Big)\Theta=0

\end{aligned}
$$
We can now express the wave function as depending on $\cos \theta$ rather than on $\theta$ itself, use another variable $x=\cos\theta$$, \dfrac{d}{d\theta} = -\sin\theta \dfrac{d}{dx}$:
$$
\begin{aligned}
\frac{\partial}{\partial x}\big((1-x^2)\frac{\partial \Theta}{\partial x}\big)+\Big(A-\frac{m_l^2}{1-x^2}\Big)\Theta=0\\
-2x\frac{\partial \Theta}{\partial x}+(1-x^2)\frac{\partial^2 \Theta}{\partial x^2}+\Big(A-\frac{m_l^2}{1-x^2}\Big)\Theta=0
\end{aligned}
$$


The solutions of Eq. 37 are known as Legendre polynomials , and they contain a power series with recursive coefficients.
$$
\Theta(\theta)=P_l^{m_l}(\cos\theta)=P_l^{m_l}(x)
$$

$$
A = l(l+1)
$$

where $P_l^{m}(x)$ are the <u>associated Legendre functions</u>.
$$
P_l^{m}(x) = (1-x^2)^{m/2} \frac{d^m}{dx^m}P_l(x)\\
P_l(x)=\frac{1}{2^l l!}\frac{d^l}{dx^l}(x^2-1)^l
$$

- $l$ is the orbital angular momentum quantum number which controls the shape (angular momentum magnitude)
- $m_l$ is the magnetic quantum number which controls orientation (projection along z-axis)

|   $m_l$   |    $l = 0$     |           $l = 1$           |              $l = 2$               |
| :-------: | :------------: | :-------------------------: | :--------------------------------: |
| $m_l = 0$ | $P_0^0(x) = 1$ |       $P_1^0(x) = x$        | $P_2^0(x) = \frac{1}{2}(3x^2 - 1)$ |
| $m_l = 1$ |      ---       | $P_1^1(x) = \sqrt{1 - x^2}$ |   $P_2^1(x) = 3x\sqrt{1 - x^2}$    |
| $m_l = 2$ |      ---       |             ---             |       $P_2^2(x) = 3 - 3x^2$        |



> [!NOTE]
>
> **Legendre's differential equation**:
> $$
> {\displaystyle (1-x^{2})P_{n}''(x)-2xP_{n}'(x)+n(n+1)P_{n}(x)=0.}
> $$



### Solving the radial function 

The radial function 24. (replacing $A=l(l+1)$) is defined as:
$$
\begin{aligned}
\frac{\partial}{\partial r}(r^2\frac{\partial R}{\partial r})+&\frac{2\mu r^2}{\bar{h}^2}(E+\frac{Ze^2}{4\pi\epsilon_0r})R-l(l+1)R=0\\
2r\frac{d R}{d r}+\frac{r^2d^2R}{d r^2}+&\frac{2\mu r^2}{\bar{h}^2}(E+\frac{Ze^2}{4\pi\epsilon_0r})R-l(l+1)R=0\\
&\downarrow\text{divided by } r^2\\
\frac{2}{r}\frac{d R}{d r}+\frac{d^2R}{d r^2}+&\Big[\frac{2\mu}{\bar{h}^2}(E+\frac{Ze^2}{4\pi\epsilon_0r})-\frac{l(l+1)}{r^2}\Big]R=0

\end{aligned}
$$
This equation is hard to solve straightly, however we know that:

- Near $r\rightarrow \infty$, several terms go to 0 (first order derivative and coulomb potential):
  $$
  \frac{d^2R^\infty}{dr^2} + \frac{2\mu E}{\hbar^2}R^\infty = 0
  $$
  Which has a general $2^{rd}$ differential equation solution, $\lambda^2 = - (\frac{2\mu E}{\hbar^2})^{1/2}$

$$
R^\infty =c_1\cdot e^{i\sqrt{\frac{2\mu E}{\hbar^2}}r}+c_2\cdot e^{-i\sqrt{\frac{2\mu E}{\hbar^2}}r}
$$

​	since wave function cannot blow up to infinity as distance increases, so $c_1=0$. $R^\infty(r)\sim e^{-\alpha r}\rightarrow \alpha = \sqrt{-\frac{2\mu E}{\hbar^2}}$

- Near $r \to 0$, electrons are heavily attracted, little kinetic energy.
  $$
  \frac{d^2R}{dr^2} + \frac{2}{r}\frac{dR}{dr} - \frac{l(l+1)}{r^2}R + \frac{\beta}{r} = 0\\
  \downarrow 
  \beta =\frac{Ze^2}{4\pi\epsilon_0r}\\
  R^0(r)\sim r^l
  $$

So, The next step is to peel off the asymptotic behavior, introducing the new function:
$$
R(r)= r^le^{-\alpha r}\mu(r)
$$

- $\mu(r)$ is an unknown function that handles the everything in between.



e.g. for the energy levels of the hydrogen-like atom are given by:
$$
E_n=\frac{-\mu Z^2e^4}{8\epsilon_0^2 h^2n^2}
$$
n is the principal quantum number and can assume integer values: $n=1,2,3,4,...$

## Appendix

### Derivation of radial function

Recall the equation $\eqref{eq:radial func}$, we can simplify it by setting $u \equiv r R(r)$:

So that, $R=u/r$, $dR/dr=[r(du/dr)-u]/r^2$, $(d/dr)[r^2(dR/dr)]=rd^2u/dr^2$
$$
-\frac{\hbar^2}{2m_e}\frac{d^2u}{dr^2}+\Big[V+\frac{\hbar^2}{2m_e}\frac{l(l+1)}{r^2}\Big]u=Eu
$$
we divided both side by $E$ and we can tidy up the equation by setting $\kappa=\dfrac{\sqrt{-2m_eE}}{\hbar}$, here $m_e=\mu$ and for bonded state $E$ is negative, so $\kappa$ is real.
$$
\frac{1}{\kappa^2}\frac{d^2u}{dr^2}=[1-\frac{Zm_ee^2}{2\pi\epsilon_0\hbar^2}\frac{1}{\kappa^2r}+\frac{l(l+1)}{(\kappa r)^2}]u
$$
This suggests that we introduce:
$$
\rho\equiv \kappa r \quad \text{and} \quad \rho_0\equiv\frac{Zm_ee^2}{2\pi\epsilon_0\hbar^2\kappa}
$$
So that:
$$
\frac{d^2u}{d\rho^2}= [1-\frac{\rho_0}{\rho}+\frac{l(l+1)}{\rho^2}]u
$$
Since this equation can not be solved directly, Next we examine the asymptotic form of the solutions. As $\rho\rightarrow\infty$, the constant term in the brackets dominates, so approximately $\frac{d^2u}{d\rho^2}=u$,

The general solution is $u = A\,e^{-\rho}+B\,e^{\rho}$

But  $e^\rho$ blows up, which is not converged, so $B=0$, so $u= A\,e^{-\rho}$ evidently.

On the other hand, as $\rho\rightarrow 0$, the centrifugal term  dominates approximately, then: $\frac{d^2u}{d\rho^2}=\frac{l(l+1)}{\rho^2}u$

The general solution is $u(\rho) = C\,\rho^{l+1}+D\,\rho^{-l}$;

But $D\rho^{-l}$ blows up, so $D=0$, thus $u\sim C\, \rho^{l+1}$

The next step is to peel off the asymptotic behavior, introducing the new function $v(\rho)$
$$
u(\rho)= \rho^{l+1}e^{-\rho}v(\rho)
$$
