# Chapter 3 Mathematics

**Source:** pages 7-8, 20-22, 26, 28-31, 34-49, 51-53, 56-64

## Additive Path Cost

$$g(n)=\sum_{i=1}^{k} c(s_{i-1},a_i,s_i)$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>The path cost to node $n$ is the sum of each action cost along its path.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $g(n)$ | cost from initial node to $n$ |
| $c(s,a,s')$ | cost of one transition |
| $k$ | number of actions |

</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Turns a path into a comparable numeric quantity.</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>Used by UCS and as the past-cost term in A*.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture:** Costs 75, 71, and 151 give $g=297$.

</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> g = sum([75, 71, 151])
> ```

</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>`sum(costs)` implements $\sum c_i$.</details>
<details><summary><strong>🎯 Interpretation</strong></summary>Lower $g$ means a cheaper route already traveled.</details>

## Best-First Evaluation Functions

$$\text{BFS: }f(n)=\operatorname{depth}(n),\quad \text{UCS: }f(n)=g(n),\quad \text{Greedy: }f(n)=h(n),\quad \text{A*: }f(n)=g(n)+h(n)$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>Each strategy defines “best next node” using a different score.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $f(n)$ | frontier priority |
| $g(n)$ | exact past cost |
| $h(n)$ | estimated remaining cost |

</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>The general best-first engine becomes different algorithms by changing $f$.</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>BFS for unit costs, UCS for unequal costs without heuristics, greedy for aggressive guidance, A* for cost plus guidance.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>
> [!example]
> **Illustrative Example - Not From Lecture:** Node A has $(g,h)=(6,4)$ and B $(4,7)$. Greedy chooses A ($h=4$); A* chooses A ($f=10<11$); UCS chooses B ($g=4$).
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> astar_priority = lambda g, h: g + h
> ```

</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>`heapq` stores tuples such as `(g+h, tie_breaker, node)`.</details>
<details><summary><strong>🎯 Interpretation</strong></summary>The scoring rule encodes the algorithm's tradeoff between past evidence and future estimate.</details>

## Admissibility and Consistency

$$0\le h(n)\le h^*(n)$$

$$h(n)\le c(n,a,n')+h(n')$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>An admissible heuristic never overestimates true remaining cost. A consistent heuristic cannot drop by more than the cost of one step.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $h^*(n)$ | true optimal remaining cost |
| $n'$ | successor of $n$ |
| $c(n,a,n')$ | transition cost |

</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>These lower-bound conditions underpin A*'s optimality guarantees.</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>Use admissibility for lower-bound reasoning; use consistency for graph search and monotone $f$ values.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture:** If a step costs 3 and the successor has $h=5$, consistency requires the predecessor's $h\le8$.

</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> def consistent(h_n, cost, h_next):
>     return h_n <= cost + h_next
> ```

</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>The inequality becomes a direct assertion over every graph edge.</details>
<details><summary><strong>🎯 Interpretation</strong></summary>Consistency implies $f(n')\ge f(n)$ because $g(n')=g(n)+c$.</details>

## Search Complexity

$$\text{BFS time/space}=O(b^d),\quad \text{DFS time}=O(b^m),\quad \text{DFS space}=O(bm)$$

$$\text{DLS time}=O(b^\ell),\quad \text{DLS space}=O(b\ell)$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>Search effort grows exponentially with depth, while DFS-style storage grows roughly with branching factor times path depth.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>$b$: branching factor; $d$: shallowest solution depth; $m$: maximum depth; $\ell$: chosen limit.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Explains why memory, not arithmetic, often limits search.</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>Use for selecting strategies and estimating feasibility.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture:** $b=10,d=6$ implies roughly one million depth-6 nodes before constants and duplicate pruning.

</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> estimated_layer = 10 ** 6
> ```

</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>`b ** d` represents the dominant exponential layer.</details>
<details><summary><strong>🎯 Interpretation</strong></summary>A small reduction in effective branching factor can be transformative.</details>

## Bidirectional Search Motivation

$$b^{d/2}+b^{d/2}=2b^{d/2}\ll b^d$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>Two searches of half depth can generate far fewer nodes than one full-depth search.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Shows the exponential advantage when forward/backward search is applicable.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture:** With $b=10,d=8$, one direction suggests $10^8$; two half-depth searches suggest about $2\times10^4$.

</details>
<details><summary><strong>🎯 Interpretation</strong></summary>The gain depends on predecessor generation and efficient frontier intersection.</details>

## Weighted A*

$$f(n)=g(n)+Wh(n)$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>Weight $W$ controls how strongly the search prefers estimated goal proximity.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>$W=1$ gives A*; increasing $W$ approaches greedy behavior.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Trades guaranteed solution quality for reduced search.</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> priority = g + weight * h
> ```

</details>
<details><summary><strong>🎯 Interpretation</strong></summary>Use when a bounded-suboptimal answer is more valuable than an expensive optimum.</details>

## Effective Branching Factor

$$N+1=1+b^*+(b^*)^2+\cdots+(b^*)^d$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>The generated-node count equals the size of a uniform tree of depth $d$ with branching factor $b^*$.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>$N$: generated nodes; $d$: solution depth; $b^*$: effective branching factor.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Provides an empirical, problem-normalized measure of heuristic quality.</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>Compare heuristics across instances solved at similar depths.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture:** Solve the polynomial numerically; there is usually no convenient closed form.

</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> def nodes(b, d): return sum(b**i for i in range(d + 1))
> ```

</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>Use bisection/root finding to choose $b$ whose geometric sum is $N+1$.</details>
<details><summary><strong>🎯 Interpretation</strong></summary>A heuristic nearer $b^*=1$ guides search more directly.</details>

## Combining Heuristics and Differential Bounds

$$h(n)=\max\{h_1(n),\ldots,h_m(n)\}$$

$$h(n)\ge |C^*(n,L)-C^*(G,L)|$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>Take the strongest admissible lower bound; landmark distance differences provide another lower bound by triangle inequality.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Improves informativeness without losing admissibility, provided component bounds are valid and costs are not double-counted.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture:** If two admissible estimates are 7 and 10, use 10—not 17 unless their costs are provably disjoint.

</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> combined = max(h1, h2)
> differential = abs(dist_to_landmark[node] - dist_to_landmark[goal])
> ```

</details>
<details><summary><strong>🎯 Interpretation</strong></summary>Maximum is safe for lower bounds; summation requires cost independence/partitioning.</details>

