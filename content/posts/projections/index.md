---
title: Projectors
date: 2023-03-09
author: Aman Shah
draft: false
math: true
showtoc: true
---

## Introduction

The purpose of this note is to give a perspicuous presentation of a special class of operators called *projectors*. Projectors find themselves used in applications ranging from elementary physics, to statistics, machine learning, and geometry among countless others. Their prominence for both theoretical and applied aspects of linear algebra make them worth the time to learn well.


## Projectors
With the preliminaries done we can now define special kind of map known as a projector.
> **Definition:** Given some direct sum $U+W = V$, we define a **projector**, $\mathbf{P}: V \to V$ as follows. Since $U+W = V$ we have any $\mathbf{v} \in V$ has unique representation as $\mathbf{v} = \mathbf{u} + \mathbf{w}$ for some choice of $\mathbf{u} \in U$ and $\mathbf{w} \in W$. With this we define $\mathbf{Pv} := \mathbf{u}$. 

 *Exercise: Prove that a projector is linear.*
 
 > **Example 3:** Consider the direct sum $X+Y$ from Example 2. We can define a projector that maps elements to the $X$ or $Y$ axis. This coincides with what we typically think of as projections.

We should point out that we can also project onto the axis of a non-perpendicular grid on the plane as well. Such an operation would also be a projector. In fact this general notion is the one to keep in mind going forward. 

### Relation to Idempotence
 We say a function, $f$, is **idempotent** if $f \circ f = f$. That is if applying the function twice is the same as applying it once. There are many examples such as the identity function or absolute value function on the real numbers. 

 Now our definition of projectors makes it simple to construct a projector given a direct sum. However, it may not be obvious if a given linear operator is a projector. It turns out there is a simple test to determine if a given linear operator, $\mathbf{P}$, is a projector.

 > **Theorem:** A linear operator, $\mathbf{P}$, is a projector if and only if $\mathbf{P}^2 = \mathbf{P}$. That is $\mathbf{P}$ is idempotent.

 We remark that the absolute value function is not a linear map on $\mathbf{R}$ but is idempotent. This does not contradict the above theorem because the above theorem states that any *linear*, idempotent operator is a projector. 
 
 This theorem will enable us to quickly check if an operator is a projector in later sections.

### Projection to Lines

#### Physical Example
Consider a sunny day and a lamp post standing erect on perfectly flat ground. Since the sun is sufficiently far away we assume the rays of light are parallel. The lamp post has a shadow on the ground as long as these rays of light are not parallel or perpendicular to the lamp post. *What happens in the case of parallel or perpendicular rays of light?* The height of the shadow is determined by looking at the ray that intersects the top of the lamp post and advecting the top of the post to the ground along this ray. The advection of this point to the ground is an example of a non-orthogonal[^1] projector. Linear algebra is a suitable medium for modeling this phenomena as we shall soon see.
    ![Visual of physical example](images/lamppost.png#center)
    *Figure 1: Picture of the top of the lamp post being advected to the tip of the shadow along the ray of light (depicted in black) that intersects the top of the post.*

#### Elementary Projectors

In general, we define an elementary projector using two objects: a given real-valued linear function $\mathbf{f}^T$, and a given vector $\mathbf{r}$. The projection of a point $\mathbf{z}$ is then defined in the following manner. Consider the point $\mathbf{z}$ and the hyperplane defined by $\mathbf{f}^T$ that it lies on. Then look at the point formed by the intersection of the foregoing hyperplane with $\text{span}\{\mathbf{r}\}$. This point of intersection is defined as the elementary projection of $\mathbf{z}$ onto $\text{span}\{\mathbf{r}\}$ given $\mathbf{f}^T$. This process can be viewed as advecting $\mathbf{z}$ along the line segment connecting it to $\text{span}\{\mathbf{r}\}$ which lies wholly in a level set of $\mathbf{f}^T$.

In our physical analogy level sets of $\mathbf{f}^T$ correspond to rays of light and the floor corresponds to $\text{span} \{\mathbf{r}\}$.

We deduce a mathematical formula by exploiting two critical facts: the projection is equal to $\lambda \mathbf{r}$ for appropriate scalar $\lambda$, and the projection and $\mathbf{z}$ lie in the same level set of $\mathbf{f}^T$. Thus $\lambda = \frac{\mathbf{f}^{T}\mathbf{z}}{\mathbf{f}^T\mathbf{r}}$. Therefore our resulting projection is,

$$\frac{\mathbf{r}\mathbf{f}^{T}}{\mathbf{f}^T\mathbf{r}} \mathbf{z}.$$

We note in our derivation we assumed that $\mathbf{f}^{T}$ intersects $\mathbf{r}$ at a unique point. This is equivalent to assuming $\mathbf{f}^{T}\mathbf{r} \neq 0$ which makes our expression well defined. Given the derivation we can summarize our findings with the following.

> **Definition:** We say an operator $\mathbf{P}$ is an **elementary projector** if $\mathbf{P} = \frac{\mathbf{r}\mathbf{f}^{T}}{\mathbf{f}^T\mathbf{r}}$.

We can verify this is in fact a projector by calculating $\mathbf{P}^2$ and observing the $\mathbf{P}$ is idempotent. Thus our elementary projector is a projector as expected.

We note an equivalent definition of elementary projector is the following.

> **Definition:** Given a direct sum $U+W = V$, we define a projector $\mathbf{P}$ exactly as before. If $U$ is one dimensional then we call $\mathbf{P}$ an **elementary projector**. 

Both definitions of an elementary projector are equivalent, however the first gives us a formula and method to compute an elementary projector. For clarity and completeness we demonstrate a proof that these are equivalent.

> **Theorem:** Every projector, $\mathbf{P}$, onto a one dimensional subspace can be written as  $\frac{\mathbf{r}\mathbf{f}^{T}}{\mathbf{f}^T\mathbf{r}}$

#### Example 1: $2 \times 2$ Matrix Inverse
Given a matrix, 
$$
M = \begin{bmatrix}a & b \newline c & d\end{bmatrix} = \begin{bmatrix}
    \vert & \vert \newline
    p   & q   \newline
    \vert & \vert
\end{bmatrix},
$$
it is well-known that the inverse matrix is,
$$
M^{-1} = \frac{1}{ad-bc}\begin{bmatrix}d & -b \newline -c & a\end{bmatrix}.
$$
![Visual of change of coordinates](images/projection.png#center)
*Figure 1: The orange and green lines correspond to the $p$ and $q$ axes, respectively. Their intersection is the origin and the light blue point denotes the projection onto $\text{span }p$*

Viewing the matrix, $M$, as a change of coordinates leads to a perspicuous derivation of the inverse. $M$ takes coordinates from the $pq$ grid and changes them to coordinates of the $xy$ grid. Hence, the inverse should be the matrix that transforms $xy$ coordinates $pq$ coordinates. Moving a point written in $xy$ coordinates onto the line $\text{span }p$ geometrically corresponds to translating the point along lines parallel to $\text{span }q$ until it intersects $\text{span }p$. This is exactly an elementary projection where $r = p$ and $f^T$ has level sets parallel to $\text{span }q$. To determine $f^T$ precisely can be identified with a $1 \times 2$ matrix that sends $\text{span } q$ to $0$. One can arrive at $f^T = \begin{bmatrix} d & -b\end{bmatrix}$ by guessing or by rotating $q$ ninety degrees counterclockwise . Thus we conclude,
$$
    \frac{f^{T}}{f^Tr} = \frac{1}{ad-bc} \begin{bmatrix} d & -b \end{bmatrix},
$$
is the operator we need to apply to $xy$ coordinates to find the $p$-coordinate in our $pq$ grid. This is exactly the first row of our inverse matrix above. The second row can be derived using the same methodology as above except interchanging the role of $p$ and $q$. 

This method generalizes to higher dimensions so we can understand how to geometrically derive inverses of matrices in all cases. However, it becomes tricky to determine $\mathbf{f}^T$ in higher dimensions. The cleanest method would be to use the determinant to derive the appropriate $\mathbf{f}^T$. Do you see how? This should also give complete geometric meaning to the [adjugate matrix](https://en.wikipedia.org/wiki/Adjugate_matrix) which is typically defined using cofactors and algebraic chicanery that obscures its geometric essence. 

#### Example 2: Stereographic Projection

Stereographic projection is a mapping of the unit sphere in 3d space to a plane. The mapping is defined as follows. For any point on the sphere, call it $P$, draw the line intersecting the north pole, denoted $N$, and the foregoing sphere; the intersection of this line, $\overline{PN}$, and the $xy$ plane is the stereographic projection of the point. The north pole is the only point on the sphere for which we cannot define its stereographic projection. The earliest extant record of this mapping is due to Ptolemy (100-170AD), although its discovery is possibly earlier given the sparsity of ancient texts. Furthermore, since this is a mapping of a sphere to a plane it can be used to create a map of planet Earth, but now also finds itself being used in areas such as Complex Analysis.
    ![Visual of stereographic projection](images/stereographic.png#center)
If we restrict to only looking at the plane containing the origin, $P$, and $N$ we see this operation can be described by an elementary projector. Let $\mathbf{r}$ correspond to the horizontal axis and let $\mathbf{f}^T$ have level sets parallel to the line between the North Pole and $P$. That is use the North Pole and $P$ to deduce $\mathbf{f}^T$. The elementary projector is determined and one can deduce the $x$ and $y$ components in 3d space using basic trigonometry.

### Projections to Subspaces
#### Big Theorem: Decomposition
Up until now we have only considered the simplest projectors and  basic applications. A generic projector can have $\text{dim }U > 1$. These may seem more complicated however we have the following decomposition.
> **Theorem:** Every projector $\mathbf{P}$ can be decomposed into a sum of pairwise, mutually annihilating elementary projectors. That is $\mathbf{P} = \mathbf{P}_1 + \mathbf{P_2} + \ldots + \mathbf{P}_m$ where $\mathbf{P}_i\mathbf{P}_j = 0$ if $i \neq j$.

Let $U + W = V$ be the direct sum such that $\mathbf{P}\mathbf{z} = \mathbf{P}(\mathbf{u}+\mathbf{w}) = \mathbf{u}$ where $\mathbf{u} \in U$ and $\mathbf{w} \in W$. Consider $\mathbf{u}_1, \mathbf{u}_2, \ldots, \mathbf{u}_m$ to be a basis for $U$. Then given the direct sum $\text{span } \mathbf{u}_i + (( \cup\_{j \neq i} \mathbf{u}_j ) \cup W )$ define the elementary projector, $\mathbf{P}_i$, which maps onto $\text{span }\mathbf{u}_i $. From our definitions we have that $\mathbf{P} = \mathbf{P}_1 + \ldots + \mathbf{P}_m$. The various $\mathbf{P}_i$ are also mutually annihilating(i.e. $\mathbf{P}_i\mathbf{P}_j = 0$ if $ i \neq j$) which is easily verified.
#### Example 1: Complementary Projector

#### Example 2: Null Space Projector
#### Example 3: Particular Solutions

#### Example 3: Least Squares

### Orthogonal Projectors
> **Definition:** An **orthogonal projector** is a projector whose null space and range are orthogonal. 


Again, a surprising fact is that there is a simple test to tell whether a given linear operator is an orthogonal projector. 
 > **Theorem:** A linear operator, $\mathbf{P}$, is an orthogonal projector if and only if $\mathbf{P}^2 = \mathbf{P}$ and $\mathbf{P}=\mathbf{P}^*$. That is $\mathbf{P}$ is idempotent and self-adjoint.

In particular if we write $\mathbf{P}$ with respect to an orthonormal basis, then $\mathbf{P}$ is self-adjoint reduces to checking if $\mathbf{P}$ is symmetric.

Note our earlier physical example using light is *not* an orthogonal projector because the rays of light were not perpendicular to the ground. An orthogonal projector is analogous to the school saying, “drop a perpendicular”. Be wary that in many contexts the word projector often refers to orthogonal projectors.

#### Elementary Orthogonal Projectors
Recall that we used a real-valued linear function, $\mathbf{r}^T$ , and a vector, $\mathbf{c}$, to define an elementary projector. If our coordinate system consists of basis of orthonormal vectors(as is almost always the case in applications) then the transpose of $c$ is the appropriate choice of $\mathbf{r}^T$.  This process corresponds to projection of a point onto a line in a coordinate system consisting of straight, perpendicular axes such as the Cartesian plane.

#### Example 1: Least Squares Again!
#### Example 2: Quantum Information
#### Example 3: Spectral Theory
#### Example 4: Principal Component Analysis (PCA) 
 

### Connection to Optimization
We are often in situations where we are given a norm. That is we are given a way to measure lengths in the space.

### Determinants of Projectors
### Trace of Projectors
### Follow-ups 




[^1]: Non-orthogonal refers to the fact that the ray connecting the tips of the shadow and post does not form a right angle with the ground.
