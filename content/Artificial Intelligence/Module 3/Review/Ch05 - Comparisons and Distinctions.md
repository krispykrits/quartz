# Chapter 5 Comparisons and Distinctions

| Pair | Distinction |
|---|---|
| Partial vs complete assignment | Partial leaves variables unassigned; complete assigns every variable exactly one value. |
| Consistent vs solution | Consistent violates no applicable constraint; a solution is both complete and consistent. |
| Unary vs binary vs global | Scope size 1, 2, or arbitrary; global constraints can support specialized stronger propagation. |
| Node vs arc vs path consistency | Unary filtering; directed support across one edge; extension of a consistent pair through a third variable. |
| Forward checking vs MAC | FC looks only from the latest assignment to unassigned neighbors; MAC continues arc propagation among affected unassigned variables. |
| MRV vs degree | MRV finds immediate failure risk; degree estimates future impact and breaks MRV ties. |
| MRV vs LCV | MRV chooses a variable fail-first; LCV chooses a value fail-last. |
| Backtracking vs min-conflicts | Partial, systematic, complete search vs complete-state local repair that is generally incomplete. |
| Chronological backtracking vs backjumping | Undo most recent decision vs jump to most recent causally implicated decision. |
| Cutset vs tree decomposition | Condition exponentially on a small cyclic core with low memory vs dynamic programming over bags with exponential dependence on width. |
| Hard CSP vs COP | Satisfy all hard constraints vs optimize a cost among feasible assignments. |

[[Review/Ch05 - Exam Cram|Exam Cram]]
