# Mesoscale Modelling

## Brownian Motion

### Brownian motion

The mean kinetic energy of Brownian motion is defined by the equipartition theorem:
$$
\frac{1}{2}m\langle \mathbf{v}^2\rangle=\frac{3}{2}k_BT
$$
We can split $\mathbf{v}$ in to 3 components: 
$$
\frac{1}{2}m\langle v_x^2\rangle=\frac{1}{2}k_BT\Rightarrow \langle v_x^2 \rangle=k_BT/m
$$
And On the much longer timescale $\tau$ of mesoscale observations of the particle velocity we see:
$$
V_x = \frac{1}{\tau}(x(t+\tau)-x(t))
$$

### Einstein relationships

Einstein (1905) considered the motion of the Brownian particle as a statistical random walk

Imagine a particle sitting on a 1-dimensional line. Every  seconds, a fluid molecule collides with it. With each collision, the particle takes a single "step" of length $l$ . The direction is entirely random: there is a 50% chance it steps forward $(l)$ and a 50% chance it steps backward $(-l)$.

The displacement of $i$-th step can be $s_i$, where $s_i\in \{+l,-l\}$, and the total displacement after n-step will be $X=s_1+s_2+...+s_N$.
$$
X^2=(s_1+s_2+...+s_N)\times (s_1+s_2+...+s_N) = (s_1^2+s_2^2+...+s_N^2)+\underset{\sum_{i,j;i\neq j }s_is_j=0}{2(s_1s_2+s_2s_3+...)}
$$

$$
X^2=Nl^2=\frac{t}{\tau}l^2
$$

- $\tau$: The time interval for between each individual steps (mean collision time)

Because the particle takes a massive number of random steps ($N$ is very large), we can apply the Central Limit Theorem. This theorem dictates that the sum of many independent random variables (the individual steps) will tend toward a normal (Gaussian) distribution.
$$
W(x)=(\frac{2\pi l^2t}{\tau})^{-1/2}\exp\Big[\frac{-x^2\tau}{2l^2t}\Big]
$$

###   The Macroscopic Model: The Diffusion Equation

Macroscopic diffusion is governed by Fick's Second Law, which describes how concentration changes over time.  And the Gaussian   probability distribution $W(x)$ is the solution to 1D diffusion equation:
$$
\frac{\partial \rho}{\partial t}=D\frac{\partial^2 \rho}{\partial x^2};\quad \rho(x,0)=\sigma(x)
$$

$$
D = \frac{\langle x^2\rangle}{2t}
$$

## The Langevin Equation

The Langevin equation is fundamentally just Newton's Second Law of Motion ($F = ma$, or $m \frac{dv}{dt} = \sum F$). Langevin stated that the total force on the particle comes in two distinct parts:

1. **A macroscopic, slow frictional force** (which drains energy).

2. **A microscopic, fast random force** (which injects energy).

$$
\frac{d\mathbf{v}}{dt}=-\gamma \mathbf{v}+ \mathbf{F}(t)
$$

- $-\gamma \mathbf{v}$: The dissipative (drag) term. $\gamma$ is the damping coefficient which is equal to $\frac{1}{\mu m}$. This term always pushes in the opposite direction of motion, trying to stop the particle.

- $\mathbf{F}(t)$: The Langevin Force (or stochastic/random force). This represents the rapid, unpredictable kicks from the countless invisible fluid molecules collide the particle. 



Because $F(t)$ represents the chaotic collisions of billions of molecules, we cannot write an exact formula for it. Instead, Langevin defined it by its statistical properties:

1.    The kicks are completely random.

 $$\langle \mathbf{F}(t) \rangle = 0$$, At any given moment, a push to the negative is just as likely as a push to the positive. If you average the random force over time, it perfectly cancels out to zero.

2. The kicks are completely independent (White noise)

$$\langle\mathbf{F}(t)\mathbf{F}(t^\prime)\rangle=q\sigma(t-t^\prime)$$

Where $\sigma$ is the Dirac delta, and $q$ is a constant representing the "strength" or magnitude of the random fluctuations.



## Coarse-Graining

