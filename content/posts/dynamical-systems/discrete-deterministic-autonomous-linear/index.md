---
title: Discrete Deterministic Observable Autonomous Linear Dynamical System
date: 2025-04-24T19:35:48-04:00
author: Aman Shah
draft: true
math: true
---


# Introduction
This is a note meant to exposit a ubiquitous system in a perspicuous fashion. For this note verbose description, and avoidance of shorthand is used so as not to confuse ideas and terminology. This note is one of several in a series meant to be read together that give an overview of some key ideas in dynamical and control systems theory.

# Discrete Deterministic Autonomous Linear Dynamical System

\\[
\begin{align*}
	\mathbf{x}_{t+1} &= \mathbf{A}\mathbf{x}_{t}\\
\end{align*}
\\]

- **Discrete** := the states and their transitions are described with respect to non-negative integer indices(i.e the states are $\mathbf{x}_0, \mathbf{x}_1, \mathbf{x}_2, \ldots$)  \
- **Deterministic** := the transition dynamics and consequently the states have no dependence on random behavior. In some cases it is useful to consider random noise as affecting the transition from one state to the next.
- **Autonomous** := this means the transition dynamics $f(\mathbf{x}):= \mathbf{A}\mathbf{x}$ have no dependence on $t$ which means the next state depends only the current state, and not the current time.
- **Linear** := the transition dynamics are governed by a linear map taking the states as input
- **Dynamical System** := we are describing the system by how the states evolve over time

# Discrete Deterministic Autonomous Linear Observed System

\\[
\begin{align*}
	\mathbf{x}_{t+1} &= \mathbf{A} \mathbf{x}_{t}\\
	\mathbf{y}_{t} &= \mathbf{C} \mathbf{x}_{t}  \\
\end{align*}
\\]

All the terminology applies as before with the addition of a new term.\
\
- **Observed** := we have a dynamical system as before with an additional observation equation. The adjectives beforehand apply to both the transition dynamics and the observation equation respectively.


# Computing Future States and Observations

In this case computing future states $\mathbf{x}_{t}$, and observations $\mathbf{y}_{t}$ is very simple and simply involves unrolling the recursive formula given by the transition dynamics.

\\[
\begin{align*}
	\mathbf{x}_{t} &= \mathbf{A}^{t-t_{0}} \mathbf{x}_{0} \\
	\mathbf{y}_{t} &= \mathbf{C} \mathbf{A} ^{t-t_{0}} \mathbf{x}_{0}
\end{align*}
\\]

These formulae are sufficient for much of the latter exposition so one could skip ahead and start reading stability. However the spectral view of stability will require rewriting the above formula in a more convenient form using the tools of linear algebra

# Mathematical Formalism

For these notes we assume the states are elements of a finite dimensional normed vector space over a field such as the real or complex numbers. In particular this makes the states part of a finite dimensional Banach space.

Further, we assume there is a norm on the space of linear operators. We note this is a generic norm, we do not assume compatibility with the vector space norm, or that the norm is an induced operator norm.  

## Using Coordinates
If we have a basis $\mathbf{B}$ we can describe the system in coordinates using the language of matrices and vectors. If we let $x$ be the coordinate vector of $\mathbf{x}$ and $A$ be the coordinate representation of $\mathbf{A}$ we have the following equations involving vectors and matrices.
\\[
\begin{align*}
	x_{t} &= A^{t-t_{0}} x_{0} \\
	y_{t} &= C A^{t-t_{0}} x_{0}
\end{align*}
\\]
In these notes we will default to using different fonts, but same letter for different coordinate representations of the same object. We also have many properties that depend on the norm. The norm depends on the abstract vector, however we can extend our reasoning to coordinates by using the norm $\|x\| := \|\mathbf{x}\|$ on our coordinate vectors. This will let us reason about properties dependent on norms of our abstract vectors, by using a norm on the coordinate vector space.

## Exploiting Similarity(using the Jordan Normal Form)

Note: This section is likely worth skipping until you see the need for it in subsequent sections. We place it here in case the reader prefers this order or if no knowledge of the Jordan form is had then the reader can acquire it beforehand. 

A useful tool in linear algebra is every matrix is similar to a block diagonal matrix with Jordan blocks. This means that $A = P\mathsf{A}P^{-1}$ where $\mathsf{A}$ is block diagonal with Jordan blocks. We can use this structure to understand future states and observations as follows,\
\
\\[
\begin{align*}
	x_{t} &= A^{t-t_{0}}x_{0} \\
	x_{t} &= (PJP^{-1})^{t-t_{0}}x_{0} \\
			  &= PJ^{t-t_{0}}P^{-1}x_{0} \\
 \end{align*}
\\]

We will use $\mathsf{x}$ and $\mathsf{A}$, to denote the coordinate representations of $\mathbf{x}$ and $\mathbf{A}$ with respect to the Jordan basis. By our previous section,\
\
\\[
\begin{align*}
	\mathsf{x}_{t} &= \mathsf{A}^{t-t_{0}} \mathsf{x}_{0} \\
	\mathsf{y}_{t} &= \mathsf{C} \mathsf{A}^{t-t_{0}} \mathsf{x}_{0}
\end{align*}
\\]


Every Jordan block $\mathsf{A}_i$ is of the form $\lambda_i I + N$ which leads to the following expansion when $k:=t-t_{0}$ is larger than the dimension of the state space $n$. We consider this case because we are interested in long term behavior in subsequent sections so considering $k$ large enough is the time of interest.

\\[
\begin{align*}
		\mathsf{A}_{i}^{k} &= (\lambda_{i} I + N)^{k} \\
		&= \binom{k}{0}\lambda_{i}^{k}I + \binom{k}{1}\lambda_{i}^{k-1}N + \ldots + \binom{k}{n-1}\lambda_{i}^{k-(n-1)}N^{n-1}
			\end{align*}
\\]

For clarity we will write out the first few coefficients explicitly.
\
\\[
\begin{align*}
&\lambda_{i}^k \\\\
&\frac{k}{1}\lambda_{i}^{k-1}\\\\
&\frac{k(k-1)}{2!}\lambda_{i}^{k-2} \\\\
&\frac{k(k-1)(k-2)}{3!}\lambda_{i}^{k-3} \\\\
&\vdots \\\\
&\frac{k(k-1)(k-2)\ldots(k-(n-2))}{(n-1)!}\lambda_{i}^{k-(n-1)} 
\end{align*}
\\]

Notice each fraction has a numerator that is a polynomial of the  form $k^r$ and they are being multiplied by an exponential $\lambda_{i}^{k-r}$. If we ignore all the terms that don’t depend on time we have an expression that grows like $k^{r}\lambda_{i}^{k}$.



# Stability For Dynamical Systems 
This sections requires having read the note on stability for autonomous dynamical systems. 

## Equilibrium States[^1]
An equilibrium state is a state from which the system does not deviate; that is if we start at $\mathbf{e}$ and follow the transition dynamics we stay at $\mathbf{e}$. In our particular system, this means $\mathbf{e}$ is an equilibrium if and only if $\mathbf{A}\mathbf{e}=\mathbf{e}$. 

We begin by analyzing if there any equilibrium states, if so how many and is there anything else we can say about them?

Since our equilibrium state must map to itself under $\mathbf{A}$, and every matrix maps $0$ to itself, we have at least $1$ equilibrium state being the origin. Any nonzero solution of $\mathbf{A}\mathbf{e}=\mathbf{e}$ are eigenvectors corresponding eigenvalue $1$. This means that we either have $1$ equilibrium state, the origin, or infinitely many where the infinitely many equilibrium states form a subspace.

### What Stability Reveals About Equilibrium States 
An occurrence that is not immediately obvious is that if an equilibrium state is stable then all equilibrium points are stable. Trivially $0$ is an equilibrium state. We will simply show if any equilibrium state $\mathbf{e}$ is stable if and only if $0$ is stable.\
\
Let $\mathbf{e}$ be a non-zero equilibrium state. Then if the origin is stable, then for all positive $\epsilon$ there exists a positive $\delta$ such that if $|\mathbf{x}_{0}| < \delta$ then  $|\mathbf{x}_{t}| < \epsilon$. Our goal is to show for all positive $\epsilon$ there there exists a positive $\delta$ such that $|\mathbf{x}_{0} - \mathbf{e}| < \delta$ implies $|\mathbf{x}_{t} - \mathbf{e}| < \epsilon$.  We can take $\delta$ to be the $\delta$ corresponding to $\epsilon$ for stability around $0$. Then if we take $|\mathbf{x}_{0}-\mathbf{e}| < \delta$, which by stability around the origin implies $|\mathbf{A}^{t-t_0}(\mathbf{x}_{0}-\mathbf{e})| = |\mathbf{A}^{t-t_0}\mathbf{x}_{0}-\mathbf{e}| = |\mathbf{x}_{t}-\mathbf{e}| < \epsilon$.

Now assume $\mathbf{e}$ is a non-zero equilibrium state that is also stable. We shall show the stability of the origin follows. We use the add zero trick to derive the estimate that $|\mathbf{x}_{t}| = |\mathbf{A}^{t-t_{0}}\mathbf{x}_{0}| = |\mathbf{A}^{t-t_{0}}(\mathbf{x}_{0}+\mathbf{e}-\mathbf{e})| = |\mathbf{A}^{t-t_{0}}(\mathbf{x}_{0}+\mathbf{e}) - \mathbf{e}|$. For positive $\epsilon$ take the $\delta$ corresponding to stability for $\mathbf{e}$ and remember we are showing that $|\mathbf{x}_{0} - 0| < \delta$ implies $|\mathbf{x}_{t}-0| <\epsilon$. Since $|\mathbf{x}_{0}+\mathbf{e}-\mathbf{e}| < \delta$ stability around $\mathbf{e}$ implies that $|\mathbf{x}_{t}| < \epsilon$ by our earlier estimate. Thus if one equilibrium state is stable they all are, making the term “stability” an adjective for the system not just a particular equilibrium state. This is NOT true in general systems.

Furthermore, we also have that asymptotic(or exponential) stability implies a unique equilibrium state, and since $0$ is always an equilibrium state, asymptotic(or exponential) stability imply $0$ is the unique equilibrium state. This is because an equilibrium state exhibiting asymptotic(or exponential) stability is also global asymptotic(or exponential) for our systems and starting from any initial condition we see convergence to the asymptotic(or exponentially) stable equilibrium state. This means that if two distinct equilibrium states existed starting from any initial condition would imply convergence to both of them which is only possible if both equilibrium states coincide.

Note: I would argue that this use of terminology calling systems stable, asymptotically stable, or exponentially stable is in poor taste because it doesn’t add any clarity and obfuscates the ideas to learners. Why not say the origin is asymptotically stable, instead of saying the system is asymptotically stable, or the this equilibrium point is stable as opposed to the system is stable? One coincides with terminology outside this special case making cross reading definitions easier.



## Collapse of Ideas
### Global vs Local
A key result is that for our systems is that local and global asymptotic(or exponential stability) are the same thing, that is one implies the others. 

Global asymptotic(or exponential) stability trivially implies local asymptotic(or exponential) stability by taking any norm ball to satisfy the local asymptotic(or exponential) stability definition. The nontrivial statement being made is that local asymptotic(or exponential) stability implies global asymptotic(or exponential) stability.

Local asymptotic stability implies for any positive $\epsilon$, there exists a positive $\delta$ such that states within $\delta$ of $\mathbf{e}$ converge to $\mathbf{e}$ when used as initial states following the transition dynamics. We don’t have convergence guaranteed for any $\mathbf{x}_{0}$ however we take a state on the line segment between $\mathbf{x}_{0}$ and $\mathbf{e}$ that is within $\delta$ of $\mathbf{e}$, and this initial state does converge to $\mathbf{e}$ following the transition dynamics. This turns out to also imply $\mathbf{x}_{0}$ will converge to $\mathbf{e}$. The point on the line segment with endpoints $\mathbf{x}_{0}$ and $\mathbf{e}$ within $\delta$ of $\mathbf{e}$ can be written as $\mathbf{e} + \mu(\mathbf{x}_{0} - \mathbf{e})$ for some choice of $\mu$. Then it follows that $\|\mathbf{A}^{t-t_0}(\mathbf{e}+\mu(\mathbf{x}_{0}-\mathbf{e})) - \mathbf{e}\| = |\mu|\|\mathbf{A}^{t-t_0}\mathbf{x}_{0} - \mathbf{e}\|$ This expression can be made arbitrarily small for $t$ large enough, so $\|\mathbf{A}^{t-t_0}\mathbf{x}_{0}-\mathbf{e}\|$ can also be arbitrarily small for $t$ large enough, from which the conclusion follows. \
\
Local exponential stability implies global exponential stability applies by almost the exact same argument. We note that $\|\mathbf{A}^{t-t_0}(\mathbf{e}+\mu(\mathbf{x}_{0}-\mathbf{e})) - \mathbf{e}\| = |\mu|\|\mathbf{A}^{t-t_0}\mathbf{x}_{0} - \mathbf{e}\| \leq \alpha\|\mu(\mathbf{x}_{0}-\mathbf{e})\|\exp(-\beta(t-t_0))$ from which we conclude, $\|\mathbf{A}^{t-t_0}\mathbf{x}_{0} - \mathbf{e}\| \leq \alpha\|(\mathbf{x}_{0}-\mathbf{e})\|\exp(-\beta(t-t_0))$. The key part requiring justification is that the same choice of constants $\alpha$ and $\beta$ work for any $\mathbf{x}_{0}$ and this follows from the final inequality.
\
Since local asymptotic(or exponential) stability is equivalent to global asymptotic(or exponential) stability, it becomes commonplace to remove the qualifying adjective entirely and simply discuss asymptotic stability and exponential stability.

### Attractive implies Stable(this is not about marriage)

Since we have linear transition dynamics, the only attractive point can be the origin.

\\[
\|\mathbf{A}^{t-t_{0}}\mathbf{x}_{0}\| = \|\mathbf{A}^{t-t_{0}}(\mathbf{x}_{0})\| \\
= \|\mathbf{A}^{t-t_{0}}(\beta_{1}\mathbf{b}_{1} + \beta_{2}\mathbf{b}_{2} + \ldots + \beta_{n}\mathbf{b}_{n})\| \\
\leq  |\beta_{1}| \| \mathbf{A}^{t-t_{0}}\mathbf{b}_{1}\| + |\beta_{2}|\|\mathbf{A}^{t-t_{0}}\mathbf{b}_{2}\| + \ldots + |\beta_{n}\|\mathbf{A}^{t-t_{0}}\mathbf{b}_{n}\|
\\]

Since we have attraction to the origin, we have the the norm of future states on any of the basis elements can be bounded. Since the basis is finite we can upper bound all of them uniformly. By equivalence of norms we have stability of the origin.   


### Equivalent Definitions of Stability

#### General Definition
An equilibrium state, $\mathbf{e}$, being stable means that for any positive $\epsilon$ there exists a positive $\delta$ such that any initial condition within $\delta$ of $\mathbf{e}$ will stay within $\epsilon$ of $\mathbf{e}$ for all future states. \

#### Trajectory Definition
For our particular systems it turns out stability of an equilibrium state, $\mathbf{e}$, is equivalent to given an initial state, future states will be bounded near $\mathbf{e}$ for all time. That is for any $\mathbf{x}_{0}$, we have $\|\mathbf{x}_{t} - \mathbf{e}\| < M$ for every possible time, $t$. This is also often written as for all $\mathbf{x}_{0}$ we have $\sup_{t\geq t_{0}}\| \mathbf{A}^{t-t_{0}}\mathbf{x}_{0} - \mathbf{e}\| = M < \infty$

To show the general definition implies future states are bounded for all time for our system, suppose $\mathbf{e}$ is a stable equilibrium state for our system. Then we can take $\epsilon := 1$ or any fixed constant and we have that there exists positive $\delta$ such that if $\|\mathbf{x}_{0} - \mathbf{e}\| < \delta$ then $\|\mathbf{x}_{t} - \mathbf{e}\| < 1$. Now for any initial state $\mathbf{x}_{0}$ we may not have $\|\mathbf{x}_{0} - \mathbf{e}\| < \delta$, however we can look at some point on the line segment between $\mathbf{x}_{0}$ and $\mathbf{e}$ that is within $\delta$ of $\mathbf{e}$. That is we choose a $\mu$ such that $\mathbf{e} + \mu(\mathbf{x}_{0}-\mathbf{e})$ is within $\delta$ of $\mathbf{e}$. Now by stability of the state $\mathbf{e}$, we have $\|\mathbf{A}^{t-t_0}(\mathbf{e}+\mu(\mathbf{x}_{0}-\mathbf{e})) - \mathbf{e}\| < 1$ which reduces to $\|\mu \left(\mathbf{A}^{t-t_0}\mathbf{x}_{0}-\mathbf{e}\right)\| < 1$. This shows all future states are bounded when starting at $x_0$ from the estimate $\|\mathbf{A}^{t-t_0}\mathbf{x}_{0}-\mathbf{e}\| < \frac{1}{|\mu|}$.\
\
Let us assume that we have a state $\mathbf{e}$, that satisfies the property that for every initial condition $\mathbf{x}_{0}$ we have $\|\mathbf{x}_{t} - \mathbf{e}\| < M$ for every possible time, $t$. Then given a positive $\epsilon$ our goal is find $\delta$ such that $\|\mathbf{x}_{0} - \mathbf{e}\| < \delta$ implies $\|\mathbf{x}_{t} - \mathbf{e}\| < \epsilon$. However we know if we choose a particular $\mathbf{x}_{0}$ we have that $\|\mathbf{x}_{t} - \mathbf{e}\| < M_{\mathbf{x}_{0}}$(the subscript is highlighting that this constant depends on the initial state chosen and is not the same for every initial state). Given a basis $\mathbf{b}_{1}, \mathbf{b}_{2}, ..., \mathbf{b}_{n}$ we have corresponding  constants $M_{\mathbf{b}_{1}}, M_{\mathbf{b}_{2}}, ..., M_{\mathbf{b}_{n}}$. Now any initial state can be written uniquely as $\mathbf{x}_{0} -\mathbf{e}= \beta_1(\mathbf{b}_{1}-\mathbf{e}) + \beta_2(\mathbf{b}_{2}-\mathbf{e}) + \ldots + \beta_n(\mathbf{b}_{n}-\mathbf{e})$, so we simply use the following constant $M: = \max M_{\mathbf{b}_{i}}$ to bound that $\|\mathbf{x}_{t} - \mathbf{e}\| = \|\mathbf{A}^{t-t_0}\mathbf{x}_{0} - \mathbf{e}\| = \|\beta_1 \mathbf{A}^{t-t_0}(\mathbf{b}_{1}-\mathbf{e}) + \beta_2 \mathbf{A}^{t-t_0}(\mathbf{b}_{2}-\mathbf{e}) + \ldots + \beta_n \mathbf{A}^{t-t_0}(\mathbf{b}_{n}-\mathbf{e})\| < M(|\beta_1| + \ldots + |\beta_n|) = M\|x_{0}-e\|_{1} \leq M\kappa \|x_{0}-e\| = M\kappa \| \mathbf{x}_{0} - \mathbf{e} \|$. Thus for $\delta = \frac{\epsilon}{\kappa M}$ the conclusion follows. Here equivalence of norms was fundamental to the argument.



#### Matrix Power Definition

Another equivalent characterization of stability is that $\sup_{k \geq 0} \|\mathbf{A}^{k}\| = M< \infty$. This notion of stability doesn’t apply to a particular equilibrium state which is because per our earlier section if one equilibrium state is stable they all are, so stability becomes a property of the system. As such there should be a criterion on the system that determines stability independent of particular states.\
\
To show this implies the trajectory criterion, we have the following trivial estimates,\
\\[
\sup_{t \geq t_{0}} \|\mathbf{A}^{t-t_{0}}\mathbf{x}_{0}\| \leq \left( \sup_{t \geq t_{0}} \|\mathbf{A}^{t-t_{0}}\|_{\text{op}} \right) \|\mathbf{x}_{0}\| < \left( \sup_{t \geq t_{0}} \Xi \|\mathbf{A}^{t-t_{0}}\|\right) \|\mathbf{x}_{0}\| < \Xi M \| \mathbf{x}_{0} \|
\\]\
From this estimate it follows that trajectories from any initial condition are bounded. Note that $\| \cdot \|_{\text{op}}$ is the induced operator norm, and the constant $\eta$ comes from equivalence of the operator norm to the norm using on the space of linear operators.( $\xi \|\mathbf{A}\| \leq \| \mathbf{A} \|_{\text{op}} \leq \Xi \|\mathbf{A}\|$)

To show the trajectory definition implies the matrix power condition, will exploit finite dimensionality of the space so assume a basis $\mathbf{b}_{1}, \mathbf{b}_{2}, \ldots, \mathbf{b}_{n}$ and $\mathbf{y}$ has coordinate representation $y$ with respect to this basis. Additionally, let $M_{i} := \sup_{k\geq 0} \|\mathbf{A}^{k}\mathbf{b}_{i}\|$ and $M := \max_{i}M_{i}$

\\[
\begin{align*}
	\sup_{k \geq 0} \|\mathbf{A}^{k}\|_{\text{op}} &= \sup_{k \geq 0} \left( \sup_{\|\mathbf{y}\|=1} \|\mathbf{A}^{k}\mathbf{y}\| \right) \\
	&= \sup_{k \geq 0} \left( \sup_{\|\mathbf{y}\|=1} \|\mathbf{A}^{k}\left(\beta_{1}\mathbf{b}_{1} + \ldots + \beta_{n}\mathbf{b}_{n}\right)\| \right) \\
	&\leq \sup_{k \geq 0} \sup_{\|\mathbf{y}\|=1} |\beta_{1}| \| \mathbf{A}^{k} \mathbf{b}_{1} \| + |\beta_{2}| \| \mathbf{A}^{k}\mathbf{b}_{2}\| + \ldots + |\beta_{n}| \| \mathbf{A}^{k}\mathbf{b}_{n}\| \\
	&\leq M \sup_{k \geq 0} \sup_{\|\mathbf{y}\|=1} |\beta_{1}| + |\beta_{2}| + \ldots + |\beta_{n}|
\end{align*}
\\]

Since we know $\kappa\|\mathbf{y}\|=\kappa\|y\| \leq \| y \|_{1}  = |\beta_{1}| + \ldots + |\beta_{n}| \leq \Kappa\|y\|=\Kappa\|\mathbf{y}\|$, and $\|\mathbf{A}\| \leq \frac{1}{\xi}\| \mathbf{A} \|_{\text{op}}$ the conclusion follows.

#### Spectral Definition
Another equivalent characterization of stability is that every eigenvalue of $\mathbf{A}$ has modulus less than 1, $|\lambda| < 1$, or if the eigenvalue has modulus 1 it corresponds to Jordan block of size 1. This knowledge comes from analyzing the Jordan Normal Form of the $\mathbf{A}$. Here we will have $\mathsf{A}_{i}$ denote the $i$-th Jordan block and its $k$-th power explicitly is,

\\[
\mathsf{A}_{i}^{k} = 
\begin{bmatrix}
\lambda_{i}^k && k\lambda_{i}^{k-1} && \frac{k(k-1)}{2!}\lambda_{i}^{k-2} && \ldots && \frac{k(k-1)(k-2)\ldots(k-(n_{i}-2))}{(n_{i}-1)!}\lambda_{i}^{k-(n_{i}-1)} \\
0 && \lambda_{i}^k && k\lambda_{i}^{k-1} && \ldots && 
\vdots   \\
0 && 0 && \lambda_{i}^k  && && \vdots \\
\vdots && \vdots && \vdots && \ddots && \vdots \\
0 && 0 && 0 && \ldots && \lambda_{i}^k
\end{bmatrix}
\\]

If $\mathsf{b}_{1}, \ldots, \mathsf{b}_{n_{i}}$ are the coordinate representations of vectors corresponding to the Jordan block $\mathsf{A}_{i}$, by the trajectory definition of stability, any equilibrium point is stable iff $\sup_{k\geq 0} \|\mathsf{A}^{k}\mathsf{b}_{j}\| < \infty$ for each $\mathsf{b}_{j}$ and the same can be done for every Jordan block. If this applies for all these basis vectors clearly it implies for any initial condition the trajectory is bounded. By the upper triangular structure, we have stability iff each term of $\mathsf{A}_{i}^{k}$ has bounded modulus. This is because $\mathsf{A}^{k}\mathsf{b}_{1} = \lambda_{i}^k \mathsf{b}_{1}$ which is bounded iff the modulus of the coefficient is bounded. By induction this will imply that the modulus of every coefficient needs to be bounded as $k$ tends to infinity. $|\lambda_{i}|^{k}$ is bounded iff $|\lambda_{i}| \leq 1$. Given $|\lambda_{i}| \leq 1$ for $k|\lambda_{i}|^{k-1}$ to be bounded we need $|\lambda_{i}|^{k-1}$ to offset the growth from $k$. If $|\lambda_{i}| < 1$, this is trivially satisfied, and if $|\lambda_{i}| = 1$ this is impossible. So if $|\lambda_{i}| = 1$ our conditions our only satisfied if the Jordan block is of size 1. If the modulus is less than 1, since the exponential decays faster the boundedness holds for every term. Thus the result is shown.\


#### Lyapunov Definition
Our last equivalent characterization is by construction of what is called a Lyapunov function. The idea behind a Lyapunov function is that some related quantities let you determine information about the states of the system. \
\
For example, if we know the norm of the states we can infer if the states stay bounded or converges to zero based on if the norm converges to zero. Another example, and closer to the original motivation is “energy”. For example in a physical system, if we have an object moving analyzing the kinetic energy or similar quantities involved lets us deduce information about the states. \
\
This approach is especially important, because it generalizes the most. The spectral theory approach only works for our particular system, the trajectory and matrix power conditions apply to slightly more general systems(namely linear non-autonomous dynamical systems), but the Lyapunov function approach works even in the case of general nonlinear dynamical systems. We won’t go into full generality, but will go through the key results for our particular system.\
\
We said some related functions provide insight into the states. In this case, consider the Euclidean norm, $V(x) = x^{H}Px$ with $P$ positive definite, and assume an arbitrary basis and use coordinate vectors for ease of notation. Our space is assumed to have a norm that may not be Euclidean, however that doesn’t restrain us from looking at the Euclidean norm. Intuitively, if we want the norm to stay bounded over a trajectory this would be satisfied if the Euclidean norm was decreasing over that trajectory(i.e $V(x_{t+1}) \leq V(x_{t}$)).  At first glance this may seem stronger than the trajectory being bounded for any initial condition as it creates a non-increasing sequence on the norm of the states, but it turns out this isn’t true because the linear structure prevents the Euclidean norm from going up and then down. Clearly, if this was the case the then $\kappa \|\mathbf{x}_{t}\| \leq V(x_t) \leq V(x_0) \leq \Kappa\|\mathbf{x}_{0}\|$ which implies the trajectory would be bounded even for our original norm and for any starting condition if such a $V(\cdot)$ existed. For $V(\cdot)$ to exist we exploit the non-increasing condition and find, 
\\[
x_{t+1}^TPx_{t+1} \leq x_{t}^TPx_{t} \\
x_{t}A^TPAx_{t} \leq x_{t}^TP{x} \\
x_{t}^T(A^TPA - P)x_{t} \leq 0
\\]
So if there exists a $P$ such that $A^TPA - P$, which is referred to as Stein or Discrete Lyapunov Equation, is negative semi-definite we have shown stability holds by the bounded trajectory condition. Thus existence of $P$ satisfying the Stein equation is sufficient for stability. 

To show existence of such a $P$ is necessary we need to argue that the Stein Equation has a solution given the system is stable. This is not difficult but a touch long, so we will simply leave the existence to a separate note.

[TODO: Come back and argue the converse elegantly, linear operator look, change of coordinates etc, possibly LMI feasibility]

### Equivalent Definitions of Asymptotic Stability

#### General Definition
An equilibrium state, $\mathbf{e}$ is asymptotically stable iff it is stable and there exists a positive $\delta$ such that if the initial state is within $\delta$ of $\mathbf{e}$, then future states converge to $\mathbf{e}$. \
\
Normally this is called local asymptotic stability for an autonomous system, in contrast to global asymptotic stability but since these notions are equivalent for our system we omit the qualifier, and may implicitly assume $\delta$ is as large as needed in future arguments. In addition, we showed earlier that if a system is asymptotically stable $\mathbf{e}$ is the only equilibrium point hence for this section we will often assume that $\mathbf{e}=0$ because this is the only case.\
\

#### Trajectory Definition

There is no analogous trajectory definition as like there is for  a stable equilibrium state that comes about quite naturally. If one were trying mimic the case of Lyapunov stability, then we might try to say something like $\limsup_{t \geq t_{0}}\|A^{t-t_{0}}x - e\| = 0$. However this is true by definition of asymptotic convergence.

#### Matrix Power Definition
Another equivalent characterization of asymptotic stability of the equilibrium state is that $\lim_{t-t_{0} \to \infty} \| \mathbf{A}^{t-t_{0}} \| = 0$. A common equivalent form is written as $\lim_{t-t_{0} \to \infty}  \mathbf{A}^{t-t_{0}}= 0$. (Can a similar remark that the limit converges to a given matrix if an equilibrium is stable?)

We show asymptotic stability implies the matrix power definition via the following chain of inequalities,\

\\[
\lim_{t-t_{0} \to \infty} \| \mathbf{A}^{t-t_{0}} \|  
\leq 
\lim_{t-t_{0} \to \infty} \frac{1}{\xi}\| \mathbf{A}^{t-t_{0}} \|_{op} \\
\leq
\lim_{t-t_{0} \to \infty} \frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \| \mathbf{A}^{t-t_{0}}\mathbf{y} \| \\
\leq
\lim_{t-t_{0} \to \infty} \frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \| \mathbf{A}^{t-t_{0}}\mathbf{y} \| 
\leq \\
\lim_{t-t_{0} \to \infty} \frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \| \mathbf{A}^{t-t_{0}}\left( \beta_{1}\mathbf{b}_{1} + \beta_{2}\mathbf{b}_{2} + \ldots + \beta_{n}\mathbf{b}_{n}\right) \| 
\leq \\
\lim_{t-t_{0} \to \infty} \frac{1}{\xi} \sup_{\| \mathbf{y}\| =1}  | \beta_{1} | \|\mathbf{A}^{t-t_{0}}\mathbf{b}_{1}\| +  |\beta_{2}| \| \mathbf{A}^{t-t_{0}}\mathbf{b}_{2}\| + \ldots + |\beta_{n}| \|\mathbf{A}^{t-t_{0}}\mathbf{b}_{n}\|
\leq \\
\lim_{t-t_{0} \to \infty} \frac{M}{\xi} \sup_{\| \mathbf{y}\| =1}  | \beta_{1} |  +  |\beta_{2}|  + \ldots + |\beta_{n}|
\\]
By equivalence of norms we have $\|y\|_{1} = | \beta_{1} |  +  |\beta_{2}|  + \ldots + |\beta_{n}| \leq \Kappa\|y\|=\Kappa\|\mathbf{y}\|=\Kappa$, and expanding $M=\max_{i} \|\mathbf{A}^{t-t_{0}}\mathbf{b}_{i} \|$ we can further reduce the above to,
\\[
\lim_{t-t_{0} \to \infty} \frac{\Kappa}{\xi} \max_{i} \|\mathbf{A}^{t-t_{0}}\mathbf{b}_{i} \|
\\]

For $t$ sufficiently, large by asymptotic stability any of the $n$ basis vectors used as initial states will generate future states that are arbitrarily close to $0$, and since there are finitely many basis elements we can simply take $t$ to be large enough so that any of the generated states past that point using any of the initial states is sufficiently small in norm. Hence this quantity is upper bounded by $0$, and every norm is lower bounded by $0$, so this limit converges to $0$, and $\lim_{t-t_{0} \to \infty} \| \mathbf{A}^{t-t_{0}} \| = 0$. 


Now we can show that the matrix power definition implies the standard definition.

\\[
\lim_{t-t_{0} \to \infty} \| \mathbf{A}^{t-t_{0}}\mathbf{x}_{0}\| 
\leq
\lim_{t-t_{0} \to \infty} \| \mathbf{A}^{t-t_{0}} \|_{\text{op}} \|\mathbf{x}_{0}\| 
\leq \\
\lim_{t-t_{0} \to \infty} \Xi \| \mathbf{A}^{t-t_{0}} \| \|\mathbf{x}_{0}\| = 0.
\\]

This means that every initial state converges to the unique equilibrium state, the origin, when following the transition dynamics. We separately still need to show the origin is Lyapunov stable, however this follows from realizing if the limit of the norm goes to zero, the supremum of the norm over the entire sequence must be upper bounded hence the matrix power definition of Lyapunov stability shows stability.

#### Spectral Definition
Another equivalent characterization of asymptotic stability of the equilibrium state is $\mathbf{A}$ having eigenvalues strictly in the unit circle. This is often referred to as $\mathbf{A}$ being Schur. This, akin to the case of Lyapunov stability, is easily shown using the Jordan form. We maintain the same notation as before where $\mathsf{A}_{i}$ denotes the $i$-th Jordan block and its $k$-th power explicitly is,

\\[
\mathsf{A}_{i}^{k} = 
\begin{bmatrix}
\lambda_{i}^k && k\lambda_{i}^{k-1} && \frac{k(k-1)}{2!}\lambda_{i}^{k-2} && \ldots && \frac{k(k-1)(k-2)\ldots(k-(n_{i}-2))}{(n_{i}-1)!}\lambda_{i}^{k-(n_{i}-1)} \\
0 && \lambda_{i}^k && k\lambda_{i}^{k-1} && \ldots && 
\vdots   \\
0 && 0 && \lambda_{i}^k  && && \vdots \\
\vdots && \vdots && \vdots && \ddots && \vdots \\
0 && 0 && 0 && \ldots && \lambda_{i}^k
\end{bmatrix}
\\]

If $\mathsf{b}_{1}, \ldots, \mathsf{b}_{n_{i}}$ are the coordinate representations of vectors corresponding to the Jordan block $\mathsf{A}_{i}$, then we can simply analyze their behavior under $\mathbf{A}$. This is because if the system is asymptotically stable, then any basis vector as an initial state will tend towards $0$. On the other hand, if we have any initial state, it can be decomposed as a linear combination of basis vectors, and the triangle inequality shows that the initial state will tend towards $0$ if the basis vectors tend toward $0$. Thus any initial state tends towards $0$ iff any set of basis vectors has each vector tend towards $0$.

Thus we iff conditions such that  $\lim_{ \to \infty} \|\mathsf{A}^{k}\mathsf{b}_{j}\| =0$ for each $\mathsf{b}_{j}$ and the same can be done for every Jordan block. By the upper triangular structure, we have convergence to $0$ iff each term of $\mathsf{A}_{i}^{k}$ convergences to $0$. This is because $\mathsf{A}^{k}\mathsf{b}_{1} = \lambda_{i}^k \mathsf{b}_{1}$ which goes to $0$ iff the modulus of the coefficient is strictly less than $1$. By induction this will imply that the modulus of every coefficient needs to go to $0$ as $k$ tends to infinity. Given $|\lambda_{i}| < 1$ for $k|\lambda_{i}|^{k-1}$ to tend to $0$ we need $|\lambda_{i}|^{k-1}$ to offset the growth from $k$. Since $|\lambda_{i}| < 1$, this is trivially satisfied.\


#### Lyapunov Function Definition
The motivation for the Lyapunov function remains identical to the case of Lyapunov stability, however instead of the norm remaining bounded we want the norm to tend towards $0$. This means instead we want strict inequalities such as $V(x_{t+1}) < V(x_{t})$.

### Exponential Stability
#### General Definition
An equilibrium state, $\mathbf{e}$, is exponentially stable iff it is stable and there exists a positive $\delta$ such for any initial state within $\delta$ of $\mathbf{e}$, future states converge to $\mathbf{e}$ faster than an exponential.\

Mathematically, we mean there exists positive $\alpha$ and $\beta$ such that 
$\|\mathbf{A}^{t-t_{0}}\mathbf{x}_{0} - \mathbf{e}\| \leq \alpha \|\mathbf{x}_{0} - \mathbf{e}\|\exp(-\beta(t-t_{0}))$

Again, we note local and global exponential stability are equivalent, so $\delta$ can be taken as large as we like because any initial condition will generate futures states that converge  to the equilibrium state. In addition, like with asymptotic stability $0$, is the unique equilibrium state.

#### Trajectory definition
There is no analogous trajectory definition, because the definition of exponential stability already adds a constraint to trajectories. 

#### Matrix Power Definition
An equivalent characterization of exponential stability of the origin is $\|\mathbf{A}^{t-t_{0}}\| \leq \alpha \exp\left(-\beta(t-t_{0})\right)$. 

To show this matrix power condition implies exponential stability of the origin we observe that for any initial condition $\mathbf{x}_{0}$,

\\[
\|\mathbf{A}^{t-t_{0}}\mathbf{x}_{0} - \mathbf{e}\| = \|\mathbf{A}^{t-t_{0}}\left(\mathbf{x}_{0} - \mathbf{e}\right)\|  \\
\leq
\|\mathbf{A}^{t-t_{0}}\|_{\text{op}} \| \mathbf{x}_{0} - \mathbf{e}\| \\
\leq
\Xi \|\mathbf{A}^{t-t_{0}}\|\| \mathbf{x}_{0} - \mathbf{e}\| \\
\leq 
\Xi \alpha  \| \mathbf{x}_{0} - \mathbf{e}\| \exp\left(-\beta(t-t_{0})\right)
\\]
Thus we have shown the origin is exponentially stable.


Now to show that exponential stability implies the matrix power condition we take an approach analogous to our proof in asymptotic stability.

\\[
\| \mathbf{A}^{t-t_{0}} \|  
\leq 
\frac{1}{\xi}\| \mathbf{A}^{t-t_{0}} \|_{op} \\
\leq
\frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \| \mathbf{A}^{t-t_{0}}\mathbf{y} \| \\
\leq
\frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \| \mathbf{A}^{t-t_{0}}\mathbf{y}-\mathbf{e} \| \\
\leq 
\frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \alpha\|\mathbf{y}-\mathbf{e}\|\exp(-\beta(t-t_{0})) \\
\leq
\frac{1}{\xi} \sup_{\| \mathbf{y}\| =1} \alpha\|\mathbf{y}\|\exp(-\beta(t-t_{0})) \\
\leq
\frac{\alpha}{\xi}  \exp(-\beta(t-t_{0})) \\
\\]
Thus we have exponential stability implies the matrix power condition. Here used the fact that $\mathbf{e}=0$ and the constants $\alpha$ and $\beta$ don’t depend on the initial condition and the fact that global and local exponential stability are the same so we can use these constants over the unit ball.



#### Spectral Theory Definition (Asymptotic is Exponential)

A happy coincidence is that asymptotic stability implies exponential stability for our special systems. In general exponential implies asymptotic, but the converse is not true. This follows by analyzing the Jordan form, and taking a closer look at the arguments made when discussing the spectral definition of asymptotic stability.
\\[
\mathsf{A}_{i}^{k} = 
\begin{bmatrix}
\lambda_{i}^k && k\lambda_{i}^{k-1} && \frac{k(k-1)}{2!}\lambda_{i}^{k-2} && \ldots && \frac{k(k-1)(k-2)\ldots(k-(n_{i}-2))}{(n_{i}-1)!}\lambda_{i}^{k-(n_{i}-1)} \\
0 && \lambda_{i}^k && k\lambda_{i}^{k-1} && \ldots && 
\vdots   \\
0 && 0 && \lambda_{i}^k  && && \vdots \\
\vdots && \vdots && \vdots && \ddots && \vdots \\
0 && 0 && 0 && \ldots && \lambda_{i}^k
\end{bmatrix}
\\]

We will show that if there exists positive constants $\alpha, \beta$ that define an exponential that can bound the basis vectors, we can find an exponential that bounds everything.
By the structure of the matrix, 

\\[
\|\mathsf{A}^{k}\mathsf{b}_{j}\| \leq \| \binom{k}{j-1}\lambda^{k-(j-1)}\mathsf{b}_{1} + \binom{k}{j-2}\lambda^{k-(j-2)}\mathsf{b}_{2} + \ldots + \binom{k}{0}\lambda^{k}\mathsf{b}_{j} \| \\
\leq 
\binom{k}{j-1}|\lambda|^{k-(j-1)}\|\mathsf{b}_{1}\| + \binom{k}{j-2}|\lambda|^{k-(j-2)}\|\mathsf{b}_{2}\| + \ldots + \binom{k}{0}|\lambda|^{k}\|\mathsf{b}_{j}\| \\
\leq 
p(k)|\lambda|^{k-(j-1)} \\
\leq p(k)|\lambda|^{k-(n_{i}-1)} \\
\leq  p(k)|\lambda|^{k-(n-1)} \\
\leq q(k) |\lambda|^{k} \\
\leq Ck^{n_{i}-1} |\lambda|^{k} \
\\]

A standard ratio argument from analysis, shows that $\frac{(k+1)^{n_{i}-1} |\lambda|^{k+1}}{k^{n_{i}-1} |\lambda|^{k}} \to |\lambda| < 1$ from which we get that for $k\geq k_{0}$ we have $\frac{(k+1)^{n_{i}-1} |\lambda|^{k+1}}{(k)^{n_{i}-1} |\lambda|^{k}} < |\lambda| <\rho < 1$ which means by multiplication, $\frac{k^{n_{i}-1} |\lambda|^{k}}{k_{0}^{n_{i}-1}|\lambda|^{k_{0}}} \leq \rho^{k-k_{0}}\implies k^{n_{i}-1}|\lambda|^{k}\leq M \rho^{k} \quad \forall k\geq k_{0}$. Notice the denominator is independent of $k$ it is a fixed constant based on $k_{0}$ as is $\rho^{-k_{0}}$, so these are absorbed into $M$. Now this bound only holds for $k\geq k_{0}$, however it shouldn’t be hard to see that since there are only finitely many terms before $k_0$ we can bump the constant in front up, to make it dominate for all $k$. This gives up for all $k$ we have $Ck^{n_{i}-1}|\lambda|^{k} \leq \zeta \rho^{k}$ where $\rho < 1$ and $\zeta > 0$. We can do this for every basis vector and by choosing the coefficient to be the maximum among all of them we end up finding that, 

\\[
\|\mathsf{A}^{k}\mathsf{x}\| \leq n \zeta \rho^{k} = n \zeta \exp(\ln(\rho^{k})) =  n \zeta \exp(k\ln(\rho))
\\]
which is exactly the definition of exponential stability.

#### Lyapunov Function Definition
By the equivalence of asymptotic and exponential we have the same viewpoint as for asymptotic stability.


# Stability for Observed Systems
All the terminology above still applies however the adjective internal is added in the case of an observed system. So there is internal stability, internal asymptotic stability, etc...\

# New Concepts for Observed Systems

## Equivalent Definitions of Observability
### General Definition
Observability is simply the idea that you can determine the initial state of the system the sequence of outputs. That is every possible initial state corresponds to a unique output sequence. Observable is an adjective describing the system. It is thus commonplace to see the pair ($\mathbf{A}$, $\mathbf{C}$), being called observable when the observed system defined by these operators is observable. 

Mathematically we mean that given any initial state, $\mathbf{x}_{0}$, the mapping from to the space of output sequences defined by the transition dynamics is injective. In notation $\mathbf{x}_{0} \to (\mathbf{y}_{0}, \mathbf{y}_{1}, \mathbf{y}_{2},\dots)$  is injective.

### Finite Horizon Definition
Since our states are finite dimensional it is perhaps unsurprising that we don’t need the entire sequence of observations, but only finite information to determine the state. It turns out we can equivalently define an observed system to be observable, iff the initial state can be determined from the first $n:=\text{dimension of state space}$ observations. 

Mathematically we mean that given any initial state, $\mathbf{x}_{0}$, the mapping from initial states to the space of the first $n$ observations defined by the transition dynamics is injective. In notation $\mathbf{x}_{0} \to (\mathbf{y}_{0}, \mathbf{y}_{1},\ldots, \mathbf{y}_{n-1})$  is injective.

If we know that the map from initial state to sequence of observations is injective, then we can show that the map from the initial state to the first $n$ observations is injective. Assume we have two distinct initial states, we know the sequences of observations generated are distinct by assumption. If the first $n$ observations are distinct when comparing for any two distinct initial states, then our map from initial state to first $n$ observations is also injective. However if the first $n$ observations are not distinct then our desired conclusion is not true. To see that this is not possible we invoke the Cayley-Hamilton theorem, which says a matrix satisfies its characteristic polynomial.

\\[
\alpha_{n}\mathbf{A}^{n} + \alpha_{n-1}\mathbf{A}^{n-1} + \ldots + \alpha_{0}\mathbf{I} = 0 \\ 
\mathbf{C}\mathbf{A}^{n} = \beta_{n-1}\mathbf{A}^{n-1} + \ldots + \beta_{0}\mathbf{I}
\\]

By the Cayley-Hamilton theorem and induction, we see that every observation is a linear combination of the previous $n$, with the coefficients depending only on $\mathbf{A}$. This means that if the first $n$ observations are identical for two distinct initial states, then the entire sequence of observations are identical why by our assumption means we have a contradiction. Thus the first $n$ observations must be distinct for two distinct initial states.

If we know the map from initial states to the first $n$ observations is injective, then we can show the map from initial states to the sequence of observations is injective. If we have any two distinct initial states, we can assume they map to an identical sequence of observations. We simply look at the first $n$ observations, and our assumption implies that these states are identical yielding a contradiction. 

### Observability Matrix / Kalman Rank Test

The Kalman Rank test is an algebraic test that says a system is observable iff

\\[
\mathrm{rank} \begin{bmatrix}
 C \\
 CA \\
 CA^{2} \\
 \vdots \\
 CA^{n-1}
\end{bmatrix} = n
\\]

This follows trivially from the finite-horizon definition by setting up the following linear system,\

\\[
\begin{bmatrix}
 C \\
 CA \\
 CA^{2} \\
 \vdots \\
 CA^{n-1}
\end{bmatrix}x_{0} = 
\begin{bmatrix}
 y_{0} \\
 y_{1} \\
 y_{2} \\
 \vdots \\
 y_{n-1}
\end{bmatrix}
\\]

This system of equations represents the map from initial state to first $n$ observations. Since a sequence is observable iff the map is injective, by the rank-nullity theorem and the fact that a map in injective iff the dimension of the null space is zero, we can conclude observability iff rank of the matrix is $n$. This test is thus the same as the finite horizon definition after one puts down coordinates and writes down the linear system.

### Popov-Belevitch-Hautus(PBH) Test

The PBH test is another test based on rank. It assert thats a system is observable iff
\\[
\mathrm{rank} \begin{bmatrix}
 \lambda I - A \\
 C \\
\end{bmatrix} = n \qquad \forall \lambda \in \sigma{A}
\\]
The intuition for this test is based on the the equivalence between the mapping from the initial state to the first $n$ observations being injective to the mapping having a trivial null space. Thus we can simply analyze when the observability matrix has a trivial nullspace. For this matrix to have a trivial nullspace, no state can remain “hidden” from $\mathbf{C}$. That is the nullspace of $\mathbf{C}$ cannot contain some invariant subspace of $\mathbf{A}$. Analyzing the Jordan decomposition, which is a decomposition of $\mathbf{A}$ into invariant subspaces, reveals that any vector under repeated iterations of $\mathbf{A}$ will have an image that has some non-zero component along an eigenvector. This means that the only things we need to check that cannot “hide” from $\mathbf{C}$ are the eigenvectors. 

For formal proof assume there exists a non-zero vector for which this is true. Then $\mathbf{A}\mathbf{x} = \lambda \mathbf{x}$ and $\mathbf{C}\mathbf{x} = 0$. Clearly using $\mathbf{x}$ as the initial condition we see the sequence of observations will be $0$ contradicting observability.

For the other direction, assume the PBH test is satisfied. Then by using the Jordan decomposition of the operator, we see that any non-zero initial condition will eventually generate a non-zero observation.

### Gramians

A $k$-step Gramian is defined as $\sum_{n=0}^{k-1} C^T(A^{k})^TA^{k}C$. The Gramian with no prefix refers to the same summation except with no upper bound on $k$. This is an approach that hinges on Euclidean Geometry and norms being nonzero iff the vector is nonzero. 

The test here is that a system is observable iff the $n$-step Gramian is positive definite.

A more common test found in the literature that is less applicable is for an asymptotically stable system, the Gramian is positive definite iff the system is observable.

Lyapunov approach by telescoping

## Equivalent definitions of Detectability

### General Definition
This is weaker than observability and means that any state indistinguishable from $0$ by observation converges to 0. So Any initial state, $\mathbf{x}$, that maps to the sequence of $0$ observations satisfies $\mathbf{A}^{t-t_{0}}\mathbf{x}$ tends to $0$ as $t$ goes to infinity.

### Observability Matrix 
This is sometimes characterized in terms of the observability matrix. It is simply stated as any state in the nullspace of the observability matrix, creates future states that tend $0$ as $t$ goes to infinity.

### PBH Test

### Gramians




# Comments on Mathematical Setting
Here the transition dynamics require a vector space, often we find Banach spaces the natural choice for control theory over a sufficiently nice field like C or R. Distinctions are made for those who care, and for those who don’t it is neither here nor there

[^1]: Equilibrium points are a concept widely used, and have many synonyms : stationary point, steady state, fixed-point, critical point
[^2]: An equation of this form is called a Stein Equation, or Discrete Lyapunov Equation.

---
Annotations: 0,44887 SHA-256 aa1fae26751384e3448d  
@Aman Shah: 137,4 1929 2585,460 11276,10 12852,779 14030,39 17805,12 17846 17874,4 17928,2 17931,4 18050,267 18748,12 19463,70 19872,145 20031,4 20052,4 20090,14 20132,4 20144,4 20170,4 20179,8 20200,5 20222,37 20272,93 20378,655 21046,711 21819,57 21877,2150 24050,4 24088,4 24132,4 24142,37 24188,594 24787,26 24824,4687 29525,4 29546,4 29584,14 29626,4 29638,4 29664,4 29673,8 29694,5 29716,37 29766,93 29872,1018 30903,3783 34700,4 34721,4 34759,14 34801,4 34813,4 34839,4 34848,8 34869,5 34891,37 34941,93 35047,2156 37206,14 37421,2 37426,33 37460,67 37614,4 37639,6111 43752 43754,26 43794,24 43934,430  
...
