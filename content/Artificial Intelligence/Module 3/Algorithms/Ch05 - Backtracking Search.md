# Backtracking Search

**Source:** slides/pages 31–33.

## Purpose
Systematically extend a partial assignment; choose a variable, order its values, check consistency, perform inference, recurse, and undo on failure.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 31–33. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def backtrack(assignment, variables, domains, consistent, select_var, order_values, infer):
    if len(assignment) == len(variables):
        return assignment.copy()
    var = select_var(variables, domains, assignment)
    for value in order_values(var, domains, assignment):
        if consistent(var, value, assignment):
            assignment[var] = value
            snapshot = {v: set(d) for v, d in domains.items()}
            if infer(var, value, domains, assignment):
                result = backtrack(assignment, variables, domains, consistent, select_var, order_values, infer)
                if result is not None:
                    return result
            domains.clear(); domains.update(snapshot)
            del assignment[var]
    return None
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
