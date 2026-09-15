# Conflict-Directed Backjumping

**Source:** slides/pages 40–41.

## Purpose
Use conflict sets to jump to the most recent decision actually implicated in failure, then merge downstream conflict causes into that variable.

## Inputs and Outputs
Inputs are the relevant CSP variables/domains/constraints or search state. Output is a reduced CSP, a solution/failure result, or an updated search state as appropriate.

## Lecture Procedure
The steps here follow the lecture's algorithmic description on slides 40–41. See [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] for the source-order explanation and examples.

## Intuition
Exploit explicit constraint structure so unsupported values, bad decisions, or redundant search regions are eliminated before exhaustive enumeration.

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
def merge_conflict(conf, failed_var, jump_var):
    # Illustrates the lecture update: conf(Xi) <- conf(Xi) U (conf(Xj) - {Xi})
    conf[jump_var] |= (conf[failed_var] - {jump_var})
    return conf[jump_var]

def most_recent_conflict(conflict_set, order_index):
    return max(conflict_set, key=lambda v: order_index[v])
```

## Strengths and Limitations
Use the lecture's method-selection guidance: stronger inference generally costs more per search node but can shrink the tree; local repair can be fast but is incomplete; structural algorithms are especially powerful when the graph has favorable structure.

## Exam-Level Understanding
Be able to state the update rule, trace the lecture example, explain why the algorithm prunes or repairs, and give the complexity result when the lecture supplies one.
