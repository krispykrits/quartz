---
chapter: 2
course: Machine Learning
source: Mitchell 1997 Chapter 2 lecture
---

# Hypothesis Space and General-to-Specific Ordering

*Source slides: 5--7*

## Definition

The hypothesis space $H$ is the set of candidate hypotheses available to
the learner.

For EnjoySport, each hypothesis is a conjunction of six constraints. A
constraint can be a specific attribute value, `?`, or `∅`.

## General-to-Specific Ordering

$$h_j\ge_g h_k \iff \forall x\in X:\;[(h_k(x)=1)\to(h_j(x)=1)]$$

$h_j$ is at least as general as $h_k$ when every instance accepted by
$h_k$ is also accepted by $h_j$.

## Intuitive Explanation

A more-general rule accepts a larger set of instances. Replacing a
specific constraint with `?` usually moves upward toward greater
generality.

## Why It Matters

The partial order gives search algorithms structure. They can generalize
or specialize hypotheses locally rather than explicitly enumerate all of
$H$.

## EnjoySport Size

The lecture gives: $$5\cdot4\cdot4\cdot4\cdot4\cdot4=5120$$
syntactically distinct hypotheses, but
$$1+(4\cdot3\cdot3\cdot3\cdot3\cdot3)=973$$ semantically distinct
hypotheses after equivalent `∅` hypotheses are merged.

## Connections

-   \[\[Algorithms/FIND-S\]\]
-   \[\[Concepts/Version Space\]\]
-   \[\[Concepts/S and G Boundaries\]\]
-   \[\[Mathematics/Ch02 - Mathematics\]\]
