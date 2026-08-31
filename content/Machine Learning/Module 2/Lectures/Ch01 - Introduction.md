---
title: "Chapter 1 - Introduction"
tags: [machine-learning, probabilistic-ml, lecture, chapter-01]
type: lecture
source: "Murphy PML Chapter 1 lecture slides"
---

# Chapter 1 — Introduction

_Source slides: 1–61_

## 🎯 Big Picture

The lecture defines machine learning through Tom Mitchell's **task (T), performance (P), and experience (E)** formulation, then adopts a probabilistic perspective in which unknown quantities are represented using probability distributions. This gives the chapter a common language for prediction, uncertainty, model fitting, and decision-making.

The main technical development is [[Concepts/Supervised Learning|supervised learning]]. The lecture moves from [[Concepts/Classification|classification]] and [[Concepts/Regression|regression]] into loss functions, [[Concepts/Empirical Risk Minimization|empirical risk minimization]], [[Concepts/Maximum Likelihood Estimation|maximum likelihood]], probabilistic prediction, and [[Concepts/Generalization and Overfitting|generalization]]. The central warning is that excellent training performance does not guarantee good future performance.

The lecture then introduces [[Concepts/Unsupervised Learning|unsupervised learning]], clustering, [[Concepts/Latent Factors and PCA|latent factors and PCA]], [[Concepts/Self-Supervised Learning|self-supervised learning]], and [[Concepts/Reinforcement Learning|reinforcement learning]]. It concludes with practical representations for images, text, categorical variables, and missing data, then places ML within neighboring fields and discusses reward hacking, alignment, and augmented intelligence.

## Lecture Roadmap

```text
What is ML? — Task + Performance + Experience
                    ↓
          Probabilistic viewpoint
                    ↓
             Supervised Learning
             ↙               ↘
      Classification       Regression
             ↓               ↓
      Probabilities        MSE / Gaussian
             ↘               ↙
          Loss / Likelihood
                    ↓
             Model Fitting
                    ↓
          Generalization
                    ↓
       Train / Validation / Test
                    ↓
            No Free Lunch
                    ↓
           Unsupervised Learning
        ↙             ↓             ↘
  Clustering    Latent Factors   Self-Supervision
                    ↓
          Reinforcement Learning
                    ↓
       Data Representation / Missingness
                    ↓
      Alignment & Augmented Intelligence
```

## What I Should Know After This Lecture

- Explain Mitchell's T/P/E definition.
- Explain why the lecture uses probability.
- Distinguish supervised, unsupervised, and reinforcement learning.
- Distinguish classification and regression.
- Explain design matrices, decision rules, and decision trees.
- Calculate and interpret misclassification rate, empirical risk, softmax, NLL, MSE, IDF, and TF-IDF.
- Explain Gaussian likelihood and its connection to least squares.
- Distinguish epistemic and aleatoric uncertainty.
- Explain population risk, generalization gap, underfitting, and overfitting.
- Explain train/validation/test roles and no-free-lunch.
- Explain clustering, latent factors, probabilistic PCA, and self-supervision.
- Explain RL policies and credit assignment.
- Explain one-hot encoding, feature crosses, bag-of-words, TF-IDF, embeddings, OOV handling, and MCAR/MAR/NMAR.

## ⏱️ 60-Second Lecture Summary

Machine learning uses experience to improve measured performance on a task. Supervised learning uses labeled input-output pairs; classification predicts discrete classes and regression predicts real values. Training is usually expressed as minimizing a loss, but the real goal is low expected loss on future data.

The probabilistic viewpoint represents uncertainty explicitly. Softmax converts classification logits to probabilities; likelihood-based fitting leads to negative log-likelihood; and a fixed-variance Gaussian regression model connects maximum likelihood to least squares and MSE.

Unsupervised learning uses input-only data to discover or model structure through methods such as clustering and latent-factor models. Self-supervised learning manufactures proxy prediction tasks from unlabeled data. Reinforcement learning learns a state-to-action policy from reward. Throughout all paradigms, data representation and assumptions strongly influence what can be learned.

## 1. What Is Machine Learning?

_Source slides: 3–5_

See [[Concepts/Machine Learning and Probabilistic Perspective]].

Tom Mitchell's definition says that a program learns from **experience E**, with respect to a **task T** and **performance measure P**, if its performance at T, as measured by P, improves with E.

The lecture's probabilistic stance treats unknown quantities—including future values and model parameters—as random variables with probability distributions.

## 2. Supervised Learning

_Source slides: 6–33_

See [[Concepts/Supervised Learning]].

The learner receives input-output pairs and learns a mapping from an input space to an output space. The two primary cases introduced are [[Concepts/Classification]] and [[Concepts/Regression]].

### Iris Example

Slides 9–15 use Iris as the running classification example. Four numerical measurements describe flowers from three species. The pair plot shows Setosa as comparatively easy to separate, while Versicolor and Virginica overlap more.

The decision-tree slides demonstrate how feature-threshold rules recursively divide the feature space into prediction regions.

## 3. Loss, Probability, and Model Fitting

_Source slides: 16–27_

See:

- [[Concepts/Empirical Risk Minimization]]
- [[Concepts/Predictive Uncertainty and Softmax]]
- [[Concepts/Maximum Likelihood Estimation]]

The lecture first introduces misclassification rate and then generalizes it to arbitrary loss functions. Fitting is expressed as minimizing empirical risk.

Probabilistic classification represents uncertainty with class probabilities. Softmax converts unconstrained logits into a valid probability distribution.

Negative log probability becomes a loss, leading to negative log-likelihood and maximum-likelihood estimation.

For regression, squared loss and MSE measure residual error. Modeling targets with a fixed-variance Gaussian distribution makes NLL proportional to MSE plus a constant, producing the important equivalence between Gaussian MLE and least squares.

## 4. Polynomial Regression, DNNs, and Generalization

_Source slides: 27–33_

Polynomial regression applies a feature transformation and remains linear in its parameters. As degree increases toward the number of training observations minus one, training error can approach zero.

Slide 29 demonstrates the danger: training MSE keeps decreasing as polynomial degree rises, but test MSE eventually increases. This motivates [[Concepts/Generalization and Overfitting]].

Deep neural networks extend feature transformation by learning the representation itself through recursively composed functions.

## 5. Unsupervised Learning

_Source slides: 34–41_

See [[Concepts/Unsupervised Learning]].

The learner receives inputs without targets. The lecture describes clustering, latent-factor modeling, PCA, nonlinear latent models, and [[Concepts/Self-Supervised Learning|self-supervised learning]].

Slide 37 shows K-means with $K=3$ on Iris. Slide 39 visualizes PCA as a lower-dimensional linear subspace through higher-dimensional observations.

## 6. Reinforcement Learning

_Source slides: 42–45_

See [[Concepts/Reinforcement Learning]].

An agent learns a policy mapping states to actions from interaction and reward. Because rewards may be delayed, the learner faces the credit-assignment problem.

Slide 44 uses Yann LeCun's cake analogy: unsupervised/predictive learning provides the bulk of learning, supervised learning is the icing, and RL is the cherry.

## 7. Data and Representation

_Source slides: 46–55_

See [[Concepts/Data Representation and Missing Data]].

The lecture surveys common image and text datasets, then introduces categorical encoding, feature crosses, bag-of-words, TF-IDF, embeddings, OOV handling with subwords, and missing-data mechanisms.

## 8. Broader Context

_Source slides: 56–60_

The lecture relates ML to predictive analytics, data mining, data science, statistics, and AI.

It also discusses reward hacking: optimizing a specified reward can exploit gaps between the stated objective and the true intended preference. This is framed as an alignment problem.

Inverse reinforcement learning attempts to infer reward from human behavior.

The lecture finally contrasts AGI-style autonomy with augmented intelligence, where AI functions as a smart tool while a human remains involved.

## Final Synthesis

```text
Experience / Data
       ↓
Representation
       ↓
Model
       ↓
Loss / Likelihood
       ↓
Parameter Fitting
       ↓
Training Performance
       ↓
Generalization
       ↓
Future Decisions
```

> [!important] Central lesson
> Successful learning is not the same as memorizing the training data. The objective is useful performance on future data.

## Continue Studying

- [[Mathematics/Ch01 - Mathematics]]
- [[Review/Ch01 - Concept Map]]
- [[Review/Ch01 - Exam Cram]]
- [[Active Recall/Ch01 - Active Recall]]
