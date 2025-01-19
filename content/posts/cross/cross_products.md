---
title: "Cross Products"
date: 2024-03-01T05:19:40-05:00
author: Aman Shah
draft: true
math: true
---

## Introduction
The cross product is an operation between two vectors that exists in Euclidean space, and for this note specifically three-dimensional Euclidean space. The cross product is intimately related to rotations and its algebraic properties, while seemingly bizarre at first glance become natural when motivated sufficiently. Here we will exposit some motivation and often skirted nuances of the cross product that are often left to students to figure out themselves.
## Definition
Suppose we are given two vectors $\mathbf{a}, \mathbf{b} \in \mathbf{R}^3$. Now we will use $a, b \in \mathbf{R}^3$ to denote the coordinate vectors of $\mathbf{a}$ and  $\mathbf{b}$ with respect to a given orthonormal basis, $\mathbf{B}$.
\\[
a \times b = \begin{bmatrix} 
															a_2b_3 - a_3b_2 \\
															a_3b_1 - a_1b_3 \\
															a_1b_2 - a_2b_1
															\end{bmatrix}.
\\]
Now this formula is seemingly bizarre, and at first glance it is not clear why this has anything to do with Euclidean spaces in particular. *Why did we specify the basis was orthonormal (keep reading for the answer)?*

### Motivation Using Gaussian Elimination

Given the same two coordinate vectors as above we can ask how does one construct the plane containing these two vectors. We know that a plane $r^H$ contains the vectors if $r^Ha = r^Hb = 0$. Writing this out explicitly we find that,
\\[
\begin{bmatrix} 
															a_1 & a_2 & a_3 \\
															b_1 & b_2 & b_3 
\end{bmatrix}
\begin{bmatrix} 
															r_1 \\
															r_2 \\
															r_3 															
\end{bmatrix}
=
\begin{bmatrix} 
															0 \\
															0 \\
															0
\end{bmatrix}.
\\]
Now when solving for the component of $r^T$ we find that we get infinitely many solutions. We have three variables and two equations making the solution set a line. Explicitly this line is,
\\[
 \mathbf{span}\begin{bmatrix} 
															a_2b_3 - a_3b_2 \\
															a_3b_1 - a_1b_3 \\
															a_1b_2 - a_2b_1
															\end{bmatrix}.
\\]
*Verify this yourself.*
 
At first glance it might seem as though we can simply pick a vector from this line, label is as the cross product, and be on our merry way. 
### Motivation Using Riesz-Representation

### Motivation Using Skew-Symmetric Matrices
### What In The Type?!?!
### A Preferred Notation
## Possibly Pernicious (Pseudo)-Vector?
### Prepare For Trouble...
### And Make It Double... 
### Resolution
### David Meredith’s Identity
### When Does Our Formula Actually Work?
## Useful Identities
### Determinant Identity
### Grassmann’s Triple Product
### Jacobi’s Identity
### Lagrange’s Identity
## Applications:
### Least Squares!
### Join and Meet Projective Geometry 
## Computing A Cross
### Backwards Stability
### Forwards Stability
### Conditioning
### Techniques
## Exterior Algebra
## Random History
### Joseph Louis Lagrange
### William Rowan Hamilton
### Josiah Willard Gibbs




