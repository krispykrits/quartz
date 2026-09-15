# Breadth-First Search

**Source:** pages 28-30

BFS expands the shallowest frontier node first. For unit action costs, it is best-first search with $f(n)=\operatorname{depth}(n)$.

## Procedure

Use a FIFO queue and a reached set. Test the initial state, then test each child when generated. This early goal test avoids inserting unnecessary siblings after a goal child.

## Properties

- Complete for finite branching factor.
- Cost-optimal when every action has the same cost.
- Time: $O(b^d)$.
- Space: $O(b^d)$; this is its chief practical weakness.

## Common Confusion

BFS is not cost-optimal with unequal step costs; use [[Algorithms/Ch03 - Uniform-Cost Search|Uniform-Cost Search]].

## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
from collections import deque
from typing import Hashable

Graph = dict[Hashable, list[Hashable]]


def breadth_first_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
) -> list[Hashable] | None:
    """
    Return a shallowest path through an unweighted graph.
    """
    if start == goal:
        return [start]

    frontier = deque([(start, [start])])
    reached = {start}

    while frontier:
        state, path = frontier.popleft()

        for successor in graph.get(state, []):
            if successor in reached:
                continue

            new_path = path + [successor]

            # Early goal test: check when the child is generated.
            if successor == goal:
                return new_path

            reached.add(successor)
            frontier.append((successor, new_path))

    return None


graph = {
    "A": ["B", "C"],
    "B": ["D", "E"],
    "C": ["F"],
    "D": [],
    "E": ["G"],
    "F": ["G"],
    "G": [],
}

print(breadth_first_search(graph, "A", "G"))
```

BFS uses a FIFO queue. It is complete for a finite branching factor and cost-optimal when all actions have equal cost.

