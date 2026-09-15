---
title: Chapter 1 - Decision and Learning Rules
tags: [artificial-intelligence, algorithms]
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: algorithms
---
# Chapter 1 - Decision and Learning Rules

## Expected-Utility Action Selection
**Purpose:** choose the action with the highest probability-weighted utility.
```text
for each action a:
    score[a] = Σ_s P(s | a, evidence) U(s,a)
return action with maximum score
```
**Limitation:** exact evaluation may be infeasible in large uncertain environments.
See [[Ch01 Mathematics#Expected-Utility Action Rule]].

## Perceptron Learning Rule
1. Compute $w^	op x+b$.
2. Convert to binary prediction $\hat y$.
3. Compute error $y-\hat y$.
4. Update $w\leftarrow w+\eta(y-\hat y)x$.
5. Repeat.

**Failure mode:** XOR is not linearly separable.

## Gradient Learning
```text
gradient = derivative of loss with respect to parameters
parameters = parameters - learning_rate * gradient
```
Used to adjust learned parameters toward lower prediction error.

## Bayesian-Network Factorization
Represent a joint probability through a directed graph and local conditional probability models, exploiting conditional independence.

## Goal-Directed Planning Pattern
```text
Need(goal) + Achieves(action, goal) + Feasible(action) → Do(action)
```
The lecture warns that real planning also needs resources, uncertainty, preferences, and time.
