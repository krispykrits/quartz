# Mini-batch Gradient Descent

**Source:** pp. 10–11.

## Purpose
Combine Batch GD and SGD by computing each gradient from a small random mini-batch.

## Why Use It
The lecture emphasizes hardware-optimized matrix operations, especially on GPUs. Its trajectory is less erratic than SGD, particularly with larger mini-batches.

## Tradeoff
It tends to walk closer to the minimum than SGD, but on problems with local minima it may be harder to escape them.

## Figure 10
Batch GD's path stops at the minimum; stochastic and mini-batch paths continue to walk around it. Batch steps are more expensive.
