---
title: Linear Systems of Equations
date: 2025-09-12T12:11:15-04:00
author: Aman Shah
draft: true
math: true
---
## Prerequisites 
Linear systems of equations are introduced in early mathematical education. Though simple, there is a rich theory that connects them to higher level mathematics and a vast array of applications. Please make sure you either know the content of or skim the following notes prior to reading this.
- [Vector Spaces](/posts/visualizing_vectors)
- [Hyperplanes](/posts/hyperplanes)
## Algebraic Problem
In general we want to find real numbers $x_1, x_2, \ldots, x_n$ that satisfy the following equations, where all the other variables are given,
\\[
\begin{align*}
a_{1,1}x_{1} + a_{1,2}x_{2} + &\ldots + a_{1,n}x_{n} = b_{1} \\
a_{2,1}x_{1} + a_{2,2}x_{2} + &\ldots + a_{2,n}x_{n} = b_{2} \\
& \cdots  \\
& \cdots  \\
a_{m,1}x_{1} + a_{m,2}x_{2} + &\ldots + a_{m,n}x_{n} = b_{m} 
\end{align*}
\\]
### General Problem
Given the algebraic problem above we can ascribe “meaning” to the problem by using the framework and tools developed by linear algebra. This allows us to view the algebraic problem geometrically and gain insight into the problem from geometry or  vice versa where the algebra can provide insight into geometry.\

#### Representation of Linear Maps
The most common approach is to look at the problem as a representation of a linear map between vector spaces. So for example we can rewrite this is  

#### Hyperplane Interpretation
Another approach is to treat each equation as describing that a point $x$ lie in the level set of a given hyperplane.

### Invertible Problem
A very prominent class of problems is when there exists a solution for every choice of $b$ and this solution is unique.

#### Representation of Linear Maps
Everything stated about representations of linear maps prior still applies except now that general linear map is also invertible. This doesn’t provide any particularly new insight.

#### Change of Basis Interpretation
Now that we know the map is invertible the map could possibly also represent a change of basis between coordinate systems. 

#### Flag Interpretation
COME BACK LATER
## Conditions For Solvability
### Fredholms’ Theorem of Alternative
## Theoretical Solving
Now that we know what the problem is, how we can interpret the problem and when there exists a solution, we now turn to actually computing the solution. 
### Invertible A
When A is invertible we can simply compute $A^{-1}$ and this has a wonderful geometric interpretation explored in [Matrix Inverse](/posts/matrix_inverse)
### Non-Invertible A
When A is non-invertible we have to turn to a new notion of generalized inverses
## Selected Examples
- [Chemical Balance](/posts/chemical_balance)
- [Least Squares](/posts/least_squares)