---
title: Hypothesis Space
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: concept
source: Mitchell 1997 Chapter 1 lecture
---
_Source slide: 19_
# Hypothesis Space
## Definition
A set H of candidate hypotheses considered by a learning algorithm.
## Technical Explanation
Learning can be viewed as search through H for a hypothesis that best fits training examples and prior constraints. In the checkers example, H consists of possible weight vectors for the linear evaluator.
## Intuitive Explanation
The learner searches among the kinds of answers it is allowed to represent.
## Two Major Algorithmic Choices
1. **Hypothesis space:** e.g., linear functions, decision trees, neural networks.
2. **Search strategy:** e.g., gradient descent or greedy specialization.
## Why It Matters
This perspective unifies the algorithms introduced later in the book.
## Connections
[[Concepts/Function Approximation]] · [[Algorithms/Least Mean Squares]]
