# Batch Gradient Descent

**Source:** pp. 7–9.

## Purpose
Iteratively minimize MSE using the gradient calculated from the entire training set.

## Gradient
$$\nabla_w MSE(w)=\frac{2}{m}X^T(Xw-y).$$

## Update
$$w_{next}=w-\eta\nabla_wMSE(w).$$

## Steps
1. Randomly initialize $w$.
2. Compute the gradient over all training data.
3. Subtract learning-rate-scaled gradient.
4. Repeat until convergence/tolerance.

## Termination
The lecture proposes a large iteration limit and interruption when the gradient norm is below tolerance $\epsilon$.

## Strength / Limitation
Stable path toward the minimum for linear-regression MSE, but every step uses the full training set and can be very slow for large $m$. Feature scaling is important.
