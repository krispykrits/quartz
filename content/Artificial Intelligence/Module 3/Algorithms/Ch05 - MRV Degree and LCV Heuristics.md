# MRV Degree and LCV Heuristics

**Source:** slides/pages 34–36.

## Purpose
Choose variables by minimum remaining values, break ties by largest unassigned degree, and order values by least constraining effect.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 34–36. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def select_mrv_degree(unassigned, domains, neighbors):
    m = min(len(domains[v]) for v in unassigned)
    tied = [v for v in unassigned if len(domains[v]) == m]
    return max(tied, key=lambda v: sum(n in unassigned for n in neighbors[v]))

def order_lcv(var, domains, neighbors, allowed):
    def eliminations(value):
        return sum(1 for n in neighbors[var] for y in domains[n]
                   if not allowed(var, value, n, y))
    return sorted(domains[var], key=eliminations)
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
