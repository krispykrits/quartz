---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Why and How

## Why view concept learning as search?
Because the learner chooses among hypotheses in $H$. The general-to-specific ordering makes that search structured.

## Why does FIND-S start maximally specific?
So it generalizes only when positive evidence forces a change.

## Why is ignoring negative examples a limitation?
Negative examples can eliminate hypotheses that fit every positive example but still classify some negatives incorrectly.

## Why use a version space?
Because multiple hypotheses can be equally consistent with the observed training data.

## Why can S and G represent the whole version space?
The representation theorem states that every consistent hypothesis lies between at least one S member and one G member.

## Why do positive examples generalize S?
If S rejects a positive example, S is too specific.

## Why do negative examples specialize G?
If G accepts a negative example, G is too general.

## Why query an instance that splits the version space?
Either possible label eliminates roughly half of the hypotheses.

## Why can a restricted H lead to an empty version space?
The true concept may not be representable in H.

## Why can an unrestricted H not generalize by itself?
For unseen instances, equally consistent hypotheses may predict opposite labels.

## Why is inductive bias necessary?
Because assumptions beyond the observed data are required to choose among those competing predictions.
