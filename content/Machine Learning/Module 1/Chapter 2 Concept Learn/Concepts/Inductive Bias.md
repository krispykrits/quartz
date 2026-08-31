---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Inductive Bias

_Source slides: 19-23_

## Restricted Hypothesis Space
The conjunction-only EnjoySport hypothesis space cannot represent every Boolean concept. The lecture gives the example:

> Sky = Sunny **or** Sky = Cloudy

If the true target concept is not in $H$, Candidate Elimination can converge to an empty version space.

## Unbiased Hypothesis Space
The lecture proposes:

$$
H'=\mathcal P(X)
$$

so every Boolean concept can be represented.

## Futility of Bias-Free Learning
Even with every Boolean function available, unseen instances remain undecidable because consistent hypotheses can split evenly between positive and negative labels.

> [!important]
> An unbiased learner cannot generalize beyond observed examples.

## Formal Definition

$$
\forall x_i\in X:
(B\land D_c\land x_i)
\vdash
L(x_i,D_c)
$$

The inductive bias is the minimal set of assumptions $B$ that allows deductive inference to reproduce the learner's inductive predictions.

## Bias Comparison

| Learner | Inductive bias |
|---|---|
| Rote learner | No bias; stores examples and does not generalize |
| Candidate Elimination | $c\in H$ |
| FIND-S | $c\in H$, and all instances are negative unless entailed positive by training data |

> [!important]
> Stronger bias can support more generalization from less data, but increases the risk of excluding the true concept if the bias is wrong.

## Connections
- [[Concepts/Inductive Learning Hypothesis|Inductive Learning Hypothesis]]
- [[Algorithms/FIND-S|FIND-S]]
- [[Algorithms/Candidate Elimination|Candidate Elimination]]
- [[Mathematics/Ch02 - Mathematics#Inductive bias entailment|Math treatment]]
