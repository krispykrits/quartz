# Bidirectional Search

**Source:** pages 38-39, 55

Search forward from the initial state and backward from the goal until the frontiers intersect. Its motivation is

$$b^{d/2}+b^{d/2}\ll b^d.$$

It requires a way to generate predecessors and an efficient intersection test. It is most attractive when a specific goal is known and reverse actions are practical.

Bidirectional heuristic search is subtler than simply running two A* searches: optimality/efficiency reasoning must evaluate pairs of frontier nodes, not each frontier independently.

## Python Implementation

> [!example]
> **Illustrative Python Example - Not From Lecture**

```python
from collections import deque
from typing import Hashable

Graph = dict[Hashable, list[Hashable]]


def reverse_graph(graph: Graph) -> Graph:
    reversed_graph = {state: [] for state in graph}

    for state, successors in graph.items():
        for successor in successors:
            reversed_graph.setdefault(successor, []).append(state)

    return reversed_graph


def reconstruct_path(
    meeting_state: Hashable,
    forward_parent: dict[Hashable, Hashable | None],
    backward_parent: dict[Hashable, Hashable | None],
) -> list[Hashable]:
    forward_path = []
    state = meeting_state

    while state is not None:
        forward_path.append(state)
        state = forward_parent[state]

    forward_path.reverse()

    backward_path = []
    state = backward_parent[meeting_state]

    while state is not None:
        backward_path.append(state)
        state = backward_parent[state]

    return forward_path + backward_path


def bidirectional_search(
    graph: Graph,
    start: Hashable,
    goal: Hashable,
) -> list[Hashable] | None:
    """
    Bidirectional BFS for an unweighted directed graph.
    """
    if start == goal:
        return [start]

    backward_graph = reverse_graph(graph)

    forward_frontier = deque([start])
    backward_frontier = deque([goal])

    forward_parent = {start: None}
    backward_parent = {goal: None}

    while forward_frontier and backward_frontier:
        # Expand whichever frontier currently contains fewer nodes.
        if len(forward_frontier) <= len(backward_frontier):
            current = forward_frontier.popleft()

            for successor in graph.get(current, []):
                if successor in forward_parent:
                    continue

                forward_parent[successor] = current

                if successor in backward_parent:
                    return reconstruct_path(
                        successor,
                        forward_parent,
                        backward_parent,
                    )

                forward_frontier.append(successor)
        else:
            current = backward_frontier.popleft()

            for predecessor in backward_graph.get(current, []):
                if predecessor in backward_parent:
                    continue

                backward_parent[predecessor] = current

                if predecessor in forward_parent:
                    return reconstruct_path(
                        predecessor,
                        forward_parent,
                        backward_parent,
                    )

                backward_frontier.append(predecessor)

    return None


graph = {
    "A": ["B", "C"],
    "B": ["D"],
    "C": ["E"],
    "D": ["F"],
    "E": ["F"],
    "F": ["G"],
    "G": [],
}

print(bidirectional_search(graph, "A", "G"))
```

This implementation requires a specific goal and the ability to generate predecessor states by reversing the graph.

