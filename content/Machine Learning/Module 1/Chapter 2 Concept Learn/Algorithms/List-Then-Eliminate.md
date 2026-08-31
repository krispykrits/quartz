---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# List-Then-Eliminate

_Source slide: 12_

## Purpose
Maintain exactly the hypotheses that remain consistent with all observed data.

## Steps
1. Initialize the version space to all of $H$.
2. For each new training example, remove every hypothesis inconsistent with the example.
3. The remaining hypotheses are $VS_{H,D}$.

## Strength
Correct and conceptually simple.

## Limitation
Requires exhaustive enumeration of $H$, which the lecture says is intractable except for the smallest problems.

## Connection
This limitation motivates [[Algorithms/Candidate Elimination|Candidate Elimination]].
