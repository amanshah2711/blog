---
title: Sylvester Equation
date: 2026-06-09T19:39:00-04:00
author: Aman Shah
draft: true
math: true
---


## Introduction
The Sylvester equation is a matrix equation that generalizes many important relationships in linear algebra. In this note we exposit perspicuous approaches to showing when the Sylvester equation admits solutions, and properties about those solutions. 

## Sylvester Equation

The Sylvester equation is defined as the matrix equation 
\\[
AX + XB = C
\\]
where $A \in \mathbb{R}^{n \times n}$, $B \in \mathbb{R}^{m \times m}$, and $C \in \mathbb{R}^{n \times m}$ are given and $X \in \mathbb{R}^{n \times m}$ is unknown.

### Existence of Solutions
We will handle this in two parts the first where we can solve for $X$ given any $C$, and the second where solutions may exist. The analogue is to solving a linear system $Ax=b$ when $A$ is invertible and when $A$ is not invertible. Our primary tool in this analysis will be Fredholm theory. There are several other approaches to showing solutions exist exposited in standard references.

#### Mathematical Setting
We consider the inner product space, $\mathbb{R}^{n \times m}$ where the inner product is the Frobenius inner product, $\langle A, B \rangle = tr(A^TB)$. We also define the operator $L(X) = AX + XB$, which is easily verified to be linear. In this scenario the Fredholm alternative can be phrased as,

1. There exists a solution to $L(X) = C$ where $L(X) = AX + XB$
2. There exists a $W \in \mathbb{R}^{n \times m}$ such that $\langle W, L(X) \rangle$ for all $X \in \mathbb{R}^{n \times m}$ and $\langle W, C \rangle \neq 0$ 

#### Fredholm Implies A Solution

For a solution to exist, for every C we ultimately need the second alternative to never be true. One way for this to occur is that only $W=0$ satisfies $\langle W, L(X) \rangle$ for all $X \in \mathbb{R}^{n \times m}$, for if this is true $\langle W, C \rangle = 0$ for any choice of $C$. 

Expanding and using properties of trace we find that,

\\[
\begin{aligned}
	\langle W, L(X) \rangle 
		&= \langle W, AX + XB \rangle \\
		&= tr(W^{T}(AX + XB)) \\
		&= tr(W^{T}AX) + tr(W^{T}XB) \\
		&= tr(W^{T}AX) + tr(BW^{T}X) \\
		&= tr((W^{T}A + BW^{T})X) \\
		&= \langle A^{T}W + WB^{T}, X \rangle									
\end{aligned}
\\]
For $\langle W, L(X) \rangle = \langle A^{T}W + WB^{T}, X \rangle= 0$ for all $X \in \mathbb{R}^{n \times m}$, we must have $A^{T}W + WB^{T} = 0$. We must now exploit this equality to deduce that $W$ must be 0.

Let $\phi(\cdot)$ denote the minimal polynomial of $A$ given by the Cayley-Hamilton theorem. We know $\phi(A) = a_{0} + a_{1}A + \ldots + a_{n}A^{n} = 0$. In addition, the transpose of $A$ satisfies the same minimal polynomial, that is $\phi(A^{T}) = 0$. By right multiplying by $W$ we can invoke our equality given by Fredholm theory, to see that $\phi(A^T)W = W\phi(-B^T)$ = 0. If $A$ and $-B$, and consequently $A^T$ and $-B^T$, have no common eigenvalues then $\phi(-B^T)$ is invertible, which implies $W$ must be $0$, and thus if $W$ must be $0$ then the equation is solvable for every $C$. 

When solving $Ax=b$ we know if $A$ is invertible we can solve for any choice of $b$; for our Sylvester equation, the analogue is the condition that $A$ and $-B$ have no common eigenvalues. As with solutions $Ax=b$ we know we can solve for $x$ sometimes when $A$ is not invertible, the usual condition is phrased as $b$ lies in the column space of $A$. Analogously we can amend our earlier proof to understand for exactly which $C$ we can solve the Sylvester equation.

When $A$ and $-B$ share a common eigenvalue, $\phi(-B^T)$ is not invertible, because the factors $(-B^T - \lambda_i)^{m_i}$ are zero for the $\lambda_i$ that are common eigenvalues. Selecting $W = uv^T$ where $u$ is the left eigenvector of $A$ corresponding to $\lambda_i$, and $v$ is the right eigenvector of $-B$ corresponding to $\lambda_i$, we have $A^{T}W + WB^T = 0$. This non-zero choice of $W$ is now satisfies our requirement from Fredholm theory, which means $tr(W^TC) = 0$.

#### Using Vec

Noting that $L$ is linear allows us to rewrite the equation as a traditional linear system of the form $Ax=b$. To achieve this form the operation $vec(\cdot)$ which takes a matrix and stacks the columns into a vector is helpful. Using $vec$ on our linear system we find that, 

\\[
\begin{aligned}
	&vec(AX+XB) = vec(C) \\
 	\implies &vec(AX)+vec(XB) = vec(C) \\
 	\implies &(I \otimes A)vec(X) +(B^{T} \otimes I)vec(X) = vec(C) \\
 	\implies &((I \otimes A) +(B^T \otimes I))vec(X) = vec(C)
\end{aligned}
\\]

Now we have a usual linear system, from which we can use any of the litany of equivalent facts to deduce when the matrix $(I \otimes A) +(B^T \otimes I)$ is invertible.


## Applications
### Linear Equations
Taking $C, X \in \mathbb{R}^{n \times 1}$ and $B=0$ we have a typical linear equation, $AX=C$, where $A$ is a known rectangular matrix and $C$ is a given vector.

### Matrix Inversion
Letting all matrices involved be square, we can find the left or right inverse (both coincide) by setting $C=I$ and setting either $B$ or $A$ to 0 depending on if we want to solve for $A^{-1}$ or $B^{-1}$ respectively.

### Matrix Commutation
By setting $C=0$ and setting $B=-A$ we end up with $AX=XA$, so any solution of the Sylvester equation is a matrix that commutes with $A$. 

### Eigenvector Computation
By choosing $C=0$ and $-B$ to be the scalar eigenvalue we have that any solution to the Sylvester equation is a right eigenvector of $A$. We can find left eigenvectors of $B$ in similar fashion.

## Special Cases Of Interest
### Continuous Lyapunov Equation
In dynamical systems and control theory, one often encounters the continuous Lyapunov equation,
\\[
AX + XA^T = -Q
\\]
where $Q$ is symmetric positive definite, or symmetric positive semi-definite. 

## Perturbation Theory

## Backwards Error

## References

