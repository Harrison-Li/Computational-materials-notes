# Many-electron system

**Eigenvalues are orthonormal**

$\int\psi_{nlm}\psi_{n'l'm'}$

$\left\{\begin{aligned}&n=n',l=l',m=m'\rightarrow &&=1\\&else&&=0\end{aligned}\right.$

Spatial Spin

$\left\{\begin{aligned}\alpha \,\text{for spin up}\\\beta\,\text{for spin down}\end{aligned}\right.$

$\int\alpha\alpha^\star=\int\beta\beta^\star=1$

$\int\alpha\beta=\int\alpha^\star\beta^\star=0$



**Variational method**

Assume each $\psi_i$ is larger than the ground state

Trail $\psi=\sum_iC_i\psi_i$ (linear combination of eigenvectors)

$\left\{\begin{aligned}&E-\epsilon_0=\frac{\sum|C_i|^2(\epsilon-\epsilon_0)}{\sum|C_i|^2}\\&\epsilon_i\ge\epsilon_0\\&|C_i|^2\ge 0\end{aligned}\right.$$\longrightarrow$ $E-\epsilon_0\ge 0$

## Multi-electron wavefunctions

Two-electron wave function must be anti-symmetric
$$
\psi_\text{total}(x_1,x_2)=\frac{1}{\sqrt{2}}(\psi_1(x_1)\psi_2(x_2)-\psi_1(x_2)\psi_2(x_1))
$$
For muti-electrons
$$
\frac{1}{\sqrt{6}}
\begin{vmatrix}
\psi_1(x_1) & \psi_2(x_1) & \psi_3(x_1) \\
\psi_1(x_2) & \psi_2(x_2) & \psi_3(x_2) \\
\psi_1(x_3) & \psi_2(x_3) & \psi_3(x_3)
\end{vmatrix}
$$

## Born-Oppenheimer Approximation

$$
\hat{H} = -\frac{1}{2m}\sum_i^n\grad_1^2-\frac{1}{4\pi\epsilon_0}\sum_A\sum_i\frac{Z_Ae^2}{|r_{Ai}|}+\frac{1}{4\pi\epsilon_0}\sum_i\sum_j\frac{1}{2}\frac{1}{|r_{ij}|}
$$

