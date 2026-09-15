# Forward Checking

**Source:** slides/pages 37–38.

## Purpose
After assigning X=x, delete inconsistent values from every unassigned neighbor and fail immediately if a neighbor domain becomes empty.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 37–38. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def forward_check(var, value, domains, neighbors, assignment, allowed):
    for y in neighbors[var]:
        if y in assignment:
            continue
        domains[y] = {vy for vy in domains[y] if allowed(var, value, y, vy)}
        if not domains[y]:
            return False
    return True
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
