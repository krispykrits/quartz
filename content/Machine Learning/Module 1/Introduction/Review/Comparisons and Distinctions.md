---
title: Chapter 1 - Comparisons and Distinctions
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: review
source: Mitchell 1997 Chapter 1 lecture
---
# Comparisons and Distinctions
| A | B | Main distinction |
|---|---|---|
| Direct feedback | Indirect feedback | Direct supplies desired action/label; indirect may reveal only eventual outcome |
| `ChooseMove` | $V$ | Action mapping vs. board evaluation |
| $V$ | $\hat V$ | Ideal target vs. learnable approximation |
| Target function | Representation | What should be learned vs. how candidate functions are encoded |
| Hypothesis space | Search strategy | Candidate solutions vs. method for moving among them |
| Training distribution | Performance/evaluation distribution | What learner sees vs. conditions under which P is measured |

> [!warning]
> **Don't Confuse These:** $V\neq\hat V$. The lecture defines an ideal V, then learns an approximation because the ideal function is not efficiently computable.

> [!important]
> **Main Difference:** T, P, and E specify the learning problem; the four checkers design choices specify how a learner will be constructed to solve it.
