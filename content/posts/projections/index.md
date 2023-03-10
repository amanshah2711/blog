---
title: "Projections"
date: 2023-03-09
author: Aman Shah
draft: false
math: true
---
## Physical Example
Consider a sunny day and a lamp post standing erect on perfectly flat ground. Since the sun is sufficiently far away we assume the rays of light are parallel. The lamp post has a shadow as long as these rays of light are not parallel or perpendicular to the lamp post. The height of the shadow is determined by looking at the ray that intersects the top of the lamp post and advecting the top of the post to the ground along this ray. The advection of this point to the ground is an example of a non-orthogonal[^1] projection. Linear algebra is a suitable medium for modeling this phenomena as we shall soon see.
## Projection to Lines
### Elementary Projections
In general, we define an elementary projection using two objects: a given real-valued linear function $\mathbf{r}^T$, and a given vector $\mathbf{c}$. The projection of a point $\mathbf{z}$ is then defined in the following manner. Consider the point $\mathbf{z}$ and the hyperplane defined by $\mathbf{r}^T$ that it lies on. Then look at the point formed by the intersection of the foregoing hyperplane with $\text{span}\{\mathbf{c}\}$. This point of intersection is defined as the elementary projection of $\mathbf{z}$ onto $\text{span}\{\mathbf{c}\}$ given $\mathbf{r}^T$. This process can be viewed as advecting $\mathbf{z}$ along the line segment connecting it to $\text{span}\{\mathbf{c}\}$ which lies wholly in a level set of $\mathbf{r}^T$.

In our physical analogy level sets of $\mathbf{r}^T$ correspond to rays of light and the floor corresponds to $\text{span} \{\mathbf{c}\}$.

We deduce a mathematical formula by exploiting two critical facts: the projection is equal to $\lambda \mathbf{c}$ for appropriate scalar $\lambda$, and the projection and $\mathbf{z}$ lie in the same level set of $\mathbf{r}^T$. Thus $\lambda = \frac{\mathbf{r}^{T}\mathbf{z}}{\mathbf{r}^T\mathbf{c}}$. Therefore our resulting projection is,

$$\frac{\mathbf{c}\mathbf{r}^{T}}{\mathbf{r}^T\mathbf{c}} \mathbf{z}.$$

#### Example 1: Matrix Inverse
#### Example 2: Stereographic Projection
### Elementary Orthogonal Projections
It is common to restrict discussion of elementary projections to those that are orthogonal. That is the level sets of $\mathbf{r}^T$ are perpendicular to $\mathbf{c}$. If our coordinate system consists of basis of orthonormal vectors then the transpose of $\mathbf{c}$ is the appropriate choice of $\mathbf{r}^T$.  This process corresponds to projection of a point onto a coordinate systems consisting of straight, perpendicular axes such as the Cartesian plane.
## Projections to Vector Spaces
### Big Theorem: Decomposition

[^1]: Non-orthogonal refers to the fact that the ray connecting the tips of the shadow and post does not form a right angle with the ground.
