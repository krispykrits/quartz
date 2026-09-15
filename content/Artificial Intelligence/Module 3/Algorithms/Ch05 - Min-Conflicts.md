# Min-Conflicts

**Source:** slides/pages 43–46.

## Purpose
Start from a complete assignment; repeatedly choose a conflicted variable and move it to a minimum-conflict value, breaking ties randomly.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 43–46. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
import random

def min_conflicts(variables, domains, conflicts, max_steps=10000):
    current = {v: random.choice(tuple(domains[v])) for v in variables}
    for _ in range(max_steps):
        bad = [v for v in variables if conflicts(v, current[v], current) > 0]
        if not bad:
            return current
        var = random.choice(bad)
        scores = [(conflicts(var, val, current), val) for val in domains[var]]
        best = min(s for s, _ in scores)
        current[var] = random.choice([val for s, val in scores if s == best])
    return None
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
