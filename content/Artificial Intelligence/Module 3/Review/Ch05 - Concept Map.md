# Chapter 5 Concept Map

```text
CSP <X,D,C>
  ├─ representation → variables / domains / constraints / assignments
  ├─ propagation
  │   ├─ node consistency
  │   ├─ arc consistency → AC-3 → O(cd^3)
  │   ├─ path / k-consistency
  │   └─ global constraints → Alldiff / bounds / Hall sets
  ├─ systematic search
  │   ├─ backtracking
  │   ├─ MRV + degree + LCV
  │   ├─ forward checking / MAC
  │   └─ conflicts → backjumping → no-goods
  ├─ local repair
  │   ├─ min-conflicts
  │   └─ constraint weighting / restarts / plateau remedies
  └─ graph structure
      ├─ components
      ├─ trees → O(nd^2)
      ├─ cutset conditioning → O(d^c(n-c)d^2)
      └─ tree decomposition → width w → O(nd^(w+1))
```

The lecture's final synthesis is: **model → propagate support → branch strategically → analyze/learn or repair → exploit graph decomposition**.

[[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]] · [[Mathematics/Ch05 - Mathematics|Mathematics]]
