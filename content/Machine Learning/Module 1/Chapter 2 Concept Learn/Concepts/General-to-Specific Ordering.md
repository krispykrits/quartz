---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# General-to-Specific Ordering

_Source slide: 7_

## Definition

$$
h_j\ge_g h_k
\iff
\forall x\in X:
[(h_k(x)=1)\to(h_j(x)=1)]
$$

A hypothesis $h_j$ is more general than or equal to $h_k$ if every instance accepted by $h_k$ is also accepted by $h_j$.

## Technical Explanation
The positive set of the more-specific hypothesis is contained in the positive set of the more-general hypothesis.

## Intuitive Explanation
A general hypothesis says “yes” to more instances. A specific hypothesis imposes more restrictions.

## Why It Matters
The ordering lets search algorithms move locally through $H$ by generalization and specialization instead of enumerating every hypothesis.

## Connections
- [[Algorithms/FIND-S|FIND-S]]
- [[Concepts/S and G Boundaries|S and G Boundaries]]
- [[Algorithms/Candidate Elimination|Candidate Elimination]]
- [[Mathematics/Ch02 - Mathematics#General-to-specific ordering|Math treatment]]
