---
title: Matrix Computations by Golub and Van Loan 4th Edition Errata
date: 2026-06-22T22:18:30-04:00
author: Aman Shah
draft: true
math: true
---

## Introduction
This list of errors is not complete, nor official. This is intended to be a collection of errors found throughout my occasionally skimming of this book. Further errors can be contributed from others, and will be appropriately credited. The link to the books errata given in the front matter appears to be dead, so it is possible many of these have been discovered by prior readers.

## Errata
- Pg. 115, the Matrix $A$ uses $v$ for the latter $n-1$ elements of the first column while the subsequent analysis uses the letter $z$. Either $A$ needs to use $z$ or the subsequent uses of $z$ need to be replaced with $v$.
- Pg. 119 *atithmetic* should be ***arithmetic*** 
- Pg. 123 Under “To prove the theorem we must verify (3.3.2), i.e.,” The lower left entry of the block matrix is incorrect. $\left|v\right| + \left|\alpha\right|\left|{f}\right|$ should be $\left|v\right| + \left|\alpha\right|\left|{\hat{z}}\right|$
- Pg. 123 Under “while (3.3.6) and (3.3.8) imply”, we have that $2\left|\hat{z}\right|\left|w\right|$ should be $2\left|\hat{z}\right|\left|w^T\right|$ 
- Pg. 132 “The *rowpiv* and *colpiv* representations can be used to form $Pb$ and $Qy$”, is true but should read to form $Q^{T}y$ as stated in the line prior.

- Pg. 141 *estimation problem thatis* should be corrected to:  ***estimation problem that is***. 
- Pg. 155 In theorem 4.1.1. $\sum_{i=1,i \neq j}^{n-1} \left|c_{ij}\right|+\frac{\left|w_j\right|}{\left|\alpha\right|}\sum_{i=1,i \neq j}^{n-1} \left|v_{i}\right| < (\left|c_{jj}\right|-\left|w_{j}\right|) + \frac{\left|w_{j}\right|}{\left|\alpha\right|}(\left|\alpha\right| - \left|v_{j}\right|)$ should be less than or equal to instead of strictly less than. Consider the matrix $A = \begin{bmatrix} 1 && 1 \\ 1 && -1 \end{bmatrix}$. This $A$ is diagonally dominant and the inequality does not hold strictly.
- Pg. 159 “The unsymmetric analog of Algorithm 4.1.2...” appears to be incorrect as there is only Algorithm 4.1.1.
- Pg. 159 “Numerical issues that associated with the factorization of a diagonaly dominant matrix...” has **diagonally** misspelled, and grammatically it should be either **that are** or ~~that~~.
- Pg. 163 “The computation of the factorization $A= LDL^{T}$ via Algorithm 4.1.2” is incorrect because **Algorithm 4.1.1** is the computation of this factorization of $A$.

## Possible Clarifications
- Pg. 125 For problem 3.3.1 it seems that if you use the method in the proof of theorem 3.3.1 then you can still keep $2$ as the bound instead of $3$. My guess is the problem would rather you just do $\left| A - \hat{L}\hat{U} \right| \leq \left|A - fl(A)\right| + \left|fl(A) - \hat{L}\hat{U}\right|$, then apply theorem 3.3.1 and bump the bound up to 3. While not an explicit error, I think this is an important clarification. I thought the intent of the problem was forcing you to do the theorem yourself step-by-step with a modification, not trivially modify the result.
- Pg. 156 This is not a true “error”, but my remark as the reader. The authors use “stable” for Gaussian elimination with partial pivoting, thus the growth factors associated with partial pivoting are deemed “stable”. The potential clarification is that the proof implicitly uses the fact that since the Schur complement is diagonally dominant Gaussian elimination with no pivoting and with partial pivoting are equivalent hence the algorithm is “stable” by former analysis.  Additionally, a relevant remark is that we get stronger stability results for Gaussian elimination on diagonally dominant matrices because the pivot growth factor can be bounded with a much tighter bound than an exponential, so there is a stronger and truer stability than for Gaussian elimination with partial pivoting in the general case with no mention or proof at all.
