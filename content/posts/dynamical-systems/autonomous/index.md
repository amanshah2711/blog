---
title: Properties of Autonomous Dynamical Systems 
date: 2025-04-24T19:35:48-04:00
author: Aman Shah
draft: false
math: true
---
{{TOC}}
# Introduction

This note is intended to exposit key ideas of autonomous dynamical systems. Many definitions and terms used for dynamical systems have equivalent definitions for special cases such linear-time invariant, or linear time-varying   systems. The purpose here is to provide a general background, so that the specific notions can be shown to follow from the general definitions and principles. The hope is that this overview will lead to a deeper understanding of what some notions such as stability mean, as well as make it easy for the reader to purvey different sources more easily. The equivalence of definitions and slight terminology differences can make cross referencing or understanding sources quite difficult at just a glance.

# Dynamical Systems

## Discrete Deterministic Autonomous Dynamical System
\\[
\mathbf{x}_{t} = f(\mathbf{x}_{t-1})
\\]

- **Discrete** := the states and their transitions are described with respect to non-negative integer indices(i.e the states are $\mathbf{x}_0, \mathbf{x}_1, \mathbf{x}_2, \ldots$)  \
- **Deterministic** := the transition dynamics and consequently the states have no dependence on random behavior. In some cases it is useful to consider random noise as affecting the transition from one state to the next.
- **Autonomous** := this means the function $f$ has no dependence on $t$. This means the next state depends only on the current state, and not the current time.
- **Dynamical System** := we are describing the system by how the states evolve over time


## Continuous Deterministic Autonomous Dynamical System
\\[
\frac{d\mathbf{x}}{dt}(t)= f(\mathbf{x}(t))
\\]

- **Continuous** := the states and their transitions are described with respect to a connected subset of real numbers(ex. $t\geq 0$, $t \in \mathbb{R}$, $t \in [a, b]$ )
- **Deterministic** := the transition dynamics and consequently the states have no dependence on random behavior. In some cases it is useful to consider random noise as affecting the transition from one state to the next.
- **Autonomous** := this means the function $f$ has no dependence on $t$. This means the next state depends only on the current state, and not the current time.
- **Dynamical System** := we are describing the system by how the states evolve over time


## Terminology And Its Justification
In either case $f$ will be referred to as the transition dynamics, and a solution for a given initial time, $t_0$, and initial state, $\mathbf{x}_{0}$, will be referred to as a trajectory. 

Many subsequent ideas are based on the relationship between the pair of initial state and initial time and corresponding trajectory. The mapping between the pair of initial state and initial time to the trajectory is sometimes referred to as flow. 

We will denote this mapping by $\Phi$ where $\Phi(\mathbf{x}_{0}, t_{0}, t)$ denotes the state at time $t$ when starting at state $\mathbf{x}_{0}$ at initial time, $t_{0}$. It should be understood that $t$ must be greater than or equal to $t_{0}$. It may be possible to extend to all time in some cases, but in the general case we do not have any such guarantees.


## Equilibrium State And Its Adjectives[^1]
An equilibrium state is a state from which the system does not deviate; that is if we start at $\mathbf{e}$ and calculate the trajectory  using the transition dynamics we stay at $\mathbf{e}$. 

*Note : Since the system is autonomous, the initial starting time does NOT affect the trajectory. That is starting at state $\mathbf{e}$ at two different initial times will result in the same sequence of states related by a shift in time.*

For a variety of reasons people are interested in the “sensitivity” of these equilibrium states. The key idea is that starting at an equilibrium state, $\mathbf{e}$, we stay at $\mathbf{e}$, but  for nearby states do we move away from $\mathbf{e}$, stay near $\mathbf{e}$, move towards $\mathbf{e}$, and if towards $\mathbf{e}$ how quickly? The next few definitions provide a language to discuss and characterize properties of this ilk.

### Isolated 
Here isolated is an adjective describing equilibrium state. An isolated equilibrium state, $\mathbf{e}$, is an equilibrium state for which there exists a topological neighborhood containing $\mathbf{e}$, that contains no other equilibrium state. 

In our setting of Banach spaces this means there is a ball containing $\mathbf{e}$ that contains no other equilibrium state, or explicitly there is a positive $\delta$ such that for any point, $\mathbf{x}$ distinct from $\mathbf{e}$ satisfying, $\|\mathbf{x}-\mathbf{e}\| < \delta$, we have that $\mathbf{x}$ is not an equilibrium state.

### Lyapunov Stable
An equilibrium state, $\mathbf{e}$, is called Lyapunov stable, or stable in the sense of Lyapunov, or just stable if we can guarantee future states stay arbitrarily close to $\mathbf{e}$ if our initial state is sufficiently close enough to $\mathbf{e}$. 

Precisely, we mean $\mathbf{e}$ is Lyapunov stable if for all positive $\epsilon$, there exists a positive $\delta$ such that for all $\mathbf{x}_0$ with $\|\mathbf{x}_0 - \mathbf{e}\| < \delta$ we have $\|\Phi(\mathbf{x}_{0}, t_{0}, t) - \mathbf{e}\| < \epsilon$.\


For those with mathematical background, this is simply saying the flow is continuous with respect to the initial states, where continuity is defined using usual epsilon-delta notions. Here the state space is the domain, and the target space is the space of functions where the trajectories lie equipped with the supremum norm. 

Note: Lyapunov stable, and its cousins below, are adjectives describing an equilibrium state. 
 
### Attractive
Attractive is an adjective for an equilibrium state. Without any qualifier attractive means the same as locally attractive(described below). The following qualifiers are adjectives describing an equilibrium state, where locally, globally, and uniformly act as adverbs modifying the adjective of attractive. For this note and in general a good practice should be if no adverb modifying the adjective is given, assume the weakest form. So in this case locally attractive is the weakest so attractive on its own should refer to this concept.

#### Locally Attractive
We say the equilibrium state $\mathbf{e}$ is locally attractive iff there exists a positive $\delta$ such that for all initial states $\mathbf{x}_{0}$ within $\delta$ of $\mathbf{e}$, we have the trajectory converging to $\mathbf{e}$.

Mathematically we mean there exists positive $\delta$ such that if $\|\mathbf{x}_{0} - \mathbf{e}\| < \delta$ then $\lim_{t \to \infty} \Phi(\mathbf{x}_{0}, t_{0}, t) \to \mathbf{e}$.

#### Globally Attractive
We say thatthe equilibrium state $\mathbf{e}$ is globally attractive iff any trajectory converges to $\mathbf{e}$. 

Mathematically, we mean there for any $\mathbf{x}_{0}$ we have $\lim_{t \to \infty} \Phi(\mathbf{x}_{0}, t_{0}, t) \to \mathbf{e}$.


 
### Asymptotically Stable

#### Adjectives(Local, Global, and Uniform)

In the same way we were able to add adverbs to attractive, we can extend them to apply to asymptotically stable, by simply requiring ‘adverb’ asymptotically stable to mean stable and ‘adverb’ attractive.

So $\mathbf{e}$ is locally asymptotically stable iff it is stable and locally attractive.

$\mathbf{e}$ is globally asymptotically stable iff it is stable and globally attractive.

$\mathbf{e}$ is uniformly locally(or globally) asymptotically stable iff it is stable and uniformly locally(or globally) attractive. It turns out in our setting, of finite dimensional, spaces any locally(or globally) asymptotically stable equilibrium state, is also uniformly locally(or globally) asymptotically stable. We will provide a short proof later, however we bring up the definition even though it is satisfied because this is a notion that will be built upon later. 



#### Marginally Stable
An equilibrium point $\mathbf{e}$, is marginally stable if it is Lyapunov stable, and it is not locally asymptotically stable. That is we can guarantee future states are arbitrarily close to $\mathbf{e}$, if we take any ball around $\mathbf{e}$, no matter how small, there exists an initial state such that our future states do not converge to $\mathbf{e}$.

Note: This can be a confusing term, because some people treat it as a synonym of Lyapunov stable, so the definition stated here is not ubiquitous.

### Exponentially Stable
An equilibrium state, $\mathbf{e}$ is called exponentially stable, if we take any initial state that is sufficiently close to $\mathbf{e}$ our future states will converge to $\mathbf{e}$ faster than an exponential.

Precisely, we mean $\mathbf{e}$ is exponentially stable, if there exists positive $\delta$ such that if $\|\mathbf{x}_0 - \mathbf{e}\| < \delta$ then $\Phi(\mathbf{x}_{0}, t_{0}, \cdot)$ converges to $\mathbf{e}$ faster than an exponential meaning we have $\|\Phi(\mathbf{x}_{0}, t_{0}, t)-\mathbf{e}\| < \alpha \|\mathbf{x}_0-\mathbf{e}\|\exp(-\beta(t-t_0))$. 

Remark: Note in the definition of asymptotically stable we require stable in the sense of Lyapunov + attractive. For exponentially stable we do NOT in the definition require stable in the sense of Lyapunov. This is because the definition as is, implies stable in the sense of Lyapunov. See exponential implies asymptotic.
#### Adjectives(Local, Global, and Uniform)
#### Exponential implies Asymptotic




[^1]: Equilibrium points are a concept widely used, and have many synonyms : stationary point, steady state, fixed-point critical point