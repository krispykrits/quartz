---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Consistency and Version Spaces

_Source slide: 12_

## Consistency
A hypothesis $h$ is consistent with $D$ iff it correctly classifies every training example in $D$.

## Version Space

$$
VS_{H,D}
\equiv
\{h\in H\mid Consistent(h,D)\}
$$

## Technical Explanation
The version space contains **all** hypotheses in $H$ that have not been ruled out by the observed training data.

## Intuitive Explanation
Every new labeled example crosses out hypotheses that disagree with it. The survivors are the version space.

## Why It Matters
Consistency does not imply that a hypothesis is the true concept. Multiple hypotheses may remain equally compatible with the data.

## Connections
- [[Algorithms/List-Then-Eliminate|List-Then-Eliminate]]
- [[Concepts/S and G Boundaries|S and G Boundaries]]
- [[Algorithms/Candidate Elimination|Candidate Elimination]]
- [[Concepts/Active Learning and Query Selection|Active Learning]]
