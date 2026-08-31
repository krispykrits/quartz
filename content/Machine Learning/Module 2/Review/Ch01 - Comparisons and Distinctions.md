---
title: "Chapter 1 Comparisons and Distinctions"
type: review
---

# Comparisons and Distinctions

| Feature | Supervised | Unsupervised | Reinforcement Learning |
|---|---|---|---|
| Signal | $(x,y)$ pairs | $x$ only | reward from interaction |
| Main object | mapping / $p(y\mid x)$ | structure / $p(x)$ | policy $a=\pi(x)$ |
| Examples | classification, regression | clustering, latent factors | game/robot control |
| Central issue | generalization | useful structure/evaluation | credit assignment |

## Classification vs. Regression

| Classification | Regression |
|---|---|
| Discrete output | Real-valued output |
| Iris species | Toxicity / plant height |
| zero-one/NLL examples | squared loss/MSE |
| categorical probabilities | Gaussian output model |

## Epistemic vs. Aleatoric

| Epistemic | Aleatoric |
|---|---|
| model uncertainty | data uncertainty |
| lack of knowledge | intrinsic stochasticity |
| knowledge-related | described as irreducible |

## Empirical vs. Population Risk

| Empirical | Population |
|---|---|
| observed training average | expectation under true $p^*$ |
| directly computable | unknown directly |
| used for fitting | true future objective |

## Train vs. Validation vs. Test

| Split | Purpose |
|---|---|
| Train | fit parameters |
| Validation | model selection |
| Test | final unbiased estimate |

## MCAR vs. MAR vs. NMAR

| Type | Missingness depends on |
|---|---|
| MCAR | nothing in data |
| MAR | observed information |
| NMAR | missing values themselves |

> [!important]
> The lecture states that the book assumes MAR.
