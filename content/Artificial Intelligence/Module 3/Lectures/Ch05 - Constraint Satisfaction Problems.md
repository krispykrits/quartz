# Chapter 5 — Constraint Satisfaction Problems

**Source:** 60-slide lecture deck, *Constraint Satisfaction Problems: Representation, inference, search, local repair, and problem structure*, based on AIMA 4th ed., Sections 5.1–5.5.

## Big Picture
The lecture opens the atomic-state “black box.” A CSP represents state as variable/value pairs and exposes constraints among variables. That structure supports generic propagation, strategic branching, local repair, conflict learning, and graph decomposition.

## Lecture Roadmap
- **Lecture 1 (slides 1–29):** formulation and propagation.
- **Lecture 2 (slides 30–60):** search, local repair, and structural tractability.

## Learning Objectives
1. Formulate $\langle X,D,C\rangle$ and distinguish assignments, constraints, and solutions.
2. Apply node, arc, path, and k-consistency; trace AC-3 and analyze its cost.
3. Explain MRV, degree, LCV, forward checking, and MAC.
4. Compare systematic search with min-conflicts local search.
5. Use components, trees, cutsets, and tree decompositions to predict tractability.

## 60-Second Summary
Model a problem as variables with domains plus constraints. Propagate unsupported values before and during search. When branching is necessary, use MRV/degree to choose variables and LCV to order values; forward checking or MAC detects failures early. Conflict sets and no-goods explain and remember failures. For large feasible spaces, min-conflicts repairs complete assignments. Finally, inspect the constraint graph: disconnected components, trees, small cutsets, or small tree width can make otherwise exponential CSPs far easier.

## 1. Representation: from atomic states to factored CSPs — slides 3–14
A CSP is $\langle X,D,C\rangle$. Each constraint is $\langle scope(C_j),rel(C_j)\rangle$. Assignments may be partial or complete; a solution is complete and consistent. The Australia map-coloring example has seven variables, three-color domains, and nine adjacency inequalities. Assigning SA=blue immediately removes blue from five neighbors, shrinking their joint choices from $3^5=243$ to $2^5=32$—about 86.8% pruned.

Scheduling is modeled with start-time variables, precedence inequalities such as $T_1+d_1\le T_2$, shared-resource disjunctions, and deadline bounds. The lecture contrasts finite discrete, infinite discrete, continuous, linear continuous, and nonlinear integer domains. It also models 8-queens with one variable per column and distinguishes unary, binary, ternary, n-ary, and global constraints. Cryptarithmetic uses `Alldiff`, leading-digit restrictions, and carry variables. Hard CSP feasibility is contrasted with constrained optimization over preference costs.

See [[Concepts/Ch05 - CSP Representation and Solutions|CSP Representation and Solutions]] and [[Concepts/Ch05 - Domain Types and Constraint Arity|Domain Types and Constraint Arity]].

## 2. Propagation and local consistency — slides 15–29
Propagation can run before search, after each decision, and until a fixed point. Outcomes are: all singleton domains (solved), an empty domain (failure), or a reduced CSP that still requires branching.

**Node consistency** filters unary constraints. **Arc consistency** is directional: every $x\in D_i$ needs some supporting $y\in D_j$. The $Y=X^2$ example shows revising X with respect to Y yields $D_X=\{0,1,2,3\}$ while revising Y with respect to X yields $D_Y=\{0,1,4,9\}$.

### AC-3 — slides 19–21
AC-3 starts with all directed arcs, calls REVISE, and re-enqueues incoming arcs when a domain changes because old supports may have become invalid. In $A<B<C$ with $D_A=D_B=D_C=\{1,2,3\}$ and $D_C=\{2\}$, revising $(B,C)$ makes $D_B=\{1\}$; revisiting $(A,B)$ then empties $D_A$. Worst-case cost is $O(cd^3)$.

See [[Algorithms/Ch05 - AC-3 Arc Consistency|AC-3 Arc Consistency]].

**Path consistency** can expose cyclic inconsistency missed by arc consistency, as in a two-color triangle. **k-consistency** generalizes extension guarantees; strong n-consistency can permit backtrack-free assignment after it is established, but establishing it is exponentially expensive in the worst case.

Global constraints can propagate more strongly than primitive decompositions. `Alldiff` detects when more variables than distinct remaining values must be assigned. Sudoku uses 81 variables and 27 `Alldiff` constraints; singleton cascades can solve easy puzzles, while hard puzzles can stall at a non-singleton fixed point. “Naked triples” are presented as Hall-set reasoning: if k variables have a union of exactly k values, those values are reserved and can be removed elsewhere in the unit.

See [[Concepts/Ch05 - Node Arc Path and k-Consistency|Node, Arc, Path, and k-Consistency]] and [[Concepts/Ch05 - Global Constraints and Bounds Propagation|Global Constraints and Bounds Propagation]].

## 3. Backtracking search and heuristics — slides 31–39
Backtracking searches partial assignments. Commutativity removes the unnecessary $n!$ assignment-order factor, reducing leaves from $n!d^n$ to $d^n$ under the standard CSP action view.

The recursive skeleton separates four decisions: variable selection, value ordering, inference, and recovery/learning. **MRV** selects the variable with the fewest legal values (fail-first). **Degree** breaks ties by choosing the variable constraining the most unassigned neighbors. **LCV** tries the value that rules out the fewest neighbor values (fail-last).

See [[Algorithms/Ch05 - Backtracking Search|Backtracking Search]] and [[Algorithms/Ch05 - MRV Degree and LCV Heuristics|MRV, Degree, and LCV]].

**Forward checking** removes values inconsistent with the latest assignment from unassigned neighbors only. The lecture's Australia table reaches $D_{SA}=\emptyset$ after WA=R, Q=G, V=B, proving that partial assignment is a no-good. Rollback must restore every inferred deletion.

**MAC** starts AC-3 after a decision, seeding arcs from unassigned neighbors toward the assigned variable. It is stronger than forward checking because it propagates among unassigned variables as well.

See [[Algorithms/Ch05 - Forward Checking|Forward Checking]] and [[Algorithms/Ch05 - Maintaining Arc Consistency MAC|MAC]].

## 4. Conflict-directed recovery and learning — slides 40–42
If SA fails because Q, NSW, and V collectively block its values while T is irrelevant, chronological backtracking wastes effort on T. Backjumping records $conf(SA)=\{Q,NSW,V\}$ and jumps to the most recent implicated variable, V. Conflict-directed backjumping merges the failed variable's causes into the jump variable. A **no-good** records a combination that cannot occur in any solution; the lecture example $\{WA=red,NT=green,Q=blue\}$ can be learned as a constraint.

See [[Algorithms/Ch05 - Conflict-Directed Backjumping|Conflict-Directed Backjumping]] and [[Algorithms/Ch05 - No-Good Learning|No-Good Learning]].

## 5. Local search and repair — slides 43–48
Local search uses complete assignments and allows violated constraints. Its satisfaction objective is the number or weighted sum of violations; zero means solution. **Min-conflicts** repeatedly selects a conflicted variable and moves it to a minimum-conflict value, with random tie-breaking and optional restarts. In 8-queens, one queen per column defines a complete state and the objective counts attacking pairs.

The lecture reports that n-queens can be remarkably favorable for min-conflicts because solutions are dense, while emphasizing the completeness caveat: exhausting the step limit does not prove unsatisfiability. Constraint weighting raises the weights of persistently violated constraints, distinguishing plateau states and redirecting search. Local repair is also natural for online CSPs because an existing feasible schedule is valuable state when new constraints arrive.

See [[Algorithms/Ch05 - Min-Conflicts|Min-Conflicts]] and [[Algorithms/Ch05 - Constraint Weighting|Constraint Weighting]].

## 6. Structural tractability — slides 49–57
Disconnected components solve independently; Tasmania is disconnected from mainland Australia. A **tree CSP** needs no backtracking after directional arc consistency: revise parent domains against children backward, then assign supported values forward. Complexity is $O(nd^2)$.

**Cutset conditioning** enumerates a small cyclic core, propagates it, then solves the forest. For Australia, $S=\{SA\}$ breaks mainland cycles. If $|S|=c$, cost is $O(d^c(n-c)d^2)$; finding a minimum cycle cutset is NP-hard.

A **tree decomposition** uses bags satisfying coverage, constraint coverage, and running intersection. If largest bag size is $w+1$, bag domains are at most $d^{w+1}$ and solving costs $O(nd^{w+1})$ given the decomposition. Finding minimum tree width is NP-hard. The lecture closes with **symmetry breaking** and a method-selection table matching solver techniques to CSP structure.

See [[Algorithms/Ch05 - Tree CSP Solver|Tree CSP Solver]], [[Algorithms/Ch05 - Cutset Conditioning|Cutset Conditioning]], [[Algorithms/Ch05 - Tree Decomposition Dynamic Programming|Tree Decomposition]], and [[Concepts/Ch05 - Symmetry Breaking and Method Selection|Symmetry Breaking and Method Selection]].

## 7. Integration Exercise — slide 58
Given $D_A=\{1,2\}$, $D_B=\{1\}$, $D_C=\{1,2,3\}$, $D_D=\{2,3\}$ and constraints $A\ne B$, $A<C$, $B<D$, $C\ne D$: MRV selects B=1; propagation forces A=2, then C=3, then D=2. Solution: $(A,B,C,D)=(2,1,3,2)$.

## Diagram Guide
- **Slide 6:** Australia constraint graph—nodes are regions; edges are binary inequality constraints; Tasmania is isolated.
- **Slide 9:** scheduling network—directed arrows encode precedence; the axle tool is a shared-resource conflict; both chains feed Inspect.
- **Slide 20:** A→B→C chain demonstrates why AC-3 must revisit incoming arcs after domain deletion.
- **Slide 35:** highlighted SA node illustrates the degree heuristic's future impact.
- **Slide 45:** 8-queens board depicts a complete assignment and a reassignment move for local repair.
- **Slides 50–55:** tree, cutset, and tree-decomposition diagrams show how graph structure yields tractable subproblems. On an exam, identify nodes/bags, edge meanings, separators/shared variables, and the complexity consequence.

## Warnings and Limitations
- Arc consistency is local, not complete; cycles can remain inconsistent.
- Stronger consistency is not free; high k can be exponentially expensive.
- Forward checking does not propagate among two unassigned variables.
- Min-conflicts is incomplete.
- Minimum cycle cutset and minimum tree width are NP-hard to find.
- Symmetry breaking must preserve at least one representative of every equivalence class.

## Navigation
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Concept Map|Concept Map]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]
- [[Review/Ch05 - Key Terms|Key Terms]]
- [[Review/Ch05 - Why and How|Why and How]]
- [[Review/Ch05 - Exam Cram|Exam Cram]]
- [[Review/Ch05 - Practice Questions|Practice Questions]]
- [[Active Recall/Ch05 - Active Recall|Active Recall]]
