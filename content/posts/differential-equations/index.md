---
title: “Existence / Uniqueness of Differential Equations”
date: 2026-04-09T12:34:16-04:00
author: Aman Shah
draft: true
math: true
---

{{TOC}}
## Introduction
Differential equations are a ubiquitous model of continuous-time dynamics. Used by almost every STEM discipline for the interested reader it is often worth trying to learn a basic outline of when these models actually generate solutions. There are many varieties of differential equations, however this note will be focused on ordinary differential equations.

## Mathematical Landscape
We are going to work a finite dimensional vector space $V$. We will denote vectors in bold-face characters, and coordinate representations in other typefaces. So for example, $\mathbf{v} \in V$, and $v \in \mathbb{R}^n$ where $v$ is the coordinate representation of $\mathbf{v}$ under some basis. We will be talking about derivatives which require notions of limits so we will assume that $V$ is a topological vector space. We will do our best to phrase arguments in this manner.

## The Notion of Derivative

We are interested in curves in $V$. Curves correspond to the intuitive idea of a path taken in $V$, which mathematically is represented by $\mathbf{x} : I \subset \mathbb{R} \to V$. The image of a curve looks like a picture in the vector space $V$. Here are some examples.

Derivatives correspond to rates of changes, or tangent lines and this is true in the more general framework we have here. We will define a derivative of a curve $\mathbf{x}(\cdot)$ at time $t$ as follows,

\\[
\partial \mathbf{x} (t) = \lim_{s \to 0}\frac{\mathbf{x}(t+s) - \mathbf{x}(t)}{s}
\\] 

### Basic Derivative Facts

Derivatives are often useful because they allow us to translate many ideas about polynomials to differentiable functions.

 One of the key pieces that allows this is the Taylor approximation theorem which says that if $t_{0}$ is a point where $\mathbf{x}(\cdot)$ is differentiable, then

\\[
\mathbf{x}(t) = \mathbf{x}(t_{0}) + \partial \mathbf{x} (t_{0}) (t-t_{0}) + E(t-t_{0})
\\]


### An aside on relation to other derivatives in the wild

Given our ability to view $V$ as both a Banach and Topological Vector space there are notions of derivatives that often crop up in both. In Topological Spaces we have the notion of Gateaux Differentiability and in Banach Spaces we the notion of Frechet Differentiability.


## Ordinary Differential Equation(ODE)
\\[
\partial\mathbf{x}(t) = f(t, \mathbf{x}(t))
\\]

Differential equations are so ubiquitous that many terms appears in the literature that are synonyms of each others. We will cite some common conventions as we go along, however will put them as footnotes so as not to confuse the reader with different terms upon first reading. 

### Visualizing a non-autonomous ODE

Note that $f$ is dependent on time and a given input vector. For visualization purposes we will assume vector space is of dimension 2, although the same concept generalizes to higher dimensions. At a particular time $\tau$ we have a function from our vector space to our vector space. So we can visualize this by simply drawing on each vector, $v$, its image under $f(\tau, \cdot)$. This gives us a time-dependent vector field. 

## Autonomous Ordinary Differential Equation
\\[
\partial\mathbf{x}(t) = f(\mathbf{x}(t))
\\]

### Visualizing an autonomous ODE

### Autonomous = Non-Autonomous

## Initial-Value Problem
\\[
\begin{align*}
\partial\mathbf{x}(t) &= f(\mathbf{x}(t)) \\
\mathbf{x}(t_{0}) &= \mathbf{x}_{0}
\end{align*}
\\]


### Euler Polygonals
The idea behind Euler polygonals is intrinsically geometric and for many an intuitive first approach. The idea is if to start at some initial time $t_{0}$, look at the derivative at $t_{0}$ which is the slope of the tangent line to a solution, follow this tangent line for a small increment, $h$, and rinse and repeat. As we let the increment get smaller and smaller we would hope to get convergence to the true solution. 



#### Existence Theorem(Cauchy-Peano Theorem)
It turns out we do need some conditions to show existence of solutions. In this case we assume $f$ is continuous, which means we are looking for solutions that are continuously differentiable. It turns out this $f$ is enough to prove existence, but is not sufficient for uniqueness (exercise : try to come up with an example of a non-unique solution with continuous $f$). The fact that our initial-value problem has a solution when $f$ is continuous is referred to as the Cauchy-Peano Theorem.

The outline of the proof is as follows. First take a closed norm ball around $x_{0}$, and since $f$ is continuous it has $\|f(\cdot)\|$ has a maximum on this ball. This is the fastest the solution can grow, so we assume this max rate of growth and create a closed, and bounded area in the extended state space where the image of trajectory must be contained in. The idea thus far being if we have a solution it must be contained in this closed and bounded region. 


#### Uniqueness
##### Bellman-Gronwall Lemma Approach
##### Euler Polygonal Approach

### Contraction Mapping Approach (Picard-Lindelöf Theorem)

This is a theorem from mathematics stating that any differential equation of the form above has a solution that exists is locally unique, if $f$ is locally Lipschitz.

We can integrate both sides of our differential equation with respect to time, and find that 

\\[
\mathbf{x}(T) = \mathbf{x}(t_{0})+  \int_{t_{0}}^{T}f\left(\mathbf{x}(t)\right)dt
\\]

This result follows from the fundamental theorem of calculus. Then we realize if we define the operator $\mathbf{A}\mathbf{x} :=  \mathbf{x}(t_{0})+  \int_{t_{0}}^{T}f\left(\mathbf{x}(t)\right)dt$, then we are looking for a fixed point of this operator. A standard tool for existence of fixed points is the Banach Fixed Point Theorem, which states if $\mathbf{A}$ is a contraction mapping it has a unique fixed point.

We verify this to be the case

\\[
\begin{align}
\mathbf{Ax - Ay} &= \mathbf{x}(t_{0}) - \mathbf{y}(t_{0}) + \int_{t_{0}}^{T}f(\mathbf{x}(t)) - f(\mathbf{y}(t))dt \\
&\leq \int_{t_{0}}^{T} L\|\mathbf{x}(t)-\mathbf{y}(t)\| dt \\
&\leq LT\sup\{\|\mathbf{x}(t) - \mathbf{y}(t)\| : t \in [t_{0}, T]\} \\
&\leq LT\|\mathbf{x}-\mathbf{y}\|
\end{align}
\\]

We are free to choose the time horizon $T$, so we can choose is small enough that $LT < 1$ and thus enforce that $A$ is a contraction mapping.

### Go With The Flow -- How Results Influence Notation

## Special Cases of Interest

### Cauchy–Kovalevskaya Theorem

### Linear Constant Coefficient

#### Homogeneous 
#### Inhomogeneous

### Linear Time-Varying Coefficient 

#### Homogeneous
#### Inhomogeneous

