---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Active Learning and Query Selection

_Source slide: 18_

## Main Idea
An active learner may choose the next instance whose classification should be requested.

## Strategy from the Lecture
Choose an instance satisfied by roughly half of the hypotheses in the current version space.

Either possible label can then eliminate up to roughly half of the remaining hypotheses.

## Classifying New Instances
A new instance can be classified confidently when every hypothesis in the current version space agrees on its label.

The lecture notes that when they disagree, a vote over S, G, and intermediate hypotheses can provide a natural confidence score.

## Connections
- [[Concepts/Consistency and Version Spaces|Version Spaces]]
- [[Concepts/S and G Boundaries|S and G Boundaries]]
- [[Algorithms/Candidate Elimination|Candidate Elimination]]
