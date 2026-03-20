# E(n) Equivariant Graph Neural Networks

##  1. Background

### 1.1. Equivariance

Let $T_g:X\rightarrow X$ be a set of transformations on $X$ for the abstract group $g\in G$,  We say a function $\phi: X\rightarrow Y$ is equivariant to $g$ if there exists an equivalent transformation on its output space $S_g:Y\rightarrow Y$:
$$
\phi(T_g(X)) = S_g(\phi(X))
$$
In machine learning, we represent the $\phi$ as an nonlinear function, and $\mathbf{x}=\{x_1,..,x_M\}\in\mathbb{R}^{M\times n}$ as a set of $M$ dimensional point embedded in $n$ dimensional space.

Three types of equivariance on a set of particles x:

- Translation equivariance, translating the input by $g\in \mathbb{R}^n$ results in an equivalent translation of the output: e.g. Let $\mathbf{x}+g$ to be shorthand for $(x_1+g, ..., x_M+g)$, then $\mathbf{y}+g = \phi(\mathbf{x})+g=\phi(\mathbf{x}+g)$
- Rotation (and reflection) equivariance, for any orthogonal matrix $Q\in \mathbb{R}^{n\times n}$, let $Q\mathbf{x}$ to be shorthand of $(Qx_1,Qx_2,...,Qx_M)$. Then rotating the input results in an equivalent rotation of the output $Q\mathbf{y}=Q\phi(\mathbf{x})=\phi(Q(\mathbf{x}))$
- Permutation equivariance. Permuting the input results in the same permutation of the output $P(\mathbf{y})=P(\mathbf{\phi(x)})=\phi(P(\mathbf{x}))$, where $P$ is a permutation on the row indexes.

### 1.2. Graph Neural Networks

Graph Neural Networks are permutation equivariant networks that operate on graph structured data, given a graph $\mathcal{G}=(\mathcal{V},\mathcal{E})$, with nodes $v_i\in \mathcal{V}$ and edges $e_{ij}\in\mathcal{E}$, we can define a graph convolution layer:
$$
\begin{aligned}
m_{ij}&=\phi_e(h_i^l,h_j^l,a_{ij})\\
m_i&=\sum_{j\in\mathcal{N(i)}}m_{ij}\\
h_i^{l+1}&=\phi_h(h_i^l,m_i)

\end{aligned}
$$

- $h_i^l,h_j^l$ are the embedding of $v_i,v_j$ node at layer $l$
- $a_{ij}$ is the edge attributes
- $\mathcal{N(i)}$ is the set of neighbors of node $v_i$



## 2. Equivariant Graph Neural Networks

The Equivariant Graph Convolutional Layer (EGCL) takes as input the set of node embeddings $h^l=\{h_0^l,...,h_{M-1}^l\}$, coordinate embeddings $x^l=\{x_0^l,...,x_{M-1}^l\}$ and edge information $\mathcal{E}=(e_{ij})$ and outputs a transformation on $h^{l+1}$ and $x^{l+1}$. Which means $h^{l+1},x^{l+1}=\text{EGCL}(h^l,x^l,\mathcal{E})$, to be more detail, the equation that define this layer are the following:
$$
\begin{align}
m_{ij}&=\phi_e(h^l_i,h^l_j,\norm{x_i^l-x_j^l}^2,a_{ij})\\ 
x_i^{l+1}&=x_i^l+C\sum_{j\neq i}(x_i^l-x_j^l)\phi_x(m_{ij})\\
m_i&=\sum_{j\neq i}m_{ij}\\
h_i^{l+1}&=\phi_h(h_i^l,m_{i})

\end{align}
$$

### 2.1. Proof of $\mathbf{E(n)}$ equivariance

The Message block should satisfy the translation equivariant on $\mathbf{x}$ on any translation vector $g\in \mathbb{R}^n$ and it should also be rotation and reflection equivariant on $\mathbf{x}$ for any orthogonal $Q\in \mathbb{R}^{n\times n}$
$$
Q\mathbf{x}^{l+1} +g,\, \mathbf{h}^{l+1}=\text{EGCL}(Q\mathbf{x}^l+g, \mathbf{h}^l)
$$
Since the embedding vector $h$ is based on node $v_i$, so we do not encode any information about the absolute position or orientation of $x_0$ into $h_0$. which means the $h$ is invariant to the $E(n)$ transformations. Then the message in equation (3) gained by the edge and nodes are invariant to translations $\norm{x_i^l+g-x_j^l+g}^2=\norm{x_i^l-x_j^l}^2$, and it's invariant to the rotation and reflections: $\norm{Qx_i^l-Qx_j^l}^2=(x_i^l-x_j^l)^\top Q^\top Q(x_i^l-x_j^l)=(x_i^l-x_j^l)^\top\mathbf{I}(x_i^l-x_j^l)=\norm{x_i^l-x_j^l}^2$,  such that the edge operation becomes invariant:
$$
m_{ij}=\phi_e(h^l_i,h^l_j,\norm{(Qx_i^l+g)-(Qx_j^l+g)}^2,a_{ij})=\phi_e(h^l_i,h^l_j,\norm{x_i^l-x_j^l}^2,a_{ij})
$$
The we want to prove the equation (4):
$$
Qx_i^{l+1}+g=Qx_i^l+g+C\sum_{j\neq i}(Qx_i^l+g-Qx_j^l+g)\phi_x(m_{ij})
$$
derivation:
$$
\begin{aligned}
Qx_i^l+g+C\sum_{j\neq i}(Qx_i^l+g-Qx_j^l+g)\phi_x(m_{ij})&=Qx_i^l+g+C\sum_{j\neq i}(Qx_i^l-Qx_j^l)\phi_x(m_{ij})\\
&=Q\Big(x_i^l+C\sum_{j\neq j}(x_i^l-x_j^l)\phi_x(m_{ij})\Big)+g\\
&=Qx_i^{l+1}+g
\end{aligned}
$$



### 2.3. Extending EGNNs for vector type representations

In some scenarios, it can be useful to obtain an estimate of velocity of the particle at each layer, and also in some cases the initial velocity is not 0. By slightly modify the equation (4):
$$
\begin{aligned}
\mathbf{v}_i^{i+1}&=\phi_v(h^l)\mathbf{v}_i^\text{init}+C\sum_{i\neq j}(x_i^l-x_j^l)\phi_x(m_{ij})\\
\mathbf{x}_i^{l+1}&=\mathbf{x}_i^l+\mathbf{v}_i^{l+1}
\end{aligned}
$$
Now we extends the EGCL layer as $h^{l+1},\mathbf{x}^{l+1},\mathbf{v}^{l+1}=\textbf{EGCL}(h^l,\mathbf{x}^l,\mathbf{v}^l,\mathcal{E})$, the only difference is that now we broke down the coordinate

update (eq. 4) in two steps, first we compute the velocity $\mathbf{v}_i^{l+1}$  and then we use this velocity to update the position $\mathbf{x}_i^l$. The initial velocity $\mathbf{v}_i^\text{init}$ is scaled by a new function $\phi_v(h^l):\mathbb{R}^d\rightarrow \mathbb{R}^1$ that maps the node embedding $h_i^l$ to a scalar value.







[1]: Satorras, V.G., Hoogeboom, E., Welling, M., 2022. E(n) Equivariant Graph Neural Networks. https://doi.org/10.48550/arXiv.2102.09844

