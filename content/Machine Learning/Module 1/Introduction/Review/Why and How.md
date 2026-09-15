---
title: Chapter 1 - Why and How
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: review
source: Mitchell 1997 Chapter 1 lecture
---
# Why and How
## Why formalize learning with T, P, and E?
Because “learning” requires a task, a measurable criterion of improvement, and experience responsible for that improvement.

## Why can self-play be attractive?
It supplies unlimited, cheap experience. Its cost is possible distribution mismatch with human/expert play.

## Why is indirect feedback harder?
A final outcome does not directly identify which of many preceding moves caused it; this is the credit assignment problem.

## Why learn V rather than ChooseMove directly?
The lecture states that an evaluation function scoring boards is far easier to learn than the direct board-to-move function.

## Why approximate V?
The exact recursive definition is correct but not efficiently computable.

## Why use a linear representation?
To trade expressive power for a representation with few enough parameters to learn from a realistic number of examples.

## How are intermediate training targets produced?
Use the current value estimate of the successor board: $V_{train}(b)\leftarrow\hat V(Successor(b))$.

## Why can the training-value rule work?
According to the lecture, errors average out over many games and reliable end-of-game values propagate backward.

## How does LMS react to underestimation?
When $\hat V(b)<V_{train}(b)$, the positive error term nudges weights in proportion to feature values and $\eta$.

## Why view learning as search?
Different algorithms can be understood by the hypothesis space they permit and the strategy used to search it.
