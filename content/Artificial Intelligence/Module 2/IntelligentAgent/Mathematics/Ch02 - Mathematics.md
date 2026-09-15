---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- mathematics
- intelligent-agents
title: Chapter 2 - Mathematics
type: mathematics
---

# Chapter 2 — Mathematics

The lecture is conceptually heavy and contains three mathematically
meaningful expressions that deserve explicit treatment.

## Agent Function

*Source slide: 6*

$$
f : P^* \longrightarrow A
$$

<details>
<summary>
<strong>📖 How to Read This Formula</strong>
</summary>
"f maps P star to A," or more explicitly: "the agent function f maps the
set of all possible percept sequences to the set of actions."

The superscript star is read "star." Here it means sequences of any
finite length over the percept set.

</details>
<details>
<summary>
<strong>🔣 Notation & Symbols</strong>
</summary>
  Symbol              Meaning
  ------------------- ---------------------------------------
  $f$                 agent function
  $P$                 set/alphabet of possible percepts
  $P^*$               set of all possible percept sequences
  $A$                 set of possible actions
  $:$                 "is a function from" in this context
  $\longrightarrow$   maps from domain to codomain

</details>
<details>
<summary>
<strong>💡 Meaning & Purpose</strong>
</summary>
This is the lecture's external mathematical characterization of an
agent. Give the function everything the agent has perceived so far; it
returns the action the agent chooses. It describes behavior without
specifying implementation.

</details>
<details>
<summary>
<strong>🧭 When / Why to Use It</strong>
</summary>
Use it to reason about *what behavior an agent implements* independently
of how the program is coded. It is especially useful for distinguishing
the abstract agent function from the concrete agent program.

</details>
<details>
<summary>
<strong>⚠️ Assumptions / Conditions</strong>
</summary>
The lecture's crucial constraint is informational: the action can depend
on built-in knowledge and the percept sequence observed so far, not on
information never perceived. The full table is generally unbounded
unless percept-sequence length is bounded.

</details>
<details>
<summary>
<strong>🧮 Worked Example</strong>
</summary>
> [!example] Illustrative Example --- Not From Lecture

Suppose $P=\{Clean,Dirty\}$ and $A=\{Suck,Move\}$. One possible agent
function contains mappings such as: - $f([Dirty])=Suck$ -
$f([Clean])=Move$ - $f([Clean,Dirty])=Suck$

The input is a *sequence*, not merely the latest percept.

</details>
<details>
<summary>
<strong>🐍 Python Example</strong>
</summary>
> [!example] Illustrative Python Example --- Not From Lecture

``` python
def agent_function(percept_sequence):
    latest = percept_sequence[-1]
    return "Suck" if latest == "Dirty" else "Move"

print(agent_function(["Clean", "Dirty"]))  # Suck
```

</details>
<details>
<summary>
<strong>🔗 Math → Python Mapping</strong>
</summary>
  Mathematics                 Python
  --------------------------- -------------------------
  $f$                         `agent_function`
  percept sequence in $P^*$   `percept_sequence` list
  action in $A$               returned string
  $f(p_1,\ldots,p_t)$         `agent_function([...])`

</details>
<details>
<summary>
<strong>🎯 Interpretation</strong>
</summary>
The output is an action selected for a particular percept history. The
formula does **not** say that the function is rational, efficient,
learnable, or practical; it only specifies the behavioral mapping.

</details>

------------------------------------------------------------------------

## Table-Driven Agent Size

*Source slide: 35*

$$
\sum_{t=1}^T |P|^t
$$

<details>
<summary>
<strong>📖 How to Read This Formula</strong>
</summary>
"The sum from t equals one to T of the cardinality of P raised to the
t-th power."

$\sum$ is read "sum" or "summation." $|P|$ is read "the cardinality of
P," meaning the number of possible percepts.

</details>
<details>
<summary>
<strong>🔣 Notation & Symbols</strong>
</summary>
  Symbol           Meaning
  ---------------- ------------------------------------------
  $P$              set of possible percepts
  $|P|$            number of distinct percepts
  $t$              percept-sequence length
  $T$              agent lifetime measured in percepts
  $|P|^t$          number of length-$t$ percept sequences
  $\sum_{t=1}^T$   add the counts for lengths 1 through $T$

</details>
<details>
<summary>
<strong>💡 Meaning & Purpose</strong>
</summary>
A table-driven agent needs an entry for every possible percept sequence.
There are $|P|^t$ sequences of length $t$, so summing across all lengths
through lifetime $T$ gives the required number of table entries.

</details>
<details>
<summary>
<strong>🧭 When / Why to Use It</strong>
</summary>
Use it to quantify why brute-force tabulation of an agent function is
infeasible. The lecture uses the expression as a scalability argument,
not as a practical design formula.

</details>
<details>
<summary>
<strong>⚠️ Assumptions / Conditions</strong>
</summary>
The expression assumes a fixed finite set of possible percepts and
counts all possible sequences through a bounded lifetime $T$. Without a
lifetime bound, the table is unbounded.

</details>
<details>
<summary>
<strong>🧮 Worked Example</strong>
</summary>
> [!example] Illustrative Example --- Not From Lecture

If $|P|=2$ and $T=3$:

$$
\sum_{t=1}^3 2^t = 2^1+2^2+2^3=2+4+8=14
$$

So even this tiny agent needs 14 history entries for sequences of length
1--3.

</details>
<details>
<summary>
<strong>🐍 Python Example</strong>
</summary>
> [!example] Illustrative Python Example --- Not From Lecture

``` python
num_percepts = 2
lifetime = 3

entries = sum(num_percepts ** t for t in range(1, lifetime + 1))
print(entries)  # 14
```

</details>
<details>
<summary>
<strong>🔗 Math → Python Mapping</strong>
</summary>
  Mathematics      Python
  ---------------- --------------------------
  $|P|$            `num_percepts`
  $T$              `lifetime`
  $t=1,\ldots,T$   `range(1, lifetime + 1)`
  $|P|^t$          `num_percepts ** t`
  $\sum$           `sum(...)`

</details>
<details>
<summary>
<strong>🎯 Interpretation</strong>
</summary>
The result is a **count of table entries**, so it is dimensionless. It
grows exponentially with $T$ when $|P|>1$. Increasing either the number
of possible percepts or the lifetime makes the table explode. It is not
a time-complexity measurement by itself; it is a representation-size
argument.

</details>

------------------------------------------------------------------------

## Expected Utility

*Source slide: 51*

$$
EU(a)=\sum_{s'} P(s'\mid a)\,U(s')
$$

<details>
<summary>
<strong>📖 How to Read This Formula</strong>
</summary>
"Expected utility of action a equals the sum over possible next states s
prime of the probability of s prime given action a times the utility of
s prime."

The vertical bar $\mid$ is read "given." $s'$ is read "s prime."

</details>
<details>
<summary>
<strong>🔣 Notation & Symbols</strong>
</summary>
  Symbol          Meaning
  --------------- ----------------------------------------------
  $EU(a)$         expected utility of action $a$
  $a$             candidate action
  $s'$            a possible outcome/next state
  $P(s'\mid a)$   probability of outcome $s'$ given action $a$
  $U(s')$         utility assigned to outcome $s'$
  $\sum_{s'}$     sum over possible outcome states

</details>
<details>
<summary>
<strong>💡 Meaning & Purpose</strong>
</summary>
The formula averages utility across possible outcomes, but not equally:
each utility is weighted by how likely that outcome is under action $a$.
A rational utility-based agent chooses the action with the greatest
expected utility.

</details>
<details>
<summary>
<strong>🧭 When / Why to Use It</strong>
</summary>
Use expected utility when outcomes are uncertain and states differ in
desirability. It handles both likelihood and importance, which is why
utility-based reasoning goes beyond a binary goal test.

</details>
<details>
<summary>
<strong>⚠️ Assumptions / Conditions</strong>
</summary>
The lecture assumes outcome probabilities and a utility function are
available to the decision process. It also warns that modeling the
environment, computing the maximizing action, and specifying the correct
utility function can all be difficult.

</details>
<details>
<summary>
<strong>🧮 Worked Example</strong>
</summary>
> [!example] Illustrative Example --- Not From Lecture

Suppose action `FastRoute` has: - 0.8 probability of a safe, quick
arrival with utility 100, - 0.2 probability of a bad delay with utility
20.

Then:

$$
EU(FastRoute)=0.8(100)+0.2(20)=80+4=84
$$

If `SlowRoute` guarantees utility 80, then its expected utility is 80.
Under these invented values, the utility-based agent selects `FastRoute`
because $84>80$.

</details>
<details>
<summary>
<strong>🐍 Python Example</strong>
</summary>
> [!example] Illustrative Python Example --- Not From Lecture

``` python
outcomes = [
    (0.8, 100),
    (0.2, 20),
]

expected_utility = sum(probability * utility for probability, utility in outcomes)
print(expected_utility)  # 84.0
```

</details>
<details>
<summary>
<strong>🔗 Math → Python Mapping</strong>
</summary>
  Mathematics          Python
  -------------------- -------------------------
  $P(s'\mid a)$        `probability`
  $U(s')$              `utility`
  $P(s'\mid a)U(s')$   `probability * utility`
  $\sum_{s'}$          `sum(...)`
  $EU(a)$              `expected_utility`

</details>
<details>
<summary>
<strong>🎯 Interpretation</strong>
</summary>
Expected utility is a probability-weighted utility score, not the
utility that will definitely occur. Increasing the probability of a
high-utility outcome raises expected utility; increasing the probability
of a low-utility outcome lowers it, all else equal. Utility units depend
on how the utility function is defined and should not automatically be
interpreted as dollars, probability, or accuracy.

</details>
## Mathematical Quality Check

-   [x] All meaningful lecture expressions reproduced.
-   [x] Spoken reading included.
-   [x] Symbols/operators explained.
-   [x] Meaning and usage explained.
-   [x] Assumptions/conditions included where supported.
-   [x] Worked examples included and labeled when invented.
-   [x] Executable Python included.
-   [x] Math → Python mapping included.
-   [x] Results interpreted.
