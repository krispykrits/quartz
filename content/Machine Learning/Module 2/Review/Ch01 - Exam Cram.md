---
title: "Chapter 1 Exam Cram"
type: review
---

# 🔥 EXAM CRAM

## Tier 1 — MUST KNOW ⭐⭐⭐

- Mitchell: **T + P + E**.
- Supervised: labeled $(x,y)$ pairs.
- Classification: discrete; regression: real-valued.
- Empirical risk = average training loss.
- ERM: $\hat\theta=\arg\min_\theta L(\theta)$.
- Softmax: logits → class probabilities.
- MLE ↔ minimizing NLL.
- MSE = average squared residual.
- Fixed-variance Gaussian MLE ↔ least squares.
- Generalization, population risk, generalization gap.
- Train / validation / test.
- Overfitting and no-free-lunch.
- Unsupervised: clustering, latent factors, self-supervision.
- RL: policy, reward, credit assignment.
- One-hot, BOW, TF-IDF, embeddings, OOV, missingness.

## Tier 2 — VERY IMPORTANT ⭐⭐

- epistemic vs. aleatoric uncertainty;
- decision trees and thresholds;
- polynomial regression and feature engineering;
- PCA/probabilistic PCA;
- held-out NLL for unsupervised models;
- MCAR/MAR/NMAR;
- reward hacking/alignment.

## Equation Flash Review

$$
L(\theta)=\frac1N\sum_n\ell(y_n,f(x_n;\theta))
$$

$$
\hat\theta=\arg\min_\theta L(\theta)
$$

$$
\operatorname{softmax}(a)_c=
\frac{e^{a_c}}{\sum_{c'}e^{a_{c'}}}
$$

$$
NLL(\theta)=-\frac1N\sum_n\log p(y_n\mid f(x_n;\theta))
$$

$$
MSE(\theta)=\frac1N\sum_n(y_n-f(x_n;\theta))^2
$$

$$
L(\theta;p^*)=\mathbb E_{p^*(x,y)}[\ell(y,f(x;\theta))]
$$

$$
IDF_i=\log\frac{N}{1+DF_i}
$$

$$
TFIDF_{ij}=\log(TF_{ij}+1)IDF_i
$$

> [!tip]
> Use [[Mathematics/Ch01 - Mathematics]] when you need the collapsible spoken reading, worked calculation, Python implementation, and interpretation.

## If You Only Remember 10 Things

1. Learning = T/P/E.
2. Probability represents uncertainty.
3. Supervised learning uses labeled pairs.
4. Classification ≠ regression.
5. Training minimizes loss, but future performance is the objective.
6. Softmax turns logits into probabilities.
7. MLE can be implemented by minimizing NLL.
8. Gaussian fixed-variance regression connects NLL and MSE.
9. Complexity can reduce training error while increasing test error.
10. Learning paradigm and data representation determine what signal the model can exploit.

## ⚡ 5-Minute Review

```text
T/P/E → Probability → Supervised
→ Classification / Regression
→ Loss / NLL / MSE
→ ERM / MLE
→ Generalization / Overfitting
→ Train-Val-Test
→ Unsupervised / Self-Supervised
→ RL
→ Representation / Missing Data
```
