# Tree CSP Solver

**Source:** slides/pages 50–51.

## Purpose
Root a tree constraint graph, make parent domains arc-consistent with children in a backward pass, then assign supported values root-to-leaf without backtracking.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 50–51. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def tree_csp_solver(order, parent, domains, allowed):
    # Backward directional arc-consistency pass
    for child in reversed(order[1:]):
        p = parent[child]
        domains[p] = {x for x in domains[p]
                      if any(allowed(p, x, child, y) for y in domains[child])}
        if not domains[p]:
            return None
    # Forward assignment pass
    assignment = {order[0]: next(iter(domains[order[0]]))}
    for child in order[1:]:
        p = parent[child]
        assignment[child] = next(y for y in domains[child]
                                 if allowed(p, assignment[p], child, y))
    return assignment
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
