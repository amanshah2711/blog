---
title: A Tour of Dynamical and Control Systems
date: 2025-04-24T19:35:48-04:00
author: Aman Shah
draft: true
math: true
---

## Introduction

This post is meant to serve as a table of contents and brief overview of the ideas that are exposited in the series, “A Tour of Dynamical and Control Systems”. At a high level we want to think of real systems that evolve over time such as a pendulum swinging, a boat thrown into a water with particular current patterns, a stock price every morning, or a rocket landing sequence. 

The evolution of a system with time is called a dynamical system. Dynamical systems are ubiquitous and tremendously varied. For example, in the pendulum swinging we have a state at any possible time which we call a continuous state space. In contrast, the price of a stock every morning is a discrete state space, because we can only query fixed discrete time jumps. Both equations evolve over time and cannot often be described explicitly (otherwise the future stock price or future position of any entity would be known). So as occurs elsewhere in mathematics, we look at how these systems change in time. For continuous-time systems this means understanding changes at any possible instance of time which leads to modeling with differential equations. For discrete-time systems this means describing by means of an algebraic equation how the current state and current time influence the next state. These laws are simply referred to as the transition dynamics of the system.

A dynamical system provides a model of phenomena such as process in nature or man-made economic processes. However, such phenomena are not always simply observed. Engineers have the explicit goal to manipulate systems to desired outcomes. For example, ethical hunters may want to model the population of wolves and rabbits while also including their ability to affect the population. A finance firm may want to model the price of an asset while including their ability to affect the asset price. An engineer may want to use the thrusters on a rocket to get to the moon and be interested in how certain inputs to the thruster will affect the trajectory. These are examples of control systems. Control systems are simply dynamical systems where we also have a space of controls that we incorporate into our transition dynamics.

There are many widespread uses of these systems and tools. In this tour we will overview and contrast a series of mathematical models that slowly incorporate more general tools. For example we start with a linear dynamical system that is the same at every point in time, then a linear dynamical system that varies at every point in time, and linear models that then incorporate probabilistic behavior. To get an overview from simple to more complex go in the following order. Discrete and Continuous are separated, predominantly by interest.
- Mathematical Prerequisites
- Existence/Uniqueness of Flows
- [Discrete Deterministic Linear Time-Invariant Dynamical System](/posts/dynamical-systems-and-control-systems-tour/ddlti/)
- [Continuous Deterministic Linear Time-Invariant Dynamical System]
- [Discrete Deterministic Linear Time-Varying Dynamical System]
- [Continuous Deterministic Linear Time-Varying Dynamical System]
- [Discrete Deterministic Linear Time-Invariant Control System](/posts/dynamical-systems-and-control-systems-tour/dclti/)
- Continuous Deterministic Linear Time-Invariant Control System
- Discrete Deterministic Linear Time-Varying Control System
- Continuous Deterministic Linear Time-Varying Control System
