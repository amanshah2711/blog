---
title: Properties of Non-Autonomous Dynamical Systems 
date: 2025-04-24T19:35:48-04:00
author: Aman Shah
draft: false
math: true
---
{{TOC}}
## Introduction

This note is intended to exposit the ideas pertinent to general non-autonomous dynamical systems. The behavior here is slightly more complicated than for autonomous systems although the extensions are quite natural. We will aim to exposit this in a self-contained manner so that one may read about autonomous or non-autonomous systems first, and grasp the situation. 

## Dynamical Systems

### Discrete-Time

\\[
x_t = f(t, x_{t-1})
\\]

### Continuous-Time
\\[
\frac{d}{dt}x(t) = f(t, x(t))
\\]

### Terminology



### Equilibrium States and their ilk[^1]
An equilibrium state is a state from which the system does not deviate; that is if we start at $e$ and calculate the trajectory  using the transition dynamics we stay at $e$. However, in the non-autonomous case, starting at $e$ at various times can produce different trajectories. To handle this notion our notion of stability needs to incorporate the dependence on the starting time. 

#### Equilibrium State at a particular time, $t_0$
An equilibrium state, $e$ at time $t_0$ is a state such that if we start the system at time $t_0$ at state $e$, then all future states remain at $e$.

#### Equilibrium States
An equilibrium state $e$, is defined as a state such that starting at $e$ at any time results in staying at $e$. In other words $e$ is an equilibrium state if it is an equilibrium state at time $t_0$ for any choice of $t_0$.

For a variety of reasons people are interested in the “sensitivity” of these equilibrium states. The key idea is that starting at an equilibrium state $e$ we stay at $e$, but  for other nearby points do we move away from $e$, stay near $e$, move towards $e$, and if towards $e$ how quickly? The next few definitions provide a language to discuss and characterize properties of this ilk.

Terminology note: Sometimes this is referred to as uniform equilibrium state


### Lyapunov Stability and its ilk
#### Stability at a particular time, $t_0$
An equilibrium state is called Lyapunov stable at time $t_0$, or stable in the sense of Lyapunov at time $t_0$, or just stable at time $t_0$ if we can guarantee future states stay arbitrarily close to $e$ if our initial state is sufficiently close enough to $e$ at time $t_0$.

Precisely, we mean $e$ is Lyapunov stable at time $t_0$ if for all positive $\epsilon$, there exists a positive $\delta$ such that for all $x_0$ with $|e - x_0| < \delta$ we have $|e-x_t| < \epsilon$ for all $t$ after $t_0$.\
\

#### Stability
An equilibrium is called stable, if it is stable at time $t_0$ for any choice of $t_0$.

#### Uniform Stability
In addition, we have an additional notion of uniform stability.
Uniform is an adjective describing stability.
Here uniform means the choice of $\delta$ above has no dependence on $t_0$.


Note: Lyapunov stability, and its cousins below, are adjectives describing an equilibrium state. 

 
### Asymptotic Stability and its ilk


#### Asymptotic Stability at a particular time, $t_0$
An equilibrium state is called asymptotically stable at time $t_0$, if it is Lyapunov stable and if we take any initial state that is sufficiently close to $e$ at time $t_0$ our future states will converge to $e$.

Precisely, we mean $e$ is asymptotically stable at time $t_0$, if it is Lyapunov stable and if there exists positive $\delta$ such that if $|x_0 - e| < \delta$ and the system is started at $t_0$ then $x_t$ converges to $e$, meaning for for any $\epsilon$ and $t$ sufficiently large we have $|x_t-e| < \epsilon$. \
\
\

#### Asymptotic Stability
An asymptotically stable equilibrium state is a state that is asymptotically stable at all time $t_0$

#### Uniform Asymptotic Stability
Uniform refers to the fact that the choice of $\delta$ above does not depend on time $t_0$

#### Global Asymptotic Stability
Global refers to the fact that for an asymptotically stable equilibrium state any initial condition will converge to the equilibrium state


### Exponential Stability, and its ilk


#### Exponential Stability at a particular time, $t_0$
An equilibrium state is called exponentially stable at time $t_0$, if it is Lyapunov stable and if we take any initial state that is sufficiently close to $e$ at time $t_0$ and our future states will converge to $e$ faster than an exponential.

Precisely, we mean $e$ is exponentially stable, if it is Lyapunov stable and if there exists positive $\delta$ such that if $|x_0 - e| < \delta$ at time $t_0$, then $x_t$ converges to $e$ faster than an exponential meaning we have $|x_t-e| < \alpha |x_0-e|\exp(-\beta t)$. \
\
\

#### Exponential stability
Exponential stability without the suffix “at a particular time $t_0$, extends the idea, but in a way slightly different than asymptotic or Lyapunov Stability. A natural extension would be exponential stability means that the equilibrium state is exponentially stable at time $t_0$ for any choice of $t_0$. However this is *not* the definition.

Here when we say converges faster than an exponential we mean faster than $M\exp(\lambda t)$. In other words both $M$ and $\lambda$ are what define an exponential. Exponential stability with no suffix means that the same exponential can be used for all time $t_0$, that is the choice of $M$ and $\lambda$ are the same for all time $t_0$

#### Uniform Exponential Stability
Uniform exponential stability is analogous to its predecessors where the choice of $\delta$ does not depend on the starting time.

#### Global Exponential Stability
Sometimes the qualifier, global, is added when any initial state will converge to $e$(no need to start close to $e$). An equilibrium state with this property is dubbed globally exponentially stable.


[^1]: Equilibrium points are a concept widely used, and have many synonyms : stationary point, steady state, fixed-point critical point
