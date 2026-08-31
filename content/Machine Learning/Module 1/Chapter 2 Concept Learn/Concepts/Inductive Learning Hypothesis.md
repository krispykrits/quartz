---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Inductive Learning Hypothesis

_Source slide: 6_

## Lecture Statement
> Any hypothesis found to approximate the target function well over a sufficiently large set of training examples will also approximate the target function well over other unobserved examples.

## Technical Explanation
The learner observes only a subset of the instance space $X$, but the objective is useful classification over all of $X$.

## Intuitive Explanation
A learner is useful only if what it learns from seen examples carries over to unseen examples.

## Why It Matters
This idea leads directly to [[Concepts/Inductive Bias|Inductive Bias]], because generalization requires assumptions about how observed examples relate to unobserved ones.
