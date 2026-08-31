---
chapter: 2
course: Machine Learning
source: Mitchell 1997 Chapter 2 lecture
---

# Version Space

*Source slides: 12--13*

## Definition

A hypothesis $h$ is consistent with training set $D$ iff it classifies
every training example correctly.

$$VS_{H,D}\equiv\{h\in H\mid Consistent(h,D)\}$$

## Technical Explanation

The version space is not one chosen model. It is the **entire subset of
H** that the observed data has not yet ruled out.

## Intuitive Explanation

Imagine crossing candidate rules off a list whenever a new labeled
example disproves them. The rules left standing form the version space.

## Why It Matters

It makes uncertainty explicit: multiple hypotheses may explain exactly
the same observed data.

## Limitation of Naive Enumeration

List-Then-Eliminate is correct but requires enumerating $H$, which the
lecture notes is intractable except for very small spaces.

## Compact Representation

See \[\[Concepts/S and G Boundaries\]\] and \[\[Algorithms/Candidate
Elimination\]\].

## Exam-Level Understanding

Do not confuse "consistent with the training set" with "known to be the
true target concept." Consistency only means the current data has not
eliminated the hypothesis.
