---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# FIND-S

_Source slides: 9-10_

## Purpose
Find a maximally specific hypothesis consistent with the positive training examples.

## Algorithm
1. Initialize $h$ to the most specific hypothesis in $H$.
2. For each positive training instance:
   - inspect every attribute constraint;
   - if the constraint is satisfied, do nothing;
   - otherwise replace it with the next more-general constraint satisfied by the instance.
3. Ignore negative examples.
4. Output $h$.

## EnjoySport Trace

| Step | Hypothesis |
|---|---|
| $h_0$ | $\langle∅,∅,∅,∅,∅,∅\rangle$ |
| after $x_1$ (Yes) | $\langle Sunny,Warm,Normal,Strong,Warm,Same\rangle$ |
| after $x_2$ (Yes) | $\langle Sunny,Warm,?,Strong,Warm,Same\rangle$ |
| $x_3$ (No) | ignored |
| after $x_4$ (Yes) | $\langle Sunny,Warm,?,Strong,?,?\rangle$ |

## Why the Hypothesis Changes
- $x_1$: every `∅` is replaced by the observed positive values.
- $x_2$: Humidity differs, so Humidity becomes `?`.
- $x_3$: ignored because it is negative.
- $x_4$: Water and Forecast differ from the current specific values, so each becomes `?`.

## Questions Raised by the Lecture

> [!question]
> Has FIND-S converged to the target concept even though it never checks negative examples?

The slide leaves this unresolved at this point. Later version-space material shows that multiple consistent hypotheses can remain.

> [!question]
> Why prefer the maximally specific hypothesis? Are there other hypotheses equally consistent?

Yes. FIND-S does not display those alternatives.

> [!question]
> What if the training data is inconsistent or noisy?

The lecture raises this as an unresolved problem for FIND-S.

> [!question]
> What if there are several maximally specific consistent hypotheses?

FIND-S does not represent multiple alternatives, motivating version-space methods.

## Strengths
- Simple.
- Avoids enumerating all of $H$.
- Generalizes only when positive evidence forces a change.

## Limitations
- Ignores negative examples.
- Hides alternative consistent hypotheses.
- Does not address noisy/inconsistent data in the lecture.

## Python Example

> [!example]
> Illustrative Python Example - Not From Lecture

```python
EMPTY = "∅"
ANY = "?"

def find_s(examples):
    h = [EMPTY] * 6
    for x, label in examples:
        if label != "Yes":
            continue
        for i, value in enumerate(x):
            if h[i] == EMPTY:
                h[i] = value
            elif h[i] != value:
                h[i] = ANY
    return tuple(h)

examples = [
    (("Sunny","Warm","Normal","Strong","Warm","Same"), "Yes"),
    (("Sunny","Warm","High","Strong","Warm","Same"), "Yes"),
    (("Rainy","Cold","High","Strong","Warm","Change"), "No"),
    (("Sunny","Warm","High","Strong","Cool","Change"), "Yes"),
]

print(find_s(examples))
# ('Sunny', 'Warm', '?', 'Strong', '?', '?')
```

## Exam-Level Understanding
Be able to trace the algorithm and explain why the negative example cannot change the current hypothesis.
