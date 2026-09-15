# Linear Regression

**Source:** pp. 2–4.

## Definition
A linear regression model predicts a numeric output as a weighted sum of features plus a bias term.

## Technical Form
$$\hat y=w_0+w_1x_1+\cdots+w_nx_n=w^Tx.$$
Training finds $w$ that minimizes prediction error, represented in the lecture by MSE.

## Why It Matters
It is the base model used to introduce closed-form training, Gradient Descent, polynomial feature expansion, and regularization.

## Lecture Example
Life satisfaction is modeled from GDP per capita as $w_0+w_1\times GDP$. The lecture also gives randomly generated one-dimensional data and reports an example estimate such as $\hat w=[4.3,2.8]$.

## Common Confusion
Polynomial regression can still use a linear model: it is linear in the learned weights even though the transformed features contain powers.

## Related
[[Algorithms/ChRW - Normal Equation|Normal Equation]] · [[Mathematics/ChRW - Mathematics|Mathematics]]
