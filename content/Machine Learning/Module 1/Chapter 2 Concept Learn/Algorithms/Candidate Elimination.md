---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Candidate Elimination

_Source slides: 14-18_

## Purpose
Maintain the complete version space compactly through its S and G boundaries.

## Initialization
- $G$ starts with the most general hypothesis in $H$.
- $S$ starts with the most specific hypothesis in $H$.

## Positive Example
1. Remove from G any hypothesis inconsistent with the positive example.
2. Remove from S each inconsistent hypothesis.
3. Add its minimal generalizations that:
   - are consistent with the positive example;
   - remain below at least one member of G.
4. Remove from S any hypothesis more general than another member of S.

## Negative Example
1. Remove from S any hypothesis inconsistent with the negative example.
2. Remove from G each inconsistent hypothesis.
3. Add its minimal specializations that:
   - are consistent with the negative example;
   - remain above at least one member of S.
4. Remove from G any hypothesis less general than another member of G.

> [!important]
> Positive examples **generalize S** and prune G. Negative examples **specialize G** and prune S.

## Complete EnjoySport Trace

| After | S boundary | G boundary |
|---|---|---|
| $d_0$ init | $\{\langle∅,∅,∅,∅,∅,∅\rangle\}$ | $\{\langle?,?,?,?,?,?\rangle\}$ |
| $d_1$ (+) | $\{\langle Sunny,Warm,Normal,Strong,Warm,Same\rangle\}$ | $\{\langle?,?,?,?,?,?\rangle\}$ |
| $d_2$ (+) | $\{\langle Sunny,Warm,?,Strong,Warm,Same\rangle\}$ | $\{\langle?,?,?,?,?,?\rangle\}$ |
| $d_3$ (-) | unchanged | $\{\langle Sunny,?,?,?,?,?\rangle,\langle ?,Warm,?,?,?,?\rangle,\langle ?????,Same\rangle\}$ |
| $d_4$ (+) | $\{\langle Sunny,Warm,?,Strong,?,?\rangle\}$ | $\{\langle Sunny,?,?,?,?,?\rangle,\langle ?,Warm,?,?,?,?\rangle\}$ |

## What Happens at $d_3$
The negative example is:

$$
\langle Rainy,Cold,High,Strong,Warm,Change\rangle
$$

S already rejects it, so S is unchanged. The completely general hypothesis in G accepts it and must be specialized. The useful minimal specializations that still remain above S are:
- Sky = Sunny
- AirTemp = Warm
- Forecast = Same

## What Happens at $d_4$
The positive example requires S to generalize Water and Forecast to `?`. The G member that requires Forecast = Same rejects this positive example and is removed.

## Convergence
- $S=G=\{h\}$ means one unique consistent hypothesis remains.
- $S=G=\emptyset$ means no consistent hypothesis exists in $H$.

After all four EnjoySport examples, the version space has not collapsed to one hypothesis.

## Failure Mode
If the true target is outside the chosen hypothesis space, Candidate Elimination can eventually eliminate every hypothesis. See [[Concepts/Inductive Bias|Inductive Bias]].

## Connections
- [[Concepts/Consistency and Version Spaces|Version Spaces]]
- [[Concepts/S and G Boundaries|S and G Boundaries]]
- [[Concepts/Active Learning and Query Selection|Active Learning]]
