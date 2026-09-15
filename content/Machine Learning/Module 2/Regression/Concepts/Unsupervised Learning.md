---
title: "Unsupervised Learning"
tags: [machine-learning, chapter-01]
type: concept
---


# Unsupervised Learning

_Source slides: 35–41_

## Definition

Training data contains only inputs:

$$
\mathcal D_{\text{train}}=\{x_n\}_{n=1}^{N}.
$$

The lecture contrasts modeling $p(x)$ with supervised modeling of $p(y\mid x)$.

## Motivations

- labels can be expensive;
- human categories can be arbitrary;
- predicting all high-dimensional inputs may force richer representations.

## Clustering

K-means with $K=3$ is shown on unlabeled Iris data. The lecture emphasizes that there is not necessarily one uniquely correct number of clusters.

## Other Topics

- [[Latent Factors and PCA]]
- [[Self-Supervised Learning]]

## Evaluation

The lecture gives two strategies:

1. held-out NLL for density models;
2. downstream supervised-task performance.

## Mathematics

See [[Mathematics/Ch01 Mathematics#Unsupervised learning and latent variables]].
