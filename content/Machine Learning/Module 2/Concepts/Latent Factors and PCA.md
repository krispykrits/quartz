---
title: "Latent Factors and PCA"
tags: [machine-learning, chapter-01]
type: concept
---


# Latent Factors and PCA

_Source slides: 38–39_

## Latent-Factor Idea

High-dimensional observations may arise from lower-dimensional hidden factors:

$$
z_n\rightarrow x_n.
$$

Factor analysis uses:

$$
p(x_n\mid z_n;\theta)=
\mathcal N(x_n\mid Wz_n+\mu,\Sigma).
$$

Unlike regression, $z_n$ is not observed.

## Probabilistic PCA

The special case

$$
\Sigma=\sigma^2I
$$

gives probabilistic PCA.

Slide 39 visualizes PCA as a two-dimensional linear subspace through three-dimensional Iris data.

## Nonlinear Extension

Replacing $Wz+\mu$ with a DNN $f(z;\theta)$ produces a nonlinear latent manifold and leads toward variational autoencoders.

## Mathematics

See [[Mathematics/Ch01 - Mathematics#Unsupervised learning and latent variables]].
