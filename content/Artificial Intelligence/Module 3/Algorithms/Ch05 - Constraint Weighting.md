# Constraint Weighting

**Source:** slides/pages 47.

## Purpose
Score violated constraints with weights; repeatedly troublesome constraints receive larger weights and therefore greater influence on local repair.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 47. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def weighted_score(state, constraints, weights):
    return sum(weights[i] for i, c in enumerate(constraints) if not c(state))

def increase_violated_weights(state, constraints, weights):
    for i, c in enumerate(constraints):
        if not c(state):
            weights[i] += 1
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
