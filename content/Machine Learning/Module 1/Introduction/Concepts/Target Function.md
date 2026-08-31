---
title: Target Function
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: concept
source: Mitchell 1997 Chapter 1 lecture
---
_Source slide: 13_
# Target Function
## Definition
The function the learner ultimately seeks to acquire or approximate.
## Technical Explanation
The checkers example contrasts `ChooseMove : X_board → X_move` with `V : X_board → R`. The lecture chooses a board-evaluation function V because it is easier to learn than mapping every board directly to its best move.
## Intuitive Explanation
Instead of memorizing “what move should I make?”, learn “how good is this board?” and choose moves that lead to better boards.
## Limitation
The ideal recursive V is correct but not efficiently computable, motivating an approximation V-hat.
## Connections
[[Concepts/Function Approximation]] · [[Mathematics/Ch01 - Mathematics#Exact board-value function]]
