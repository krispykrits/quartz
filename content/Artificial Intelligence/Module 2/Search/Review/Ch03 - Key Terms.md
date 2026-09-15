# Key Terms

| Term | Exam-ready definition |
|---|---|
| Problem-solving agent | Agent that searches action sequences to reach a goal. |
| State space | Set of possible environment states. |
| Initial state | State from which search begins. |
| Goal test | Predicate determining whether a state is a goal. |
| Transition model | `Result(s,a)`, the successor produced by action $a$. |
| Action cost | Numeric cost $c(s,a,s')$ of a transition. |
| Path | Sequence of actions. |
| Solution | Path from initial state to a goal. |
| Optimal solution | Solution with minimum path cost. |
| Abstraction | Model that suppresses irrelevant detail while retaining needed structure. |
| Search node | Record containing state, parent, action, and path cost. |
| Frontier | Reached but unexpanded nodes. |
| Reached | States for which a node has been generated. |
| Branching factor $b$ | Number of successors per node, usually an upper/average characterization. |
| Solution depth $d$ | Depth of the shallowest solution. |
| Maximum depth $m$ | Deepest path in the search space. |
| Completeness | Guarantee of finding an existing solution and reporting failure otherwise. |
| Cost-optimality | Guarantee of returning a least-cost solution. |
| Heuristic $h(n)$ | Estimate of cheapest remaining cost from $n$ to a goal. |
| Admissible | Never overestimates true remaining cost. |
| Consistent | $h(n)\le c(n,a,n')+h(n')$ for every successor. |
| Dominance | $h_2$ dominates $h_1$ if $h_2(n)\ge h_1(n)$ everywhere while both remain admissible. |
| Relaxed problem | Problem with fewer action restrictions; its optimum can lower-bound the original. |
| Pattern database | Table of exact costs for abstracted subproblems. |
| Landmark | Selected state with precomputed distances used for bounds. |
| Effective branching factor | Uniform-tree branching factor producing the observed node count at depth $d$. |
| Satisficing | Seeking a good-enough rather than provably optimal solution. |

