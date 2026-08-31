---
title: "Predictive Uncertainty and Softmax"
tags: [machine-learning, chapter-01]
type: concept
---


# Predictive Uncertainty and Softmax

_Source slides: 18–19_

## Two Kinds of Uncertainty

**Epistemic / model uncertainty** is lack of knowledge about the true mapping.

**Aleatoric / data uncertainty** is intrinsic, irreducible stochasticity.

## Probabilistic Classification

$$
p(y=c\mid x;\theta)=f_c(x;\theta),
$$

with each output between 0 and 1 and all class outputs summing to 1.

## Softmax

Softmax converts unconstrained real-valued logits into a categorical probability distribution.

$$
\operatorname{softmax}(a)_c=
\frac{e^{a_c}}{\sum_{c'}e^{a_{c'}}}.
$$

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Predictive uncertainty and softmax]].
