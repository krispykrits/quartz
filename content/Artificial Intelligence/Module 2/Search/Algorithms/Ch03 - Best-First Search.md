# Best-First Search

**Source:** pages 20-24

## Purpose

General search framework that expands the frontier node with minimum evaluation $f(n)$.

## Inputs and Output

Input: a formal problem and evaluation function $f$. Output: a goal node/solution path or failure.

## Algorithm

1. Create the initial node.
2. Put it in a priority-queue frontier ordered by $f$; record it in `reached`.
3. Pop the lowest-$f$ node.
4. If it is a goal, return it.
5. Expand it.
6. Add an unseen child, or replace a reached state's node when the child has lower path cost.
7. Repeat until success or an empty frontier.

Different $f$ functions produce UCS, greedy best-first, and A*.

## Failure Modes

Wrong duplicate handling can discard a cheaper path. A poor $f$ can sacrifice optimality or completeness. Memory use can dominate.

## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
import heapq
from itertools import count
from math import inf
from typing import Callable, Hashable

Graph = dict[Hashable, list[tuple[Hashable, float]]]


def best_first_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
    evaluation: Callable[[Hashable, float, int], float],
) -> tuple[list[Hashable], float] | None:
    """
    General best-first graph search.

    evaluation(state, path_cost, depth) determines the priority.
    """
    tie_breaker = count()
    frontier = [
        (evaluation(start, 0.0, 0), next(tie_breaker), start, [start], 0.0)
    ]
    best_cost = {start: 0.0}

    while frontier:
        _, _, state, path, path_cost = heapq.heappop(frontier)

        # Ignore stale queue entries.
        if path_cost > best_cost.get(state, inf):
            continue

        if state == goal:
            return path, path_cost

        for successor, step_cost in graph.get(state, []):
            new_cost = path_cost + step_cost
            new_depth = len(path)

            if new_cost < best_cost.get(successor, inf):
                best_cost[successor] = new_cost
                priority = evaluation(successor, new_cost, new_depth)

                heapq.heappush(
                    frontier,
                    (
                        priority,
                        next(tie_breaker),
                        successor,
                        path + [successor],
                        new_cost,
                    ),
                )

    return None


graph = {
    "A": [("B", 2), ("C", 5)],
    "B": [("D", 6), ("C", 1)],
    "C": [("D", 2)],
    "D": [],
}

# Uniform-cost behavior: f(n) = g(n)
result = best_first_search(
    graph,
    start="A",
    goal="D",
    evaluation=lambda state, path_cost, depth: path_cost,
)

print(result)
```

The `evaluation` function determines the search strategy. For example:

- `lambda state, g, depth: depth` approximates breadth-first ordering.
- `lambda state, g, depth: g` produces uniform-cost ordering.
- `lambda state, g, depth: heuristic[state]` produces greedy ordering.
- `lambda state, g, depth: g + heuristic[state]` produces A* ordering.
