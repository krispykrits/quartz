# Logistic and Softmax Regression

**Source:** pp. 20–23.

## Logistic Regression
Estimates a probability with $\hat p=\sigma(x^Tw)$. The sigmoid maps a real-valued score into the interval from 0 to 1. The lecture classifies as 1 at $\hat p\ge0.5$, equivalent to $x^Tw\ge0$.

## Decision Boundary
Using iris petal width, Figure 21 places the boundary near 1.6 cm, where both class probabilities are 0.5. Figure 22 shows a linear boundary in petal-length/petal-width space.

## Softmax Regression
Generalizes logistic regression to multiple classes. It computes one score per class, normalizes exponentiated scores into probabilities, and predicts the class with the largest score/probability. Training uses cross entropy.

## Connection
Both models start from linear scores in $x$ and $w$, but logistic uses a sigmoid for binary probability while softmax normalizes scores across $K$ classes.
