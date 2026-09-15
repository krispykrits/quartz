# Uniform-Cost Search

**Source:** page 31

Uniform-cost search (Dijkstra's algorithm in theoretical computer science) expands the node with minimum path cost:

$$f(n)=g(n).$$

It is the appropriate uninformed strategy when action costs differ. The goal test must be late—when the goal is removed from the priority queue—because a cheaper route may still be pending.

## Properties

With positive costs (or costs bounded below by $\epsilon>0$ under the lecture's caveat), UCS is complete and cost-optimal. Its work depends on how many nodes have $g(n)$ no greater than the optimal cost $C^*$, often summarized as exponential in $C^*/\epsilon$.

## Key Update

If a newly generated path reaches a known state more cheaply, replace/update that state's frontier entry.

## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
import heapq
from itertools import count
from math import inf
from typing import Hashable

Graph = dict[Hashable, list[tuple[Hashable, float]]]


def uniform_cost_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
) -> tuple[list[Hashable], float] | None:
    """
    Return a minimum-cost path through a weighted graph.
    """
    tie_breaker = count()
    frontier = [(0.0, next(tie_breaker), start, [start])]
    best_cost = {start: 0.0}

    while frontier:
        path_cost, _, state, path = heapq.heappop(frontier)

        # Ignore an entry replaced by a cheaper path.
        if path_cost > best_cost.get(state, inf):
            continue

        # Late goal test: check when the node is removed.
        if state == goal:
            return path, path_cost

        for successor, step_cost in graph.get(state, []):
            if step_cost < 0:
                raise ValueError("UCS requires nonnegative action costs")

            new_cost = path_cost + step_cost

            if new_cost < best_cost.get(successor, inf):
                best_cost[successor] = new_cost

                heapq.heappush(
                    frontier,
                    (
                        new_cost,
                        next(tie_breaker),
                        successor,
                        path + [successor],
                    ),
                )

    return None


graph = {
    "A": [("B", 2), ("C", 5)],
    "B": [("D", 6), ("C", 1)],
    "C": [("D", 2)],
    "D": [],
}

print(uniform_cost_search(graph, "A", "D"))
# (['A', 'B', 'C', 'D'], 5.0)
```

UCS uses $f(n)=g(n)$. Unlike BFS, it accounts for unequal action costs.

