
title: Chapter 1 - Mathematics
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: mathematics
source: Mitchell 1997 Chapter 1 lecture
---
# Chapter 1 — Mathematics

This note collects every academically meaningful mathematical expression in the lecture and follows **Notation → Reading → Meaning → Usage → Calculation → Python → Interpretation**.

## Function mappings
_Source slide: 13_

$$\operatorname{ChooseMove}: X_{board}\to X_{move}$$
$$V:X_{board}\to\mathbb{R}$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
“Choose Move maps X sub board to X sub move.” “V maps X sub board to the real numbers.”
</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $X_{board}$ | Space of board states |
| $X_{move}$ | Space of moves |
| $\to$ | Maps to |
| $\mathbb R$ | Real numbers |
| $V$ | Board-value function |
</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>
The first function directly chooses a move; the second assigns a numerical score to a board. The lecture argues that learning V is easier.
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example — Not From Lecture

```python
def choose_move(board):
    return "example_move"

def V(board):
    return float(board["score"])
```
</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $X_{board}$ | `board` input |
| $\operatorname{ChooseMove}(b)$ | `choose_move(board)` |
| $V(b)$ | `V(board)` |
| $\mathbb R$ | `float` output |
</details>
<details><summary><strong>🎯 Interpretation</strong></summary>
`ChooseMove` outputs an action; V outputs a scalar evaluation. The scalar is not itself a move—it supports choosing one.
</details>

## Exact board-value function
_Source slide: 13_

$$
V(b)=\begin{cases}
100 & \text{if } b \text{ is a final, won board}\\
-100 & \text{if } b \text{ is a final, lost board}\\
0 & \text{if } b \text{ is a final, drawn board}\\
V(b') & \text{otherwise, where }b'\text{ is the best final board reachable from }b
\end{cases}
$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
“V of b equals one hundred if b is a final won board; negative one hundred if b is a final lost board; zero if b is a final drawn board; otherwise V of b prime, where b prime is the best final board reachable from b.”
</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $b$ | Current board |
| $b'$ | Best final board reachable from b |
| $V(b)$ | True value assigned to board b |
| 100 / -100 / 0 | Win / loss / draw terminal values |
</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>
Terminal boards have known values. A nonterminal board inherits the value of the best final outcome reachable from it.
</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>
It defines the ideal target the checkers learner would like to know. The lecture states it is not efficiently computable, so it motivates learning $\hat V$.
</details>
<details><summary><strong>⚠️ Assumptions / Conditions</strong></summary>
The terminal status and best reachable final outcome must be conceptually defined. The lecture's key practical condition is computational: exact evaluation is inefficient.
</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example — Not From Lecture

If b is a terminal draw, directly select the draw case: $V(b)=0$. If b is a terminal win, $V(b)=100$.
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example — Not From Lecture

```python
def terminal_value(result):
    return {"win": 100, "loss": -100, "draw": 0}[result]

print(terminal_value("draw"))  # 0
```
</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $V(b)=100$ | `"win": 100` |
| $V(b)=-100$ | `"loss": -100` |
| $V(b)=0$ | `"draw": 0` |
</details>
<details><summary><strong>🎯 Interpretation</strong></summary>
Positive terminal value means a win, negative means a loss, and zero a draw under the lecture's chosen scale. These values are utility scores, not probabilities or percentages.
</details>

## Linear approximation of board value
_Source slide: 14_

$$\hat V(b)=w_0+w_1x_1+w_2x_2+w_3x_3+w_4x_4+w_5x_5+w_6x_6$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
“V hat of b equals w sub zero plus w sub one x sub one plus w sub two x sub two plus w sub three x sub three plus w sub four x sub four plus w sub five x sub five plus w sub six x sub six.”
</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $\hat V(b)$ | Approximate value of board b |
| $w_0$ | Bias/intercept weight |
| $w_1,\ldots,w_6$ | Learnable feature weights |
| $x_1$ | # black pieces |
| $x_2$ | # red pieces |
| $x_3$ | # black kings |
| $x_4$ | # red kings |
| $x_5$ | # black pieces threatened by red |
| $x_6$ | # red pieces threatened by black |
</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>
Each feature contributes its value multiplied by a learned weight. The sum is the learner's estimate of how good the board is.
</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>
The exact V is impractical. A linear approximation has few parameters and can be learned from a realistic number of examples.
</details>
<details><summary><strong>⚠️ Assumptions / Conditions</strong></summary>
The chosen representation assumes the six features and a linear combination are adequate enough for useful approximation. The lecture explicitly frames this as a trade of expressive power for learnability.
</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example — Not From Lecture

Let $w=[1,2,-2,3,-3,-1,1]$ and $x=[1,8,7,2,1,1,2]$, with $x_0=1$.

$$\hat V(b)=1+2(8)-2(7)+3(2)-3(1)-1(1)+1(2)=7$$

The model assigns this board a value of 7 on its learned scoring scale.
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example — Not From Lecture

```python
import numpy as np
w = np.array([1, 2, -2, 3, -3, -1, 1], dtype=float)
x = np.array([1, 8, 7, 2, 1, 1, 2], dtype=float)  # x0 = 1
v_hat = np.dot(w, x)
print(v_hat)  # 7.0
```
</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $w_i$ | `w[i]` |
| $x_i$ | `x[i]` |
| $w_ix_i$ | `w[i] * x[i]` |
| $\sum_i w_ix_i$ | `np.dot(w, x)` |
| $\hat V(b)$ | `v_hat` |
</details>
<details><summary><strong>🎯 Interpretation</strong></summary>
A larger contribution $w_ix_i$ pushes the estimate according to the sign of $w_i$. The numerical score is a learned board evaluation, not a probability of winning unless an additional interpretation is supplied—which this lecture does not supply.
</details>

## Training-value rule
_Source slide: 15_

$$V_{train}(b)\leftarrow \hat V(\operatorname{Successor}(b))$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
“V sub train of b gets V hat of Successor of b.” The left arrow means the training value is assigned from the expression on the right.
</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $V_{train}(b)$ | Training target for board b |
| $\leftarrow$ | Is assigned / updated to |
| $\operatorname{Successor}(b)$ | Board following b in the game |
| $\hat V$ | Current approximate value function |
</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>
Because the true value of an intermediate board is unavailable, use the current estimated value of its successor as the training target. Values can therefore propagate backward from reliable game outcomes.
</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example — Not From Lecture

If the successor board currently has $\hat V=18$, then set $V_{train}(b)=18$.
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example — Not From Lecture

```python
successor_v_hat = 18.0
v_train = successor_v_hat
print(v_train)  # 18.0
```
</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $\hat V(\operatorname{Successor}(b))$ | `successor_v_hat` |
| $V_{train}(b)\leftarrow ...$ | `v_train = ...` |
</details>
<details><summary><strong>🎯 Interpretation</strong></summary>
The target is an estimate rather than directly observed truth for intermediate boards. The lecture says this works because errors can average out and end-game values propagate backward.
</details>

## Squared-error objective
_Source slide: 16_

$$E\equiv\sum_{\langle b,V_{train}(b)\rangle}\left(V_{train}(b)-\hat V(b)\right)^2$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
“E is defined as the sum over training pairs b and V sub train of b, of V sub train of b minus V hat of b, quantity squared.”
</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $E$ | Total squared error |
| $\equiv$ | Is defined as |
| $\sum$ | Sum over training examples |
| $V_{train}(b)$ | Target training value |
| $\hat V(b)$ | Predicted board value |
| $(\cdot)^2$ | Square of prediction error |
</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>
The objective measures mismatch between training targets and current predictions. Squaring prevents positive and negative errors from canceling and penalizes larger discrepancies more strongly.
</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>
The lecture uses this objective to fit the weights so V-hat matches the generated training values.
</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example — Not From Lecture

For targets $[10,5]$ and predictions $[8,7]$:
$$E=(10-8)^2+(5-7)^2=4+4=8.$$
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example — Not From Lecture

```python
import numpy as np
v_train = np.array([10.0, 5.0])
v_hat = np.array([8.0, 7.0])
E = np.sum((v_train - v_hat) ** 2)
print(E)  # 8.0
```
</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $V_{train}-\hat V$ | `v_train - v_hat` |
| $(...)^2$ | `(...) ** 2` |
| $\sum$ | `np.sum(...)` |
| $E$ | `E` |
</details>
<details><summary><strong>🎯 Interpretation</strong></summary>
$E=0$ means exact agreement on the supplied training pairs; larger E means greater aggregate squared discrepancy. It is an error objective, not an accuracy percentage.
</details>

## LMS weight update
_Source slide: 16_

$$w_i\leftarrow w_i+\eta\left(V_{train}(b)-\hat V(b)\right)x_i$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
“w sub i gets w sub i plus eta times V sub train of b minus V hat of b, times x sub i.”
</details>
<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $w_i$ | Weight for feature i |
| $\eta$ | Small learning rate |
| $V_{train}(b)-\hat V(b)$ | Prediction error |
| $x_i$ | Feature i value; slide specifies $x_0\equiv1$ |
</details>
<details><summary><strong>💡 Meaning & Purpose</strong></summary>
The update nudges each weight in proportion to prediction error, feature value, and learning rate. If V-hat underestimates the target, weights associated with positive features are nudged upward; the reverse occurs for overestimation.
</details>
<details><summary><strong>🧭 When / Why to Use It</strong></summary>
Apply incrementally to each generated training example to fit the linear board evaluator.
</details>
<details><summary><strong>⚠️ Assumptions / Conditions</strong></summary>
The slide specifies a **small** learning rate $\eta$ and $x_0\equiv1$.
</details>
<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example — Not From Lecture

Suppose $w_i=0.5$, $\eta=0.1$, $V_{train}=10$, $\hat V=8$, and $x_i=3$.
$$w_i\leftarrow0.5+0.1(10-8)(3)=1.1.$$
</details>
<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example — Not From Lecture

```python
w_i = 0.5
eta = 0.1
v_train = 10.0
v_hat = 8.0
x_i = 3.0
w_i = w_i + eta * (v_train - v_hat) * x_i
print(w_i)  # 1.1
```
</details>
<details><summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $w_i$ | `w_i` |
| $\eta$ | `eta` |
| $V_{train}(b)-\hat V(b)$ | `v_train - v_hat` |
| $x_i$ | `x_i` |
| $w_i\leftarrow...$ | `w_i = ...` |
</details>
<details><summary><strong>🎯 Interpretation</strong></summary>
The size of the update grows with $\eta$, the magnitude of the error, and $|x_i|$. A zero feature produces no update for that weight on that example. The update is a parameter adjustment, not itself the board score.
</details>
