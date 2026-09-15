# Why and How

## Why formulate a goal before a problem?

The goal limits which objectives and actions matter; problem formulation can then abstract the relevant world.

## Why can a finite graph create an infinite search tree?

Different paths—and repeated cycles—create distinct nodes representing the same states indefinitely.

## How does `reached` improve search?

It detects repeated states and retains the cheapest known path, preventing redundant expansion at a memory cost.

## Why is BFS optimal only for equal action costs?

Depth orders number of actions, not accumulated cost. With unequal costs, a deeper path may be cheaper.

## Why does UCS use a late goal test?

A generated goal may have an expensive path while a cheaper route is still in the frontier. Popping it proves no lower-$g$ candidate remains.

## Why does iterative deepening repeat work efficiently?

Exponential trees contain most nodes at the deepest level; regenerating the relatively few upper nodes adds modest overhead.

## How does consistency make $f$ monotone?

Because $g(n')=g(n)+c$ and $h(n)\le c+h(n')$, then $g(n)+h(n)\le g(n')+h(n')$.

## Why can A* still be impractical?

Even excellent guarantees allow exponentially many nodes, and A* retains a large frontier plus reached table.

## Why does a relaxed problem yield an admissible heuristic?

Removing restrictions cannot make the cheapest solution more expensive, so the relaxed optimum is a lower bound.

## Why use `max` rather than add admissible heuristics?

The maximum remains a lower bound. A sum may double-count the same required moves.

## How do pattern databases help?

They move computation offline: exact abstract-subproblem costs are precomputed and retrieved during search.

## How does weighted A* trade quality for speed?

Increasing $W$ emphasizes $h$, steering more directly toward the goal while weakening exact optimality.

