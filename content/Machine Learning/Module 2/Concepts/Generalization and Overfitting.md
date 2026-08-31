---
title: "Generalization and Overfitting"
tags: [machine-learning, chapter-01]
type: concept
---


# Generalization and Overfitting

_Source slides: 28–33_

## Generalization

Generalization means performing well on future/unseen data.

## Overfitting

Overfitting occurs when training risk is low but future/population risk is substantially worse.

## Lecture Figure

Slide 29 compares degree-2, degree-14, and degree-20 polynomial fits to 21 observations. Training MSE decreases with complexity, but test MSE eventually rises.

```text
Too simple → underfitting
Appropriate complexity → best generalization
Too flexible → overfitting
```

## Train / Validation / Test

- **Train:** fit parameters.
- **Validation:** choose model or complexity.
- **Test:** final unbiased performance estimate.

## No Free Lunch

No model is universally best. Success depends on whether its inductive bias matches the problem.

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Generalization and population risk]].
