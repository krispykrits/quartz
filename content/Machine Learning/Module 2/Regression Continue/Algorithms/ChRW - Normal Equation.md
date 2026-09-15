# Normal Equation

**Source:** pp. 3–4.

## Purpose
Find linear-regression parameters directly, without iterative optimization.

## Input
Feature matrix $X$ and target vector $y$.

## Output
Estimated parameter vector $\hat w$.

## Equation
$$\hat w=(X^TX)^{-1}X^Ty.$$

## Steps
1. Form $X^TX$.
2. Invert it.
3. Multiply by $X^T$.
4. Multiply by $y$.

## Strengths
No learning rate and no iterative convergence process are required. It scales linearly with training instances according to the lecture.

## Limitation
Inverting the $n\times n$ matrix costs about $O(n^{2.4})$ to $O(n^3)$, so the method becomes very slow for huge feature counts.

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> w_hat = np.linalg.inv(X.T @ X) @ X.T @ y
> ```
