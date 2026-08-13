---
title: Convex Optimization As Quickly As Possible
date: 2026-07-31T22:12:57-04:00
author: Aman Shah
draft: true
math: true
---


## Introduction

Convex optimization is a beautiful field in its expressiveness, elegance, and power.

## Problem

The end goal for many people is to solve an optimization problem of the form 
\\[
\min_{x \in C} f(x)
\\]

This page presupposes some level of awareness that problems of this form are of interest. If you need to be sold on the idea read other notes


## Convexity

Convexity is an adjective applied to subsets of a vector space that means the line segment joining any two points of the set, is contained in the set. So if you draw a straight line between any two points you will not escape the set.

Convexity can be applied to functions by defining a function to be convex if its epigraph is convex. Just as many inequalities require positive numbers, many theorems in convex analysis require the convex set to be nonempty so the adjective proper is applied to a convex function to mean the epigraph is nonempty, and does not contain a vertical line.

The key theory of convex optimizations is then built on supporting hyperplanes, and the above two theorems. The key theorem needed is that any boundary point of closed convex set, admits a supporting hyperplane.  


