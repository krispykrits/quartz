---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# EnjoySport Representation

_Source slide: 5_

## Training Data

| Ex. | Sky | AirTemp | Humidity | Wind | Water | Forecast | EnjoySport |
|---|---|---|---|---|---|---|---|
| 1 | Sunny | Warm | Normal | Strong | Warm | Same | Yes |
| 2 | Sunny | Warm | High | Strong | Warm | Same | Yes |
| 3 | Rainy | Cold | High | Strong | Warm | Change | No |
| 4 | Sunny | Warm | High | Strong | Cool | Change | Yes |

## Hypothesis Representation
A hypothesis is a conjunction of constraints over the six attributes.

Each constraint can be:
- a specific attribute value;
- `?` — any value is acceptable;
- `∅` — no value is acceptable.

Example:

$$
h=\langle Sunny, ?, ?, Strong, ?, Same\rangle
$$

## Extreme Hypotheses

Most general:
$$
\langle ?,?,?,?,?,?\rangle
$$

Most specific:
$$
\langle\emptyset,\emptyset,\emptyset,\emptyset,\emptyset,\emptyset\rangle
$$

> [!warning]
> `?` does not mean “unknown.” It means the hypothesis accepts any value at that attribute. `∅` does not mean missing data; it means the hypothesis accepts no instance.

## Connections
- [[Concepts/General-to-Specific Ordering|General-to-Specific Ordering]]
- [[Algorithms/FIND-S|FIND-S]]
- [[Algorithms/Candidate Elimination|Candidate Elimination]]
- [[Concepts/Inductive Bias|Inductive Bias]]
