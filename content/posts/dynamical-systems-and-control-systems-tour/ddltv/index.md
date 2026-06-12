---
title: Discrete Deterministic Linear Time-Varying Dynamical System
date: 2025-04-24T19:35:48-04:00
author: Aman Shah
draft: true
math: true
---

## Introduction

## Linear Time-Varying Dynamical System

\\[
\begin{align*}
	x_{t+1} &= A_{t}x_{t}\\
	y_{t} &= Cx_{t}  \\
\end{align*}
\\]

## Computing Future States

In this case computing future states $x_t$ is very simple and simply involves unrolling the recursive formula given by the transition dynamics.

## Stability
This sections requires having read the stability note for general autonomous dynamical systems. We are going to state the important results and characterizations that apply in the LTI system case. We will also remark on terminology

### Equilibrium States[^1]
An equilibrium state is a state from which the system does not deviate; that is if we start at $e$ and follow the transition dynamics we stay at $e$. In our discrete LTI dynamical system, this means $e$ is an equilibrium if and only if $Ae=e$. 

We begin by analyzing are there any equilibrium points, if so how many and is there any structure to them?

Since our equilibrium state must be a fixed point under $A$, and every matrix fixes $0$, we have at least $1$ equilibrium point being the origin. Any nonzero solution of $Ae=e$ are eigenvectors corresponding eigenvalue $1$. This means that we either have $1$ equilibrium point or infinitely many where the infinitely many equilibrium points form a subspace.

### Collapse of Ideas

#### An Equivalent Definition of Stability in the LTI Case
Stability, in general, means that for any positive $\epsilon$ there exists a positive $\delta$ such that any initial condition within $\delta$ of $e$ will stay within $\epsilon$ of $e$ for all future states. \
\
For LTV systems it turns out this is equivalent to given an initial state, future states will be bounded for all time. 
\


#### Global vs Local
A key result is that for an LTI system local and global stability are the same thing, that is one implies the others. 

The statement being made is that local asymptotic stability, or local exponential stability implies global stability, asymptotic or exponential stability.

If $|x_t - e| < \epsilon$ when $|x_0 - e| < \delta$ then we have by linearity. That $|\lambda x_0 - e| < \delta * \lambda$, then 

Remember normally global implies local.


### Lyapunov Function Approach to Stability
The Lyapunov function approach is more general and applies to a wider array of dynamical systems. In its most general form it isn’t the most intuitive so we will try to exposit some clarity to the ideas and key results.

The idea is that some functions give us hints on if the states are converging to something or not. For example, if we are interested in points converging to the origin we can consider a function like the Euclidean norm, $x^TPx$. This quantity is only zero if x is 0 and positive for nonzero $x$. If the length of $x_t$ decreases over time and tends towards $0$ we know $x_t$ gets closer to $0$. We would want to see the norm of $x_t$ decrease with time or more specifically we what would that $x_{t}^{T}Px_{t}$ decreases. That means 

\\[
x_{t+1}^TPx_{t+1} < x_{t}^TPx_{t} \\
x_{t}A^TPAx_{t} < x_{t}^TP{x} \\
x_{t}^T(A^TPA - P)x_{t} < 0
\\]

A way to satisfy this would be if $A^TPA - P$ is negative definite that is $A^TPA - P = -Q$ for PD $Q$.

#### System vs Equilibrium Point Stability

## Observability
Observability is that uses the output equation of the system. Observability is simply the idea that you can determine the initial state of the system given a sequence of outputs.


## Detectability
This is weaker than observability and means that any state indistinguishable from $0$ by observation converges to 0.



## Comments on Mathematical Setting
Here the transition dynamics require a vector space, often we find Banach spaces the natural choice for control theory over a sufficiently nice field like C or R. Distinctions are made for those who care, and for those who don’t it is neither here nor there

[^1]: Equilibrium points are a concept widely used, and have many synonyms : stationary point, steady state, fixed-point critical point

