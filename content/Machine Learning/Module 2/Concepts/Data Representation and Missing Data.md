---
title: "Data Representation and Missing Data"
tags: [machine-learning, chapter-01]
type: concept
---


# Data Representation and Missing Data

_Source slides: 47–55_

## Datasets

The lecture surveys MNIST, EMNIST, Fashion-MNIST, CIFAR-10/100, ImageNet, IMDB sentiment, WMT translation, sequence-to-sequence tasks, and language modeling.

## Categorical Data

One-hot encoding converts a $K$-valued category into an indicator vector. Feature crosses add interaction effects.

## Text

Bag-of-words counts vocabulary terms but discards order.

TF-IDF balances within-document frequency with corpus rarity.

Embeddings map sparse one-hot vectors into learned dense representations.

## OOV

A basic approach maps unknown words to `UNK`. The lecture presents subword units/wordpieces using byte-pair encoding as a better method because they exploit internal word structure.

## Missing Data

- **MCAR:** missingness independent of the data.
- **MAR:** missingness depends on observed values.
- **NMAR:** missingness depends on the missing values themselves.

The lecture states that the book assumes MAR.

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Data representation, text, and missingness]].
