---
title: "Classification"
tags: [machine-learning, chapter-01]
type: concept
---


# Classification

_Source slides: 8–21_

## Definition

Classification predicts one of $C$ unordered, mutually exclusive categories.

$$
\mathcal Y=\{1,\ldots,C\}.
$$

Binary classification uses $C=2$, often encoded as $\{0,1\}$ or $\{-1,+1\}$.

## Iris

The lecture uses three Iris species and four numerical features. The pair plot demonstrates that class separability depends strongly on the selected features.

## Decision Rules

A simple rule predicts Setosa when petal length is below 2.45. Recursively applying feature-threshold splits creates a decision tree.

## Probabilistic Classification

Instead of returning only a hard label, a model may represent:

$$
p(y=c\mid x;\theta).
$$

See [[Predictive Uncertainty and Softmax]].

## Mathematics

See [[Mathematics/Ch01 Mathematics#Classification, decision rules, and loss]].
