---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# S and G Boundaries

_Source slides: 13, 16-17_

## Definitions
- **S** — maximally specific members of the version space.
- **G** — maximally general members of the version space.

## Version Space Representation Theorem

$$
VS_{H,D}
=
\{h\in H\mid
\exists s\in S,
\exists g\in G,
g\ge_g h\ge_g s\}
$$

## Meaning
Every remaining consistent hypothesis lies between some S member and some G member in the general-to-specific ordering.

## Final EnjoySport Boundaries

$$
S=
\{\langle Sunny,Warm,?,Strong,?,?\rangle\}
$$

$$
G=
\{
\langle Sunny,?,?,?,?,?\rangle,
\langle ?,Warm,?,?,?,?\rangle
\}
$$

## Slide 17 Diagram
The figure places the S boundary at the bottom, the G boundary at the top, and intermediate consistent hypotheses between them. Arrows point from more-specific hypotheses toward more-general hypotheses.

> [!question]
> **Diagram-Based Exam Question:** If shown this figure, explain why every interior hypothesis remains consistent, identify S and G, and state the direction of the ordering.

## Connections
- [[Concepts/Consistency and Version Spaces|Version Spaces]]
- [[Algorithms/Candidate Elimination|Candidate Elimination]]
