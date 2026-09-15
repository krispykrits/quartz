# Depth-First and Depth-Limited Search

**Source:** pages 32-34

## Depth-First Search

DFS expands the deepest node first, usually with a LIFO stack. Tree-like DFS stores only the current path plus unexpanded siblings.

- Time: $O(b^m)$.
- Space: $O(bm)$.
- Not generally complete in infinite-depth or cyclic spaces.
- Not cost-optimal.

Backtracking search reduces memory further by generating one successor at a time and remembering which successor comes next.

## Depth-Limited Search

Treat nodes at depth $\ell$ as leaves. It returns three possible outcomes: solution, failure, or cutoff.

- Time: $O(b^\ell)$.
- Space: $O(b\ell)$.

A limit that is too small misses solutions; a large limit revives DFS's weaknesses.

## Python Implementations

> [!example]
> **Illustrative Python Example - Not From Lecture**

### Depth-First Search

```python
from typing import Hashable

Graph = dict[Hashable, list[Hashable]]


def depth_first_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
) -> list[Hashable] | None:
    """
    Iterative depth-first graph search.
    """
    frontier = [(start, [start])]
    reached = set()

    while frontier:
        state, path = frontier.pop()

        if state == goal:
            return path

        if state in reached:
            continue

        reached.add(state)

        # Reversing preserves the graph's displayed successor order.
        for successor in reversed(graph.get(state, [])):
            if successor not in reached:
                frontier.append((successor, path + [successor]))

    return None
```

### Depth-Limited Search

```python
from enum import Enum, auto


class SearchStatus(Enum):
    FAILURE = auto()
    CUTOFF = auto()


def depth_limited_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
    limit: int,
) -> list[Hashable] | SearchStatus:
    """
    Return a solution, FAILURE, or CUTOFF.
    """

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
            # Prevent cycles along the current path.
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

        if cutoff_occurred:
            return SearchStatus.CUTOFF

        return SearchStatus.FAILURE

    if limit < 0:
        raise ValueError("The depth limit must be nonnegative")

    return visit(start, [start], limit)


graph = {
    "A": ["B", "C"],
    "B": ["D", "E"],
    "C": ["F"],
    "D": [],
    "E": ["G"],
    "F": [],
    "G": [],
}

print(depth_first_search(graph, "A", "G"))
print(depth_limited_search(graph, "A", "G", limit=2))
print(depth_limited_search(graph, "A", "G", limit=3))
```

A cutoff means the depth limit prevented the search from determining whether a solution exists below the current boundary. It is different from failure.



