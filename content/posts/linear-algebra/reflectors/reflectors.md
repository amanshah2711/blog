---
title: "Reflectors"
date: 2024-02-27T02:15:21-05:00
author: Aman Shah
draft: true
math: true
---

## Reflectors
We will mimic the development done for projectors to develop the theory of reflectors.

> **Definition:** Given some direct sum $U+W = V$, we define a **reflector**, $\mathbf{R}: V \to V$ as follows. Since $U+W = V$ we have any $\mathbf{v} \in V$ has unique representation as $\mathbf{v} = \mathbf{u} + \mathbf{w}$ for some choice of $\mathbf{u} \in U$ and $\mathbf{w} \in W$. With this we define $\mathbf{Rv} := \mathbf{u} - \mathbf{w}$. 

 *Exercise: Prove that a reflector is linear.*
 
 > **Example 3:** Consider the direct sum $X+Y$ from Example 2. We can define a reflector that reflects over the $X$ or $Y$ axis. This coincides with what we typically think of as reflection.
### Relation to Projections
It turns out reflectors and projectors are intimately related. When we reflect a point in the plane over the $x$-axis, we could explicitly do this in 2 steps. We could first project the point onto the $y$-axis. Then we subtract twice the projection onto the $y$-axis from the original point. It turns out this method using projectors to build reflectors is more general. We sum this up as follows.
> **Theorem:** Every reflector $\mathbf{R}$ can be expressed $\mathbf{R} = \mathbf{I} - 2\mathbf{P}$ where $\mathbf{P}$ is some appropriate choice of projector.

Given the direct sum $U+W$ corresponding to the reflector $\mathbf{R}$ we define the projector $\mathbf{P}_W \mathbf{z} = \mathbf{P}_W (\mathbf{u} + \mathbf{w}) = \mathbf{w}$. From this it follows that $\mathbf{R} = \mathbf{I} - 2\mathbf{P}_W$.

### Relation to Involution
 We say a function, $f$, is an **involution** if $(f \circ f)(x) = x$. That is if applying the function twice is the same as applying the identity. There are many examples such as taking reciprocals, multiplying by $-1$, or complex conjugation. 

 Now our definition of reflectors makes it simple to construct a reflector given a direct sum. However, it may not be obvious if a given linear operator is a reflector. It turns out there is a simple test to determine if a given linear operator, $\mathbf{R}$, is a reflector.

 > **Theorem:** A linear operator, $\mathbf{R}$, is a reflector if and only if $\mathbf{R}^2 = \mathbf{I}$. That is $\mathbf{R}$ is involution.

Proving the necessity of involution is a straightforward exercise. Do you see why? However proving that if a linear operator, $\mathbf{R}$ satisfies $\mathbf{R}^2 = \mathbf{I}$ then it is a reflection is more difficult. We invoke the relation to projection to note
### Reflection Over Hyperplanes
#### Physical Example
#### Elementary Reflectors 
#### Example 1: Complex Conjugation
#### Example 2: Swapping Rows Gaussian Elimination
### Reflection Over Subspaces
#### Big Theorem: Decomposition
### Orthogonal Reflectors
#### Elementary Orthogonal Reflectors (Householder Reflectors)
### Determinants of Reflectors
### Trace of Reflectors
### Follow-ups