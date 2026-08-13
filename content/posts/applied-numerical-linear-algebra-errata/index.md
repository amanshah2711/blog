---
title: Applied Numerical Linear Algebra by James W. Demmel
date: 2026-07-02T11:31:00-04:00
author: Aman Shah
draft: true
math: true
---

## Introduction
This list is neither complete, nor official. This is intended to be a collection of errors or confusions found throughout my occasional skimming of this book. Further errors can be contributed from others, and will be appropriately credited. Jim has an errata posted on the course page of Math221 : Numerical Linear Algebra at UC Berkeley. Things added here deliberately omit previously known remarks. 

## Errata
- Pg. 20, 78, 151 all refer to the “Cauchy-Schwartz” inequality, when it is more commonly **Cauchy-Schwarz**. It appears this is not a case of multiple transliterations of a name such as Chebyshev whose name finds many spellings. Also pages 353-356 use Schwarz when referring to the additive Schwarz method, so at minimum the same Hermann Schwarz’s name has been given two distinct spellings.
- Pg. 27 Question 1.17, $fl\left(\sqrt{x^2}\right) = x$ should read $fl\left(\sqrt{x^2}\right) = \left| x \right|$
- Pg. 51 Fig. 2.2 caption omits machine epsilon, $\varepsilon$, for $+$.
- Pg. 51 Fig. 2.2 caption uses $x$ instead of $\hat{x}$ for the third relative backward error bound annotated by $\circ$.
- Pg. 96 the formula for scaled backward error uses $\|x\|$ instead of $\|\hat{x}\|$. See Theorem 7.1 (Rigal and Gaches) in Higham’s ASNA. In addition, scaled backward error picks up an extra division by machine epsilon when referenced as $R/\varepsilon$.
## Possible Clarifications
- For anyone cross-reading “Introduction to Matrix Computations” by Golub and Van Loan, Demmel’s machine epsilon is their unit roundoff.
