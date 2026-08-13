---
title: Condition Numbers
date: 2026-06-11T18:50:23-04:00
author: Aman Shah
draft: true
math: true
---

## Introduction
Condition numbers are a commonly used mathematical tool to understand how sensitive computations are. Most commonly they seem to arise in numerical linear algebra and related fields, however, many presentations seem to discuss conditioning quite differently. The purpose of this note is to serve as a backbone to connect the different approaches and collect some properties often used, but often times not explicitly proven. Maybe they are obvious to the others, however they are not obvious to me so they are expounded here. 

## Traditional Definition
Let $f: \mathcal{X} \to \mathcal{Y}$ where $\mathcal{X}$ and $\mathcal{Y}$ are normed spaces. We define the absolute condition number of $f(\cdot)$ at $x \in \mathcal{X}$ as 

\\[
cond(f,x) = \limsup_{\Delta x \to 0} \frac{\|f(x+\Delta x) - f(x)\|}{\|\Delta x\|}

\\]

Analogously, we define the relative condition number of $f$ at $x$ as,

\\[
\begin{equation}
cond(f,x) = \limsup_{\Delta x \to 0} \frac{\frac{\|f(x+\Delta x) - f(x)\|}{\|f(x)\|}}{\frac{\|\Delta x\|}{\|x\|}} 
\end{equation}
\\]


## Accuracy and Stability of Numerical Algorithms(ASNA)
This book is a classic text that covers a detailed analysis of many fundamental algorithms in numerical linear algebra, and compared to many of its counterparts it is more “mathematical” in flavor. Many texts do not state a general definition of condition number, but Higham uses the same structure throughout this book, which is as follows, 
\\[
\begin{equation}
cond(f,x) = \lim_{\epsilon \to 0^{+}} \sup \left\{ \frac{\|f(x+\Delta x)-f(x)\|}{\epsilon\| f(x)\|} : \| \Delta x \| \leq \epsilon \|x\| \right\}
\end{equation}
\\]

Our first key result will be showing that definition (2) is equivalent to (1). To do this we first introduce some notation and expand definition (1).

\\[
\begin{aligned}
A &= \limsup_{\Delta x \to 0} \frac{\frac{\|f(x+\Delta x) - f(x)\|}{\|f(x)\|}}{\frac{\|\Delta x\|}{\|x\|}} \\

&= \lim_{\epsilon \to 0^{+}} \sup\left\{ \frac{\frac{\|f(x+\Delta x) - f(x)\|}{\|f(x)\|}}{\frac{\|\Delta x\|}{\|x\|}} : \|\Delta x\| < \epsilon \right\} \\
&= \lim_{\epsilon \to 0^{+}}  A_{\epsilon}
\end{aligned}
\\]

We define for definition (2) analogously,
\\[
\begin{aligned}
B &= \lim_{\epsilon \to 0^{+}} \sup \left\{ \frac{\|f(x+\Delta x)-f(x)\|}{\epsilon\| f(x)\|} : \| \Delta x \| \leq \epsilon \|x\| \right\} \\
&= \lim_{\epsilon \to 0^{+}}  B_{\epsilon}
\end{aligned}
\\]


Step 1) Show $B \geq A$

Using the $\epsilon-\delta$ definition of limits we know that for all positive $\epsilon$ there exists a positive $\delta$ such that if $\alpha < \delta$ then $|A - A_{\alpha}| < \epsilon$. For any choice of $\alpha$ and any choice of positive $\epsilon^{\prime}$ we by definition of the supremum have for a particular choice of $\Delta x^{\alpha, \epsilon^{\prime}}$, 

\\[
\begin{equation}
A - \epsilon - \epsilon^{\prime} \leq A_{\alpha} - \epsilon^{\prime} \leq \frac{\frac{\|f(x+\Delta x^{\alpha, \epsilon^{\prime}}) - f(x)\|}{\|f(x)\|}}{\frac{\| \Delta x^{\alpha, \epsilon^{\prime}} \|}{\|x\|}} \leq A_{\alpha}
\end{equation}
\\]
\\[
\begin{equation}
A - \epsilon - \epsilon^{\prime} \leq A_{\alpha} - \epsilon^{\prime} \leq \frac{\frac{\|f(x+\Delta x^{\alpha, \epsilon^{\prime}}) - f(x)\|}{\|f(x)\|}}{\frac{\| \Delta x^{\alpha, \epsilon^{\prime}} \|}{\|x\|}} \leq B_{\frac{\| \Delta x^{\alpha, \epsilon^{\prime}} \|}{\|x\|}}
\end{equation}

\\]

If $B$ were less than $A$ then $B_{\alpha}$ would need to be less than $A$ for all $\alpha$ small enough. Observing the above two inequalities and that $\frac{\| \Delta x^{\alpha, \epsilon^{\prime}} \|}{\|x\|} < \alpha$, we can deduce that we can always find a $B_{\alpha}$ with $\alpha$ being chosen small enough, that $B_{\alpha}$ can be greater than any number strictly less than $A$. 

Step 2) Show that $B \leq A$

For this part of the proof we will use the fact that in (2) we can change the $\leq$ to $<$ with no loss of generality. We will prove this explicitly later. However if we, made this change then trivially we have $B_{\epsilon} \leq A_{\epsilon}$, since every term in the set we take the supremum over is being divided by epsilon which is larger than any of the relative errors in the denominator of (1). From $B_{\epsilon} \leq A_{\epsilon}$, it follows that $B \leq A$. 


Useful Lemma:
\\[
\begin{equation}
C := \lim_{\epsilon \to 0^{+}} \sup \left\{ \frac{\|f(x+\Delta x)-f(x)\|}{\epsilon\| f(x)\|} : \| \Delta x \| \leq \epsilon \|x\| \right\}
\end{equation}
\\]
\\[
D := \lim_{\epsilon \to 0^{+}} \sup \left\{ \frac{\|f(x+\Delta x)-f(x)\|}{\epsilon\| f(x)\|} : \| \Delta x \| < \epsilon \|x\| \right\}
\\]
\\[
\implies C = D
\\]

Since the set over which $D_{\epsilon}$ is computed is a subset of the set over which $C_{\epsilon}$ is contained in, it follows that $D_{\epsilon} \leq C_{\epsilon}$ and hence $D \leq C$. 

Showing that $D \geq C$ requires a little more effort. By definition for any positive $\epsilon$ there is a positive $\delta$ such that for all positive $\alpha, \beta$ less than $\delta$ we have the following two  relationships,
\\[
\frac{\|f(x+\Delta x)-f(x)\|}{\alpha\| f(x)\|} \leq C_{\alpha} < C + \epsilon  \quad \text{ when} \quad \| \Delta x \| \leq \alpha \|x\|
\\]
\\[
\frac{\|f(x+\Delta x)-f(x)\|}{\beta\| f(x)\|} \leq D_{\beta} < D + \epsilon  \quad \text{ when} \quad \| \Delta x \| < \beta \|x\|
\\]

For any $\kappa < \beta$ we have

\\[
\frac{\kappa}{\beta}\frac{\|f(x+\Delta x)-f(x)\|}{\kappa\| f(x)\|} \leq D_{\beta} < D + \epsilon  \quad \text{ when} \quad \| \Delta x \| < \beta \|x\|
\\]
\\[
\frac{\|f(x+\Delta x)-f(x)\|}{\kappa\| f(x)\|} \leq \frac{\beta}{\kappa}D_{\beta} < \frac{\beta}{\kappa} (D + \epsilon)  \quad \text{ when} \quad \| \Delta x \| < \beta \|x\|
\\]

From this we can establish the following,\
\
\\[
C_{\kappa} \leq \frac{\beta}{\kappa}D_{\beta} \leq \frac{\beta}{\kappa}(D+\epsilon)
\\]
We make a simple choice of $\kappa:= \frac{\beta}{1+\frac{1}{n}}$ and observe that,\

\\[
C_{\frac{\beta}{1+\frac{1}{n}}} \leq (1+\frac{1}{n})D_{\beta}
\\]

Since $D_{\beta} < D+\epsilon$ we can choose $n$ large enough such that  $(1+\frac{1}{n})D_{\beta} < D+\epsilon$, hence $C_{\kappa} < D+\epsilon$. If $C$ were greater than $D$, for some positive $\epsilon$ every $C_{\alpha}$ sufficiently small would be greater than $D+\epsilon$, so we have a contradiction and hence the conclusion follows.

*Remark: The approaching 0 from the right was added by me and is not used in this book. It is understood that the statement makes no sense if we allow $\epsilon$ to approach 0 from both sides.*


## Frechèt Derivative (special case when f continuously differentiable)

## Golub and Van Loan Approach

## Applied Numerical Linear Algebra(ANLA)

## A More Representative Choice of Norm

Let $$\|y\| := \inf\left\{\epsilon : |y| \leq \epsilon |x|\right\}$$

It is not hard to see this is a norm when every component of $x$ is non-zero. In the event some components of $x$ are zero we can restrict this norm to be defined on the set of vectors for whom the corresponding component for which $x$ is zero is also zero. This norm can be extended to possible $y$ by denoting those with non-zero components where $x$ is zero with norm $\infty$.

## References

[1^]: Higham
[2^]: Demmel
[3^]: Trefethan, Bau III
[4^]: Golub and Van Loan
[5^]: Rice
