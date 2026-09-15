# Chapter 5 Practice Questions

1. Define a CSP as a triple and explain each component.
2. Distinguish partial assignment, complete assignment, consistent assignment, partial solution, and solution.
3. Why does assigning SA=blue prune about 86.8% of the five-neighbor joint choices in the lecture example?
4. Encode a precedence relation for a task T1 of duration d1 before T2.
5. What does the shared-tool scheduling disjunction express?
6. How does the 8-queens CSP avoid same-column constraints by construction?
7. Define arc consistency using the idea of support.
8. Why are (Xi,Xj) and (Xj,Xi) distinct arcs?
9. Trace the lecture Y=X^2 revision in both directions.
10. State AC-3 and explain why incoming arcs are re-enqueued.
11. Derive the lecture's O(cd^3) AC-3 bound.
12. Give an example of a CSP that is arc-consistent but not path-consistent from the lecture.
13. Define k-consistency and strong k-consistency.
14. Why can a global Alldiff constraint detect failure missed by pairwise inequalities?
15. Explain Sudoku naked triples as Hall-set reasoning.
16. Why does commutativity reduce the standard CSP search leaves from n!d^n to d^n?
17. Define MRV and explain fail-first.
18. Define the degree heuristic and when it is used.
19. Define LCV and explain fail-last.
20. Trace forward checking for WA=R, Q=G, V=B in the lecture table.
21. Compare forward checking and MAC.
22. What rollback requirement does inference create in backtracking implementations?
23. Explain the lecture backjumping example involving Q, NSW, V, T, and SA.
24. What is a no-good and why does learning it help?
25. Compare backtracking and local search state representations.
26. State min-conflicts and explain tie handling.
27. Write the 8-queens attacking-pair objective h(q).
28. Why does a min-conflicts step limit not prove unsatisfiability?
29. What does constraint weighting change about a plateau?
30. Why is local repair natural for an online CSP such as airline scheduling?
31. How do disconnected components change complexity?
32. Explain the two passes of TREE-CSP-SOLVER.
33. Derive O(nd^2) for a tree CSP.
34. What is a cycle cutset and what is its complexity dependence on c?
35. State the three validity conditions for a tree decomposition.
36. Define tree width and state the O(nd^(w+1)) dependence.
37. What is the time-space distinction between cutset conditioning and tree decomposition noted in the lecture?
38. What must a symmetry-breaking constraint preserve?
39. Solve the slide 58 integration exercise using MRV and propagation.
40. Match a large repair CSP, a tree CSP, and a small-tree-width CSP to the lecture's recommended starting methods.
