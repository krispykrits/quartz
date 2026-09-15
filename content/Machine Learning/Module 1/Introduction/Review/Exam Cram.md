---
title: Chapter 1 - Exam Cram
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: review
source: Mitchell 1997 Chapter 1 lecture
---
# Exam Cram
## Tier 1 — MUST KNOW ⭐⭐⭐
- Mitchell's T–P–E definition and how to apply it.
- Four checkers design choices: experience, target function, representation, learning algorithm.
- $V$ versus $\hat V$.
- Six-feature linear evaluator.
- Training-value rule and LMS update.
- Four-module architecture.
- Learning as hypothesis-space search.

## Tier 2 — VERY IMPORTANT ⭐⭐
- Direct vs. indirect feedback and credit assignment.
- Training/evaluation distribution match.
- Expressive-power vs. learnability trade-off.
- Hypothesis space vs. search strategy.

## Tier 3 — SUPPORTING ⭐
- Samuel checkers, TD-Gammon, ALVINN as motivating examples.
- Six open questions on slide 20.

## Equation Cheat Sheet
$$\hat V(b)=w_0+\sum_{i=1}^{6}w_ix_i$$
$$V_{train}(b)\leftarrow\hat V(Successor(b))$$
$$E=\sum(V_{train}(b)-\hat V(b))^2$$
$$w_i\leftarrow w_i+\eta(V_{train}(b)-\hat V(b))x_i$$

## Common Confusions
- T/P/E are not the same as the four design choices.
- $V$ is the ideal value function; $\hat V$ is its approximation.
- A board-value score is not automatically a probability.
- Hypothesis space is not search strategy.

## If You Only Remember 10 Things
1. ML improves through experience.
2. Specify T, P, E.
3. Experience quality matters.
4. Indirect feedback creates credit assignment.
5. Checkers design has four choices.
6. Learn board value rather than direct moves.
7. Approximation is required because exact V is impractical.
8. Linear V-hat learns weights on board features.
9. LMS reduces mismatch with training values.
10. ML can be viewed as search through H.

## ⚡ 5-Minute Pre-Exam Review
Recite T–P–E; draw the four design choices; write the four equations above; trace Performance System → Critic → Generalizer → Experiment Generator; explain H + search strategy.
