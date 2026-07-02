# Review



## Computer and Computation

### Hardware

#### Von Neumann Architecture

<img src="assets/computer_von_neumann-02b08dc96e57e667cb872a2ca2293a7e.png" style="zoom:50%;" >

- **Control Unit (CU)**: This component directs the flow of data and operations between the CPU and other parts of the computer.
- **Arithmetic Logic Unit (ALU)**: The ALU performs arithmetic and logic operations using logic circuits or gates.
- **Registers**: These are very fast memory locations built directly inside the CPU core, used to store data temporarily during processing.
- **Cache**: This is high-speed memory that stores instructions and frequently accessed data to speed up processing.



#### Memory

- Register
- Cache memory 
- Main memory (RAM)
- External storage (SSDs, etc.)





#### Graphics Processing Unit (GPU)

GPUs come in two main types: **integrated GPUs (iGPUs)** and **discrete GPUs (dGPUs)**. Integrated GPUs are built into the same chip as the CPU and use the system’s RAM as video memory (VRAM). In contrast, discrete GPUs are separate components with their own dedicated VRAM, which allows for better performance in graphics-intensive tasks.



| Feature           | CPU (Central Processing Unit)                                | GPU (Graphics Processing Unit)                               |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Primary Function  | General-purpose processing                                   | Specialized for parallel processing and graphics rendering   |
| Architecture      | Few powerful cores                                           | Thousands of smaller cores                                   |
| Clock Speed       | Higher (typically 2-5 GHz)                                   | Lower (typically 1-2 GHz)                                    |
| Parallelism       | Limited parallelism                                          | High parallelism                                             |
| Memory            | Uses system RAM and cache                                    | Uses dedicated VRAM (for discrete GPUs)                      |
| Flexibility       | Highly flexible, suitable for a wide range of tasks          | Less flexible, optimized for specific tasks                  |
| Power Consumption | Generally lower                                              | Generally higher                                             |
| Use Cases         | Running operating systems, applications, and general computing tasks | Graphics rendering, scientific computing, machine learning, AI, cryptomining |



### Software

Firmware (software) often referred to as BIOS (Basic Input/Output System). The operating system (OS) is the backbone of any computer system, managing both hardware and software resources. It handles processes, manages the filesystem, and oversees input/output (I/O) operations. The OS ensures that different programs and users running on the computer do not interfere with each other, providing a stable and efficient environment for applications to run.

#### Scaling

This efficiency is often described using Big O notation, which classifies algorithms based on their time complexity.

- $O(1):$ For example, accessing an array element by its index is an operation that takes constant time, denoted as O(1). This means the time required to perform the operation does not depend on the size of the array.
- $O(N):$ Linear scaling, represented as O(N), occurs when the time required to complete a task grows directly in proportion to the size of the input data. An example of this is iterating through a list or reading a file line by line.
- $O(N^2):$ Quadratic scaling, or O(N2), happens when the time required grows with the square of the input size. This is common in tasks involving nested loops, such as molecular-level simulations
- $O(N\log N):$ Logarithmic scaling, denoted as O(N log N), is typical for algorithms like the Fast Fourier Transform (FFT), which is used in signal processing and other applications.
- $O(2^N):$ Exponential scaling, represented as O(2N2*N*), occurs in algorithms that solve problems recursively or involve combinatorial tasks. These algorithms can become impractical for large input sizes due to their rapidly increasing time requirements.

#### Parallel computing

$S$ represents the speedup, $N$ is the number of processors, and $B$ is the fraction of the code that is executed serially (i.e., cannot be parallelized). 
$$
S=\frac{N}{BN+(1-B)}
$$

### Cost of computation

**Moore's Law:** The number of transistors in an integrated circuit doubles every two years





## Database

### Types of Databases

#### SQL Databases (Relational Databases)

Relational databases store data in tables with rows and columns, and use Structured Query Language (SQL) to interact with the data. Each table contains records (rows) and fields (columns). Relationships between tables are established using keys, such as primary keys and foreign keys. Examples of relational databases include MySQL, PostgreSQL, and SQLite.

| Feature        | SQL Databases                                           | NoSQL Databases                                              |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Data Model     | Relational (tables with rows and columns)               | Non-relational (key-value, document, graph, or column-based) |
| Schema         | Fixed schema; changes require migrations                | Flexible or schema-less; adapts to evolving data needs       |
| Query Language | SQL (Structured Query Language)                         | Varies (e.g., MongoDB Query Language, CQL for Cassandra)     |
| Scalability    | Vertical scaling (adding more power to a single server) | Horizontal scaling (adding more servers)                     |
| Consistency    | Strong consistency enforced via ACID properties         | Often eventual consistency; trade-offs between consistency and performance |
| Use Cases      | Transactions, complex queries, structured data          | Big data, real-time analytics, unstructured/semi-structured data |
| Examples       | MySQL, PostgreSQL, SQLite                               | MongoDB, Cassandra, Redis, Neo4j                             |





## Structures

### Site 

A site in a crystal structure refers to a specific location within the unit cell where an atom, ion, or molecule resides. Each site is characterized by its position, species, occupation, and various properties that define its behavior within the crystal lattice, called site properties.

#### Position

**conversion between fractional coordinates and cartesian coordinates**
$$
\left[\begin{array}{ccc}x\\y\\z\end{array}\right]=\left[\begin{array}{ccc}a_{x}&b_x&c_x\\a_y&b_y&c_y\\a_z&b_z&c_z\end{array}\right]\left[\begin{array}{ccc}u\\v\\w\end{array}\right]
$$
Where $x,y,z$ are cartesian coordinates. $\mathbf{a,b,c}$ are lattice vectors, $u,v,w$ are fractional coordinates.



### Wyckoff Positions

Wyckoff positions provide a systematic way to describe the locations of atoms within a crystal’s unit cell, considering the crystal’s inherent symmetry.  Each Wyckoff position is denoted by a letter (e.g., *a*, *b*, *c*, ...) and has an associated multiplicity and site symmetry.



### Unit cell

Any position can be represented by:
$$
\mathbf{r}=u\mathbf{a}+v\mathbf{b}+z\mathbf{c}
$$

### Bravais Lattice

<img src="assets/crystal_system.png" style="zoom:50%;" >



### Primitive vs Conventional Unit Cells

- The primitive unit cell contains exactly one lattice point per cell and has the smallest possible volume. While it is mathematically elegant, it often doesn’t clearly show the crystal’s symmetry. In crystallographic notation, it is denoted by ‘P’.
- The conventional unit cell may contain more than one lattice point and is larger than the primitive cell. It better displays the crystal’s symmetry and is commonly used in crystallography. Conventional unit cells can be body-centered (denoted as I), face-centered (F), or base-centered (A,B,C).

<img src="https://mle4217-5219.matsci.dev/build/primitive_cell-e4a5c294cafb4a6edaa7bbfad12dac6a.png" alt="Primitive cell are not unique and can be chosen in different ways. The figure shows three different primitive cells for a lattice." style="zoom:50%;" />

Choosing a primitive unit cell is not **unique**, and different choices can be made based on the crystal structure’s symmetry. Niggli reduction is a method to convert a conventional unit cell to a unique primitive unit cell by transforming the lattice vectors to their shortest form.



### Symmetry







### Structure Prototypes







### Reciprocal Space

Given direct lattice vectors **a**, **b**, and **c**, the reciprocal lattice vectors **b\***, **c\***, and **a\*** are defined as:
$$
\mathbf{a}^*=\frac{2\pi(\mathbf{b}\times \mathbf{c})}{\mathbf{a}(\mathbf{b}\times \mathbf{c})},\mathbf{b^*}=\frac{2\pi(\mathbf{a}\times \mathbf{c})}{\mathbf{a}(\mathbf{b}\times \mathbf{c})},\mathbf{c^*}=\frac{2\pi(\mathbf{a}\times \mathbf{b})}{\mathbf{a}(\mathbf{b}\times \mathbf{c})}
$$


### Defect

#### Point defectss

<img src="assets/defects.png" alt="Various types of point defects in crystalline materials." style="zoom: 33%;" />





### Interface

Interfaces can be broadly categorized based on the degree of lattice matching between the adjacent materials: **coherent, incoherent, and semi-coherent.** A coherent interface exhibits perfect lattice matching, while an incoherent interface displays a complete mismatch. Semi-coherent interfaces represent an intermediate state, accommodating some degree of mismatch through periodic defects.



### Noncrystalline Materials

#### Radial Distribution Function (RDF)

<img src="https://mle4217-5219.matsci.dev/build/rdf-f020f0aae52ce6d932263742aec0bad8.png" alt="Radial Distribution Function (RDF) and examples of solid, liquid, and gas RDFs." style="zoom:50%;" />
$$
g(r)=\frac{1}{\rho}\cdot\frac{dn(r)}{dV_r}=\frac{V}{N}\cdot\frac{dn(r)}{4\pi r^2dr}
$$

## Model and theories

### Statistical mechanics

#### Microstates and Macrostate

In statistical mechanics, a system is described by its microstates and macrostates. A microstate is a specific configuration of the particles in the system (atomic positions, molecular configurations), while a macrostate is a collection of microstates that share certain macroscopic properties, such as temperature, pressure, and volume.

#### Phase Space

The microstate is characterized by the positions (**r**) and momenta (**p**) of all the particles in the system. The collection of all possible microstates of a system is called the phase space (Γ(**r**,**p**)), which represents all the possible configurations of the system.

### Ensemble

An ensemble is a probability distribution over microstates in phase space. Different ensembles correspond to different macroscopic constraints, such as temperature (*T*), pressure (*P*), volume (*V*), and number of particles (*N*).

**NVE**
$$
P(\Gamma)=\frac{1}{\Omega(E)}
$$
**NVT**
$$
P(E)=\frac{1}{Z}e^{-\beta E}\\
Z=e^{-\beta E}
$$
**NPT**
$$
P(E,V) = \frac{1}{Z}e^{-\beta H}\\
Z=\sum e^{-\beta H}=\sum_V\sum_\text{states}e^{-\beta(E+PV)}
$$


Temperature is related to the kinetic energy of the particles in the system. For a classical system with ***f*** quadratic degrees of freedom, the temperature is given by:
$$
T=\frac{2K}{fk_B}
$$

- **K** is the kinetic energy
- $f$ is the degree of freedom. For an unconstrained three-dimensional system, $f\approx3N$ if overall translation is removed, then $f=3N−3.$



## Optimization

### Local optimization

#### BFGS (Broyden-Fletcher-Goldfarb-Shanno)

BFGS is a *quasi-Newton* method. Newton’s method uses the *Hessian* (matrix of second derivatives) to find the optimum. However, calculating the Hessian can be computationally expensive. BFGS *approximates* the Hessian iteratively, making it more practical for many problems.

BFGS iteratively updates an approximation to the *inverse* Hessian, denoted as $H_k=H^{-1}$. The update rule uses the change in the gradient and the change in the position to improve the approximation:
$$
H_{k+1}=(I-\rho_ks_ky_k^T)H_k(I-\rho_ky_ks_k^T)+\rho_ks_ks_k^T
$$

- $s_k=x_{k+1}-x_k=\Delta x$
- $y_k=\nabla f(x_{k+1})-\nabla f(x_k)$
- $\rho_k=\dfrac{1}{y_k^Ts_k}$

$$
I^2-\rho_ks_ky_k^TI-\rho_ky_ks_k^TI+\rho_ks_ky_k^T\rho_ky_ks_k^T\\
s_k=H_{k+1}y_k
$$

### Global optimization 

#### Simulated Annealing

Starts at a high “temperature” (allowing exploration) and gradually cools down (focusing on exploitation). Accepts moves that worsen the objective function with a probability that decreases with temperature.



### Transition state theory

Knowing the energy of the transition state (the *activation energy*) is crucial for understanding the kinetics of these processes. The *minimum energy path (MEP)* is the path connecting two minima that passes through the transition state with the lowest possible energy barrier. The Nudged Elastic Band (NEB) method is a powerful technique for finding the MEP.

![Picture1](assets/Picture1.png)

NEB creates a series of intermediate configurations (“images”) between the initial and final states, forming a “band” or “chain” of states. These images are connected by fictitious “springs,” and the forces acting on the images are carefully modified to guide the band towards the MEP.



1. Create a set of $N$ images between the initial and final state on the PES, using simple linear interpolation between the initial and final state as the first elastic band. Denote the states of the images $r_1, r_2,..., r_N$, where $r_1$ is initial state and $r_N$ is the final state.
2. Introduce the spring forces between adjacent states, these spring force tends to stretch/shrink along the path of the elastic band. The force acting on image $i$ is:

$$
\mathbf{F}_s^i=k(|\mathbf{r_{i+1}}-\mathbf{r_i}|-|\mathbf{r_i}-\mathbf{r_{i-1}}|)\mathbf{\tau_i}
$$

- $k$ is the elastic constant of the band (a parameter that controls the strength of the spring forces),
- $|\mathbf{r_{i+1}}-\mathbf{r_i}|$ is the distance between the image  $i+1$ and $i$
- $\mathbf{\tau}_i$ is the unit tangent vector of the band at image $i$

3. Force projection: The true forces acting on each image (the negative gradient of the potential energy, $\mathbf{F_\text{true}}=-\nabla V(r_i)$ are projected to prevent the band from simply sliding down to the initial or final minima.
   - Calculate the true force $\mathbf{F_\text{true}^i}=-\nabla V(r_i)$

   - Remove the parallel component of the true force, which prevents the slide down towards minima directly. And remain the perpendicular force component: $\mathbf{F_\perp}^i = -\nabla V(r_i) + (\nabla V(r_i)\cdot\mathbf{\tau_i})\mathbf{\tau_i}$
   - Remove the Perpendicular component of the spring force, this allows the band to find the MEP without being constrained to a straight line.

4. Find the total force: $\mathbf{F_\text{tot}} = \mathbf{F_\perp^i} + \mathbf{F_s^i}$

5. Optimize the position according to the image state by moving them towards the direction of the force (e.g. ):

   - Gradient descent: $r_{i}^\text{new}=r_i^\text{old} + \alpha\mathbf{F_\text{tot}^i}$
   - Velocity Verlet: A common choice in molecular dynamics simulations.
   - BFGS or other quasi-Newton methods: Can be more efficient than gradient descent.

6. Tangent estimation $\tau$: 

   - Energy-weighted tangent: $\tau_i=\left\{\begin{aligned}r_{i+1}-r_i\rightarrow \text{If }V(r_{i+1})>V(r_i)>V(r_{i-1})\\r_{i}-r_{i-1}\rightarrow \text{If }V(r_{i+1})<V(r_i)<V(r_{i-1})\end{aligned}\right.$
   - Bicparabolic interpolation.

Since there are two problems from conventional elastic band method:

$F_\text{true}^i$: will pull the image directly towards the minima, preventing it move to the saddle point

$F_s^i$: tries to stretch the image along the path, making the band becomes a straight line, pulling the dot off the curvy trail.







## High-throughput computation

### Thermodynamics

#### Formation energy

The formation energy ΔEfΔ*E**f* of a compound is a key quantity for assessing the stability of a compound at 0 K. 
$$
\Delta E(A_xB_y)=E(A_xB_y)-xE(A)-yE(B)
$$







