# Denoising Diffusion Probabilistic Models

**Prerequisite**

<u>Markov chain</u>: The future state only depends on current state and not on the sequence of states that preceded it:

$$
P(x_{n+1}|x_n,x_{n-1},...x_0)=P(x_{n+1}|x_n)
$$

**The Forward Diffusion Process: Adding Noise**

The forward process or diffusion process is a predefined <u>Markov chain</u> that gradually adds Gaussian noise to the data sample $x_i$ from a real distribution $q(x_i)$. And this process happens with $T$ time steps by sequence, where at each time step $t$ $(t\in T)$, it gradually adds noise to the data in the opposite direction of sampling until signal is destroyed based on previous step $x_{t-1}$ to produce $x_t$

The transition probability distribution at each step t is defined as:

$$
q(x_t|x_{t-1})=\mathcal{N}(x_t;\sqrt{1-\beta_t}\,x_{t-1},\beta_t\mathbf{I})
$$

Where:

- $\beta_t$ is a small positive constant that determines the variance of the Gaussian noise added at timestep t. $\beta_t\mathbf{I}$ denotes the variance.
- $\beta_t$ values is defined as a variance schedule $(\beta_0, \beta_1,...,\beta_t)$, which can be linear, quadratic, cosine, or other functions, usually increasing with t.

> [!NOTE]
>
> **Question: $\sqrt{1-\beta_t}x_{t-1}$ is the mean value of the distribution, why not adding noise like: $x_t=x_{t−1}+\epsilon_t$  where $\epsilon_t ~\mathcal{N}(0,\beta_tI)$?**
>
> If we directly adding noise, the variance will be $\text{Var}(x_{t-1})+\beta_tI$. If we start with $x_0$, the after T steps, the variance of $x_t$ will be $\text{Var}(x_t)= \text{Var}(x_{t-1})+\sum_{i=1}^{T}\beta_i$, it is accumulated and grow uncontrollably. That's why we should we a scaled noise term $\sqrt{1-\beta_t}$  (since $\beta_t$ is a small positive value, typically between 0 and 1), which slightly "shrinking" the signal from the previous timestep before adding new noise.



The feature of this diffusion process is that, it can sample $x_t$ from distribution $q(x_t|x_0)$ at any arbitrary timestep t in closed form, this is achieved by a reparameterization trick:

$$
q(x_t|x_0)=\mathcal{N}(x_t;\sqrt{\bar{a_t}}\,x_0,(1-\bar{a_t})\mathbf{I})
$$

Where:

- $a_t=1-\beta_t$
- $\bar{a_t}=\prod_{s=1}^ta_s$





**The Reverse Diffusion Process: Denoising and Generation**

The goal of a diffusion model is to learn the reverse diffusion process, which transforms the noisy data at timestep $T$ (which is approximately pure noise) back into a clean data sample from the original distribution $q(x_0)$.

Assume we start from $p(\textbf{x}_T)=\mathcal{N}(\textbf{x}_T;0;\mathbf{I})$:

$$
p_{\theta}(\textbf{x}_{0:T})=p(\textbf{x}_T)\prod_{t=1}^T\,p_\theta(\textbf{x}_{t-1}|\textbf{x}_t)
$$

Unlike the forward process, the true reverse transition probability $q(\textbf{x}_{t−1}|\textbf{x}_t)$ is generally intractable because it requires knowing the distribution of all possible data points. However, it can be shown that if the forward diffusion steps are small enough $(\beta_t)$, the reverse transition probabilities are also approximately Gaussian and the distribution can be tractable when conditioned on $x_0$:

According to Bayes rule:

$$
q(x_{t-1}|x_t,x_0)=\frac{q(x_{t}|x_{t-1},x_0)\cdot q(x_{t-1}|x_0)}{q(x_t|x_0)}
$$

Due to the Markovian nature of the forward process, $q(x_t|x_{t-1},x_0)=q(x_t|x_{t-1})$

- $q(x_t|x_{t-1})=\mathcal{N}(x_t;\sqrt{1-\beta_t}\,x_{t-1},\beta_tI)$
- $q(x_{t-1}|x_0)=\mathcal{N}(x_{t-1};\sqrt{\bar{a}_{t-1}}\,x_0),(1-\bar{a}_{t-1})I$
- $q(x_t|x_0)=\mathcal{N}(x_t;\sqrt{\bar{a}_t}x_0,(1-\bar{a}_t)I)$

For a multivariate Gaussian $\mathcal{N}(x;\mu;\Sigma)$, the PDF is proportional to $\exp{(-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x - \mu))}$

So, the exponent $E_1=-\frac{1}{2\beta_t}||(x_t-\sqrt{1-\beta_t}\,x_{t-1})||^2$, $E_2=-\frac{1}{2(1-\bar{a}_{t-1})}||(x_{t-1}-\sqrt{\bar{a}_{t-1}}\,x_0)||^2$, $E_3=-\frac{1}{2(1-\bar{a}_t)}||(x_t-\sqrt{\bar{a}_t}x_0)||^2$

So, the exponent of $q(x_{t−1}∣x_t,x_0)$ is $E_1+E_2-E_3$, and we need to decompose and separate the quadric terms (e.g. $-\frac{1}{2}x_{t-1}^T\Sigma^{-1}x_{t-1}$) and the linear terms $x_{t-1}^T\Sigma^{-1}\mu$.

$$
q(x_{t−1}∣x_t,x_0)=N(x_{t−1};\tilde \mu_t(x_t,x_0),\tilde\beta_tI)
$$

Where:

- $\tilde \mu_t= \frac{\sqrt{\bar{a}_{t-1}}\beta_t}{1-\bar{a}_{t}}x_0+\frac{\sqrt{\bar{a}_t}(1-\bar{a}_{t-1})}{\bar{a}_{t-1}}x_t$
- $\tilde \beta_t=\frac{1-\bar{a}_{t-1}}{1-\bar{a}_{t}}\beta_t$




$$
p_{\theta}(\textbf{x}_{t-1}|\textbf{x}_T)=\mathcal{N}(\textbf{x}_{t-1};\mu_\theta(\textbf{x}_t,t),\sum_\theta(\textbf{x}_t,t))
$$




**Training Objective: Learning the Reverse Process**

The goal of training is to learn the parameters $\theta$ of the neural network $\epsilon_\theta$ such that the learned reverse distribution $p_\theta$ is as close as possible to the true reverse distribution $q$. This is typically achieved by maximizing the variational lower bound (VLB) on the marginal likelihood of the data $q(x_0)$.

Training is performed by optimizing the usual variational bound on negative log likelihood:

$$
\mathbb{E}[-\log{p(\textbf{x}_0)}]\leq\mathbb{E}_q[-\log\frac{p_\theta(\textbf{x}_{0:T})}{q(\textbf{x}_{1:T}|\textbf{x}_{0})}]=\mathbb{E}_q[-\log{p(\textbf{x}_T)}-\sum_{t=1}^T\log\frac{p(\textbf{x}_{t-1}|\textbf{x}_{t})}{q(\textbf{x}_t|\textbf{x}_{t-1})}]=L
$$

Recall that we can get $p(\textbf{x}_{t-1}|\textbf{x}_t)$ tractable by condition on $x_o$.

$p(x_{t-1}|x_t,x_0)=\frac{p(x_{t}|x_{t-1},x_0)\cdot p(x_{t-1},x_0)}{p(x_t,x_0)}\rightarrow q(x_{t}|x_{t-1})=\frac{q(x_{t-1}|x_t,x_0)\cdot q(x_t,x_0)}{q(x_{t-1},x_0)}$

$L=\mathbb{E}_q[-\log{p(\textbf{x}_T)}-\sum_{t=1}^T\log\frac{p_\theta(\textbf{x}_{t-1}|\textbf{x}_{t})}{q(\textbf{x}_t|\textbf{x}_{t-1})}]=\mathbb{E}_q[-\log{p_{\theta}(\textbf{x}_T)}-\sum_{t>1}^T\log\frac{p_\theta(\textbf{x}_{t-1}|\textbf{x}_{t})\cdot q(\textbf{x}_{t-1}|\textbf{x}_0)}{q(\textbf{x}_{t-1}|\textbf{x}_{t},\textbf{x}_0)\cdot q(\textbf{x}_t|\textbf{x}_0)}-\log{\frac{p_\theta(\textbf{x}_0|\textbf{x}_1)}{q(\textbf{x}_1|\textbf{x}_0)}}]$

$L=\mathbb{E}_q[-\log{p_\theta(\textbf{x}_T)}+\log{q(\textbf{x}_T|\textbf{x}_0)}-\sum_{t>1}^T\log\frac{p_\theta(\textbf{x}_{t-1}|\textbf{x}_{t})}{q(\textbf{x}_{t-1}|\textbf{x}_{t},\textbf{x}_0)}-\log{\frac{p_\theta(\textbf{x}_0|\textbf{x}_1)}{q(\textbf{x}_1|\textbf{x}_0)}}]\\=\mathbb{E}_q[-\log{p_\theta(\textbf{x}_T)}+\log{q(\textbf{x}_T|\textbf{x}_0)}-\sum_{t>1}^T\log\frac{p_\theta(\textbf{x}_{t-1}|\textbf{x}_{t})}{q(\textbf{x}_{t-1}|\textbf{x}_{t},\textbf{x}_0)}-\log{\frac{p_\theta(\textbf{x}_0|\textbf{x}_1)}{q(\textbf{x}_1|\textbf{x}_0)}}]$


$$
L=\mathbb{E}_q \left[
\underbrace{D_{\mathrm{KL}}\left(q(\mathbf{x}_T|\mathbf{x}_0) \,\|\, p(\mathbf{x}_T)\right)}_{L_T}
+ \sum_{t > 1}
\underbrace{D_{\mathrm{KL}}\left(q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0) \,\|\, p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)\right)}_{L_{t-1}}
- \underbrace{\log p_\theta(\mathbf{x}_0|\mathbf{x}_1)}_{L_0}
\right]
$$


- The term $\log \frac{p_\theta(\mathbf{x}_0|\mathbf{x}_1)}{q(\mathbf{x}_1|\mathbf{x}_0)}$ is **isolated** from the summation.

- This is often done because this first transition ($\mathbf{x}_0 \leftrightarrow \mathbf{x}_1$) needs to be handled carefully—especially if we’re conditioning on the observed data $\mathbf{x}_0$, which introduces asymmetry.





[1]: https://proceedings.neurips.cc/paper_files/paper/2020/hash/4c5bcfec8584af0d967f1ab10179ca4b-Abstract.html	" Ho, J.; Jain, A.; Abbeel, P. Denoising Diffusion Probabilistic Models. In Advances in Neural Information Processing Systems; Curran Associates, Inc., 2020; Vol. 33, pp 6840–6851."

