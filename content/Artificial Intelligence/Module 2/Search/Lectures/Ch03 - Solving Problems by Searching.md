# Solving Problems by Searching

**Source:** pages 1-70  
**Text:** *Artificial Intelligence: A Modern Approach*, 4th ed., Chapter 3 lecture notes  
**Topic:** Uninformed and informed search strategies

## Big Picture

When an action is not immediately obvious, a problem-solving agent models the world and searches through possible action sequences before acting. Algorithm behavior depends on how the frontier is ordered, how repeated states are handled, and whether domain knowledge supplies an estimate of remaining cost.

## Roadmap

1. Problem-solving agents
2. Example problems
3. Search algorithms
4. Uninformed strategies
5. Informed (heuristic) search
6. Heuristic functions

## Learning Objectives

- Formulate a search problem using its five components.
- Distinguish state spaces, search trees, paths, nodes, frontier, and reached.
- Trace and evaluate uninformed and informed search algorithms.
- Explain completeness, cost-optimality, time, and space.
- Use $g$, $h$, and $f$ correctly and explain admissibility and consistency.
- Explain where useful heuristics come from.

## 60-Second Summary

Search transforms goal-directed behavior into graph exploration. Best-first search provides the general framework; BFS, UCS, greedy search, and A* differ mainly in their evaluation function. DFS, iterative deepening, bidirectional, and memory-bounded variants navigate time-space tradeoffs. A* is cost-optimal with the required heuristic conditions but may still require exponential time and memory. Strong heuristics arise from relaxations, dominance/max combinations, pattern databases, landmarks, shortcuts, or learned experience.

## 1. From Percepts to Plans (pages 3-5)

The chapter studies atomic problem solving in episodic, single-agent, fully observable, deterministic, static, discrete, known environments. Informed algorithms estimate distance to a goal; uninformed ones do not.

The Romania example begins at Arad with a flight from Bucharest. Random choice is unavoidable without world knowledge; with a map, the agent can formulate, search, then execute. The four phases are goal formulation, problem formulation, search, and execution. Fixed plans can be executed open-loop only under the simplifying assumptions; uncertain worlds favor closed-loop monitoring.

See [[Concepts/Ch03 - Problem Formulation and Abstraction|Problem Formulation and Abstraction]].

## 2. Formal Problems and Examples (pages 6-16)

The Romania road map is a weighted graph. A problem contains a state space, initial state, goal state(s)/test, available actions, transition model, and action costs. The slides state “five components” while grouping state space with initial state. Paths are action sequences; solutions reach goals; optimal solutions minimize additive path cost. Costs are positive, with bounded runs of zero-cost actions as a technical caveat.

Abstraction must remove irrelevant detail while preserving valid and implementable actions. Standardized examples include grid/vacuum worlds, the 8-puzzle, and Knuth's infinite puzzle. Real-world examples include route/touring, VLSI layout, robot navigation, assembly sequencing, and protein design.

### Diagram: Romania Road Map (page 6)

Cities are vertices; roads are bidirectional action pairs; labels are mile costs. The diagram demonstrates that geometric appearance and accumulated road cost are different pieces of information. On an exam, identify a path as a sequence of edges and compute its cost by summing labels.

### Diagram: 8-Puzzle (page 13)

Tiles and the blank form a state. Actions slide a neighboring tile into the blank; the goal specifies a target arrangement. The figure illustrates a compact state description with a large reachable state space.

## 3. Search Trees and the General Algorithm (pages 17-24)

A search algorithm overlays a tree of paths on the state-space graph. Multiple nodes may represent the same state. The frontier holds reached but unexpanded nodes; `reached` tracks generated states; expanded nodes lie behind the frontier.

Best-first search uses a priority queue ordered by $f$. `Expand` creates a child with successor state, parent, generating action, and accumulated path cost. Duplicate paths and cycles require deliberate handling: full reached tables, cycle checks on the current path, or only no-U-turn pruning.

### Diagram: Search Tree Growth (page 18)

Arad is the root; Sibiu, Timisoara, and Zerind are first-level children. Expanding children can regenerate Arad, showing why a finite map induces an infinite tree if cycles are unrestricted.

### Diagram: Separation Property (page 19)

The frontier forms a boundary between explored and unexplored space. Every path from expanded to unreached states must cross a frontier node.

See [[Concepts/Ch03 - Search Trees Frontier and Reached|Search Trees, Frontier, and Reached]] and [[Algorithms/Ch03 - Best-First Search|Best-First Search]].

## 4. Measuring Search (pages 25-26)

The four criteria are completeness, cost-optimality, time complexity, and space complexity. Explicit graphs use $|V|+|E|$; implicit trees use branching factor $b$, shallowest goal depth $d$, and maximum depth $m$.

## 5. Uninformed Search (pages 27-39)

Uninformed algorithms know the problem definition but have no estimate of goal proximity.

- **BFS:** shallowest first; $f=\text{depth}$; FIFO; early goal test; complete and optimal for equal costs; $O(b^d)$ time and space.
- **UCS:** cheapest accumulated path first; $f=g$; late goal test; complete/cost-optimal under positive-cost conditions.
- **DFS:** deepest first; LIFO; low memory, but neither generally complete nor optimal.
- **Backtracking:** DFS generating one successor at a time.
- **Depth-limited:** DFS with limit $\ell$, distinguishing cutoff from failure.
- **Iterative deepening:** tries increasing limits; BFS-like result with DFS-like space.
- **Bidirectional:** forward and backward search aiming for roughly $b^{d/2}$ work in each direction.

The comparison table on page 39 should be understood conditionally: guarantees depend on finite branching, positive/equal costs, finite acyclic spaces, and whether backward search is applicable.

See the dedicated algorithm notes and [[Review/Ch03 - Comparisons and Distinctions|Comparisons]].

## 6. Informed Search (pages 40-55)

A heuristic $h(n)$ estimates cheapest remaining cost and equals zero at a goal. Romania uses straight-line distance to Bucharest.

Greedy best-first uses $f=h$ and may quickly approach a goal while ignoring cost already paid. A* uses $f=g+h$. With admissibility, A*'s tree-search optimality follows from a contradiction argument. Consistency imposes a triangle inequality and makes $f$ nondecreasing along paths, supporting graph-search optimality.

### Diagram: Search Contours (page 45)

Contours group nodes by $f=g+h$, like topographic elevation bands. A* expands outward in nondecreasing $f$, rather than physical distance or depth.

A* is optimally efficient under the lecture's stated comparison conditions, but can still expand exponentially many nodes and exhaust memory. Weighted A* trades optimality for speed. IDA*, RBFS, MA*, and SMA* manage memory by accepting regeneration or forgetting nodes. Bidirectional heuristic search cannot be justified by independently applying ordinary A* proofs to both directions.

See [[Concepts/Ch03 - Heuristics Admissibility and Consistency|Heuristics, Admissibility, and Consistency]], [[Algorithms/Ch03 - A-Star Search|A* Search]], and [[Algorithms/Ch03 - Memory-Bounded Heuristic Search|Memory-Bounded Heuristic Search]].

## 7. Heuristic Quality and Construction (pages 56-66)

For the 8-puzzle, $h_1$ counts misplaced tiles and $h_2$ sums Manhattan distances. Empirical results show stronger $h_2$ generates fewer nodes and has a smaller effective branching factor.

A relaxed problem removes restrictions, making its optimal cost a lower bound for the original. If admissible heuristics do not dominate one another, their maximum remains admissible. Pattern databases store exact subproblem costs. Independent pattern costs cannot simply be added if moves overlap; disjoint pattern databases use cost partitioning to make addition safe.

Landmarks and differential heuristics exploit precomputed distances and triangle inequalities; shortcuts add optimal multi-action edges. Search itself can be considered at a metalevel, where computation choices are actions. Heuristics can also be learned from solved experiences, though learned estimates may overestimate.

> [!question]
> **Professor Question (page 62):** Can we just add two pattern-database heuristics instead of maxing?
>
> The following slide answers: not in general, because shared moves would be counted twice; disjoint/cost-partitioned patterns are the exception.

See [[Concepts/Ch03 - Heuristic Construction|Heuristic Construction]].

## 8. Chapter Conclusions (pages 67-70)

The closing slides restate formulation, graph/tree distinctions, algorithm evaluation, uninformed strategies, heuristic search, and the dependence of performance on heuristic quality. Historical notes connect state-space search to Newell and Simon, Bellman, Dijkstra, Hart-Nilsson-Raphael's A*, Pearl's heuristic theory, and later memory-bounded and pattern-database work.

## Warnings and Limitations

- The environment assumptions are intentionally narrow.
- A finite state graph can yield an infinite search tree.
- “Optimal” may mean least path cost, not fewest steps.
- Early goal testing is unsafe for UCS/A*.
- Admissibility and consistency are related but not interchangeable in graph-search reasoning.
- Good worst-case guarantees do not prevent exponential practical cost.
- Adding admissible heuristics can destroy admissibility through double counting.

## Continue Studying

[[Mathematics/Ch03 - Mathematics|Mathematics]] · [[Review/Ch03 - Exam Cram|Exam Cram]] · [[Review/Ch03 - Practice Questions|Practice Questions]] · [[Active Recall/Ch03 - Active Recall|Active Recall]]

