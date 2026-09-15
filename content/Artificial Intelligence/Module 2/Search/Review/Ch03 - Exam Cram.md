# Exam Cram

## Tier 1 — MUST KNOW ⭐⭐⭐

- Five problem components and the four-phase agent process.
- State space vs. search tree; state vs. node; frontier vs. reached.
- $f$: BFS = depth, UCS = $g$, greedy = $h$, A* = $g+h$.
- Completeness, cost-optimality, time, and space.
- Admissibility vs. consistency and A*'s proof idea.
- BFS/UCS/DFS/iterative-deepening tradeoffs.

## Tier 2 — VERY IMPORTANT ⭐⭐

- Early vs. late goal tests.
- Search contours and $C^*$.
- Weighted A*, IDA*, RBFS, SMA*.
- Dominance, relaxed problems, pattern databases.
- Effective branching factor.

## Tier 3 — SUPPORTING ⭐

- Bidirectional prerequisites.
- Landmarks, differential heuristics, shortcuts.
- Metalevel and learned search control.
- Historical context.

## Equation Cheat Sheet

$$g(n)=\sum c_i,\quad f_{A*}=g+h,\quad h\le h^*,\quad h(n)\le c+h(n')$$

$$N+1=1+b^*+\cdots+(b^*)^d,\quad f_{WA*}=g+Wh$$

## Algorithm Cheat Sheet

FIFO → BFS · min-$g$ heap → UCS · stack → DFS · increasing $\ell$ → ID · min-$h$ → greedy · min-$(g+h)$ → A*.

## Common Confusions

- A node is a path record, not merely a state.
- Cheapest does not mean shallowest unless costs are equal.
- Admissible does not automatically mean consistent.
- Optimal efficiency does not mean polynomial time.
- Two admissible heuristics cannot always be added.

## If You Only Remember 10 Things

1. Search plans before action.
2. Formulation determines what search can see.
3. Trees contain paths; graphs contain states.
4. Frontier ordering defines the strategy.
5. Reached tables trade memory for duplicate control.
6. BFS is for equal costs; UCS for unequal costs.
7. DFS saves memory but loses guarantees.
8. A* combines paid and estimated cost.
9. Consistency makes $f$ nondecreasing.
10. Better heuristics reduce effective branching factor.

## 5-Minute Pre-Exam Review

Write the four $f$ functions, state the two heuristic inequalities, reproduce the algorithm comparison table from memory, explain late goal testing, then explain relaxation → admissible heuristic → smaller $b^*$.

