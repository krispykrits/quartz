---
title: Chapter 1 - Why and How
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: review
---
# Chapter 1 - Why and How
## Why does AIMA emphasize acting rationally?
It uses a general performance criterion rather than human imitation and can incorporate inference, search, planning, learning, reflexes, or heuristics.

## Why is thinking rationally insufficient?
Correct beliefs do not by themselves choose an action, especially under uncertainty, preferences, and time limits.

## Why separate belief and preference?
Probability says what is likely; utility says what is desirable.

## Why can approximation be rational?
Exact computation may cost more than the improvement it produces.

## Why can a fixed objective be dangerous?
A mispecified objective can be optimized exactly and still produce unwanted behavior.

## Why keep uncertainty about human preferences?
It can motivate learning, asking, deferring, preserving options, and allowing correction.

## Why distinguish computability from tractability?
Some problems are solvable in principle but infeasible at realistic scale.

## Why did microworlds look impressive?
They restricted objects/actions enough to make explicit modeling and search tractable.

## Why did early systems fail to scale?
Introspection was not algorithmic analysis, search exploded combinatorially, and representations were too weak.

## Why did expert systems help and then disappoint?
Domain knowledge pruned search, but knowledge acquisition, maintenance, uncertainty, brittleness, and lack of learning limited them.

## Why were Bayesian networks important?
Conditional independence allowed compact uncertain representations.

## Why did big data and deep learning matter?
More data, parallel hardware, and better training methods enabled learned representations that often replaced hand-engineered features.

## Why is benchmark success insufficient?
Open-ended environments demand robustness, transparency, safety, and beneficial behavior beyond bounded test scores.
