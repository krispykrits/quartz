# Search Trees, Frontier, and Reached

**Source:** pages 17-24

The **state space** is the problem graph. A **search tree** is built over it: every tree node represents a path from the initial state, so the same state may occur in multiple nodes.

## Node Record

- `State`
- `Parent`
- `Action`
- `Path-Cost`

Following parent links reconstructs the solution path.

## Frontier and Reached

- **Reached:** states for which at least one node has been generated.
- **Frontier:** reached nodes not yet expanded.
- **Expanded:** removed from the frontier and used to generate successors.

The frontier separates explored from unexplored regions: any route from an expanded state to an unreached state crosses it.

## Redundant Paths

Cycles can make the search tree infinite even when the state graph is finite. The lecture gives three responses:

1. remember all reached states and keep the best path;
2. avoid only cycles on the current path;
3. avoid immediate reverse actions (“no U-turn”).

The right choice depends on redundancy and memory.

See [[Algorithms/Ch03 - Best-First Search|Best-First Search]].

