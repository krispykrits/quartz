---
title: "Self-Supervised Learning"
tags: [machine-learning, chapter-01]
type: concept
---


# Self-Supervised Learning

_Source slide: 40_

## Definition

Self-supervised learning creates proxy supervised tasks from unlabeled data.

Examples in the lecture:

- predict color from grayscale;
- predict masked words from surrounding context.

Generic form:

$$
\hat x_1=f(x_2;\theta).
$$

## Why It Matters

Useful features can be learned without manually labeled latent factors and then transferred to downstream supervised tasks.

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Self-supervised prediction]].
