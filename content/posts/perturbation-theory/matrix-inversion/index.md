---
title: Matrix Inversion Perturbation Theory
date: 2026-07-04T11:17:21-04:00
author: Aman Shah
draft: false
math: true
---

## Introduction
This is the most classical origin of an important concept known as the condition number of a matrix. Our goal is to give a detailed view of different methods, because while this is a well-known topic there are several techniques and few standard presentations of total rigor.

[IN PROGRESS NOTE]

## Absolute Condition

The absolute condition number of matrix inversion with respect to a particular norm, $\|\cdot\|$, is given by the formula,

\\[
\limsup_{\Delta A \to 0} \frac{\|(A+\Delta A)^{-1} - A^{-1}\|}{\|\Delta A\|}
\\]

## Relative Condition
The relative condition number of matrix inversion with respect to a particular norm, $\|\cdot\|$, is given by the formula,

\\[
\limsup_{\Delta A \to 0} \frac{\frac{\|(A+\Delta A)^{-1} - A^{-1}\|}{\|A^{-1}\|}}{\frac{\| \Delta A \|}{\|A\|}}
\\]

## Relationship Between Absolute and Relative Condition Numbers
Glancing at the aforementioned formulae one realizes the absolute and relative condition numbers are both related by the constant, $\frac{\|A\|}{\|A^{-1}\|}$. Given this nature we will derive results for the relative condition number as that is our primary interest.

### Normwise Relative Condition Number


#### Using Elementary Definition


\\[
\limsup_{\Delta A \to 0} \frac{\frac{\|(A+\Delta A)^{-1} - A^{-1} \|}{\|A^{-1}\|}}{\frac{\| \Delta A \|}{\|A\|}}
\\]

\\[
\begin{aligned}
	(A+\Delta A)^{-1}&= (I+A^{-1}\Delta A)^{-1}A^{-1} \\
										&= (I - A^{-1}\Delta A + (A^{-1}\Delta A)^{2} - (A^{-1}\Delta A)^{3} + \ldots)A^{-1} \\
										&= A^{-1} - A^{-1}\Delta A A^{-1} + (A^{-1}\Delta A)^{2} A^{-1} - (A^{-1}\Delta A)^{3} A^{-1} + \ldots
\end{aligned}
\\]

From this it follows we can bound the numerator using the triangle inequality as follows,
\\[
\begin{aligned}
	&(A+\Delta A)^{-1} - A^{-1} = - A^{-1}\Delta A A^{-1} + (A^{-1}\Delta A)^{2} A^{-1} - (A^{-1}\Delta A)^{3} A^{-1} + \ldots \\
	\implies& \|(A+\Delta A)^{-1} - A^{-1}\| \leq \|A^{-1}\|^{2}\|\Delta A\| + \|A^{-1}\|^{3}\|\Delta A\|^{2} + \ldots
\end{aligned}
\\]

From this it follows that,\

\\[
\begin{aligned}

\frac{\|(A+\Delta A)^{-1} - A^{-1}\|}{\|A^{-1}\|} \leq \|A^{-1}\|\|\Delta A\| + \|A^{-1}\|^{2}\|\Delta A\|^{2} + \ldots
\end{aligned}
\\]

From this we find that the relative error, is upper bounded by,\

\\[
\begin{aligned}
\frac{\frac{\|(A+\Delta A)^{-1} - A^{-1}\|}{\|A^{-1}\|}}{\frac{\|\Delta A\|}{\|A\|}} \leq \|A^{-1}\|\|A\| + \|A^{-1}\|^{2}\|\Delta A\|\|A\| + \ldots
\end{aligned}
\\]

Thus the $\limsup$ is upper bounded by $\|A^{-1}\|\|A\|$.

We now need to show there is a lower bound that converges to this. We shall use some convenient notation and write $(A+\Delta A)^{-1} - A^{-1} = - A^{-1}\Delta A A^{-1} + O(\|\Delta A\|^{2})$, then apply the reverse triangle inequality\
\

\\[
\|(A+\Delta A)^{-1} - A^{-1}\| \geq \|A^{-1}\Delta A A^{-1}\| - \|O(\|\Delta A\|^{2})\|
\\]

Focusing on the first term we find that,\

\\[
\|A^{-1}\Delta A A^{-1}\| = \sup_{\|y\|=1} \|A^{-1}\Delta A A^{-1}y\|
\\]
Choose $y$ to be the vector such that $\|A^{-1}y\|=\|A^{-1}\|$, and $v^{H}$ dual to $A^{-1}y$, and $\Delta A = \frac{\epsilon yv^H}{\|A^{-1}y\|}$. It is clear that $\|\Delta A\|=\epsilon$ and the lower bound is $\|A^{-1}\|^{2}$. From this it follows that,\
\
\\[
\begin{aligned}
\frac{\frac{\|(A+\Delta A)^{-1} - A^{-1}\|}{\|A^{-1}\|}}{\frac{\|\Delta A\|}{\|A\|}} &\geq \frac{\|A\|\|A^{-1}\Delta A A^{-1}\| - \|O(\|\Delta A\|)\|}{\|A^{-1}\|} \\
&\geq \frac{\|A\|\|A^{-1}\|^{2} - \|O(\|\Delta A\|)\|}{\|A^{-1}\|} \\
&\geq \|A^{-1}\|\|A\| - \|O(\|\Delta A\|)\|
\end{aligned}
\\]

Thus the conclusion follows that the relative condition number is $\|A^{-1}\|\|A\|$.

#### The Frechèt Derivative

Let $f(A) = A^{-1}$, then we know from general theory of condition numbers that the condition number is \
\
\\[
\frac{\|D_{A}f\|\|A\|}{\|A^{-1}\|} = \|A^{-1}\|\|A\|
\\]

We note the tricky part of this computation is $\|D_{A}f\|\|A\| = \sup_{\|E\|=1}\|A^{-1}EA^{-1}\|$. Choose the same perturbation as in the last section to show this is equal to $\|A^{-1}\|^{2}$.

### Componentwise Relative Condition Number

We are not so lucky in this case to have equality, but only an upper bound.

### Distance to Nearest Ill-posed Problem
Before any comments we must define what we mean by “nearest ill-posed problem”. For matrix inversion, *ill-posed* means a problem for which there is no answer, or mathematically the problem of trying to invert a matrix for which there exists no inverse. So the distance from $A$ which we assume to be invertible and thus well-posed for inversion, is the closest distance as measured by the norm a matrix which is not invertible. Precisely we mean,

\\[
\min \{\|\Delta A\| : A + \Delta A \text{ not invertible} \}
\\]

Analogously we can define the relative distance to the nearest ill-posed problem as,

\\[
\min \left\{\frac{\|\Delta A\|}{\|A\|} : A + \Delta A \text{ not invertible} \right\}
\\]


#### Frobenius Norm
One can directly apply the  what is referred to as the Eckart-Young-Mirksy theorem[^1][^2], (some argue it should be labelled the Schmidt Approximation theorem). We provide a short self-contained proof,

Step 1: Constructing a lower bound.


If $A+\Delta A$ is not invertible, then there exists a non-zero $z$ in its null space. Exploiting the Frobenius norms’ subordinance to the 2-norm (i.e. $\|Ax\|_{2} \leq \|A\|_{F}\|x\|_{2}$), and that $Az = -\Delta A z$ we have the following chain of implications,

\\[
\begin{aligned}
	\|\Delta A\| &\geq \frac{\|Az\|_{2}}{\|z\|_{2}} \\
							 &\geq \frac{\|Az\|_{2}}{\|A^{-1}Az\|_{2}} \\
							 &\geq \frac{1}{\frac{\|A^{-1}{Az}\|_{2}}{\|Az\|_{2}}} \\
							 &\geq \frac{1}{\|A^{-1}\|_{2}} \\
							 &\geq \sigma_{n}
\end{aligned}
\\]

Step 2: Show the lower bound is attainable.

Given $A$, take a singular value decomposition, $U \Sigma V^{T}$ and construct $\Delta A:= -\sigma_{n}u_{n}v_{n}^{T}$. It is easy to show $v_{n}$ is in the null space of $A+\Delta A$ and $\|\Delta A\|_{F} = \sigma_{n}$, by simple computation.

From this it follows that for the Frobenius norm, we have 
\\[
\begin{aligned}
\sigma_{n} &= \min \{\|\Delta A\|_{F} : A + \Delta A \text{ not invertible} \} \\
\frac{\sigma_{n}}{\sqrt{\sigma_{1}^{2} + \ldots + \sigma_{n}^{2}}} &= \min \left\{\frac{\|\Delta A\|_{F}}{\|A\|_{F}} : A + \Delta A \text{ not invertible} \right\}
\end{aligned}
\\]

#### Spectral Norm
For the 2-norm, and its corresponding induced operator 2-norm, sometimes dubbed the spectral norm, we have explicit formulae. We exploit the fact that $\|A\|_{2} = \sigma_{1}$, (hence $\|A^{-1}\|_{2} = \frac{1}{\sigma_{n}}$), and the same $\Delta A$ as for the Frobenius norm, we have,

\\[
\begin{aligned}
\frac{1}{\|A^{-1}\|_{2}} &= \min \{\|\Delta A\|_{2} : A + \Delta A \text{ not invertible} \} \\
\frac{1}{\|A\|_{2}\|A^{-1}\|_{2}} &= \min \left\{\frac{\|\Delta A\|_{2}}{\|A\|_{2}} : A + \Delta A \text{ not invertible} \right\}
\end{aligned}
\\]


#### Induced Operator Norms
The proof for induced operator norms, is analogous to the Frobenius norm, except instead of using an SVD, we use vectors that maximize the induced operator norms. $(A+\Delta A)z = 0 \implies Az = -\Delta Az \implies \|Az\| \leq\|\Delta A z\| \leq \|\Delta A\|\|z\|$

\\[
\begin{aligned}
 \|\Delta A\| &\geq \frac{\|Az\|}{\|z\|} \\
			 &\geq \frac{\|Az\|}{\|A^{-1}Az\|} \\
			 &\geq \frac{1}{\frac{\|A^{-1}Az\|}{\|Az\|}} \\
			 &\geq \frac{1}{\|A^{-1}\|}
 \end{aligned}
\\]

Choose $\Delta A = -wv^H$ where $w= \argmax_{\|x\|=1}\|A^{-1}x\|$ and $v^{H}$ dual to $A^{-1}w$. We see that $(A+\delta A)A^{-1}w = (w - w) = 0$, and

\\[
\|\Delta A\| = \sup \frac{\|wv^Hz\|}{\|z\|} = \sup\frac{|v^Hz|}{\|z\|}\|w\|
\\]
Since $\|v^H\| = \frac{1}{\|A^{-1}w\|}=\frac{1}{\|A^{-1}\|}$ which is clearly attained for $z:=A^{-1}w$.

#### Unitarily Invariant Norms

### History

In 1936, Carl Eckart and Gale Young published their paper establishing the SVD for rectangular, real matrices(earlier forms for square or other matrices were known to Sylvester, Autonne, and others). In addition to establishing existence of the SVD the demonstrated the solution to the minimization problem in the Frobenius norm, was given by a simple function of the largest singular value. In this way our first result, is a restatement of the Eckart-Young result.

Leon Mirsky published an extension in 1960, that demonstrated a characterization for any unitarily invariant norm, 

#### Eckart-Young-Mirsky


#### Gastinel, Kahan



## References



[^1]:  Eckart, Carl, and Young, Gale, The Approximation of One Matrix by Another of Lower Rank, Psychometrika 1 no. 3 (1936) 211–218.
[^2]: Mirsky, L., SYMMETRIC GAUGE FUNCTIONS AND UNITARILY INVARIANT NORMS, The Quarterly Journal of Mathematics 11 no. 1 (1960) 50–59.
[^3]:  Demmel, James Weldon, On condition numbers and the distance to the nearest ill-posed problem, Numerische Mathematik 51 no. 3 (1987) 251–289.
[^4]:  Kahan, W., Numerical Linear Algebra, Canadian Mathematical Bulletin 9 no. 05 (1966) 757–801.
[^5]: Geurts, A. J., A contribution to the theory of condition, Numerische Mathematik 39 no. 1 (1982) 85–96.




