---
title: "Maximum Likelihood Estimation"
tags: [machine-learning, chapter-01]
type: concept
---


# Maximum Likelihood Estimation

_Source slides: 21, 24_

## Core Idea

A good probabilistic model assigns high probability to what actually occurred.

Negative log probability is used as a loss:

$$
\ell(y,f(x;\theta))=-\log p(y\mid f(x;\theta)).
$$

Across a dataset this produces NLL, and maximum-likelihood estimation can be expressed as minimizing NLL.

## Gaussian Regression Connection

For fixed Gaussian variance:

$$
NLL(\theta)=\frac{1}{2\sigma^2}MSE(\theta)+\text{const}.
$$

Therefore Gaussian MLE and least squares choose the same minimizing parameters.

## Mathematics

See [[Ch01 Mathematics#Negative log-likelihood and maximum likelihood]] and [[Ch01 Mathematics#Regression, Gaussian likelihood, and polynomial models]].
