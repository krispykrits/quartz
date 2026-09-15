# A* Search

**Source:** pages 42-50

A* orders the frontier by

$$f(n)=g(n)+h(n),$$

the estimated total cost of a solution through $n$.

## Cost-Optimality Proof Sketch

Assume A* returns a goal costing $C>C^*$. Some unexpanded node $n$ remains on an optimal path. Admissibility gives $f(n)=g(n)+h(n)\le C^*$. A goal has $h=0$, so the returned goal has $f=C>C^*$. A* would have expanded $n$ first, contradiction.

For graph search, consistency ensures nondecreasing $f$ along paths and supports safe state closure.

## Contours and Efficiency

A* fans out through increasing $f$ contours. It surely expands nodes with $f<C^*$ and may expand some at $f=C^*$ depending on tie-breaking. Under stated conditions it is optimally efficient among algorithms using the same heuristic, yet time and memory may remain exponential.

## Weighted A*

$$f(n)=g(n)+W h(n).$$

$W=1$ is A*; larger $W$ moves toward greedy search. With admissible $h$ and appropriate conditions, weighted A* provides a bounded-suboptimal satisficing solution, trading quality for fewer expansions.


## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
import heapq
from itertools import count
from math import inf
from typing import Hashable

Graph = dict[Hashable, list[tuple[Hashable, float]]]


def a_star_search(
    graph: Graph,
    heuristic: dict[Hashable, float],
    start: Hashable,
    goal: Hashable,
) -> tuple[list[Hashable], float] | None:
    """
    A* graph search using f(n) = g(n) + h(n).
    """
    tie_breaker = count()

    # Each entry contains: f, order, g, state, path.
    frontier = [
        (
            heuristic[start],
            next(tie_breaker),
            0.0,
            start,
            [start],
        )
    ]

    best_g = {start: 0.0}

    while frontier:
        _, _, path_cost, state, path = heapq.heappop(frontier)

        # Ignore an entry superseded by a cheaper path.
        if path_cost > best_g.get(state, inf):
            continue

        # Late goal test.
        if state == goal:
            return path, path_cost

        for successor, step_cost in graph.get(state, []):
            if step_cost < 0:
                raise ValueError("A* requires nonnegative action costs")

            new_g = path_cost + step_cost

            if new_g < best_g.get(successor, inf):
                best_g[successor] = new_g
                new_f = new_g + heuristic[successor]

                heapq.heappush(
                    frontier,
                    (
                        new_f,
                        next(tie_breaker),
                        new_g,
                        successor,
                        path + [successor],
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

result = a_star_search(
    graph,
    straight_line_distance,
    "Arad",
    "Bucharest",
)

print(result)
```

A* uses $f(n)=g(n)+h(n)$. With nonnegative action costs and a consistent heuristic, the first goal removed from the frontier has optimal path cost.


See [[Concepts/Ch03 - Heuristics Admissibility and Consistency|Heuristics, Admissibility, and Consistency]].

