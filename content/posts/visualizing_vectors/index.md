---
title: "How To Draw Pictures in Linear Algebra"
date: 2023-11-08T21:28:03-05:00
author: Aman Shah
draft: true
math: true
---

## Introduction

Any student of mathematics, physics, computer science, or any quantitative discipline inevitably comes across the word **vector**. As a byproduct of cross-discipline use, “vector” often has slightly varying definitions that obfuscate the details. Even those who understand the rigorous details may find geometric intuition hazy. In the proceeding post we exposit .

## The Definition

> ”The art of doing mathematics is finding that special case that contains all the germs of generality." 
>> -- David Hilbert

In the spirit of Hilbert’s remark, if you have minimal exposure to Linear Algebra then it suffices to denote a vector as a tuple of $n$ real numbers, $\mathbf{R}^n$. In addition Linear Algebra requires two specific operations : addition and scalar multiplication. Addition of two vectors means adding each of them component wise, and scalar multiplication means multiplying each component of the tuple by the same number (numbers are often called scalars in mathematical texts).

For the more advanced we can define a vector space as a set $V$ and field $F$ equipped with binary operations addition, $+ : V \times V \to V$, and scalar multiplication, $\cdot : F \times V \to V$ that satisfy the following,


This definition then defines a vector as an element of $V$.

Now we have a definition of what a vector is, and it is purely algebraic. In the subsequent sections we discuss how one takes this algebraic notion and connects it to geometry.


## Defining Lines

## The Algebra of Coordinates

Let’s say we are given the following image.

Before even attempting to solve any geometric problem involving multiple points we need to be able to refer to a point using algebra. To begin let us denote the point $\mathbf{v}$. Now how do we refer to $\mathbf{v}$ using numbers? We simply draw a grid and then identify the point relative to grid in the same way one could identify a point on the floor of a given room.

However this is not the only way to associate numbers to the point $\mathbf{v}$. *Do you see why?* Consider the following diagrams.

Nature has no regard for our aesthetics tastes and consequently all such coordinate systems are allowed. 

## Competing Definitions
To begin let’s examine several different definitions of the word vector.

> **Definition 1:** A **vector** is something that has both *magnitude* and *direction*.\
> Source : [Khan Academy: Vector Intro For Linear Algebra](https://www.youtube.com/watch?v=br7tS1t2SFE&t=5s)

> **Definition 2:** A **vector** is the class of all directed segments obtained from each other by translation in space\
> Source : Linear Algebra by Alexander Givental

> **Definition 3:** Until then, **vector** will mean an ordered list of numbers.[^1] \
> Source : Linear Algebra and Its Applications Fifth Edition by David C. Lay, Steven R. Lay, Judi J. McDonald

> **Definition 4:** Elements of a *vector space*[^2] are called **vectors**.\
> Source : Linear Algebra Done Right Third Edition by Sheldon Axler

These definitions all are equivalent under the right set of circumstances, however to some degree implicit assumptions are made or geometric intuition is obscured. Observe the following: definition 1 requires having some idea what magnitude and direction means, definition 2 requires nontrivial knowledge of directed segments from Euclidean Geometry, and definitions 3 and 4 contain no immediately obvious geometric connection. Rather than say more let us first develop a definition and give a solid geometric interpretation.

We shall simply take Axler’s definition to be the definition of a vector. That is a vector is simply an element of a vector space, which is a set of points that satisfy some notion of addition and scalar multiplication. This definition does not include any notions of directions or lengths so we are left wondering how can we visualize a vector? Let’s take a moment to digress about how connecting numbers to geometry.

## Examples Galore!
### Finite Dimensional
### Infinite Dimensional

## An Aside On Analytic vs. Synthetic Geometry

> “Synthetic geometry is that which studies figures as such, without recourse to formulae, whereas analytic geometry consistently makes use of such formulae as can be written down after the adoption of an appropriate system of coordinates.”
>> --Felix Klein, Elementary Mathematics From An Advanced Viewpoint
>> 
## Geometric Reasoning Justified By Analytic Methods

Consider the case where an oracle tells us we are working with the vector space $\mathbf{R}^2$ and labels a dot on the page as a distinguished point henceforth called the origin (this is really the additive identity). Now the oracle asks you to draw the vector, $v := \begin{bmatrix} 1 \\ 1 \end{bmatrix}$. How would you do it? 

This wisdom of relating argument to diagrams is best summarized by the following aphorism.

> "Geometry is the art of correct reasoning from incorrectly drawn figures."
>> --Henri Poincaré


[^1]: Later this source moves to using the definition given by Axler.
[^2]: A vector space is a set of elements that have a particular notion of addition and scalar multiplication. See Axler’s book or [Wikipedia](https://en.wikipedia.org/wiki/Vector_space#:~:text=In%20mathematics%20and%20physics%2C%20a,%22).
