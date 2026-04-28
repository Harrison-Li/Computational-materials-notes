# Bayesian Optimization with Sparse Axis-Aligned Subspaces

## Gaussian Process

### Defining the Kernel

A Gaussian Process assumes that similar inputs should produce similar outputs. To measure this "similarity," we use a covariance function, or kernel. 
$$
K^\phi(\mathbf{x,y})=\sigma_k^2\exp{\Big\{-\frac{1}{2}\sum_i\rho_i(x_i-y_i)^2\Big\}}
$$

- $K^\phi(\mathbf{x,y})$: The kernel function evaluating the covariance (similarity) between two input vectors $x$ and $y$.
- $\sigma_k^2$: The signal variance. This scales the overall output of the function, determining the average distance of the function's values away from its mean.
- $\rho_i$: The inverse squared length scale for the $i-th$ dimension (often written as $1/l_i^2$). It dictates how rapidly the function changes along that specific dimension. A large $\rho_i$ means the function changes very quickly along that axis.
- $\phi$: The collective set of all hyperparameters defining the kernel, specifically $\phi\{\rho_{1:D};\sigma_k^2\}$.

### The Joint Density

This equation defines how the inputs map to the true, hidden function values, and how those true values relate to the noisy data we actually observe.
$$
p(\mathbf{y},\mathbf{f}|\mathbf{X})=\underset{\text{Likehood}}{p(y|\mathbf{f},\mathbf{X})}\times\underset{\text{prior}}{p(\mathbf{f}|\mathbf{X})}
$$

$$
p(\mathbf{y,f|X})=\mathcal{N}(\mathbf{y|f},\sigma^2\mathbf{I}_{NN})\mathcal{N}(\mathbf{f}|0,\mathbf{K}_{\mathbf{XX}}^\phi)
$$

- $p(\mathbf{y,f|X})$: The joint probability density of observed target and the latent function values, conditioned on the input $\mathbf{X}$
- $\mathbf{X}$: A $N\times D$ matrix contains all N of our observed input data points.
- $\mathbf{I}_{NN}$: A $N\times N$ Identity matrix $\mathbf{I}_{NN}$
- $\mathbf{K_{XX}}^\phi$: The $N\times N$ covariance matrix formed by evaluating the kernel $K_\phi$ between every possible pair of points in the training set $\mathbf{X}$.
- $\sigma^2$: The variance of the independent observation noise.

### The Marginal Likelihood

In practice, we don't know the latent function values $f$, and we don't really care about them; we only care about the data we can measure.
$$
p(\mathbf{y|X},\phi)=\int d\mathbf{f}\cdot p(\mathbf{y,f|X})=\mathcal{N}(\mathbf{y},\mathbf{K_{XX}}^\phi+\sigma^2\mathbf{I}_{NN})
$$

- $p(\mathbf{y∣X},\phi)$: The marginal likelihood (or evidence). This is the probability of observing our specific targets $\mathbf{y}$ given our inputs $\mathbf{X}$ and our chosen hyperparameters $\phi$.

Then the marginal likelihood is completely defined by the data's covariance plus the noise variance. This equation is heavily used to optimize the hyperparameters $\phi$ during training by maximizing this probability.

### Making predictions 

Once the GP is trained, we want to predict the function's value at a completely new, unobserved point. A GP doesn't just give you a single number; it gives you a full probability distribution (a mean and a variance/uncertainty) for that new point. In mathematics: $P(\mathbf{f}^*|y)$

The posterior distribution of GP at query point $\mathbf{x^\star}\in D$ is the Normal distribution $\mathcal{N}(\mu_\mathbf{f}(\mathbf{x^\star}),\sigma_\mathbf{f}(\mathbf{x}^\star)^2)$, where the $\mu_\mathbf{f}(\mathbf{x^\star}),\sigma_\mathbf{f}(\mathbf{x}^\star)^2$ are given by:
$$
\begin{aligned}
\mu_\mathbf{f}(\mathbf{x^*})&={k_{*\mathbf{x}}^\phi}^T(\mathbf{K_{XX}}^\phi+\sigma^2\mathbf{I}_{NN})^{-1}\mathbf{y}\\
\sigma_\mathbf{f}(\mathbf{x^*})&=k_{**}^\phi-{k_{*\mathbf{x}}^\phi}^T(\mathbf{K_{XX}}^\phi+\sigma^2\mathbf{I}_{NN})^{-1}k_{*\mathbf{x}}^\phi
\end{aligned}
$$

- $\mathbf{x}^∗$: A new "query" point in the input space where we want to make a prediction.
- $k_{∗\mathbf{X}}^\phi$: An N-dimensional column vector containing the kernel similarities between the new query point $x^∗$ and all N original training points in $\mathbf{X}$.



### EXPECTED IMPROVEMENT

$$
\text{EI}(\mathbf{x}|y_\min,\phi)= \mathbb{E}_{p(f(\mathbf{x})|\phi,\mathcal{H})}[u(\mathbf{x}|y_\min)]
$$



## BAYESIAN OPTIMIZATION WITH SPARSE AXIS-ALIGNED SUBSPACES
