---
title: Training Experience
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: concept
source: Mitchell 1997 Chapter 1 lecture
---
_Source slides: 11–12_
# Training Experience
## Definition
The data/interactions from which the learner improves.
## Technical Explanation
The lecture emphasizes three attributes: feedback type; learner control over example sequence; and match between the training-example distribution and the distribution used to measure P.
## Intuitive Explanation
What the learner experiences determines what it has a chance to learn.
## Direct vs. Indirect Feedback
Direct feedback can pair a board with the best move. Indirect feedback may reveal only the final win/loss, creating the **credit assignment problem**: which earlier moves deserve credit?
## Checkers Design Choice
Self-play provides unlimited cheap experience, but its distribution may differ from play against human experts.
## Assumptions / Limitations
A mismatch between training experience and evaluation conditions can limit performance under the target distribution.
## Connections
[[Concepts/Well-Posed Learning Problem]] · [[Concepts/Target Function]]
