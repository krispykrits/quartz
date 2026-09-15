---
title: "Chapter 1 Concept Map"
type: review
---

# 🧩 How Everything Fits Together

```text
[[Concepts/Machine Learning and Probabilistic Perspective]]
                    ↓
       [[Concepts/Supervised Learning]]
        ↙                       ↘
[[Concepts/Classification]] [[Concepts/Regression]]
        ↓                       ↓
[[Concepts/Predictive Uncertainty and Softmax]]
        ↘                       ↙
       Loss / Likelihood / MSE
                    ↓
[[Concepts/Empirical Risk Minimization]]
                    ↓
[[Concepts/Maximum Likelihood Estimation]]
                    ↓
[[Concepts/Generalization and Overfitting]]
                    ↓
         Train / Validation / Test
```

```text
[[Concepts/Unsupervised Learning]]
       ↙             ↓              ↘
 Clustering [[Concepts/Latent Factors and PCA]]
              [[Concepts/Self-Supervised Learning]]
```

```text
[[Concepts/Reinforcement Learning]]
State → Policy → Action → Environment → Reward
```

```text
[[Concepts/Data Representation and Missing Data]]
One-hot → BOW → TF-IDF → Embeddings → OOV/Subwords
                              ↓
                       Missingness assumptions
```

## Mathematical Spine

```text
Loss
 ↓
Empirical Risk
 ↓
arg min
 ↓
Fitted Parameters
 ↓
Population Risk
 ↓
Generalization Gap
```

See [[Ch01 Mathematics]].
