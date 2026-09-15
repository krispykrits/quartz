# Greedy Best-First Search

**Source:** pages 40-41

Greedy best-first search expands the node with minimum estimated remaining cost:

$$f(n)=h(n).$$

In Romania, straight-line distance to Bucharest guides the search toward cities that appear geographically close. Greedy search can be fast, but it ignores path cost already paid. It is not generally cost-optimal and can be misled by local heuristic attraction.

Contrast with [[Algorithms/Ch03 - A-Star Search|A* Search]], which balances $g$ and $h$.


## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
import heapq
from itertools import count
from typing import Hashable

Graph = dict[Hashable, list[tuple[Hashable, float]]]


def greedy_best_first_search(
    graph: Graph,
    heuristic: dict[Hashable, float],
    start: Hashable,
    goal: Hashable,
) -> tuple[list[Hashable], float] | None:
    """
    Expand the node with the smallest h(n).

    Path cost is tracked for reporting but does not affect priority.
    """
    tie_breaker = count()
    frontier = [
        (heuristic[start], next(tie_breaker), start, [start], 0.0)
    ]
    reached = {start}

    while frontier:
        _, _, state, path, path_cost = heapq.heappop(frontier)

        if state == goal:
            return path, path_cost

        for successor, step_cost in graph.get(state, []):
            if successor in reached:
                continue

            reached.add(successor)

            heapq.heappush(
                frontier,
                (
                    heuristic[successor],
                    next(tie_breaker),
                    successor,
                    path + [successor],
                    path_cost + step_cost,
                ),
            )

    return None


graph = {
    "Arad": [
        ("Sibiu", 140),
        ("Timisoara", 118),
        ("Zerind", 75),
    ],
    "Sibiu": [
        ("Fagaras", 99),
        ("Rimnicu Vilcea", 80),
    ],
    "Fagaras": [("Bucharest", 211)],
    "Rimnicu Vilcea": [("Pitesti", 97)],
    "Pitesti": [("Bucharest", 101)],
    "Timisoara": [],
    "Zerind": [],
    "Bucharest": [],
}

straight_line_distance = {
    "Arad": 366,
    "Sibiu": 253,
    "Timisoara": 329,
    "Zerind": 374,
    "Fagaras": 176,
    "Rimnicu Vilcea": 193,
    "Pitesti": 100,
    "Bucharest": 0,
}

print(
    greedy_best_first_search(
        graph,
        straight_line_distance,
        "Arad",
        "Bucharest",
    )
)
```

Greedy best-first search uses $f(n)=h(n)$. It may reach a goal quickly, but it ignores the path cost already paid and is not generally cost-optimal.
