# AC-3 Arc Consistency

**Source:** slides/pages 19–21.

## Purpose
Enforce arc consistency to a fixed point by repeatedly revising directed arcs and re-enqueuing incoming arcs after domain deletion.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 19–21. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
from collections import deque

def revise(xi, xj, domains, constraint):
    removed = False
    for x in list(domains[xi]):
        if not any(constraint(xi, x, xj, y) for y in domains[xj]):
            domains[xi].remove(x)
            removed = True
    return removed

def ac3(domains, neighbors, constraint, initial_arcs=None):
    queue = deque(initial_arcs or [(x, y) for x in domains for y in neighbors[x]])
    while queue:
        xi, xj = queue.popleft()
        if revise(xi, xj, domains, constraint):
            if not domains[xi]:
                return False
            for xk in neighbors[xi] - {xj}:
                queue.append((xk, xi))
    return True
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
