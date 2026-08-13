---
title: Discrete Sylvester Equation
date: 2026-06-13T01:45:07-04:00
author: Aman Shah
draft: true
math: true
---


## Introduction

## Discrete Sylvester Equation

The discrete Sylvester equation is defined as the matrix equation 
\\[
AXB - X = C
\\]
where $A \in \mathbb{R}^{n \times n}$, $B \in \mathbb{R}^{n \times n}$, and $C \in \mathbb{R}^{n \times n}$ are given and $X \in \mathbb{R}^{n \times n}$ is unknown.
### Existence of Solutions
We will handle this in two parts the first where we can solve for $X$ given any $C$, and the second where solutions may exist. The analogue is to solving a linear system $Ax=b$ when $A$ is invertible and when $A$ is not invertible. Our primary tool in this analysis will be Fredholm theory. There are several other approaches to showing solutions exist exposited in standard references.

#### Mathematical Setting
We consider the inner product space, $\mathbb{R}^{n \times m}$ where the inner product is the Frobenius inner product, $\langle A, B \rangle = tr(A^TB)$. We also define the operator $L(X) = AXB-X$, which is easily verified to be linear. In this scenario the Fredholm alternative can be phrased as,

1. There exists a solution to $L(X) = C$ where $L(X) = AXB-X$
2. There exists a $W \in \mathbb{R}^{n \times m}$ such that $\langle W, L(X) \rangle$ for all $X \in \mathbb{R}^{n \times m}$ and $\langle W, C \rangle \neq 0$ 

#### Fredholm Implies A Solution
For a solution to exist, for every C we ultimately need the second alternative to never be true. One way for this to occur is that only $W=0$ satisfies $\langle W, L(X) \rangle$ for all $X \in \mathbb{R}^{n \times m}$, for if this is true $\langle W, C \rangle = 0$ for any choice of $C$. 

Expanding and using properties of trace we find that,
\\[
\begin{aligned}
	\langle W, L(X) \rangle &= \langle W, AXB-X \rangle\\
	&= tr(W^{T}(AXB-X)) \\
	&= tr(W^{T}AXB - W^{T}X) \\
	&= tr(W^{T}AXB) - tr(W^{T}X) \\
	&= tr(BW^{T}AX) - tr(W^{T}X) \\
	&= tr((BW^{T}A-W^{T})X) \\
	&= \langle A^{T}WB^{T}-W, X \rangle
\end{aligned}
\\]

Thus for $\langle W, L(X) \rangle = 0$ for all $X \in \mathbb{R}^{n \times n}$ we need $A^{T}WB^{T}-W = 0$. It now remains to show that this equality implies $W=0$. If only $W=0$ satisfies this equality, the system is solvable for any choice of $C$.

To show this we invoke the Cayley-Hamilton theorem and assume the polynomial $\phi(\cdot)$ is the polynomial for which $\phi(A)=0$ given. We expand $\phi(A) = a_{0}I + a_{1}A + \ldots + a_{n}A^{n}$. Now we left multiply $W^{T}$, and we exploiting our equation $BW^{T}A = W^{T}$ we find that 
\\[
\begin{aligned}
W^{T}\phi(A) &= a_{0}W^{T} + a_{1}W^{T}A + \ldots + a_{n}W^{T}A^{n} \\
 &= a_{0}B^{n}W^{T}A^{n} + a_{1}W^{T}B^{n-1}A^{n} + \ldots + a_{n}W^{T}A^{n} \\
 &= (a_{0}B^{n} + a_{1}B^{n-1} + \ldots + a_{n}I)W^{T}A^{n}
\end{aligned}
\\]
If we define the polynomial $\varphi(x) = x^{n}\phi(\frac{1}{x})$, we have any non-zero root, $z$, of $\phi(\cdot)$ gives $\frac{1}{z}$ as a root for $\varphi(\cdot)$. Thus if $B$ does not have any of its eigenvalues being reciprocals of any eigenvalues of $A$ we have $\varphi(B)$ is invertible. Thus $W^{T}\phi(A) = \varphi(B)W^{T}A^{n} = 0$, and invertibility of $\varphi(B)$ implies $W^{T}A^{n} = 0$ and thus since $W^{T} = B^{n}W^{T}A^{n} = B^{n} 0 = 0$. Thus the system is solvable for any choice of $C$.

#### Using vec

## Special Cases Of Interest
### Stein Equation / Discrete Lyapunov Equation
In dynamical systems and control theory, one often encounters the continuous Lyapunov equation,
\\[
AXA^T - X = Q
\\]
where $Q$ is symmetric positive definite, or symmetric positive semi-definite. 

## References