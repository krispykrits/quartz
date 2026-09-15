---
title: Chapter 1 - Mathematics
tags: [artificial-intelligence, mathematics, probability, optimization]
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: mathematics
---
# Chapter 1 - Mathematics

The lecture spans logic, probability, decision theory, optimization, sequential decision making, learning rules, complexity, and neural computation. Each formula follows **Notation → Reading → Meaning → Usage → Calculation → Python → Interpretation**.

## Classical Logic Example
_Source slide: 7_

$$
\forall x(Man(x)\Rightarrow Mortal(x)),\;Man(Socrates)\;\vdash\;Mortal(Socrates)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“For all x, if x is a man then x is mortal; Socrates is a man; therefore Socrates is mortal.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\forall x$ | for every x |
| $\Rightarrow$ | implies |
| $\vdash$ | therefore / derivable consequence |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Illustrates the laws-of-thought tradition: correct inference can be represented formally.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use formal logic for certain symbolic reasoning.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The lecture warns that real-world knowledge is rarely fully certain, so probability is also needed.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

Substitute Socrates for x. From Man(Socrates) and the universal implication, Mortal(Socrates) follows.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
is_man={"Socrates":True}
if is_man["Socrates"]:
    print("Mortal(Socrates)")
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $Man(Socrates)$ | `is_man["Socrates"]` |
| $Mortal(Socrates)$ | `printed conclusion` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The conclusion follows under the premises. It is not a probability or degree of belief.

</details>

---

## Expected-Utility Action Rule
_Source slide: 9_

$$
a^*(e)=\arg\max_{a\in A}\mathbb{E}[U\mid a,e]=\arg\max_{a\in A}\sum_{s\in S}P(s\mid a,e)U(s,a)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“a star of e equals arg max over actions a in A of expected utility given a and e, equal to arg max over actions a in A of the sum over states s in S of probability of s given a and e times utility of s and a.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $a^*(e)$ | best action for evidence e |
| $P(s\mid a,e)$ | belief probability |
| $U(s,a)$ | utility/preference |
| $\arg\max$ | argument that maximizes |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Chooses the action with highest probability-weighted utility and separates belief from preference.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for uncertain action selection with utilities.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The lecture says exact computation can be impossible in large, uncertain, changing environments.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

Action A: 0.8×100 + 0.2×0 = 80. Action B: 1.0×70 = 70. Choose A.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
actions={"A":[(0.8,100),(0.2,0)],"B":[(1.0,70)]}
eu={a:sum(p*u for p,u in xs) for a,xs in actions.items()}
print(eu,max(eu,key=eu.get))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $P(s\mid a,e)$ | `p` |
| $U(s,a)$ | `u` |
| $\sum P U$ | `sum(p*u for p,u in xs)` |
| $\arg\max$ | `max(eu,key=eu.get)` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Expected utility is not a guaranteed outcome; it is a weighted average used for comparison.

</details>

---

## Metalevel Computation Rule
_Source slide: 10_

$$
c^*=\arg\max_{c\in C}(\mathbb{E}[U\mid c,e]-Cost(c))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“c star equals arg max over computations c in C of expected utility given c and e minus the cost of c.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $c$ | candidate computation |
| $C$ | set of computations |
| $Cost(c)$ | computational cost |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Select computation based on net expected value rather than assuming more computation is always better.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for limited-rationality decisions about search/inference effort.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Both computation value and cost may only be estimated.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

quick: 60-5=55; medium: 75-15=60; deep: 80-30=50. Choose medium.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
vals={"quick":(60,5),"medium":(75,15),"deep":(80,30)}
net={k:v-c for k,(v,c) in vals.items()}
print(net,max(net,key=net.get))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $\mathbb{E}[U\mid c,e]$ | `v` |
| $Cost(c)$ | `c` |
| net value | `v-c` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Net value can peak before unlimited computation; more thinking can become irrational if it costs too much.

</details>

---

## Uncertain Human Preference Model
_Source slide: 11_

$$
P(\theta\mid choices,context)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“The probability of theta given choices and context.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\theta$ | human preferences |
| $\mid$ | given |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Represents uncertainty over what humans truly want.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use conceptually for assistance/alignment models that infer preferences.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The slide does not specify a full preference-learning model.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

If one preference hypothesis makes observed choices four times more likely than another, its posterior probability rises after normalization.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
prior={"fast":0.5,"safe":0.5}
like={"fast":0.2,"safe":0.8}
u={k:prior[k]*like[k] for k in prior}
z=sum(u.values())
print({k:v/z for k,v in u.items()})
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $P(\theta)$ | `prior` |
| $P(choices\mid\theta)$ | `like` |
| $P(\theta\mid choices)$ | `normalized posterior` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The posterior preserves uncertainty; that uncertainty can motivate asking or deferral.

</details>

---

## Planning Deductive Pattern
_Source slide: 14_

$$
Need(g),\;Achieves(a,g),\;Feasible(a)\Rightarrow Do(a)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Need g, achieves a g, feasible a, implies do a.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $g$ | goal |
| $a$ | action |
| $\Rightarrow$ | implies |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Seed of planning: reason from goals to feasible means.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use to connect logical inference to action choice.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Real planning must also handle resources, uncertainty, preferences, and time.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

If a goal is needed, an action achieves it, and it is feasible, the simplified rule licenses doing the action.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
need=True
achieves=True
feasible=True
print(need and achieves and feasible)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $Need(g)$ | `need` |
| $Achieves(a,g)$ | `achieves` |
| $Feasible(a)$ | `feasible` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

This is a schematic inference rule, not a full planning algorithm.

</details>

---

## Bayes Rule
_Source slide: 15_

$$
P(H\mid E)=\frac{P(E\mid H)P(H)}{P(E)}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Probability of H given E equals probability of E given H times probability of H divided by probability of E.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $H$ | hypothesis |
| $E$ | evidence |
| $P(H)$ | prior |
| $P(E\mid H)$ | likelihood |
| $P(H\mid E)$ | posterior |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Updates uncertain belief after observing evidence.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use when prior, likelihood, and evidence probability are available.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

$P(E)$ must be nonzero.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

0.8×0.1/0.2 = 0.4.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
p_h=0.1
p_e_h=0.8
p_e=0.2
print(p_e_h*p_h/p_e)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $P(H)$ | `p_h` |
| $P(E\mid H)$ | `p_e_h` |
| $P(E)$ | `p_e` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The result is updated belief, not certainty.

</details>

---

## Decision-Theory Action Rule
_Source slide: 17_

$$
a^*=\arg\max_a\sum_oP(o\mid a)U(o)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“a star equals arg max over a of the sum over outcomes o of probability of o given a times utility of o.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $o$ | outcome |
| $P(o\mid a)$ | outcome probability |
| $U(o)$ | outcome utility |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Decision theory combines probability and utility.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for uncertain choices with valued outcomes.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Requires probabilities and utilities.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

X: 0.6×100+0.4×20=68; Y: 65; choose X.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
acts={"X":[(0.6,100),(0.4,20)],"Y":[(1.0,65)]}
s={a:sum(p*u for p,u in xs) for a,xs in acts.items()}
print(s,max(s,key=s.get))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $P(o\mid a)$ | `p` |
| $U(o)$ | `u` |
| $\arg\max$ | `max(s,key=s.get)` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The rule values probability-weighted outcomes, not best-case outcome alone.

</details>

---

## Markov Decision Process Tuple
_Source slide: 17_

$$
M=\langle S,A,T,R,\gamma\rangle
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“M equals the tuple S, A, T, R, gamma.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $S$ | states |
| $A$ | actions |
| $T$ | transition model |
| $R$ | reward |
| $\gamma$ | discount factor |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Lists the components of an MDP.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use to formalize sequential decision problems linking planning, control, and RL.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The slide does not develop the Markov property formally.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

A two-state example can specify S={safe,risky}, A={stay,move}, and gamma=0.9.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
M={"S":["safe","risky"],"A":["stay","move"],"gamma":0.9}
print(M)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $S$ | `M["S"]` |
| $A$ | `M["A"]` |
| $\gamma$ | `M["gamma"]` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The tuple defines a problem, not its optimal policy.

</details>

---

## Bellman Optimality Equation
_Source slide: 17_

$$
V^*(s)=\max_a\left[R(s,a)+\gamma\sum_{s\prime}T(s,a,s\prime)V^*(s\prime)\right]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“V star of s equals max over actions a of reward R of s a plus gamma times the sum over next states s prime of transition T times V star of s prime.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $V^*(s)$ | optimal state value |
| $R(s,a)$ | immediate reward |
| $T(s,a,s\prime)$ | transition probability |
| $\gamma$ | discount |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Optimal value equals immediate reward plus discounted expected future optimal value.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for sequential decisions in an MDP.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Full solution algorithms are outside this lecture.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

If reward=5, next value=10, gamma=0.9, one-action backup=14.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
reward=5
gamma=0.9
next_value=10
print(reward+gamma*next_value)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $R(s,a)$ | `reward` |
| $\gamma$ | `gamma` |
| $V^*(s\prime)$ | `next_value` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Larger gamma gives more weight to future consequences.

</details>

---

## Generic Feedback Objective
_Source slide: 22_

$$
\min_{\pi}\mathbb{E}_{\pi}\left[\sum_{t=0}^{\infty}\gamma^tC(s_t,a_t)\right]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Minimize over policies pi the expected discounted sum from t equals zero to infinity of cost C of state s sub t and action a sub t.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\pi$ | policy |
| $C(s_t,a_t)$ | time-t cost |
| $\gamma^t$ | discount weight |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Stochastic optimal control minimizes expected cost over time.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for feedback-control decision sequences.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The dynamics are not fully specified on this introductory slide.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

Costs 10,4,2 with gamma 0.9 give 10+3.6+1.62=15.22.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
costs=[10,4,2]
gamma=0.9
print(sum((gamma**t)*c for t,c in enumerate(costs)))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $t$ | `enumerate index` |
| $\gamma^t$ | `gamma**t` |
| $C(s_t,a_t)$ | `c` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Lower is better. Future costs matter less when gamma<1.

</details>

---

## McCulloch-Pitts Style Neuron
_Source slide: 25_

$$
y=\mathbf{1}\left[\sum_{i=1}^{n}w_ix_i\ge\theta\right]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“y equals the indicator that the sum from i equals one to n of w sub i times x sub i is at least theta.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $x_i$ | input |
| $w_i$ | weight |
| $\theta$ | threshold |
| $\mathbf{1}$ | indicator |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Weighted threshold neuron fires when input exceeds threshold.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use as the historical neuron model in the lecture.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Binary output; historical simplification.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

Inputs [1,0,1], weights [0.6,0.2,0.7], threshold 1.0 → sum 1.3 → y=1.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
x=[1,0,1]
w=[0.6,0.2,0.7]
theta=1.0
score=sum(a*b for a,b in zip(w,x))
print(score,int(score>=theta))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $w_ix_i$ | `a*b` |
| $\sum$ | `sum(...)` |
| $\mathbf{1}$ | `int(score>=theta)` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Increasing positive weighted input can push the neuron across threshold.

</details>

---

## Hebbian Learning Intuition
_Source slide: 25_

$$
\Delta w_{ij}=\eta x_ix_j
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Delta w sub i j equals eta times x sub i times x sub j.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\Delta w_{ij}$ | weight change |
| $\eta$ | learning rate |
| $x_i,x_j$ | unit activities |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Co-active units strengthen their connection.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for the lecture's historical Hebbian intuition.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Not a complete modern learning model.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

eta=0.1, xi=1, xj=0.8 → delta=0.08.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
eta=0.1
xi=1.0
xj=0.8
print(eta*xi*xj)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $\eta$ | `eta` |
| $x_i$ | `xi` |
| $x_j$ | `xj` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

More co-activation or larger eta gives a larger update.

</details>

---

## Perceptron Prediction and Update
_Source slide: 27_

$$
\hat y=\mathbf{1}[w^\top x+b\ge0],\qquad w\leftarrow w+\eta(y-\hat y)x
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“y hat equals the indicator that w transpose x plus b is nonnegative; w is updated to w plus eta times y minus y hat times x.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\hat y$ | prediction |
| $w^\top x$ | dot product |
| $b$ | bias |
| $\eta$ | learning rate |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Linear classification plus an error-driven weight update.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for linearly separable binary classification.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

A single-layer perceptron cannot represent XOR.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

For a misclassified positive x=[1,1] at eta=.1, add .1*x to w.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
w=[-0.2,-0.2]
x=[1,1]
y=1
score=sum(a*b for a,b in zip(w,x))
yhat=int(score>=0)
eta=0.1
w=[wi+eta*(y-yhat)*xi for wi,xi in zip(w,x)]
print(yhat,w)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $w^\top x$ | `sum(a*b...)` |
| $\hat y$ | `yhat` |
| $w\leftarrow...$ | `list update` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The update shifts a linear boundary; it cannot overcome nonlinearly separable structure like XOR.

</details>

---

## Search Growth
_Source slide: 28_

$$
O(b^d)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Big O of b to the d.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $b$ | branching factor/actions per step |
| $d$ | search depth |
| $O$ | asymptotic growth |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Illustrates combinatorial explosion.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use to reason about naive search scaling.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Approximate general growth, not an exact runtime for every algorithm.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

b=10,d=6 → about 1,000,000 depth-d combinations.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
b=10
d=6
print(b**d)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $b$ | `b` |
| $d$ | `d` |
| $b^d$ | `b**d` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Adding one search level multiplies work by roughly b.

</details>

---

## Rule-Based Inference Schema
_Source slide: 29_

$$
C_1\land\cdots\land C_k\Rightarrow H\;(strength\ \alpha)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“C one and through C k imply H, with strength alpha.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $C_i$ | conditions |
| $\land$ | AND |
| $H$ | conclusion |
| $\alpha$ | rule strength |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Encodes expert knowledge as conditions leading to a conclusion.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use to understand expert-system inference.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

Strength alpha is not automatically a probability unless the system defines it that way.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

If fever AND positive culture, conclude infection with illustrative strength 0.8.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
fever=True
positive=True
alpha=0.8
if fever and positive:
    print("infection",alpha)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $C_1\land C_2$ | `fever and positive` |
| $H$ | `"infection"` |
| $\alpha$ | `alpha` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A rule can make a large domain-specific inference step.

</details>

---

## Gradient Learning Rule
_Source slide: 32_

$$
\theta\leftarrow\theta-\eta\nabla_{\theta}L(f_{\theta}(x),y)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Theta is updated to theta minus eta times the gradient with respect to theta of loss L of f theta of x and y.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\theta$ | parameters |
| $\eta$ | learning rate |
| $\nabla_\theta$ | gradient |
| $L$ | loss |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Moves parameters in a locally loss-reducing direction.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use as the generic optimization rule behind gradient learning/backpropagation.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The slide does not specify a particular loss or optimizer.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

For L=(theta-3)^2, theta=0, eta=.1, gradient=-6, new theta=.6.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
theta=0.0
eta=0.1
grad=2*(theta-3)
theta=theta-eta*grad
print(theta)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $\theta$ | `theta` |
| $\eta$ | `eta` |
| $\nabla L$ | `grad` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Learning rate controls step size; the lecture's main idea is parameter adjustment to reduce prediction error.

</details>

---

## Bayesian Network Factorization
_Source slide: 34_

$$
P(X_1,\ldots,X_n)=\prod_{i=1}^{n}P(X_i\mid Parents(X_i))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“The joint probability of X one through X n equals the product from i equals one to n of the probability of X i given its parents.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $X_i$ | random variable |
| $Parents(X_i)$ | parent variables |
| $\prod$ | product |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Conditional independence makes a large joint distribution manageable through local terms.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use for compact uncertainty modeling in Bayesian networks.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The graph must encode appropriate conditional independences.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

For A→B, P(A,B)=P(A)P(B|A); .2×.7=.14.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
p_a=0.2
p_b_a=0.7
print(p_a*p_b_a)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $P(A)$ | `p_a` |
| $P(B\mid A)$ | `p_b_a` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Factorization reduces representation complexity when conditional independence exists.

</details>

---

## Learning-Curve Intuition
_Source slide: 35_

$$
error(N)\approx\alpha N^{-\beta}+\epsilon_{\infty},\qquad\beta>0
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Error of N is approximately alpha times N to the negative beta plus epsilon infinity, with beta greater than zero.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $N$ | training-data size |
| $\alpha$ | scale constant |
| $\beta$ | positive exponent |
| $\epsilon_\infty$ | asymptotic error floor |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Captures decreasing error with more data and diminishing returns toward a floor.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use to understand data scale as a capability source.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The slide labels this as intuition, not a universal empirical law.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

alpha=1,beta=.5,eps=.1: N=100 gives .2; N=10000 gives .11.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
def err(n,a=1,b=.5,e=.1): return a*n**(-b)+e
print(err(100),err(10000))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $N$ | `n` |
| $\alpha$ | `a` |
| $\beta$ | `b` |
| $\epsilon_\infty$ | `e` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

More data reduces the decaying term, but the curve approaches the error floor.

</details>

---

## Deep-Learning Layer Computation
_Source slide: 36_

$$
h^{(\ell)}=\sigma(W^{(\ell)}h^{(\ell-1)}+b^{(\ell)}),\qquad\hat y=g(h^{(L)})
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“h superscript ell equals sigma of W superscript ell times h superscript ell minus one plus b superscript ell; y hat equals g of h superscript L.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $h^{(\ell)}$ | layer representation |
| $W^{(\ell)}$ | weight matrix |
| $b^{(\ell)}$ | bias |
| $\sigma$ | activation |
| $\hat y$ | prediction |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Each layer applies an adjustable transformation and nonlinearity, producing learned internal representations.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use to understand multilayer neural computation.

</details>

<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The slide does not prescribe a particular activation or output function.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Lecture

Scalar example: h0=2,W=.5,b=.1,ReLU → h1=1.1.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Lecture

```python
h0=2.0
W=0.5
b=0.1
h1=max(0.0,W*h0+b)
print(h1)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $h^{(\ell-1)}$ | `h0` |
| $W^{(\ell)}$ | `W` |
| $b^{(\ell)}$ | `b` |
| $\sigma$ | `max(0,...)` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Changing learned weights changes internal representation and downstream prediction.

</details>

## Mathematical Quality Check
- [x] All major lecture expressions reconstructed.
- [x] Spoken reading included for every block.
- [x] Symbols and operators explained.
- [x] Meaning and purpose explained.
- [x] Usage and assumptions included.
- [x] Worked examples included and labeled as illustrative.
- [x] Executable Python included.
- [x] Math → Python mapping included.
- [x] Interpretation included.
