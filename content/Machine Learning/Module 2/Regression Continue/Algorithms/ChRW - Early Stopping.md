# Early Stopping

**Source:** p. 19.

## Purpose
Regularize an iterative model by stopping when validation error reaches its minimum.

## Procedure
1. Train the model iteratively.
2. Track training and validation error.
3. Training error naturally decreases.
4. Validation error initially decreases.
5. Stop when validation error reaches its minimum, before it begins rising.

## Interpretation
A rising validation error while training error continues downward signals that the model has begun overfitting. The lecture calls early stopping a “beautiful free lunch.”
