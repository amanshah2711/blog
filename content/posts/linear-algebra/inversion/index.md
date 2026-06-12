---
title: "Matrix Inverse"
date: 2023-05-01T07:20:50-04:00
author: Aman Shah
draft: true
math: true
---

## Prerequisites
- [Projections](/posts/projections)
- [Shears](/posts/shears)
- [Determinants](/posts/oriented_area_vs_area)
- [Gaussian Elimination](/posts/)

## Problem Statement
Given a matrix square matrix $A$ we want to find an explicit formula for the matrix $A^{-1}$. There are many ways to define $A^{-1}$ and at this juncture we will simply say it is the matrix satisfying,
\\[
AA^{-1} = A^{-1}A = I
\\].
## 2-by-2 Matrix Inverse
We will work through the 2-by-2 case in explicit detail for pedagogical clarity and because the 2-by-2 matrix inverse formula is the most used by students. For the following two sections let 
\\[
A = \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \begin{bmatrix} u & v\end{bmatrix}
\\]
### Passive Interpretation
Since $A$ is an invertible matrix we can, without loss of generality, think of $A$ as representing a change of coordinates from a basis $\mathbf{B}$ to a basis $\mathbf{C}$. Mathematically this means if we have coordinate vectors with respect to basis $\mathbf{B}$ then we have $\mathbf{x}= \mathbf{B}x$ where $x$ is the coordinate vector and we further have $\mathbf{x} = \mathbf{C}\mathsf{x} = \mathbf{B}x = \mathbf{C}Ax$. Observe that $\mathsf{x}$ is the representation of $\mathbf{x}$ with respect to basis, $\mathbf{C}$, and $A$ takes a coordinate vector from basis $\mathbf{B}$ and moves it to a coordinate vector for $\mathbf{C}$ and consequently the big chain of equalities must be satisfied for $A$ to have this interpretation. $A^{-1}$ is then the matrix that reverts to our original coordinates, which then means $\mathbf{x} = \mathbf{C}\mathsf{x} = \mathbf{B} A^{-1}\mathsf{x}$. 

Using the notation for $A$ above we see that $\mathbf{B} = \mathbf{C}A$, and consequently $A$ denotes how the basis $\mathbf{B}$ is represented in the $\mathbf{C}$ coordinate system. Thus $u$ and $v$ are representations of the basis vectors $\mathbf{B}$ written in the $\mathbf{C}$ coordinate system. Our goal is then to find the inverse relationship, that is how to represent the basis of $\mathbf{C}$ with respect to the $\mathbf{B}$ coordinate system.\

To do this we recognize we need two pieces of information: the basis $\mathbf{C}$ and some way to project them onto the coordinate system of $\mathbf{B}$. Since we have the $\mathbf{B}$ written with respect to $\mathbf{C}$ it should be clear that the standard coordinate vectors are in fact known. Then the latter question of how to project them is given by the tool of the elementary projector. 

We will first project our point onto the $\mathbf{u}$ axis, along lines parallel to $\mathbf{v}$. To do this we need hyperplanes containing $\mathbf{v}$. Now if we look at $v$ which is the representation of $\mathbf{v}$ with respect to the basis $\mathbf{C}$, we have $v = \begin{bmatrix} v_1 \\ v_2 \end{bmatrix}$ and likewise $u = \begin{bmatrix} u_1 \\ u_2 \end{bmatrix}$. A hyperplane that contains $\mathbf{v}$ in this coordinate system is $f^H = \text{constant} * \begin{bmatrix} v_2 & -v_1\end{bmatrix}$. Now notice the constant is there because we have found hyperplanes containing $v$ although we need families of hyperplanes that is we need to determine the spacing between the parallel lines(or hyperplanes in general). We know that $u$ is one unit in the “horizontal direction” so we know that $f^Hu= \text{constant} * \begin{bmatrix} v_2 & -v_1\end{bmatrix}u = 1$ from which we deduce our constant to be $\lambda := u_1v_2-v_1u_2$. So now we have $f^H = \frac{1}{u_1v_2-v_1u_2} \begin{bmatrix} v_2 & -v_1\end{bmatrix}$ projects points along the lines parallel to $v$ in a way consistent with finding the $u$ coordinate of a point. \
\
Using the same guess and check schema we wish to project our point onto the $\mathbf{v}$ access along lines parallel to $\mathbf{u}$ which require finding a family of hyperplanes that contain $\mathbf{u}$ and measure $\mathbf{v}$ as 1. In the same way we deduce $g^H = \text{constant} * \begin{bmatrix} u_2 -u_1\end{bmatrix}$ and the need to satisfy $g^Hv = \text{constant} * \begin{bmatrix} u_2 & -u_1\end{bmatrix}v= 1$ which yields our constant to be $\mu  = v_1u_2 - u_1v_2$. Now we find that $g^H =  \frac{1}{v_1u_2 - u_1v_2}\begin{bmatrix} u_2 & -u_1\end{bmatrix}$. For notation sake we will re-express $g^H= \frac{1}{u_1v_2-v_1u_2}\begin{bmatrix} -u_2 & u_1\end{bmatrix}$.\
\
Thus $f^H$ and $g^H$ take coordinates in basis $\mathbf{C}$ and tell you how to find the corresponding coordinates in $\mathbf{B}$. This means they do exactly what $A^{-1}$ needs to do and thus we can deduce $A^{-1}$ as a matrix with rows $A^{-1}=\begin{bmatrix} f^H \\ g^H \end{bmatrix}$. Writing this out fully we have,\
\
\\[
A^{-1} = \frac{1}{u_1v_2 - v_1u_2}\begin{bmatrix} v_2 & -v_1 \\ -u_2 & u_1 \end{bmatrix} = \frac{1}{ad-bc}\begin{bmatrix}d & -b \\ -c & a\end{bmatrix}
\\]

We have come up with a derivation, and now you should verify that $A^{-1}$ satisfies the defining property we want of an inverse.


Make this an aside at the end: This is easy enough to deduce by observation, or geometrically one could rotate the vector $v$ by 90 degrees although this requires using some basic tools from orthogonal structure which is not essential to the problem.

#### Cramer’s Rule[^1]  
When solving linear systems $Ax = b$, we have that $x=A^{-1}b$ and using the formula for $A^{-1}$ with $b$ gives explicit formulas for $x_1$ and $x_2$. These formulae for an explicit solution are often referred to as Cramer’s rule. 

In particular, Cramer’s rule is often referred to when the solution is written using determinants.

### Active Interpretation
We can also interpret $A$ as a representation of a linear map, in which case we view the points as actively moving. Our goal then becomes to simply move the points back to their starting point. Doing so directly is quite hard but it turns out it is quite simple to do if we iteratively apply elementary shears.
\

### When All Else Fails ...
Gaussian elimination or any method can do the trick. Here assuming we have no geometric or higher insights into the problem we can attempt to deduce $A^{-1}$ directly. This means we are looking for a matrix $B$ satisfying $BA = I$. Explicitly this gives us four equations,\
\
\\[
b_{11}a + b_{12}c = 1 \\
b_{11}b + b_{12}d = 0 \\
b_{21}a + b_{22}c = 0 \\
b_{21}b + b_{22}d = 1 \\
\\]

Notice there are 4 variables, but the first two equations contain the same two variables and the last two equations have only the other two variables. This gives a system that can be solved by Gaussian elimination.

## n-by-n Matrix Inverse

### Passive Interpretation
Everything is identical to the 2-by-2 case, however identifying the projector to use is not as simple to guess and check. 

#### Cramer’s Rule

### Active Interpretation

## Adjugate Matrix

## Follow up
One may be interested in the case an inverse does not exist, then we move to the notion of generalized inverses. This is exactly the characterization of when we can solve but not perfectly.


[^1]: Stigler’s Law of Eponymy possibly? Cramer’s Law while published by Cramer was known in special cases to Maclauren many years prior.