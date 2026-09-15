---
title: Least Mean Squares
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: algorithm
source: Mitchell 1997 Chapter 1 lecture
---
# Least Mean Squares (LMS)
_Source slide: 16_
## Purpose
Adjust the linear evaluator's weights so predictions better match generated training values.
## Inputs
Training pair $\langle b,V_{train}(b)\rangle$, current weights, features $x_0\ldots x_6$, and small learning rate $\eta$.
## Output
Updated weights and therefore an updated hypothesis $\hat V$.
## Steps
1. For each training example, compute current $\hat V(b)$.
2. For $i=0$ through 6, update $w_i\leftarrow w_i+\eta(V_{train}(b)-\hat V(b))x_i$.
3. Continue over training examples.
## Intuition
Underprediction causes an upward nudge proportional to feature contribution; overprediction reverses the direction.
## Parameters
$\eta$: small learning rate; $x_0\equiv1$.
## Mathematical Treatment
See [[Ch01 Mathematics#LMS weight update]] and [[Ch01 Mathematics#Squared-error objective]].
## Limitations / Conditions
The lecture specifically uses LMS with the chosen linear representation; the representation itself limits what functions can be expressed.
## Exam-Level Understanding
Be able to perform one update by hand and explain the sign and magnitude of the change.
