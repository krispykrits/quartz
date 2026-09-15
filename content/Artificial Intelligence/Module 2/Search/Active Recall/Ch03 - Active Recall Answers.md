# Active Recall Answers

1. Computationally simulating action sequences/paths until reaching a goal or establishing failure.
2. Episodic, single-agent, fully observable, deterministic, static, discrete, and known environments with atomic states.
3. Goal formulation, problem formulation, search, execution.
4. State space/initial state, goal states or test, actions, transition model, and action-cost function.
5. A path is an action sequence; a solution reaches a goal; an optimal solution has least path cost.
6. It suppresses irrelevant detail so search is tractable while retaining what makes a plan valid and implementable.
7. $n2^n$.
8. The state space contains problem states and transitions; the search tree contains generated paths and may repeat states.
9. State, parent, action, and path cost.
10. Reached but not yet expanded nodes.
11. A record of states already generated, typically with their best known node/path.
12. Remember all reached states; check cycles only on the current path; prohibit immediate reversals.
13. Completeness, cost-optimality, time complexity, and space complexity.
14. Branching factor, shallowest solution depth, and maximum search depth.
15. $f(n)=\operatorname{depth}(n)$.
16. With equal costs, the first generated goal is at the shallowest and therefore cheapest depth; further siblings are unnecessary.
17. $f(n)=g(n)$.
18. A generated goal may be expensive; popping it establishes that no cheaper frontier path remains.
19. Time $O(b^m)$ and space $O(bm)$ for the lecture's tree-like DFS characterization.
20. Solution, failure, or cutoff.
21. Most nodes in an exponential tree are on the deepest level, so repeated upper-level generation is a small fraction of total work.
22. $2b^{d/2}$ can be exponentially smaller than $b^d$.
23. $h(n)$ estimates the cheapest cost from $n$ to a goal, with $h=0$ at a goal.
24. Greedy uses $f=h$; A* uses $f=g+h$.
25. $0\le h(n)\le h^*(n)$: it never overestimates true remaining cost.
26. $h(n)\le c(n,a,n')+h(n')$; therefore $f=g+h$ is nondecreasing along a path.
27. All nodes reachable on paths whose nodes have $f<C^*$; it may also expand some with $f=C^*$.
28. The branching factor of a uniform tree that would generate the observed number of nodes at the solution depth; smaller means better guidance.
29. Relaxed problems, maxima of admissible heuristics, pattern databases, landmarks/differential heuristics, shortcuts, or learning from experience (any five).
30. Their abstract solutions may use the same moves, so addition double-counts cost unless patterns/costs are disjointly partitioned.

Return to [[Active Recall/Ch03 - Active Recall|Active Recall]].

