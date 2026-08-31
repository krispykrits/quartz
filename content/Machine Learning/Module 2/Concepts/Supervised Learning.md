---
title: "Supervised Learning"
tags: [machine-learning, chapter-01]
type: concept
---


# Supervised Learning

_Source slides: 7–33_

## Definition

Learn a mapping from inputs to outputs using labeled examples.

$$
f:\mathcal X\rightarrow\mathcal Y
$$

The training set contains pairs:

$$
\mathcal D_{\text{train}}=\{(x_n,y_n)\}_{n=1}^{N}.
$$

The complete read/notation/example/Python treatment is in [[Mathematics/Ch01 - Mathematics#Supervised mapping and training set]].

## Terminology

- $x$ — feature, covariate, predictor.
- $y$ — label, target, response.
- $N$ — number of examples.
- $D$ — number of features.

## Main Tasks

- [[Classification]] — discrete output.
- [[Regression]] — real-valued output.

## Why It Matters

The remainder of the supervised section builds on this structure: define a prediction model, define a loss or probability model, fit parameters, and test whether the learned relationship generalizes.
