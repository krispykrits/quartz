# Chapter 5 Active Recall Answers

1. A CSP is $\langle X,D,C\rangle$: variables, their domains, and constraints restricting allowable combinations.
2. Partial leaves some variables unassigned; complete assigns all; consistent violates no applicable constraint; a partial solution is partial+consistent; a solution is complete+consistent.
3. Five neighbors go from 3 choices each to 2: $1-2^5/3^5=1-32/243\approx86.8\%$.
4. $T_1+d_1\le T_2$.
5. Either front axle work finishes before rear starts or rear finishes before front starts, preventing overlap on the shared tool.
6. One variable represents the queen row in each column, so exactly one queen per column is built into the representation.
7. Every $x\in D_i$ must have some $y\in D_j$ satisfying $C_{ij}(x,y)$.
8. Revising $D_i$ against $D_j$ can remove different values than revising $D_j$ against $D_i$; support is directional.
9. With digits 0–9 and Y=X², X keeps {0,1,2,3}; Y keeps {0,1,4,9}.
10. Process directed arcs; REVISE deletes unsupported values; if a domain changes, re-enqueue incoming arcs because previous supports may have vanished.
11. An arc can be reinserted at most d times due to deletions; each REVISE can cost d², across c constraints/arcs: O(cd³).
12. The WA–NT–SA triangle with two colors: each inequality edge is arc-consistent but the triangle is impossible; path consistency empties a relation.
13. k-consistency extends any consistent assignment to k−1 variables to any kth; strong k-consistency means every level 1 through k holds.
14. Global Alldiff can reason about the union of values across many variables; if m variables have only n<m distinct values, failure is immediate.
15. If k cells under Alldiff collectively have exactly k candidate values, those values are reserved for those cells and removed from other cells in the unit.
16. Assignment order is commutative: the same variable/value set is reached regardless of order, so the solver does not branch over n! order permutations.
17. MRV chooses the unassigned variable with the fewest legal values, exposing imminent failure as early as possible.
18. Among MRV ties, choose the variable involved in the most constraints on other unassigned variables.
19. LCV tries the value that eliminates the fewest neighbor values, preserving future flexibility.
20. WA=R removes R from NT/SA; Q=G removes G from NT/SA/NSW; V=B removes B from NSW/SA, emptying SA.
21. FC only prunes neighbors of the latest assignment; MAC continues AC-3-style propagation through affected arcs and can detect multi-step cascades.
22. All inferred deletions caused by a failed decision must be undone; implementations use reversible structures, trails, or persistent domains.
23. SA conflicts with Q, NSW, V; T is irrelevant. Record conf(SA)={Q,NSW,V} and jump to the most recent member V instead of T.
24. A no-good is a forbidden combination of assignments; learning it prevents rediscovering the same contradiction under different irrelevant prefixes.
25. Backtracking uses partial assignments and maintains feasibility; local search uses complete assignments that may violate constraints and repairs one variable at a time.
26. Choose a random conflicted variable, assign a value minimizing conflicts, and break ties randomly; restarts can improve robustness.
27. $h(q)=\sum_{i<j}\mathbf{1}[q_i=q_j\lor|q_i-q_j|=|i-j|]$.
28. Min-conflicts is incomplete; reaching max_steps only says the repair process did not find a solution within that budget.
29. Weights distinguish states with the same raw violation count by making historically troublesome constraints contribute more to the score.
30. An existing schedule is valuable state; repair can restore feasibility while minimizing changed assignments rather than rebuilding from scratch.

[[Active Recall/Ch05 - Active Recall|Active Recall]]
