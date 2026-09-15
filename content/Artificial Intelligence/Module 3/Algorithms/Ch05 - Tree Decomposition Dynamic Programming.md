# Tree Decomposition Dynamic Programming

**Source:** slides/pages 54–55.

## Purpose
Represent the CSP as a tree of overlapping bags; each bag acts as a meta-variable over internally consistent tuples, with neighboring bags agreeing on shared variables.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 54–55. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def compatible(tuple_a, tuple_b, shared):
    return all(tuple_a[v] == tuple_b[v] for v in shared)

def filter_child_support(parent_tuples, child_tuples, shared):
    # One message-passing step over a tree decomposition.
    return [p for p in parent_tuples
            if any(compatible(p, c, shared) for c in child_tuples)]
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
