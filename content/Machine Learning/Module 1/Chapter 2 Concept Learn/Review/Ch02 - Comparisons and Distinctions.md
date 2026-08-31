---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Comparisons and Distinctions

## FIND-S vs Candidate Elimination

| Dimension | FIND-S | Candidate Elimination |
|---|---|---|
| Output | One maximally specific hypothesis | Entire version space via S and G |
| Positive examples | Generalize h | Generalize S and prune G |
| Negative examples | Ignored | Specialize G and prune S |
| Preserves alternatives? | No | Yes |
| Represents uncertainty? | No | Yes |

> [!important]
> FIND-S commits to one maximally specific hypothesis. Candidate Elimination preserves all hypotheses consistent with the data.

## S vs G

| S | G |
|---|---|
| Maximally specific consistent hypotheses | Maximally general consistent hypotheses |
| Lower boundary | Upper boundary |
| Generalized by positive examples | Specialized by negative examples |

## Consistent vs Correct
**Consistent** means a hypothesis agrees with every observed label. It does not prove that the hypothesis equals the true target concept over all of $X$.

## `?` vs `∅`
- `?` = any value is accepted.
- `∅` = no value is accepted.

## Biased vs Unbiased Hypothesis Space
A restricted H can exclude the target. An unrestricted H can represent every Boolean target but, according to the lecture, cannot decide unseen classifications without additional assumptions.

> [!warning]
> “Unbiased” does not mean “best.” In this chapter, a completely unbiased learner cannot generalize.
