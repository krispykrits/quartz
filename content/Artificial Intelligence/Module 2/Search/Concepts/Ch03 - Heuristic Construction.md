# Heuristic Construction

**Source:** pages 56-66

## Classic 8-Puzzle Heuristics

- $h_1$: number of misplaced tiles.
- $h_2$: sum of Manhattan distances.

Both are admissible; $h_2$ dominates $h_1$ because it is never smaller and is often closer to the true remaining cost.

## Sources of Better Heuristics

- **Relaxed problems:** remove action restrictions; the relaxed optimum is a lower bound.
- **Maximum of admissible heuristics:** preserves admissibility and keeps the strongest estimate per state.
- **Pattern databases:** precompute exact costs for selected subproblems.
- **Disjoint pattern databases:** costs may be added only when move costs are partitioned so they cannot be counted twice.
- **Landmarks/differential heuristics:** precompute distances to selected landmarks and derive lower bounds by the triangle inequality.
- **Shortcuts:** insert precomputed optimal macro-edges.
- **Learning from experience:** learn approximate cost-to-go from solved examples, while managing possible overestimation.

> [!question]
> **Professor Question (page 62):** Can we just add two pattern-database heuristics instead of maxing?

No, not in general: their solutions may share moves, so naïve addition double-counts cost. Disjoint patterns with appropriate cost accounting make addition valid.

## Metalevel Search

The agent can reason about which computational action—such as expanding a node—has value. This turns search control itself into a decision problem.

