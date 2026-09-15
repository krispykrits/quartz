# Stochastic Gradient Descent

**Source:** pp. 9–10.

## Purpose
Reduce the per-update cost of Gradient Descent by using one random instance at each step.

## Behavior
The objective bounces up and down while decreasing on average. SGD can get close to the minimum but continues to bounce instead of settling exactly.

## Learning Schedule
The lecture resolves the speed/stability dilemma by gradually reducing the learning rate: large early steps make progress and can escape local minima; smaller later steps help settle near the global minimum.

## Epoch
By convention, a round of $m$ iterations is called an epoch.

## Strengths
Fast updates, can train on huge datasets because only one instance is needed at a time, and randomness can help escape local minima on irregular objectives.

## Limitation
Randomness prevents smooth convergence unless the learning rate is managed well.
