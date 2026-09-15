---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Mathematics

This note teaches each academically meaningful mathematical expression using:

**Notation → Reading → Meaning → Usage → Calculation → Python → Interpretation**

## Target concept

_Source slide: 4_

$$
c:X\to\{0,1\}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“c maps X to the set zero, one.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $c$ | target concept |
| $X$ | instance space |
| $\to$ | maps to |
| $\{0,1\}$ | Boolean output classes |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Every possible instance in $X$ receives either a negative label 0 or a positive label 1.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use this notation to formalize the concept-learning task as Boolean classification.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

For an EnjoySport day $x$, if the target concept says the person enjoys the sport, then $c(x)=1$; otherwise $c(x)=0$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
def c(enjoys_sport: bool) -> int:
    return 1 if enjoys_sport else 0

print(c(True))   # 1
print(c(False))  # 0
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $x\in X$ | an input instance |
| $c(x)$ | `c(...)` |
| $0,1$ | integer class labels |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The output is a class label, not a probability or confidence score.

</details>

## Training-example notation

_Source slide: 4_

$$
\langle x,c(x)\rangle
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“the ordered pair x, c of x.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $x$ | input instance |
| $c(x)$ | correct target label |
| $\langle\cdot,\cdot\rangle$ | ordered pair |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

A supervised training example pairs an input with its known output.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

For the first EnjoySport example:
- input = Sunny, Warm, Normal, Strong, Warm, Same
- output = Yes

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
x = ("Sunny","Warm","Normal","Strong","Warm","Same")
example = (x, 1)
print(example)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $x$ | `x` |
| $c(x)$ | `1` |
| $\langle x,c(x)\rangle$ | `(x, 1)` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

One ordered pair gives one observed fact about the target. It does not determine the target everywhere in $X$.

</details>

## Hypothesis-space size

_Source slide: 7_

$$
5\cdot4\cdot4\cdot4\cdot4\cdot4=5120
$$

$$
1+(4\cdot3\cdot3\cdot3\cdot3\cdot3)=973
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Five times four times four times four times four times four equals five thousand one hundred twenty.”

“One plus the quantity four times three times three times three times three times three equals nine hundred seventy-three.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

The multiplication counts combinations of allowable constraints across the six EnjoySport attributes.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The first count is syntactic. The second is semantic because all hypotheses containing `∅` reject every instance and therefore collapse into one behavior.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

$$
5\times4^5=5120
$$

$$
1+4\times3^5=1+4(243)=973
$$

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
syntactic = 5 * 4**5
semantic = 1 + 4 * 3**5
print(syntactic, semantic)
# 5120 973
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| multiplication | `*` |
| exponent | `**` |
| $4^5$ | `4**5` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Different written hypotheses can be semantically equivalent. The count also illustrates why explicit enumeration can become undesirable.

</details>

## General-to-specific ordering

_Source slide: 7_

$$
h_j\ge_g h_k
\iff
\forall x\in X:
[(h_k(x)=1)\to(h_j(x)=1)]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“h sub j is more general than or equal to h sub k if and only if, for all x in X, if h sub k of x equals one, then h sub j of x equals one.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $h_j,h_k$ | hypotheses |
| $\ge_g$ | more general than or equal to |
| $\iff$ | if and only if |
| $\forall$ | for all |
| $x\in X$ | x belongs to X |
| $\to$ | logical implication |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Every instance accepted by the more-specific hypothesis must also be accepted by the more-general hypothesis.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

It structures the hypothesis space for FIND-S and Candidate Elimination.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

$\langle Sunny,?,?,?,?,?\rangle$ is more general than $\langle Sunny,Warm,?,Strong,?,?\rangle$ because every instance accepted by the second has Sunny sky and is therefore also accepted by the first.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
ANY = "?"

def covers(h, x):
    return all(c == ANY or c == v for c, v in zip(h, x))

general = ("Sunny","?","?","?","?","?")
specific = ("Sunny","Warm","?","Strong","?","?")
x = ("Sunny","Warm","High","Strong","Cool","Change")

print(covers(specific, x))  # True
print(covers(general, x))   # True
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $h(x)=1$ | `covers(h, x)` |
| $\forall$ | `all(...)` |
| `?` | `ANY` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

“More general” means accepting a superset of positive instances. It does **not** mean better, more accurate, or more correct.

</details>

## Version space

_Source slide: 12_

$$
VS_{H,D}
\equiv
\{h\in H\mid Consistent(h,D)\}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“V S sub H comma D is defined as the set of h in H such that h is consistent with D.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $VS_{H,D}$ | version space |
| $H$ | hypothesis space |
| $D$ | training data |
| $h\in H$ | h belongs to H |
| $\mid$ | such that |
| $Consistent(h,D)$ | h agrees with every labeled example in D |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The version space is every hypothesis the observed data has not eliminated.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

If $H=\{h_1,h_2,h_3\}$ and $h_2$ is inconsistent, then:

$$
VS_{H,D}=\{h_1,h_3\}
$$

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
H = ["h1", "h2", "h3"]
consistent = {"h1": True, "h2": False, "h3": True}
VS = [h for h in H if consistent[h]]
print(VS)
# ['h1', 'h3']
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $H$ | `H` |
| $h\in H$ | `for h in H` |
| consistency filter | `if consistent[h]` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A hypothesis in the version space is consistent, not proven to be the true target concept.

</details>

## Version-space representation theorem

_Source slide: 13_

$$
VS_{H,D}
=
\{h\in H\mid
\exists s\in S,
\exists g\in G,
g\ge_g h\ge_g s\}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“V S sub H comma D equals the set of h in H such that there exists an s in S and there exists a g in G, where g is more general than or equal to h and h is more general than or equal to s.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\exists$ | there exists |
| $S$ | maximally specific boundary |
| $G$ | maximally general boundary |
| $g\ge_g h\ge_g s$ | h lies between g and s |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

S and G can represent a large version space without storing every interior hypothesis explicitly.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
def between(is_more_general, g, h, s):
    return is_more_general(g, h) and is_more_general(h, s)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $g\ge_g h$ | `is_more_general(g, h)` |
| $h\ge_g s$ | `is_more_general(h, s)` |
| logical conjunction | `and` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The theorem says the version space is the ordered region bracketed by its two extreme boundaries.

</details>

## Unbiased hypothesis space

_Source slide: 20_

$$
H'=\mathcal P(X)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“H prime equals the power set of X.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $H'$ | expanded hypothesis space |
| $\mathcal P(X)$ | power set of X |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Every subset of X corresponds to one possible Boolean concept, so every target concept becomes representable.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
from itertools import combinations

X = ('a', 'b', 'c')
power_set = [
    set(combo)
    for r in range(len(X) + 1)
    for combo in combinations(X, r)
]
print(len(power_set))  # 8
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $X$ | `X` |
| $\mathcal P(X)$ | all subsets generated with `combinations` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Representability alone does not guarantee generalization. The lecture uses this unrestricted space to show that bias is still necessary.

</details>

## Inductive bias entailment

_Source slide: 22_

$$
\forall x_i\in X:
(B\land D_c\land x_i)
\vdash
L(x_i,D_c)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“For all x sub i in X, B and D sub c and x sub i logically entail L of x sub i comma D sub c.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $B$ | inductive bias |
| $D_c$ | training data for target concept c |
| $L(x_i,D_c)$ | learner's classification |
| $\land$ | logical and |
| $\vdash$ | logically entails |
| $\forall$ | for all |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The bias is the extra assumption that makes the learner's inductive prediction reproducible by deductive reasoning.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

If the observed data leaves two unseen labels possible, an assumption restricting the target to a smaller hypothesis space may eliminate one of those possibilities and permit a prediction.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
allowed_hypotheses = ["h1", "h2"]  # operational representation of bias
prediction = 1
print(prediction)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python idea |
|---|---|
| $B$ | modeling/search restrictions |
| $D_c$ | training dataset |
| $L(x_i,D_c)$ | model prediction |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

In this chapter, inductive bias is not presented as a defect. It is the logical ingredient needed to generalize beyond observed examples.

</details>
