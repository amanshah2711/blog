---
title: "Hyperplanes"
date: 2023-03-09
author: Aman Shah
draft: true
math: true
showtoc: true
showbreadcrumbs: true
---
## Mathematical Definition

Given an $n$-dimensional vector space, $V$,  a linear functional is a real-valued linear function on $V$ that we denote $\mathbf{w}^H$.[^1]

Now it can be verified *(and you should show)* that the set of all linear functionals is in fact a vector space. Since these linear functionals form a vector space, denoted $V^H$, we are free to view them as we would any other vector! Thus all your geometric intuition about vectors can carry over to linear functionals. However, there is a more appropriate way to view these vectors that gives us better intuition about how linear functionals are related to vectors in $V$. 

The mental model one should have is that $\mathbf{w}^H$ corresponds to a family of hyperplanes that are all parallel. Imagine parallel lines on a sheet of a paper, or parallel sheets stacked as though they were pancakes. We will clarify why this interpretation is valid in later sections, but for now use this thought as guiding intuition.  
 


## Hyperplanes
A common problem that arises is understanding the shape of the locus of $\mathbf{w}^T \mathbf{x}=\alpha$ given $\mathbf{w}^T \neq 0$. We realize that given any two number of points on the locus, any affine combination[^2] of these points is on the locus. That is if two points determine a line, then the line connecting them is on the locus. If three points determine a plane, then any point on the plane is contained in the locus. We can continue for any number of points. However can we find points that determine a line, a plane, and so on and so forth? The answer is yes. We can find $n$ points that determine an $n-1$ dimensional hyperplane by looking for axis intercepts.

Putting down arbitrary coordinates we find that our equation reduces to,

\\[
f_1 \beta_1 + f_2 \beta_2 + \ldots + f_n \beta_n = \alpha
\\]

The intersection with the $i$-th coordinate axis is seen as $\frac{\alpha}{f_i} $. If $f_i = 0$ then choose any other point and add arbitrary $\beta_i$ as there is no intercept. Thus we have $n$ points that determine uniquely an $n-1$ dimensional hyperplane. The key insight in this realization is that if all points are shifted uniformly so that one is at the origin, then the non-zero points form a vector space of dimension $n - 1$. Thus the locus is an $n-1$ dimensional hyperplane.

Conversely, we can show that any hyperplane has a corresponding functional that it lies in the locus of. To determine this functional translate the hyperplane so it contains the origin. Construct a basis for the space where the first $n-1$ basis elements lie wholly in the hyperplane. With respect to this basis $\mathbf{f}^T = k\mathbf{e}_n^T $ has the hyperplane as its locus for any $k$ and $\alpha = 0$. By choosing $\alpha = \mathbf{f}^T\mathbf{x}$ for any $\mathbf{x}$ on the unshifted hyperplane, we have the unshifted hyperplane contained in the locus.

Hence we can switch between hyperplane and functional with no real loss of generality.

### Writing Down In Coordinates

Assume we are given a basis $\mathbf{B}$ for $V$ consisting of elements $\mathbf{b}_i$. We want to understand what the linear functional $\mathbf{w}^H$ looks like in a given coordinate system. We observe that for any $\mathbf{x}$, we can write $\mathbf{x}$ in terms of the basis elements, and use the linearity of $\mathbf{w}^H$. Precisely we mean,

\\[
\begin{align}
\mathbf{w}^H \mathbf{x} &= \mathbf{w}^H(\beta_1 \mathbf{b}_1 + \beta_2 \mathbf{b}_2 + \ldots + \beta_n \mathbf{b}_n ) \\
&= \beta_1 \mathbf{w}^H\mathbf{b}_1 + \beta_2 \mathbf{w}^H\mathbf{b}_2 + \ldots + \beta_n \mathbf{w}^H\mathbf{b}_n .
\end{align}
\\]
From this we see that the linear functional is determined by its value on $n$ linearly independent points. We also note that if we define $w_i = \mathbf{w}^H\mathbf{b}_i$ then the above expression becomes, 
\\[
\mathbf{w}^H \mathbf{x} = w_1 \beta_1 + w_2 \beta_2 + \ldots + w_n \beta_n .
\\]
Thus given this coordinate system on $V$, we can express $\mathbf{w}^H$ using the $n$ numbers $w_i$.

### Warning: Row Vectors or Not?

Looking at the expression $\mathbf{w}^T = \omega_1 \mathbf{e}_1^T + \omega_2 \mathbf{e}_2^T + \ldots + \omega_n\mathbf{e}_n^T $, we realize in coordinates that $\mathbf{w}^T\mathbf{x} = \omega_1 \beta_1 + \omega_2 \beta_2 + \ldots + \omega_n \beta_n$. Therefore it is tempting to view this as a dot product between the coordinate vector $x$ and a coordinate vector, $ w$ formed from the $\omega_i$. In this coordinate system that is true, but it is a mistake to associate the linear functional $ \mathbf{w}^T$ with the coordinate vector $w$. Here is why.

Assume we have another basis, $\mathbf{A}$ of $V$ related to $\mathbf{B}$ by $\mathbf{A}K = \mathbf{B}$. It follows that $
\mathfrak{w}^T \mathbf{A}^{-1} = \mathbf{w}^T$ and $w^T \mathbf{B}^{-1} = \mathbf{w}^T$. From this it follows that $w^TK^{-1}\mathbf{A}^{-1} = \mathbf{w}^T$. The coordinate vector $w$ with respect to  basis $\mathbf{B}$ becomes coordinate vector $ Kw$. Our linear functional is now represented by row vector $w^TK^{-1}$ while $w^TK^T$ is the row vector given by $w$ after changing basis. These are not equal except in the rare instances that $K^{-1} = K^T$. The conclusion is that change of basis affects linear functionals and coordinate vectors differently.

## Double Duals
The dual space of the dual space is a mouthful referred to commonly as the double dual. The double dual is the space of linear functionals that take as input other linear functionals. By the same arguments as before we can say this space is dimension $n$. However, a nice property of the double dual is that there exists an isomorphism between a vector space and its double dual that does not depend on basis. 

Consider the element of the double dual that takes a linear functional and evaluates it at a particular point. This element being identified with the point of evaluation is the desired isomorphism.  Thus we say that $(V^0)^0 = V$. Note to show the map of evaluation is an isomorphism requires a basis of the space.[^3]

## Annihilators
Let $U$ be a subspace of $V$. Then we define the annihilator $U^\perp$ as the set of all linear functionals that map all elements of $U$ to $0$. 

Take for example $U$ is a line through the origin in three dimensional space. The annihilator of $U$ is set of functionals that represent planes containing the line. In other words, take any plane that contains the line $U$, and spin it treating $U$ as the axis of rotation. Every rotation yields a new plane contained in the annihilator(in the sense that there is a functional with locus corresponding to this plane). 

This view of the annihilator reveals that the annihilator of the annihilator is basically $U$ itself. Why? Consider the set of functionals representing the plane that contains the line. Evaluating each of these functionals on the line yields $0$ because the line is in the locus of the functionals. We will say a vector annihilates a subset of the dual space, if every element of the subset gets sent to $0$ under the evaluation map of that vector. In general, the annihilator of the annihilator consists of maps that evaluate elements of the annihilator at points in $U$. Succinctly, $U$ annihilates the annihilator.

## Theorems of Alternatives
For many problems we can say one of two statements must hold. These types of statements are useful in understanding when solutions to various problems exist.

### Fredholm’s Alternative

A prime use of linear algebra is to solve equations of the form $ \mathbf{L} \mathbf{x} = \mathbf{y}$. If we denote the image of the domain as $Range(\mathbf{L})$ then the following holds.

> There exists a solution if and only if $\mathbf{y}$ annihilates the annihilators of $Range(\mathbf{L})$.

This is tantamount to saying that the range of $\mathbf{L}$ is the intersection of the hyperplanes containing $\mathbf{L}$ and that a solution is possible only if $\mathbf{y}$ lies in the intersection of these hyperplanes. This follows because an element of the annihilator is a functional that can be identified with a hyperplane that contains $Range(\mathbf{L})$. As a statement of alternatives we can reformulate the above as the following.

> 1. There exists a solution to $ \mathbf{L} \mathbf{x} = \mathbf{y}$.
> 2. There exists $\mathbf{w}^T$ such that $\mathbf{w}^T \mathbf{L} = \mathbf{0}^T$ and $\mathbf{w}^T \mathbf{y} \neq 0 $.

#### Application: Overdetermined Least Squares

### Farkas’ Alternative (Farkas’ Lemma)

This alternative is similar in spirit, although relies on the fact that a hyperplane divides the space into two half-spaces.

> There exists a solution of $ \mathbf{L} \mathbf{x} = \mathbf{y}$ where $\mathbf{x}$ has non-negative components if and only if $\mathbf{y}$ is in the same half-space as the image of (component-wise) non-negative vectors relative to any hyperplane through $0$ whose half-space wholly contains the image.

The image of non-negative vectors form a convex cone and a solution exists if and only if the cone and $\mathbf{y}$ cannot be separated by a hyperplane. The inability to be separated corresponds is equivalent to containment in the cone and therefore the existence of solution. This idea is more commonly expressed as the following statement of alternatives.
> 1. There exists a solution of $\mathbf{L} \mathbf{x} = \mathbf{y}$ where $\mathbf{x}$ has non-negative components
> 2. There exists $\mathbf{w}^T$ such that $\mathbf{w}^T\mathbf{y} < 0$ and $\mathbf{w}^T \mathbf{L}$ is non-negative component-wise. 

*Note: Farkas Lemma is typically proved with machinery outside of linear algebra, although hopefully it is clear why a linear algebra student could conjecture Farkas Lemma.*

### Gordan’s Alternative (Gordan's Lemma)
This alternative is similar to Farkas Alternative because it relies on divisions using half-spaces. Succinctly it states the following.

> There exists a solution of $ \mathbf{L} \mathbf{x} = 0$ where $\mathbf{x}$ has non-negative components that sum to $1$ if and only if the image of (component-wise) non-negative vectors does not lie in the interior of a halfspace of a hyperplane through the origin.

The image of non-negative vectors that sum to $1$ corresponds to the convex hull of the image of the basis vectors. The statement then states that a solution exists if and only if $0$ is in the convex hull, otherwise we can find a hyperplane that separates $0$ and the hull. This idea is more commonly expressed as the following statement of alternatives.

> 1. There exists a solution of $\mathbf{L} \mathbf{x} = 0$ where $\mathbf{x}$ has non-negative components that sum to $1 $.
> 2. There exists $\mathbf{w}^T$ such that $\mathbf{w}^T \mathbf{L} < 0 $ component-wise. 

*Note: Gordan's Lemma is typically proved with machinery outside of linear algebra, although hopefully it is clear why a linear algebra student could conjecture Gordan's Lemma.*

## Polynomials
### Evaluation
### Integration

## Quadrature
### Adams-Bashforth Methods
### Adams-Moulton Methods
### Nystrom Methods
### Milne-Simpson Methods
### Open/Closed Newton-Cotes Methods
### Runge-Kutta Methods
### Backward Differentiation Formulas (BDF)
## When In A Normed Space...
### Hahn-Banach Theorem
## When in A Euclidean Space...
## When in A Minkowski Space...



[^1]: The superscript $H$ has no meaning. It helps identifies linear functionals and should be thought of a reminder that this entity corresponds to a family of hyperplanes.
[^2]: An affine combination is a linear combination such that the coefficients sum to $1$.
[^3]: This means this result is true for finite dimensional spaces, but not necessarily for infinite dimensional ones. 
