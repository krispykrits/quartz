---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Exam Cram

## Tier 1 - MUST KNOW ⭐⭐⭐
- Concept learning: $c:X\to\{0,1\}$.
- Hypothesis space $H$.
- General-to-specific ordering.
- FIND-S starts maximally specific and ignores negatives.
- Version space = all hypotheses consistent with D.
- S = maximally specific boundary.
- G = maximally general boundary.
- Positive examples generalize S.
- Negative examples specialize G.
- Inductive bias is necessary for generalization.

## Tier 2 - VERY IMPORTANT ⭐⭐
- EnjoySport representation: specific value, `?`, `∅`.
- 5120 syntactic vs 973 semantic hypotheses.
- Version-space representation theorem.
- Candidate Elimination convergence conditions.
- Active query selection.
- Restricted H can exclude the target.

## Tier 3 - SUPPORTING ⭐
- Rote learner comparison.
- Confident classification when all version-space hypotheses agree.
- Slide 17 version-space diagram.

## Equation Cheat Sheet

$$
c:X\to\{0,1\}
$$

$$
h_j\ge_g h_k
\iff
\forall x\in X:
[(h_k(x)=1)\to(h_j(x)=1)]
$$

$$
VS_{H,D}
=
\{h\in H\mid Consistent(h,D)\}
$$

$$
VS_{H,D}
=
\{h\in H\mid
\exists s\in S,
\exists g\in G,
g\ge_g h\ge_g s\}
$$

$$
\forall x_i\in X:
(B\land D_c\land x_i)
\vdash
L(x_i,D_c)
$$

## Algorithm Cheat Sheet
**FIND-S:** start specific → process positives → minimally generalize → ignore negatives.

**Candidate Elimination:** maintain S/G → positive examples push S upward → negative examples push G downward.

## Common Confusions
- More general ≠ more accurate.
- Consistent ≠ proven correct.
- Version space ≠ one hypothesis.
- `?` ≠ unknown.
- `∅` ≠ missing data.
- Unbiased ≠ able to generalize.

## If You Only Remember 10 Things
1. Concept learning is Boolean-function learning.
2. Learning is search through H.
3. H limits what can be represented.
4. Generality is defined by positive-set containment.
5. FIND-S uses only positive examples.
6. FIND-S returns one maximally specific hypothesis.
7. Version spaces preserve all consistent hypotheses.
8. S and G compactly represent the version space.
9. Candidate Elimination uses both positive and negative examples.
10. Generalization requires inductive bias.

## ⚡ 5-Minute Pre-Exam Review
Trace EnjoySport once. Recite the S/G update directions. Read the generality and version-space formulas aloud. Explain why bias-free learning cannot generalize.
