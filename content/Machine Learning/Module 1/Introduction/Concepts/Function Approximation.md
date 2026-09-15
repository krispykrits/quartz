---
title: Function Approximation
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: concept
source: Mitchell 1997 Chapter 1 lecture
---
_Source slides: 13–16_
# Function Approximation
## Definition
Replacing a difficult target function with a learnable approximation from a restricted representation.
## Technical Explanation
Mitchell represents V-hat as a linear combination of six board features. This deliberately trades expressive power for a small number of learnable parameters.
## Intuitive Explanation
The exact evaluator is too difficult; use a compact scoring rule whose weights can be learned from experience.
## Key Trade-off
More restricted representation → easier learning, but less expressive power.
## Connections
[[Concepts/Target Function]] · [[Concepts/Hypothesis Space]] · [[Algorithms/Least Mean Squares]] · [[Ch01 Mathematics#Linear approximation of board value]]
