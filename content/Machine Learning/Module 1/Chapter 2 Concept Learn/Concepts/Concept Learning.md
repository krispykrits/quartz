---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Concept Learning

_Source slides: 4-6_

## Definition
Concept learning is **inferring a Boolean-valued function from training examples of its input and output**.

$$
c:X\to\{0,1\}
$$

## Technical Explanation
$X$ is the instance space. The target concept $c$ assigns every instance a positive or negative class. The learner observes selected labeled examples $\langle x,c(x)\rangle$ and chooses a hypothesis $h\in H$ intended to approximate $c$.

## Intuitive Explanation
You see several yes/no examples and try to infer the hidden rule that generated the labels.

## Why It Matters
Concept learning provides a concrete setting for studying representation, search, consistency, generalization, and inductive bias.

## Example
EnjoySport predicts whether a friend enjoys her favorite water sport from six attributes of the day.

## Connections
- [[Concepts/EnjoySport Representation|EnjoySport Representation]]
- [[Concepts/Inductive Learning Hypothesis|Inductive Learning Hypothesis]]
- [[Concepts/General-to-Specific Ordering|General-to-Specific Ordering]]
- [[Concepts/Consistency and Version Spaces|Version Spaces]]

## Exam-Level Understanding
Be able to distinguish $c$, $h$, $X$, $H$, and the observed training examples.
