---
title: "Empirical Risk Minimization"
tags: [machine-learning, chapter-01]
type: concept
---


# Empirical Risk Minimization

_Source slides: 16–17_

## Core Idea

Empirical risk is average loss on observed training examples:

$$
L(\theta)=\frac1N\sum_n\ell(y_n,f(x_n;\theta)).
$$

Training chooses:

$$
\hat\theta=\arg\min_\theta L(\theta).
$$

> [!important]
> `arg min` returns the parameter value that produces the minimum—not the minimum loss itself.

## Limitation

A model can achieve low empirical risk and still perform poorly on unseen data. ERM therefore leads directly to [[Generalization and Overfitting]].

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Classification, decision rules, and loss]].
