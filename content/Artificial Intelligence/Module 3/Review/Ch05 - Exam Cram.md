# Chapter 5 Exam Cram

## Tier 1 — MUST KNOW ⭐⭐⭐
- $\langle X,D,C\rangle$, assignment, consistency, solution.
- Arc consistency support condition and AC-3 queue/re-enqueue logic; $O(cd^3)$.
- Backtracking skeleton; MRV, degree, LCV.
- Forward checking vs MAC.
- Min-conflicts and its incompleteness.
- Tree CSP two-pass solver and $O(nd^2)$.

## Tier 2 — VERY IMPORTANT ⭐⭐
- Node/path/k-consistency and why stronger consistency costs more.
- `Alldiff`, Hall-set/naked-triple reasoning, bounds propagation.
- Conflict sets, backjumping, no-goods.
- Components, cutsets, tree decomposition, tree width.

## Tier 3 — SUPPORTING ⭐
- Domain-type solver implications, COP vs CSP, symmetry breaking, constraint weighting, online repair.

## Equation Cheat Sheet
- Arc support: $\forall x\in D_i\exists y\in D_j:C_{ij}(x,y)$
- AC-3: $O(cd^3)$
- MRV: $\arg\min |D_i^{legal}|$
- Degree: $\arg\max deg_{unassigned}(X_i)$
- Tree CSP: $O(nd^2)$
- Cutset: $O(d^c(n-c)d^2)$
- Tree width: $O(nd^{w+1})$

## Algorithm Cheat Sheet
AC-3 = revise → delete unsupported → re-enqueue affected incoming arcs.  
Backtracking = select variable → order values → check → infer → recurse → undo.  
Min-conflicts = complete state → choose conflicted variable → minimum-conflict value → repeat.  
Tree solver = backward arc consistency → forward supported assignment.

## Common Confusions
Arc consistency is directional. Path consistency is stronger than edge-wise arc consistency. Forward checking is not MAC. Min-conflicts failure is not proof of unsatisfiability. Tree width is largest bag size minus one.

## If You Only Remember 10 Things
1. CSP = variables + domains + constraints.
2. Solution = complete + consistent.
3. Propagation removes unsupported choices.
4. AC-3 revisits arcs because support can disappear.
5. MRV fail-first; LCV fail-last.
6. Degree breaks MRV ties by future impact.
7. MAC propagates farther than forward checking.
8. No-goods remember contradictions.
9. Min-conflicts repairs complete assignments but is incomplete.
10. Graph structure can turn exponential search into polynomial/linear solving.

## 5-Minute Pre-Exam Review
Trace one AC-3 deletion cascade; explain one MRV/degree/LCV choice; compare FC and MAC; state min-conflicts; derive tree $O(nd^2)$; explain cutset c and tree width w.
