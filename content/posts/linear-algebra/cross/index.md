---
title: "Cross Products"
date: 2024-03-01T05:19:40-05:00
author: Aman Shah
draft: true
math: true
---

## Introduction
The cross product is an operation between two vectors that exists in three-dimensional Euclidean space, $\mathbf{E}^3$. The cross product is intimately related to rotations and its algebraic properties, while seemingly bizarre at first glance become natural when motivated sufficiently. Here we will exposit some motivation and often skirted nuances of the cross product that are often left to students to figure out themselves.\
\
The cross product requires a solid understanding of Euclidean spaces and linear algebra so consider skimming the following notes as needed.
- [Euclidean spaces](/posts/euclidean_geometry/)
- [Hyperplanes](/posts/hyperplanes)
- [Areas and Oriented Areas](/posts/oriented_area_vs_area/)

## Definition
Suppose we are given two vectors $\mathbf{a}, \mathbf{b} \in \mathbf{E}^3$. Now we will use $a, b \in \mathbb{R}^3$ to denote the coordinate vectors of $\mathbf{a}$ and  $\mathbf{b}$ with respect to a given orthonormal basis, $\mathbf{B}$.
\\[
a^{\cancel{c}} b = \begin{bmatrix} 
															a_2b_3 - a_3b_2 \\
															a_3b_1 - a_1b_3 \\
															a_1b_2 - a_2b_1
															\end{bmatrix}.
\\]
Now this formula is seemingly bizarre, and at first glance it is not clear why this has anything to do with Euclidean spaces in particular. *Why did we specify the basis was orthonormal (keep reading for the answer)?* \
\
Also an important thing to pay attention to in this note is “types”. In this case we see the cross product is an operation that takes in two coordinate vectors with respect to an orthonormal basis, and outputs a coordinate vector with respect to the same orthonormal basis. 


### Motivation Using Gaussian Elimination
Given two coordinate vectors as above we can ask how does one construct the plane containing these vectors. We know that a plane, $r^H$, contains the vectors if $r^Ha = r^Hb = 0$. Writing this out explicitly we find that,
\\[
\begin{align}

\begin{bmatrix} 
															r_1 & r_2 & r_3 \\														
\end{bmatrix}
\begin{bmatrix} 
															a_1 \\
															a_2 \\
															a_3 
\end{bmatrix}
&=
0
\\
\begin{bmatrix} 
															r_1 & r_2 & r_3 \\														
\end{bmatrix}
\begin{bmatrix} 
															b_1 \\
															b_2 \\
															b_3 
\end{bmatrix}
&=
0
\end{align}
\\]
Now when solving for the component of $r^H$ we find that we get infinitely many solutions. We have three variables and two linearly independent equations so our solution is a line in the dual space. Explicitly this line is,
\\[
 \mathbf{span}\begin{bmatrix} 
															(a_2b_3 - a_3b_2) & (a_3b_1 - a_1b_3) & (a_1b_2 - a_2b_1)
															\end{bmatrix}.
\\]
*Verify this yourself.*
 
Now it seems any family of hyperplanes chosen from this line suffices as they all contain $\mathbf{a}$ and $\mathbf{b}$ in their zero level set, although nothing yet said is intrinsic to Euclidean spaces. Why did we need $\mathbf{a}$ and $\mathbf{b}$ to be orthonormal to one another? 

What characterizes a Euclidean space from others is the choice of distinguished maps between the dual space and the vector space. In an orthonormal basis, a family of hyperplanes can be canonically associated with a vector by taking the transpose, in a way that is preserved across all orthonormal bases. In this scenario we mean we can instead consider the vector, 
\\[
a^{\cancel{c}} b = \begin{bmatrix} 
															a_2b_3 - a_3b_2 \\
															a_3b_1 - a_1b_3 \\
															a_1b_2 - a_2b_1
															\end{bmatrix}
\\],
and as we move from one orthonormal basis to another, the vector  and the linear functional both maintain the same coordinates. The crux idea used here is if something is to be considered a vector it should look and change as a vector changes. So all that happened is we found the hyperplane containing $\mathbf{a}$ and $\mathbf{b}$, then simply using the defining property of Euclidean spaces, we canonically associate with every family of hyperplanes a unique vector, namely the vector orthogonal to the hyperplane. So now it should be clear that $a^{\cancel{c}}b$ represents a hyperplane that contains $\mathbf{a}$ and $\mathbf{b}$ while also corresponding to a vector that is orthogonal to this hyperplane.

Note that we could have chosen the same vector multiplied by any non-zero scalar however, there is no a priori reason to choose a specific one and it will turn out the default choice has some nice properties that make it more desirable. Also, the assumption that $\mathbf{a}$ and $\mathbf{b}$ are linearly independent is also not needed. If they are linear dependent, the above formula simply gives $0$.

### Motivation using Riesz Representation
We know that Euclidean geometry has an intimate connection with areas and volumes from classic formulas like $\mathbf{volume} = \mathbf{base} * \mathbf{height}$. This formula for volume critically depends on Euclidean concepts because height is measured as distance orthogonal to the base. Now in vector spaces, we have a general formula for volume given by the determinant. Given three vectors $\mathbf{a}, \mathbf{b}, \mathbf{c}$ we know the oriented volume of the parallelepiped, is given by \\[
\mathbf{det} \begin{bmatrix} a & b & c \end{bmatrix}
\\]
 
If we are given $\mathbf{a}$ and $\mathbf{b}$ which define a plane, or a base of a parallelepiped, what is the oriented volume for a given vector, $\mathbf{c}$. We have a function of $\mathbf{c}$ that is,
\\[
	\mathbf{r}^H \mathbf{c} = \mathbf{det} \begin{bmatrix} a & b & c \end{bmatrix}
\\]
 This is a linear functional, and therefore defines a family of hyperplanes. This is intuitively clear when thinking of volume as the product of base and height because any height vector from the plane parallel to the base will create a parallelepiped of the same volume. 
 
 Now from this we can compute the function $\mathbf{r}^H$ explicitly and achieve the same answer as before. *As an exercise write out the formula and find $r^H$ such that $r^Hc = \mathbf{det} \begin{bmatrix} a & b & c \end{bmatrix}$*. 
 
Once again this is a linear functional and no property of Euclidean space has yet been used. We know Euclidean spaces allow us to canonically identify a linear functional with a vector by taking the transpose if we have a representation of the linear functional with respect to an orthonormal basis. This vector associated to the linear functional is simply the vector perpendicular to the family of hyperplanes defined by the linear functional. Thus simply taking the transpose of the $r^H$ earlier gives us the desired vector $a^{\cancel{c}}b$. This relationship between linear functional and vector is called the Riesz representation of the linear functional. This idea is present in all motivations, however it is most prominent here where we are starting with a known linear functional -- the determinant -- and are directly taking its Riesz representation to be the cross product.
 
### Motivation Using Skew-Symmetry (Rotation around the $v$ axis via Rodrigues’ Formula)
Suppose we are given a vector $\mathbf{v} \in \mathbf{E}$ and want to consider how to develop rotations by 90 degrees around the $\mathbf{v}$-axis. We can realize that if we rotate around the $\mathbf{v}$ axis the only component that moves is the component of the vector orthogonal to $\mathbf{v}$. So to extract this component we can use elementary orthogonal projectors. Now this problem fundamentally hinges on characterizing rotations.

#### Aside: 2D Rotations
If we are in 2D Euclidean space, $\mathbf{E}^2$, and have an orthonormal basis it is easy to define $\mathbf{J}:= \text{90 degree counter clockwise rotation}$. With respect to the basis we have $J = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$. This representation of $J$ should be clear from analyzing where the unit vector in the horizontal and the unit vector in the vertical direction get mapped to by a rotation. Alternatively, we could consider that rotations should have the effect that the output of a 90 degree rotation, $Jx$ should be perpendicular to $x$. From this we have that $x^H J x = 0$ which is equivalent to $J^H = -J$. A matrix with this property is called skew-symmetric and a general linear operator is called skew-adjoint. If we add the constraint $|Jx| = |x|$ then $J$ is uniquely determined except for sign, and the two signs correspond to $\pm J$ which are rotations clockwise or counterclockwise by 90 degrees. Thus it is clear what rotations by 90 degrees, $\mathbf{J}$, are in 2D.

 In 3D this problem gets a little more complicated. To characterize rotations by 90 degrees around an axis we can appeal to the characterization we used in 2D. If our rotation, $\mathbf{R}$ rotates by 90 degrees it needs to satisfy,\
\\[
	\mathbf{x}^H \mathbf{R} \mathbf{x} = 0  \qquad \forall \mathbf{x} \in \mathbf{E}^3 \\
	\mathbf{R}^2 = -(\text{projection onto plane perpendicular to } \mathbf{v}) = -\left(\mathbf{I} - \frac{ \mathbf{v} \mathbf{v}^H}{\mathbf{v}^H \mathbf{v}}\right) \\
	
\\]
The first property is just the algebraic statement that the output $\mathbf{R}\mathbf{x}$ is perpendicular to $\mathbf{x}$, and the second is saying that rotating by 90 degrees twice is the same as rotating by 180 degrees which is the same as multiplying by a minus sign. These two properties are enough to characterize the entire operator up to a plus or minus sign. Condition 1 has an equivalent form as before,

\\[
	R = -R^H \\
	R^2 = -(\text{projection onto plane perpendicular to v}) = -\left(I - \frac{vv^H}{v^Hv}\right) \\
\\]

Given these equations we will use one corollary of these two equations to deduce $R$ explicitly very easily. The corollary we will use is that $\text{span } \mathbf{v}$ is the null space of $\mathbf{R}$. This should be intuitive because thus far we have been modeling the operation of projecting to the plane perpendicular to $\mathbf{v}$ and rotating 90 degrees. If our starting vector is on the $\mathbf{v}$ axis then its projection on the plane perpendicular to $\mathbf{v}$ ought to be $0$. Any other vector will have non-zero projection onto the plane perpendicular to $\mathbf{v}$ and hence won’t be zero under $\mathbf{R}$. 

The proof is follows from if $\mathbf{R}\mathbf{x} = 0$ then $\mathbf{R}^2\mathbf{x} = 0$, from whence is follows from condition 2 that $\mathbf{x}$ is a scalar multiple of $\mathbf{v}$. So this shows that the nullspace of $\mathbf{R}$ is a subset of $\text{span } \mathbf{v}$. The fact that $\text{span } \mathbf{v}$ is a subset of the null space follows from the fact that $\text{det } \mathbf{R}^2 = (\text{det } \mathbf{R})^2 = 0$ which implies that $\text{det } \mathbf{R} = 0$. This means that $\mathbf{R}$ has a nontrivial nullspace and since this nullspace is contained in a 1 dimensional subspace it must equal the 1 dimensional subspace, $\text{span } \mathbf{v}$.


Now with our corollary we have, 

\\[
Rv = 0\\
R = -R^H \\
R^2 = \frac{vv^H}{v^Hv} - I
\\]
From this we can deduce that $R$ as follows given that $v = \begin{bmatrix} \xi & \eta & \zeta \end{bmatrix}^H$. Since $R$ is skew-symmetric we know,\
\\[
R = 
\begin{bmatrix} 
	0 & r_1 & r_2 \\
	-r_1 & 0 & r_3 \\
	-r_2 & -r_3 & 0 
\end{bmatrix}
\\]
Utilizing the fact $v$ is in the nullspace of $R$ we have the following relations,
\\[
\begin{bmatrix}
r_1 \\
r_2 
\end{bmatrix} \in
\text{span }
\begin{bmatrix}
-\zeta \\
\eta
\end{bmatrix} \\
\begin{bmatrix}
-r_1 \\
r_3 
\end{bmatrix} \in
\text{span }
\begin{bmatrix}
-\zeta \\
\xi
\end{bmatrix} \\
\begin{bmatrix}
-r_2 \\
-r_3 
\end{bmatrix} \in
\text{span }
\begin{bmatrix}
-\eta \\
\xi
\end{bmatrix}
\\] 

Now we can rewrite these relations to make the choice of signs match, so we can easily deduce a solution.
\\[
\begin{bmatrix}
r_1 \\
r_2 
\end{bmatrix} \in
\text{span }
\begin{bmatrix}
-\zeta \\
\eta
\end{bmatrix}
\\]
\\[
\begin{bmatrix}
-r_1 \\
r_3 
\end{bmatrix} \in
\text{span }
\begin{bmatrix}
\zeta \\
-\xi
\end{bmatrix}
\\]
\\[
\begin{bmatrix}
-r_2 \\
-r_3 
\end{bmatrix} \in
\text{span }
\begin{bmatrix}
\eta \\
-\xi
\end{bmatrix}
\\]
From this we can clearly see that a consistent choice that satisfies $v$ being in the nullspace of $R$ is

\\[
R = 
\kappa \begin{bmatrix} 
	0 & -\zeta & \eta \\
	\zeta & 0 & -\xi \\
	-\eta & \xi & 0 
\end{bmatrix}
\\]

Now to satisfy our third condition we have,

\\[
R^2 = \kappa^2 
\begin{bmatrix}
-(\zeta^2 + \eta^2) & \eta \xi & \zeta \xi \\
\eta\xi & -(\zeta^2 + \xi^2) & \eta \zeta \\
\zeta\xi & \eta \zeta & -(\eta^2 + \xi^2) 
\end{bmatrix}
= 
\frac{1}{\xi^2 + \eta^2 + \zeta^2}
\begin{bmatrix}
\xi^2-1 & \eta \xi & \zeta \xi \\
\eta\xi & \eta^2 - 1 & \eta \zeta \\
\zeta\xi & \eta \zeta & \zeta^2 - 1
\end{bmatrix}
\\]

Equality is satisfied for suitable choice of $\kappa$ and from this we conclude,

\\[
R = 
\frac{1}{\sqrt{\xi^2 + \eta^2 + \zeta^2}} \begin{bmatrix} 
	0 & -\zeta & \eta \\
	\zeta & 0 & -\xi \\
	-\eta & \xi & 0 
\end{bmatrix}
\\]
This is the explicit formula for rotating by 90 degrees around an axis generated by the vector $\mathbf{v}$. Now we can characterize rotations around the $\mathbf{v}$ axis as,

\\[
\mathbf{Q} = \frac{\mathbf{v}\mathbf{v}^H}{\mathbf{v}^H\mathbf{v}} + \mathbf{R}
\\]

A particular property mathematicians and others care about is that of continuity. Looking at our formula for $R$ we are aware that $R$ is dependent on the choice of $v$. For $v=0$, we have $R = 0$ and for any nonzero $v$ we have that $R$ doesn’t depend on $v$ up to positive scalar multiples. So we see that $R$ suddenly drops to $0$ if we move from $v$ to $0$ and then picks up a minus sign after crossing $0$ because rotating 90 degrees counter clockwise  around $v$ and $-v$ are not the same. What this tells us is that $R$ depends on $v$ in a way that is not continuous. To rectify this issue it turns out if we simply remove the $\kappa^2$ term we will have $R$ vary continuously with $v$. This is because we are multiplying $R$ by the length of $v$ and thus as $v$ get smaller and goes toward $0$, $R$ also tends to $0$ because the outputs of the projection and rotation are getting scaled by the length of $v$ which is tending to 0. So we move to $0$ in a continuous way, and thus establish continuity. We establish the connection between $v$ and $R$ using the following notation,

\\[
v^{\cancel{c}} = 
\begin{bmatrix} 
	0 & -\zeta & \eta \\
	\zeta & 0 & -\xi \\
	-\eta & \xi & 0 
\end{bmatrix}
\\]

And we note that the skew symmetric $v^{\cancel{c}}$ depends continuously on $v$. 
### A Preferred Notation
The notation of v cross used here was developed by William Kahan and some similar notations were used before him. A large benefit of this style of operation is that we gain associativity which mean’s expression order doesn’t matter and a sequence of repeated crosses ends up being well defined.

We also need to comment on the notation. Prior to now we always wrote $v^{\cancel{c}}x$ so the symbol $\cancel{c}$ was an operation that took in $v$ and $x$ and outputted a coordinate vector. However we now have an overloaded notation where we can look at $\cancel{c}$ acting just on a $v$ and it outputs the skew-symmetric matrix. Overloading notation can be confusing, although in this case as long as one knows what the two meanings are they interact in such a way that no errors will be made.
### What In The Type?!?!
It’s important to be careful and discuss types and clarify what has happened in the last three motivations. The result of a cross product is a vector. Some will be pedantic and say this is not the case, but it really is a matter of convention and what we are talking about.

In the Gaussian Elimination approach, we defined things in terms of coordinate vectors so it is important to realize that our output was a coordinate vector. We can look at the vector corresponding to coordinate vector, but we need to recognize the formula may look different in different bases.

In the Riesz Representation approach, we defined things using the determinant and the notion of the Riesz representation of the linear functional. This definition is “broader” in the sense that it didn’t choose a particular choice of basis in its definition although to actually write down the expression an orthonormal basis is still used. The output however, one could say is not dependent on the coordinate representation because it was defined in terms of the determinant.

In the Skew-Symmetric Matrix Approach, we defined the skew-symmetric matrix $v^{\cancel{c}}$ which explicitly depends on the basis. We could take the same steps in this approach but the form of the expression would change if we were not in an orthonormal basis. $v^{\cancel{c}}x$ I


## Possibly Pernicious (Pseudo)-Vector?
Some will call the cross product a pseudo-vector and not truly a vector and this only serves to confuse fledgling students. This ends up also being a matter of semantics where the meaning of the operations should not be lost to the reader.

### Prepare For Trouble...
We in our definition gave a formula with respect to an orthonormal basis. For an operation to be well-defined, mathematicians say a formula must be valid for all equivalent inputs. This has simple meaning, if we have an operation defined in terms of coordinates, then the formula on coordinates must output a coordinate vector that corresponds to the same vector regardless of the coordinates chosen. So for example, if we use the orthonormal basis for $E^3$ of $e_1, e_2, e_3$ and have another orthonormal basis $e_1, e_2, -e_3$, then the coordinate vector outputted with respect to each basis must correspond to the same actual vector. If this did not hold our formula is not well-defined with respect to orthonormal bases.

So it our cross product operation well defined?
### And Make It Double... 
Consider $e_1^{\cancel{c}}e_2$. The output coordinate vector would be $\begin{bmatrix} 0 & 0 & 1 \end{bmatrix}^H$. However, if we used the basis $e_1, e_2, e_3$ or $e_1, e_2, -e_3$ this coordinate vector has different meaning. $\begin{bmatrix} 0 & 0 & 1 \end{bmatrix}^H$ means we have 1 multiple of the third basis vector but here the basis vectors are different! So our formula is clearly not well-defined across different orthonormal bases, because for different orthonormal coordinates we do not get answers that generate the same output vector! 

This was overlooked until now because we have been working in particular coordinates, and not considered what happens between coordinates. 
### Resolution
One way to resolve this issue is simply to pick a particular orthonormal basis as the defining one, and then say in every other basis the formula needs to be the one that makes it consistent with the vector identified in the special defining orthonormal basis. If we do this no issues arise and everything is consistent, because we have stated that our formula depends on a special choice of basis.

However, this leaves the question of do we need to restrict our formula so severely that it only works in one basis. Or can we say that our formula works if we use several different coordinate systems?
### David Meredith’s Identity
\\[
Adj(L^T) v^{\cancel{c}} = (Lv)^{\cancel{c}}L
\\]
### When Does Our Formula Actually Work?
From this we establish that our formula works for all orthonormal bases that maintain the same orientation.
## Useful Identities
### Determinant Identity
\\[
	u^Hv^{\cancel{c}}w = \text{det } \begin{bmatrix} v & w & u \end{bmatrix}
\\]
### Grassmann’s Triple Product
\\[
	(u^{\cancel{c}}v)^{\cancel{c}} = vu^H - uv^H
\\]
### Jacobi’s Identity
\\[
	(u^{\cancel{c}}v)^{\cancel{c}} = u^{\cancel{c}}v^{\cancel{c}} - v^{\cancel{c}} u^{\cancel{c}}
\\]
### Lagrange’s Identity
## Applications:
### The Surjective Relationship between Skew-Symmetry and Rotations
### Least Squares!
### Join and Meet Projective Geometry 
## Computing A Cross
### Backwards Stability
### Forwards Stability
### Conditioning
### Techniques
## Connection to Exterior Algebra
## Random History
### Joseph Louis Lagrange
### William Rowan Hamilton
### Josiah Willard Gibbs




