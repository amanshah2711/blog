---
title: Linear Systems Perturbation Theory
date: 2026-06-09T00:00:47-04:00
author: Aman Shah
draft: true
math: true
---

## Introduction

## Perturbations with respect to b
If we consider perturbations in $b$ we mean our original problem is $Ax=b$ and we are instead solving the perturbed problem, $A\hat{x} = b+\Delta b$. Our interest is in how changes to the input data, $b$, affect the solution $x$. Note that $\Delta x := \hat{x} - x$, so that $A(x+\Delta x) = b + \Delta b$, and $A\Delta x = \Delta b$

### Normwise
#### Using Elementary Definition


\\[
\limsup_{\Delta b \to 0} \frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta b\|}{\|b\|}}
\\]

Using the definitions we have that $\Delta x = A^{-1}\Delta b$, and consequently we derive an upper bound assuming subordinance between the matrix and vector norms $\| \Delta x\| \leq \|A^{-1}\|\|\Delta b\|$ ,

\\[
\frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta b\|}{\|b\|}} \leq \frac{\|A^{-1}\|\|b\|}{\|x\|}
\\]

Note that if $\|\Delta b\| = \mu w$ where $w$ maximizes $\|A^{-1}\|$, then the inequality is an equality.

Now unfolding the definition we derive the condition number of linear system solving with respect to perturbations in $b$,

\\[
\begin{aligned}
\limsup_{\Delta b \to 0} \frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta b\|}{\|b\|}} &= \lim_{\epsilon \to 0^{+}} \sup \left\{\frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta b\|}{\|b\|}} : \|\Delta b\| \leq \epsilon \right\} \\
&= \lim_{\epsilon \to 0^{+}} \frac{\|A^{-1}\|\|b\|}{\|x\|} \\
&= \frac{\|A^{-1}\|\|b\|}{\|x\|}
\end{aligned}
\\]


#### Using Frechèt Derivative

Using the traditional formulation we have $x(b) = A^{-1}b$, and thus 

\\[

\frac{\|D_{b}x\|\|b\|}{\|x\|} = \frac{\|A^{-1}\|\|b\|}{\|x\|} 
\\]

### Componentwise

By taking absolute values we find that $|\Delta x| \leq |A^{-1}||\Delta b|$, and consequently for any absolute norm,
\\[
\begin{aligned}
\frac{\|\Delta x\|}{\|x\|} &\leq \frac{\||A^{-1}||\Delta b|\|}{\|x\|} \\
&\leq \epsilon\frac{\||A^{-1}||b|\|}{\|x\|}
\end{aligned}
\\]
This bound is attainable for $\Delta b = \epsilon diag(sgn(v)) bdiag(sgn(b))$, and hence the condition number is exactly $\frac{\||A^{-1}||b|\|}{\|x\|}$.

#### Using Frechèt Derivative


## Perturbations with respect to A
If we consider perturbations in $A$ we mean our original problem is $Ax=b$ and we are instead solving the perturbed problem, $(A+\Delta A)\hat{x} = b$. Our interest is in how changes to the input data, $A$, affect the solution $x$. Note that $\Delta x := \hat{x} - x$, so that $(A+\Delta A)(x+\Delta x) = b$, and hence $\Delta x = (A+\Delta A)^{-1}\Delta A x$.
### Normwise
The norms used here are vector norms and the corresponding operator norms. 

#### Using Elementary Definition

\\[
\limsup_{\Delta A \to 0} \frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}}
\\]
As with perturbations with respect to $b$, we will begin by deriving an upper bound from the definitions and a lower bound picking a clever choice of $\Delta A$ so that as $\Delta A$ tends to 0 the relative condition number is sandwiched to $\|A^{-1}\|\|A\|$.
\\[
\begin{aligned}
\frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}} &\leq \frac{\frac{\|(A+\Delta A)^{-1}\|\|\Delta A\|\|x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}} \\
&\leq \frac{\|(A+\Delta A)^{-1}\|\|\Delta A\|}{\frac{\|\Delta A\|}{\|A\|}}\\
&\leq \|(A+\Delta A)^{-1}\|\|A\|  \\
&\leq \frac{\|A^{-1}\|\|A\|}{1-\|A^{-1}\|\|\Delta A\|}
\end{aligned}
\\]

Now to show this bound is attainable, let $w:= \argmax_{\|x\|=1} \|A^{-1}x\|$ and $v^{H}$ be dual to $x$, meaning $\|x\| = v^Hx$ and $\|v^H\| = 1$. Now we show the perturbation, $\epsilon wv^H$  has norm $\epsilon$ as follows,

\\[
\begin{aligned}
\|wv^H\| &= \sup_{\|z\|=1}\|wv^Hz\| \\
				 &= \sup_{\|z\|=1} |v^Hz| \|w\| \\
			   &= \sup_{\|z\|=1}|v^Hz|
\end{aligned}
\\]
By Hölder’s inequality, $|v^Hz| \leq \|v^H\|\|z\|$ and this bound is attained for $z := \frac{x}{\|x\|}$, so $\epsilon wv^H$  has norm $\epsilon$. Now to show attainment of the bound is simple, but tedious algebra,

\\[
\begin{aligned}
\Delta x &= -(A+\Delta A)^{-1}\Delta x \\
			   &= -(A+ \epsilon wv^H)^{-1} \epsilon wv^Hx \\
			   &= -(A+ \epsilon wv^H)^{-1}\epsilon w \|x\| \\
			   &= -\left( A^{-1} - \frac{A^{-1}(\epsilon w)v^HA^{-1}}{1+\epsilon v^HA^{-1}w}\right) \epsilon w \|x\| \\
			   &= -\epsilon \|x\|\left( I- \frac{A^{-1}(\epsilon w)v^H}{1+\epsilon v^HA^{-1}w}\right) A^{-1}w \\
			   &=  -\epsilon \|x\|\left( A^{-1}w- \frac{A^{-1}(\epsilon w)v^HA^{-1}w}{1+\epsilon v^HA^{-1}w}\right) \\
			   &= -\frac{\epsilon\|x\|}{1+\epsilon v^HA^{-1}w}A^{-1}w
\end{aligned}
\\]

From this the conclusion follows as,

\\[
\begin{aligned}
\frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}} &= \frac{\frac{\| -\frac{\epsilon\|x\|}{1+\epsilon v^HA^{-1}w}A^{-1}w\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}} \\
&= \frac{\|A^{-1}\|\|A\|}{| 1+\epsilon v^HA^{-1}w|}
\end{aligned}
\\]

So now as $\epsilon$ tends to $0$ we have a lower and upper bound on the condition number that both converge to $\|A\|\|A^{-1}\|$.

*Note: the above proof is applies only operator norms. For a general matrix norm and vector norm pair that are compatible, we have the upper bound $\|A\|\|A^{-1}\|$*

#### Using Frechèt Derivative

Here we have $x(A) = A^{-1}b$,

\\[
\frac{\|D_{A}x(A)\|\|A\|}{\|x\|}
\\]

 This requires evaluating, $D_{A}x(A)$ which is difficult because the derivative of a vector-valued function with matrix inputs is generally a tensor. Using directional derivatives makes it easier to evaluate the induced norm, and we see that $D_{A}x(A)E = \frac{d}{d\mu}(A+\mu E)^{-1}b = -A^{-1}EA^{-1}b = -A^{-1}Ex$. From this $\sup_{E \neq 0} \frac{\|A^{-1}Ex\|}{\|E\|} = \|A^{-1}\|\|x\|$. Hence it follows that,
 \\[
\frac{\|D_{A}x(A)\|\|A\|}{\|x\|} = \frac{\|A^{-1}\|\|x\|\|A\|}{\|x\|} = \|A^{-1}\|\|A\|
\\]
### Componentwise

#### Using Elementary Definition 

Here, as is typical, we will use the componentwise relative norm.

\\[
\limsup_{\|\Delta A\| \to 0} \frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}}
\\]

Unrolling the definitions we have 

\\[
\begin{aligned}
\limsup_{\|\Delta A\| \to 0} \frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}} &= \lim_{\epsilon \to 0^{+}} \left\{ \frac{\frac{\|\Delta x\|}{\|x\|}}{\frac{\|\Delta A\|}{\|A\|}} : \|\Delta A\| < \epsilon \right\} \\
	&= \lim_{\epsilon \to 0^{+}} \left\{ \frac{\frac{\|\Delta x\|}{\|x\|}}{\|\Delta A\|} : \|\Delta A\| < \epsilon \right\} \\
	&= \lim_{\epsilon \to 0^{+}} \left\{ \frac{\frac{\|\Delta x\|}{\|x\|}}{\|\Delta A\|} : |\Delta A| < \epsilon |A| \right\}
\end{aligned}
\\]

Here we use,

\\[
\begin{aligned}
&(A+\Delta A)(x+\Delta x) = b \\
\implies& Ax + A\Delta x = b - \Delta A x - \Delta A \Delta x \\
\implies& \Delta x = -A^{-1}\Delta A x - A^{-1}\Delta A \Delta x \\
\implies& |\Delta x| \leq |A^{-1}||\Delta A||x| + |A^{-1}||\Delta A||\Delta x| \\
\implies& \|\Delta x\| \leq \||A^{-1}||\Delta A||x|\| + \||A^{-1}||\Delta A|\|\|\Delta x\| \\
\implies& (1-\||A^{-1}||\Delta A|\|)\|\Delta x\| \leq \||A^{-1}||\Delta A||x|\|\\
\implies& \|\Delta x\| \leq \frac{\||A^{-1}||\Delta A||x|\|}{1-\||A^{-1}||\Delta A|\|}  \\
\implies& \|\Delta x\| \leq \frac{\epsilon\||A^{-1}|| A||x|\|}{1-\epsilon\||A^{-1}|| A|\|} \\
\implies& \frac{\|\Delta x\|}{\|x\|} \leq \frac{\epsilon}{1-\epsilon\||A^{-1}|| A|\|} \frac{\||A^{-1}|| A||x|\|}{\|x\|}
\end{aligned}
\\]

The above demonstrates that $\| |A^{-1}||A||x|\|$ is an upper bound for the relative condition number when using an absolute norm. For the infinity norm, and its induced norm we can show this is the relative condition number. 

Chose $\Delta A = \epsilon diag(sgn(v))|A|diag(sgn(x))$, where $v^T$ is the row of $|A^{-1}|$ such that $|A^{-1}||A||x|$. By this choice $\|A^{-1}\Delta A x\| = \| |A^{-1}||A||x|\|$. Now we shift things around,\
\

\\[
\begin{aligned}
	&\Delta x = -A^{-1}\Delta A x - A^{-1}\Delta A \Delta x \\
	&\implies -A^{-1}\Delta A x = \Delta x + A^{-1}\Delta A \Delta x \\
	&\implies | A^{-1}||\Delta A|| x| \leq |\Delta x| + |A^{-1}||\Delta A|| \Delta x| \\
	&\implies \| | A^{-1}||\Delta A|| x| \| \leq \|\Delta x\| + \||A^{-1}||\Delta A| \| \|\Delta x\| \\
	&\implies \frac{\|\Delta x\|}{\|x\|} \geq \frac{\| | A^{-1}||\Delta A|| x| \|}{\|x\|}\frac{1}{1+ \||A^{-1}||\Delta A| \|} \\
	&\implies \frac{\|\Delta x\|}{\|x\|} \geq \frac{\| | A^{-1}||A|| x| \|}{\|x\|}\frac{\epsilon}{1+ \||A^{-1}||\Delta A| \|}
\end{aligned}
\\]







## Perturbations with respect to A and b

### Normwise

### Componentwise

  
# Deal with Later
  
### Distance to nearest ill-posed problem
Often times in expositions one will see geometric interpretations of these condition numbers. The most clear one being linked to the SVD and condition number for matrix inversion. It is not the case that the condition numbers of matrix inversion and condition numbers of linear system solving always coincide, so we keep them separate but note that for the spectral norm the matrix condition number has the geometric interpretation as distance to singularity, while this is not true always

#### Coping with overloading

