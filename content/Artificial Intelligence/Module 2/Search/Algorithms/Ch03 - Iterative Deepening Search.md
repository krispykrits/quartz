# Iterative Deepening Search

**Source:** pages 35-37

Run depth-limited search with $\ell=0,1,2,\ldots$ until it returns a solution or genuine failure rather than cutoff.

Repeated upper-level work is inexpensive because most nodes in an exponential tree lie at the deepest level.

## Properties

- Complete on finite acyclic spaces.
- Optimal for equal action costs.
- Time: $O(b^d)$ with a solution; $O(b^m)$ when none exists.
- Space: $O(bd)$ with a solution.

It combines BFS's shallowest-solution behavior with DFS-like memory use.


## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
from enum import Enum, auto
from typing import Hashable

Graph = dict[Hashable, list[Hashable]]


class SearchStatus(Enum):
    FAILURE = auto()
    CUTOFF = auto()


def depth_limited_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
    limit: int,
) -> list[Hashable] | SearchStatus:

    def visit(
        state: Hashable,
        path: list[Hashable],
        remaining_depth: int,
    ) -> list[Hashable] | SearchStatus:
        if state == goal:
            return path

        if remaining_depth == 0:
            return SearchStatus.CUTOFF

        cutoff_occurred = False

        for successor in graph.get(state, []):
            if successor in path:
                continue

            result = visit(
                successor,
                path + [successor],
                remaining_depth - 1,
            )

            if result is SearchStatus.CUTOFF:
                cutoff_occurred = True
            elif result is not SearchStatus.FAILURE:
                return result

        return (
            SearchStatus.CUTOFF
            if cutoff_occurred
            else SearchStatus.FAILURE
        )

    return visit(start, [start], limit)


def iterative_deepening_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
) -> list[Hashable] | None:
    """
    Try depth limits 0, 1, 2, ... until a solution is found
    or depth-limited search returns genuine failure.
    """
    depth = 0

    while True:
        result = depth_limited_search(
            graph,
            start,
            goal,
            limit=depth,
        )

        if isinstance(result, list):
            return result

        if result is SearchStatus.FAILURE:
            return None

        depth += 1


graph = {
    "A": ["B", "C"],
    "B": ["D", "E"],
    "C": ["F"],
    "D": [],
    "E": ["G"],
    "F": [],
    "G": [],
}

print(iterative_deepening_search(graph, "A", "G"))
```

Iterative deepening obtains BFS-like shallowest-solution behavior while retaining depth-first search's modest memory use.
