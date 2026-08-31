---
title: "Regression"
tags: [machine-learning, chapter-01]
type: concept
---


# Regression

_Source slides: 22–27_

## Definition

Regression predicts a real-valued output:

$$
y\in\mathbb R.
$$

Examples in the lecture include toxicity level and plant height.

## Residuals and MSE

A residual is the difference between observed and predicted output. Squared loss penalizes the residual's magnitude, and MSE averages squared residuals over the dataset.

## Gaussian Interpretation

The lecture models the output as Gaussian around the regression prediction. With fixed variance, minimizing Gaussian NLL is equivalent to minimizing MSE.

## Linear and Polynomial Regression

Linear regression uses an affine weighted sum. Polynomial regression first transforms the input into polynomial features and remains linear in its parameters.

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Regression, Gaussian likelihood, and polynomial models]].
