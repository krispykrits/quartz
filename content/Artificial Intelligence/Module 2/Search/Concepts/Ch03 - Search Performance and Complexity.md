# Search Performance and Complexity

**Source:** pages 25-26, 30-39, 46-47, 57-58

## Evaluation Criteria

- **Completeness:** finds a solution when one exists and reports failure otherwise.
- **Cost-optimality:** returns a least-cost solution.
- **Time complexity:** number of generated/expanded nodes.
- **Space complexity:** maximum nodes retained.

For explicit graphs, complexity may be expressed using $|V|+|E|$. For implicitly generated spaces, use branching factor $b$, shallowest solution depth $d$, and maximum depth $m$.

The effective branching factor $b^*$ summarizes observed heuristic-search effort. Smaller $b^*$ means the heuristic has reduced the search tree more effectively.

## Important Warning

A* can be complete, cost-optimal, and optimally efficient among comparable algorithms while still expanding exponentially many nodes. “Optimal efficiency” is not the same as “fast in absolute terms.”

See [[Mathematics/Ch03 - Mathematics|Mathematics]] and [[Review/Ch03 - Comparisons and Distinctions|Comparisons]].

