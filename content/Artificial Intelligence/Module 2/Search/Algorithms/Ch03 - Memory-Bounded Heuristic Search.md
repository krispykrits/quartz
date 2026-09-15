# Memory-Bounded Heuristic Search

**Source:** pages 50-54

## IDA*

Iterative-deepening A* uses an $f$-cost threshold instead of a depth limit. Each iteration performs depth-first exploration and sets the next threshold to the smallest exceeded $f$. It uses little memory but revisits states.

## RBFS

Recursive best-first search maintains the best alternative $f$ value (`f_limit`). It follows the best successor, backs up revised $f$ values, and unwinds when the current choice exceeds the best alternative. Space is linear, but regenerated subtrees can increase time.

## MA* and SMA*

Memory-bounded A* variants use all available memory. When full, SMA* forgets the worst leaf while backing up its value to the parent, allowing regeneration if it later becomes promising. It is complete when memory can hold the shallowest solution path and optimal when memory can hold the necessary frontier.

## Tradeoff

These methods exchange repeated computation for bounded memory; they address A*'s storage bottleneck rather than changing the underlying heuristic objective.

## Python Implementations

> [!example]
> **Illustrative Python Example - Not From Lecture**

### Iterative-Deepening A*

```python
from math import inf
from typing import Hashable

Graph = dict[Hashable, list[tuple[Hashable, float]]]


def ida_star_search(
    graph: Graph,
    heuristic: dict[Hashable, float],
    start: Hashable,
    goal: Hashable,
) -> tuple[list[Hashable], float] | None:
    """
    Iterative-deepening A* using an f-cost threshold.
    """
    threshold = heuristic[start]
    path = [start]

    def search(
        path_cost: float,
        current_threshold: float,
    ) -> tuple[list[Hashable], float] | float:
        state = path[-1]
        f_value = path_cost + heuristic[state]

        if f_value > current_threshold:
            return f_value

        if state == goal:
            return path.copy(), path_cost

        smallest_excess = inf

        for successor, step_cost in graph.get(state, []):
            if successor in path:
                continue

            path.append(successor)

            result = search(
                path_cost + step_cost,
                current_threshold,
            )

            if isinstance(result, tuple):
                return result

            smallest_excess = min(smallest_excess, result)
            path.pop()

        return smallest_excess

    while True:
        result = search(0.0, threshold)

        if isinstance(result, tuple):
            return result

        if result == inf:
            return None

        # Use the smallest f-value that exceeded the old threshold.
        threshold = result


graph = {
    "A": [("B", 2), ("C", 5)],
    "B": [("D", 4), ("E", 6)],
    "C": [("F", 2)],
    "D": [("G", 5)],
    "E": [("G", 2)],
    "F": [("G", 2)],
    "G": [],
}

heuristic = {
    "A": 6,
    "B": 5,
    "C": 3,
    "D": 4,
    "E": 2,
    "F": 1,
    "G": 0,
}

print(ida_star_search(graph, heuristic, "A", "G"))
```

### Recursive Best-First Search

```python
from __future__ import annotations

from dataclasses import dataclass


@dataclass
class RBFSNode:
    state: Hashable
    parent: RBFSNode | None
    path_cost: float
    f_value: float

    def build_path(self) -> list[Hashable]:
        path = []
        node: RBFSNode | None = self

        while node is not None:
            path.append(node.state)
            node = node.parent

        return list(reversed(path))


def recursive_best_first_search(
    graph: Graph,
    heuristic: dict[Hashable, float],
    start: Hashable,
    goal: Hashable,
) -> tuple[list[Hashable], float] | None:
    """
    Recursive best-first search with a changing f-limit.
    """

    def rbfs(
        node: RBFSNode,
        f_limit: float,
        current_path: set[Hashable],
    ) -> tuple[RBFSNode | None, float]:
        if node.state == goal:
            return node, node.f_value

        successors = []

        for successor, step_cost in graph.get(node.state, []):
            if successor in current_path:
                continue

            new_g = node.path_cost + step_cost

            # Preserve backed-up information from the parent.
            new_f = max(
                new_g + heuristic[successor],
                node.f_value,
            )

            successors.append(
                RBFSNode(
                    state=successor,
                    parent=node,
                    path_cost=new_g,
                    f_value=new_f,
                )
            )

        if not successors:
            return None, inf

        while True:
            successors.sort(key=lambda child: child.f_value)
            best = successors[0]

            if best.f_value > f_limit:
                return None, best.f_value

            alternative = (
                successors[1].f_value
                if len(successors) > 1
                else inf
            )

            current_path.add(best.state)

            result, revised_f = rbfs(
                best,
                min(f_limit, alternative),
                current_path,
            )

            current_path.remove(best.state)
            best.f_value = revised_f

            if result is not None:
                return result, result.f_value

    initial = RBFSNode(
        state=start,
        parent=None,
        path_cost=0.0,
        f_value=heuristic[start],
    )

    result, _ = rbfs(
        initial,
        inf,
        {start},
    )

    if result is None:
        return None

    return result.build_path(), result.path_cost


print(
    recursive_best_first_search(
        graph,
        heuristic,
        "A",
        "G",
    )
)
```

IDA* repeatedly performs depth-first searches with increasing $f$ thresholds. RBFS retains the best alternative $f$-value and backtracks when the current path exceeds that alternative. Both reduce memory usage compared with ordinary A*, but they may regenerate previously explored states.

