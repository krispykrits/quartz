# Chapter 5 Mathematics — Constraint Satisfaction Problems

**Source:** slides/pages 4, 7–14, 17–25, 31, 34–36, 45, 47, 49, 51, 53, 55–56.

> [!note]
> Worked calculations and Python snippets below are **Illustrative - Not From Lecture** unless they reproduce a numerical calculation explicitly shown on the cited slide.

## CSP Definition
$$\langle X,D,C\rangle$$
<details><summary><strong>📖 How to Read This Formula</strong></summary>A CSP consists of variables $X$, domains $D$, and constraints $C$.</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>$X=\{X_1,\dots,X_n\}$; $D=\{D_1,\dots,D_n\}$; $C=\{C_1,\dots,C_m\}$. Each constraint is $\langle scope(C_j),rel(C_j)\rangle$.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>The representation exposes internal state structure and legal relations.</details>
<details><summary><strong>🐍 Python Example</strong></summary>

```python
variables = ["WA", "NT", "Q", "NSW", "V", "SA", "T"]
domains = {v: {"red", "green", "blue"} for v in variables}
```
</details>

## Propagation Pruning Fraction
After $SA=blue$, five neighbors shrink from 3 to 2 colors:
$$3^5=243,\qquad 2^5=32,\qquad 1-\frac{32}{243}\approx 86.8\%.$$
<details><summary><strong>🧮 Worked Example</strong></summary>The lecture compares 243 unconstrained joint choices with 32 choices after one propagation step; 211 of 243 are removed.</details>
<details><summary><strong>🐍 Python Example</strong></summary>

```python
before, after = 3**5, 2**5
fraction_pruned = 1 - after / before
print(before, after, fraction_pruned)
```
</details>

## Scheduling Precedence and Resource Disjunction
$$T_1+d_1\le T_2$$
$$ (Axle_F+10\le Axle_B)\lor(Axle_B+10\le Axle_F) $$
<details><summary><strong>📖 How to Read This Formula</strong></summary>The first says task 1 must finish before task 2 starts. The disjunction says either front axle work finishes before rear axle work starts, or vice versa.</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>To encode precedence and mutual exclusion in scheduling CSPs.</details>

## 8-Queens Constraints
For $i\ne j$:
$$Q_i\ne Q_j\land |Q_i-Q_j|\ne |i-j|.$$
<details><summary><strong>💡 Meaning & Purpose</strong></summary>The first condition prevents same-row attacks; the absolute-difference condition prevents diagonal attacks. One variable per column prevents same-column attacks by construction.</details>

## Arc Consistency Support
$$\forall x\in D_i\;\exists y\in D_j:C_{ij}(x,y).$$
<details><summary><strong>📖 How to Read This Formula</strong></summary>Every value in $D_i$ must have at least one supporting value in $D_j$ satisfying the binary constraint.</details>
<details><summary><strong>🧮 Worked Example</strong></summary>For $D_i=\{1,2\}$, $D_j=\{2,3\}$, $X_i<X_j$, value 2 is supported by 3. If $D_j$ becomes $\{2\}$, value 2 loses support and is deleted.</details>

## AC-3 Complexity
$$T_{AC-3}=O(cd\cdot d^2)=O(cd^3).$$
<details><summary><strong>🔣 Notation & Symbols</strong></summary>$c$ is the number of binary constraints up to a constant factor of directed arcs; $d$ is maximum domain size.</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>An arc can be reinserted at most $d$ times due to deletions, and each REVISE can inspect $O(d^2)$ value pairs.</details>

## k-Consistency
A CSP is $k$-consistent when any consistent assignment to any $k-1$ variables can be extended consistently to any kth variable.
<details><summary><strong>🎯 Interpretation</strong></summary>$k=1$ node consistency; $k=2$ arc consistency; $k=3$ path consistency for binary CSPs. Strong $k$-consistency means all levels $1\ldots k$ hold.</details>

## Global Resource Lower-Bound Test
$$\sum_i \min D_i > 10 \Rightarrow \text{inconsistent}.$$
For four $P_i\in\{3,4,5,6\}$, the lower bound is $12>10$.

## Flight-Capacity Bounds
Given $F_1+F_2=420$, $D_1=[0,165]$, $D_2=[0,385]$:
$$F_1\ge420-385=35,\qquad F_2\ge420-165=255.$$
Thus $D_1=[35,165]$ and $D_2=[255,385]$.

## Backtracking Search-Space Reduction by Commutativity
Naive action-order leaves:
$$n!d^n.$$
Choosing one variable at each node leaves:
$$d^n.$$
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Assignment order does not change the resulting partial assignment, so the solver strategically chooses an order without branching over permutations of that order.</details>

## MRV
$$X^*=\arg\min_{X_i\;unassigned}|D_i^{legal}|.$$
## Degree Tie-Breaker
$$X^*=\arg\max_{X_i\;tied}deg_{unassigned}(X_i).$$
## Least-Constraining Value
$$v^*=\arg\min_{v\in D_X}\sum_{Y\in N(X)}\#\{y\in D_Y:\neg C_{XY}(v,y)\}.$$
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python idea |
|---|---|
| $\arg\min |D_i|$ | `min(vars, key=lambda v: len(domains[v]))` |
| $\arg\max deg$ | `max(tied, key=unassigned_degree)` |
| LCV elimination count | count neighbor values rejected by a candidate value |
</details>

## 8-Queens Conflict Objective
$$h(q)=\sum_{1\le i<j\le8}\mathbf{1}[q_i=q_j\lor|q_i-q_j|=|i-j|].$$
<details><summary><strong>📖 How to Read This Formula</strong></summary>Sum one for every attacking queen pair. A solution has $h(q)=0$.</details>

## Weighted Constraint Objective
$$H_w(s)=\sum_j w_j\mathbf{1}[C_j\text{ is violated in }s].$$
<details><summary><strong>💡 Meaning & Purpose</strong></summary>Frequently violated constraints accumulate larger weights, giving the local-search landscape more topography and directing effort toward historically difficult constraints.</details>

## Independent Components
If each component has constant size $c$:
$$T(n)=\frac{n}{c}d^c=O(n)\quad\text{for fixed }c,d,$$
instead of $O(d^n)$.

## Tree CSP Complexity
$$T(n,d)=O((n-1)d^2+nd)=O(nd^2).$$
<details><summary><strong>💡 Meaning & Purpose</strong></summary>A tree has $n-1$ edges; each edge revision costs at most $d^2$, followed by a linear assignment pass.</details>

## Cutset Conditioning Complexity
If $|S|=c$:
$$T=O\left(d^c(n-c)d^2\right).$$
<details><summary><strong>🎯 Interpretation</strong></summary>Exponential cost is confined to the small cyclic core; the remainder is solved as a tree.</details>

## Tree Width
Largest bag size is $w+1$:
$$|D_{bag}|\le d^{w+1}\Rightarrow T=O(nd^{w+1}).$$
<details><summary><strong>🎯 Interpretation</strong></summary>For constant tree width $w$, solving is polynomial in $n$ given the decomposition, but time and memory grow exponentially with $w$.</details>

## Symmetry Count
With $d$ interchangeable color names, each structural coloring corresponds to:
$$d!$$
name permutations. For three colors, $3!=6$ equivalent members.
