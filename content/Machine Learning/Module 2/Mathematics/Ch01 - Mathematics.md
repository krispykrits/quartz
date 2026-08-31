---
title: "Chapter 1 Mathematics"
tags: [machine-learning, mathematics, chapter-01]
type: mathematics
---

# 🧮 Chapter 1 — Mathematics

> [!important]
> The equation stays visible. Expand the `<details>` blocks to study **Reading → Notation → Meaning → Usage → Calculation → Python → Interpretation**.



## Supervised mapping and training set


### Supervised mapping

_Source slide(s): 7_

$$
f:\mathcal X\rightarrow\mathcal Y
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$f$ maps the input space $\mathcal X$ to the output space $\mathcal Y$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $f$ — learned mapping/model.
- $\mathcal X$ — input space.
- $\mathcal Y$ — output space.
- $\rightarrow$ — maps to.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The expression states the supervised-learning problem abstractly: use a function to transform an input into an output.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** a function maps a petal-length measurement to a predicted class.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def f(petal_length):
    return "Setosa" if petal_length < 2.45 else "Other"

print(f(1.4))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $f$ → `f`
- input $x$ → `petal_length`
- output $y$ → returned class

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The code is one concrete instance of a mapping from an input domain to an output domain.

</details>

### Training set

_Source slide(s): 7_

$$
\mathcal D_{\text{train}}=\{(x_n,y_n)\}_{n=1}^{N}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The training dataset is the set of input-output pairs $x$ sub $n$, $y$ sub $n$, for $n$ from one through $N$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\mathcal D_{\text{train}}$ — training dataset.
- $x_n$ — features for example $n$.
- $y_n$ — target for example $n$.
- $N$ — number of examples.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Each supervised training example contains both an input and its desired output.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** three labeled flower examples give $N=3$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
training_data = [
    ([5.1, 3.5, 1.4, 0.2], "Setosa"),
    ([6.0, 2.9, 4.5, 1.5], "Versicolor"),
    ([6.5, 3.0, 5.8, 2.2], "Virginica"),
]
print(len(training_data))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $(x_n,y_n)$ → each tuple/list pair
- $N$ → `len(training_data)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The training set is the experience used to fit a supervised model.

</details>

### Design matrix

_Source slide(s): 11_

$$
X\in\mathbb R^{N\times D}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$X$ is an $N$ by $D$ real-valued matrix.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $X$ — design matrix.
- $N$ — examples/rows.
- $D$ — features/columns.
- $\mathbb R$ — real numbers.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Tabular numerical data can be organized with one example per row and one feature per column.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** two Iris-like rows with four features produce a $2\times4$ matrix.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
X = np.array([
    [5.1, 3.5, 1.4, 0.2],
    [6.0, 2.9, 4.5, 1.5],
])
print(X.shape)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $N$ → `X.shape[0]`
- $D$ → `X.shape[1]`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The matrix shape directly reports how many examples and features are represented.

</details>

### Image dimensionality

_Source slide(s): 11_

$$
D=C_{\text{channels}}D_1D_2
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$D$ equals the number of channels times dimension one times dimension two.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $C_{\text{channels}}$ — number of image channels.
- $D_1,D_2$ — spatial dimensions.
- $D$ — flattened input dimension.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Flattening an image creates one input feature for every channel-location combination.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For a $32\times32$ RGB image, $D=3\times32\times32=3072$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
channels = 3
height = 32
width = 32
D = channels * height * width
print(D)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- multiplication in formula → Python `*`
- $D$ → `D`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A small color image already has thousands of raw dimensions.

</details>


## Classification, decision rules, and loss


### Classification output space

_Source slide(s): 8_

$$
\mathcal Y=\{1,\ldots,C\}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The output space $\mathcal Y$ contains classes one through $C$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $C$ — number of classes.
- $\mathcal Y$ — set of allowed class labels.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Classification chooses among discrete, unordered, mutually exclusive classes.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For Iris, $C=3$: Setosa, Versicolor, Virginica.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
classes = ["Setosa", "Versicolor", "Virginica"]
C = len(classes)
print(C)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $C$ → `len(classes)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The mathematical labels can be mapped to human-readable category names.

</details>

### Decision rule

_Source slide(s): 14_

$$
f(x;\theta)=
\begin{cases}
\text{Setosa}, & x_{\text{petal length}}<2.45\\
\text{Versicolor or Virginica}, & \text{otherwise}
\end{cases}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$f$ of $x$ parameterized by theta predicts Setosa when petal length is less than 2.45; otherwise it predicts Versicolor or Virginica.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $x$ — flower features.
- $\theta$ — rule parameters, including feature and threshold.
- $2.45$ — lecture threshold.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

A threshold divides feature space into prediction regions.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

Lecture-grounded: if petal length is 1.4, then $1.4<2.45$, so predict Setosa.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def iris_rule(petal_length):
    return "Setosa" if petal_length < 2.45 else "Versicolor or Virginica"

print(iris_rule(1.4))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- inequality $x<2.45$ → `petal_length < 2.45`
- cases → Python conditional

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The rule is sufficient to isolate Setosa in the lecture example but not to separate the other two species.

</details>

### Misclassification rate

_Source slide(s): 16_

$$
L(\theta)=
\frac1N\sum_{n=1}^{N}
I[y_n\neq f(x_n;\theta)]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$L$ of theta equals one over $N$ times the sum from $n$ equals one to $N$ of the indicator that $y$ sub $n$ is not equal to the model prediction.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $L(\theta)$ — misclassification rate.
- $I[\cdot]$ — indicator, 1 if true and 0 otherwise.
- $y_n$ — true class.
- $f(x_n;\theta)$ — predicted class.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Count incorrect predictions and divide by the number of examples.

</details>


<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The lecture notes that this loss treats all mistakes as equally costly.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** one error among five predictions gives $L=1/5=0.20$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
y_true = ["cat", "cat", "dog", "dog", "cat"]
y_pred = ["cat", "dog", "dog", "dog", "cat"]
rate = sum(a != b for a, b in zip(y_true, y_pred)) / len(y_true)
print(rate)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $I[y_n\neq\hat y_n]$ → `a != b`
- $\sum$ → `sum(...)`
- $1/N$ → divide by `len(...)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A value of 0.20 means 20% of examples were misclassified.

</details>

### General empirical risk

_Source slide(s): 16_

$$
L(\theta)=
\frac1N\sum_n\ell(y_n,f(x_n;\theta))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$L$ of theta equals one over $N$ times the sum of the loss between each true target and model prediction.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\ell$ — per-example loss.
- $L$ — average dataset loss.
- Remaining symbols follow the supervised setup.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Generalizes zero-one loss so different kinds or magnitudes of mistakes can receive different costs.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** losses $[0.2,0.1,1.4,0.3]$ average to 0.5.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
losses = [0.2, 0.1, 1.4, 0.3]
risk = sum(losses) / len(losses)
print(risk)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\ell_n$ → entries of `losses`
- average → `sum(...) / len(...)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The empirical risk summarizes observed training cost under the selected loss function.

</details>

### Empirical risk minimization

_Source slide(s): 17_

$$
\hat\theta=\arg\min_\theta L(\theta)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Theta-hat equals the value of theta that minimizes $L$ of theta.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\hat\theta$ — fitted parameters.
- $\arg\min$ — argument/value producing the minimum.
- $L(\theta)$ — training objective.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Select parameter values with the smallest empirical risk.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** if losses for $\theta=1,2,3$ are 0.8, 0.42, 0.19, then $\hat\theta=3$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
losses = {1: 0.80, 2: 0.42, 3: 0.19}
theta_hat = min(losses, key=losses.get)
print(theta_hat)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\arg\min$ → `min(..., key=...)`
- $\theta$ → dictionary key

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The output is the best parameter value among the candidates—not the loss value itself.

</details>


## Predictive uncertainty and softmax


### Class probability constraints

_Source slide(s): 18_

$$
p(y=c\mid x;\theta)=f_c(x;\theta),
\qquad
0\leq f_c\leq1,
\qquad
\sum_{c=1}^{C}f_c=1
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The probability that $y$ equals class $c$, given $x$ and theta, equals the class-$c$ model output; each class output lies between zero and one, and the outputs sum to one.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $p(y=c\mid x;\theta)$ — conditional class probability.
- $f_c$ — model output for class $c$.
- $C$ — number of classes.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

A probabilistic classifier must output a valid categorical distribution.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** $[0.03,0.17,0.80]$ satisfies the constraints.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
probs = [0.03, 0.17, 0.80]
assert all(0 <= p <= 1 for p in probs)
assert abs(sum(probs) - 1.0) < 1e-12
print(probs)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- bounds → `0 <= p <= 1`
- $\sum f_c=1$ → `sum(probs)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The model can express both its preferred class and uncertainty over alternatives.

</details>

### Softmax

_Source slide(s): 19_

$$
\operatorname{softmax}(a)_c=
\frac{e^{a_c}}{\sum_{c'}e^{a_{c'}}}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Softmax of $a$ for class $c$ equals $e$ raised to $a$ sub $c$, divided by the sum over all classes $c$ prime of $e$ raised to $a$ sub $c$ prime.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $a_c$ — logit for class $c$.
- $e^{a_c}$ — exponentiated logit.
- denominator — sum over all class exponentials.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Converts arbitrary real-valued logits into nonnegative probabilities that sum to one.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For logits $[2,1,0]$, probabilities are approximately $[0.665,0.245,0.090]$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
a = np.array([2.0, 1.0, 0.0])
a = a - np.max(a)
exp_a = np.exp(a)
p = exp_a / exp_a.sum()
print(p)
print(p.sum())
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $e^{a_c}$ → `np.exp(a)`
- denominator → `exp_a.sum()`
- fraction → vector division

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The largest logit receives the largest probability, but every class probability depends on all logits.

</details>


## Negative log-likelihood and maximum likelihood


### Negative log probability loss

_Source slide(s): 21_

$$
\ell(y,f(x;\theta))=-\log p(y\mid f(x;\theta))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The loss equals the negative logarithm of the probability assigned to the observed target.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $p(\cdot)$ — probability assigned to the observed target.
- $\log$ — logarithm.
- leading minus sign — converts high probability into low loss.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Penalizes a model when it assigns low probability to what actually occurred.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** $-\log(0.9)\approx0.105$ but $-\log(0.1)\approx2.303$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import math
print(-math.log(0.9))
print(-math.log(0.1))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\log$ → `math.log`
- negative sign → unary `-`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Being confidently wrong is expensive under NLL.

</details>

### Dataset NLL

_Source slide(s): 21_

$$
NLL(\theta)=
-\frac1N\sum_{n=1}^{N}
\log p(y_n\mid f(x_n;\theta))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Negative log-likelihood of theta equals negative one over $N$ times the sum from $n$ equals one to $N$ of the log probability assigned to each observed target.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $NLL(\theta)$ — average negative log-likelihood.
- $N$ — number of examples.
- $p(y_n\mid f(x_n;\theta))$ — probability assigned to the observed target.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Aggregates negative log probability across the dataset.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** true-label probabilities $[0.9,0.7,0.8]$ produce their average negative log probability.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
p_true = np.array([0.9, 0.7, 0.8])
nll = -np.mean(np.log(p_true))
print(nll)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- per-example $\log p$ → `np.log(p_true)`
- $-1/N\sum$ → `-np.mean(...)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Lower NLL means the model gives greater probability, on average, to observed outcomes.

</details>

### MLE as NLL minimization

_Source slide(s): 21_

$$
\hat\theta_{\mathrm{mle}}=
\arg\min_\theta NLL(\theta)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Theta-hat M-L-E equals the value of theta that minimizes negative log-likelihood.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\hat\theta_{\mathrm{mle}}$ — maximum-likelihood estimate.
- $\arg\min$ — parameter value minimizing NLL.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Maximizing likelihood is equivalent to minimizing negative log-likelihood.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** choose the candidate parameter with the smallest NLL.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
candidate_nll = {"A": 0.8, "B": 0.42, "C": 0.55}
theta_mle = min(candidate_nll, key=candidate_nll.get)
print(theta_mle)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\arg\min$ → `min(..., key=...)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The chosen parameter setting makes the observed data most likely among the candidates.

</details>


## Regression, Gaussian likelihood, and polynomial models


### Affine linear model

_Source slide(s): 20, 25_

$$
f(x;\theta)=b+w^Tx
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$f$ of $x$ parameterized by theta equals bias $b$ plus $w$ transpose $x$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $w$ — weights/regression coefficients.
- $b$ — bias/intercept.
- $w^Tx$ — dot product.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Forms a prediction by adding weighted feature contributions and a constant offset.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

With $w=[2,-1]$, $x=[3,4]$, $b=5$: $5+2(3)-1(4)=7$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
w = np.array([2.0, -1.0])
x = np.array([3.0, 4.0])
b = 5.0
print(b + w @ x)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $w^Tx$ → `w @ x`
- $b+$ → `b +`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The weights determine feature influence; the bias shifts the prediction.

</details>

### Squared loss and MSE

_Source slide(s): 22_

$$
\ell_2(y,\hat y)=(y-\hat y)^2
$$

$$
MSE(\theta)=
\frac1N\sum_{n=1}^{N}
(y_n-f(x_n;\theta))^2
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“L-two loss equals actual minus predicted, squared. Mean squared error equals one over $N$ times the sum of those squared residuals.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $y_n$ — actual target.
- $f(x_n;\theta)$ or $\hat y_n$ — prediction.
- residual — $y_n-\hat y_n$.
- $N$ — number of examples.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Squaring prevents signs from canceling and penalizes large residuals more strongly.

</details>


<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The lecture notes that $\ell_1$ loss may be preferable when outliers are a concern.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

For $y=[3,5,7]$ and $\hat y=[2,5,9]$, MSE $=(1+0+4)/3\approx1.667$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
y = np.array([3.0, 5.0, 7.0])
y_hat = np.array([2.0, 5.0, 9.0])
residuals = y - y_hat
mse = np.mean(residuals ** 2)
print(residuals)
print(mse)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- residual → `y - y_hat`
- square → `** 2`
- $1/N\sum$ → `np.mean(...)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

MSE is in squared target units and is not an accuracy percentage.

</details>

### Gaussian likelihood

_Source slide(s): 24_

$$
\mathcal N(y\mid\mu,\sigma^2)=
\frac{1}{\sqrt{2\pi\sigma^2}}
\exp\left(-\frac{(y-\mu)^2}{2\sigma^2}\right)
$$

$$
p(y_n\mid x_n;\theta)=
\mathcal N(y_n\mid f(x_n;\theta),\sigma^2)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$y$ is Gaussian with mean mu and variance sigma squared; for regression, the mean is the model prediction $f$ of $x_n$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\mu$ — Gaussian mean.
- $\sigma^2$ — variance.
- $f(x_n;\theta)$ — predicted conditional mean.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Represents regression uncertainty by placing a Gaussian distribution around the predicted mean.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** evaluate the density at $y=5$, mean $4.5$, variance $1$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import math
y = 5.0
mu = 4.5
sigma2 = 1.0
density = (1 / math.sqrt(2 * math.pi * sigma2)
           * math.exp(-((y - mu) ** 2) / (2 * sigma2)))
print(density)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- square root → `math.sqrt`
- exponential → `math.exp`
- squared residual → `(y - mu) ** 2`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Values nearer the predicted mean receive greater density; variance controls spread.

</details>

### Gaussian NLL–MSE equivalence

_Source slide(s): 24_

$$
NLL(\theta)=
\frac{1}{2\sigma^2}MSE(\theta)+\text{const}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Negative log-likelihood equals mean squared error divided by two sigma squared, plus a constant.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\sigma^2$ — fixed Gaussian variance.
- `const` — terms not depending on $\theta$.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Shows why fixed-variance Gaussian maximum likelihood and least squares select the same parameters.

</details>


<details>
<summary><strong>⚠️ Assumptions / Conditions</strong></summary>

The lecture's equivalence assumes fixed variance $\sigma^2$.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

If MSE is 1.667 and $\sigma^2=2$, the theta-dependent NLL term is $1.667/4\approx0.417$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
mse = 1.6666666667
sigma2 = 2.0
theta_dependent_nll = mse / (2 * sigma2)
print(theta_dependent_nll)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $1/(2\sigma^2)$ → `/ (2 * sigma2)`
- MSE → `mse`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A positive scaling and theta-independent constant do not change the minimizing parameter values.

</details>

### Polynomial feature map and regression

_Source slide(s): 27_

$$
\phi(x)=[1,x,x^2,\ldots,x^D]
$$

$$
f(x;w)=w^T\phi(x)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Phi of $x$ contains one, $x$, $x$ squared, through $x$ to degree $D$; prediction equals $w$ transpose phi of $x$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\phi(x)$ — polynomial feature vector.
- $D$ — polynomial degree in this slide's notation.
- $w$ — coefficients.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Transforms the input into nonlinear features while keeping the model linear in its parameters.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For $x=4$, $\phi=[1,4,16]$ and $w=[2,3,0.5]$, prediction is $22$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
x = 4.0
phi = np.array([1.0, x, x**2])
w = np.array([2.0, 3.0, 0.5])
print(w @ phi)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\phi(x)$ → `phi`
- powers → `x**2`
- $w^T\phi$ → `w @ phi`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The model is nonlinear as a function of $x$ but linear as a function of $w$.

</details>

### Deep function composition

_Source slide(s): 30_

$$
f(x;\theta)=
f_L(f_{L-1}(\cdots f_1(x)\cdots))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$f$ is the composition of layer one through layer $L$, with each layer receiving the previous layer's output.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $f_1,\ldots,f_L$ — layer functions.
- $L$ — number of layers.
- $\theta$ — collection of parameters.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Deep neural networks construct complex functions by recursively composing simpler transformations.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** apply multiply-by-two, add-three, then square.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def f1(x): return 2 * x
def f2(x): return x + 3
def f3(x): return x ** 2
print(f3(f2(f1(4))))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- nested $f_L(f_{L-1}(...))$ → nested Python calls

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Each layer transforms the representation produced by the previous layer.

</details>


## Generalization and population risk


### Training risk

_Source slide(s): 31_

$$
L(\theta;\mathcal D_{\text{train}})
=
\frac{1}{|\mathcal D_{\text{train}}|}
\sum_{(x,y)\in\mathcal D_{\text{train}}}
\ell(y,f(x;\theta))
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Training risk equals average loss over every input-target pair in the training dataset.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $|\mathcal D_{\text{train}}|$ — training-set size.
- $\sum_{(x,y)\in\mathcal D}$ — sum over training pairs.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Measures observed performance on the sample used for fitting.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** average losses $[0.1,0.4,0.2,0.3]$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
losses = [0.1, 0.4, 0.2, 0.3]
train_risk = sum(losses) / len(losses)
print(train_risk)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- dataset cardinality → `len(losses)`
- average → `sum / len`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

This is observable, but it can underestimate future loss.

</details>

### Population risk

_Source slide(s): 31_

$$
L(\theta;p^*)=
\mathbb E_{p^*(x,y)}
[\ell(y,f(x;\theta))]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Population risk of theta under $p$ star equals the expected loss under the true joint distribution $p$ star of $x$ and $y$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $p^*$ — true unknown data-generating distribution.
- $\mathbb E$ — expectation.
- $\ell$ — loss.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Represents the true objective: expected loss on future data.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** a finite weighted expectation of losses.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
losses = [0.1, 0.5, 1.0]
probabilities = [0.5, 0.3, 0.2]
risk = sum(p * l for p, l in zip(probabilities, losses))
print(risk)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- expectation → weighted sum `sum(p * l ...)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Population risk is conceptually what we want to minimize, but the true distribution is unknown.

</details>

### Generalization gap

_Source slide(s): 31_

$$
L(\theta;p^*)-
L(\theta;\mathcal D_{\text{train}})
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Population risk minus training risk.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- first term — future/true expected loss.
- second term — observed training loss.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Measures how much worse the model is expected to perform beyond its training sample.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

If population risk is 0.19 and training risk is 0.04, the gap is 0.15.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
train_risk = 0.04
population_risk = 0.19
gap = population_risk - train_risk
print(gap)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- subtraction in formula → Python subtraction

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A large positive gap is characteristic of overfitting.

</details>


## Unsupervised learning and latent variables


### Unsupervised training set

_Source slide(s): 35_

$$
\mathcal D_{\text{train}}=\{x_n\}_{n=1}^{N}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The training dataset is the set of inputs $x$ sub $n$ for $n$ from one through $N$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $x_n$ — observed input.
- no $y_n$ appears because labels are not supplied.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Defines input-only training data.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** four unlabeled 2D observations.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
X = [[1.0, 1.2], [1.1, 1.0], [5.0, 5.2], [5.2, 4.9]]
print(len(X))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $x_n$ → each list element
- $N$ → `len(X)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The learner must exploit structure in the inputs themselves.

</details>

### Factor analysis

_Source slide(s): 38_

$$
p(x_n\mid z_n;\theta)=
\mathcal N(x_n\mid Wz_n+\mu,\Sigma)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$x$ sub $n$ given latent factor $z$ sub $n$ and theta is Gaussian with mean $Wz_n+\mu$ and covariance Sigma.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $z_n\in\mathbb R^K$ — latent factor.
- $x_n\in\mathbb R^D$ — observation.
- $W$ — linear mapping.
- $\mu$ — mean offset.
- $\Sigma$ — covariance.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Explains high-dimensional observations using lower-dimensional unobserved factors.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** map a 2D latent vector into a 3D observation-space mean.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
z = np.array([1.0, 2.0])
W = np.array([[1.0, 0.5], [0.2, 1.0], [1.5, -0.5]])
mu = np.array([0.1, 0.1, 0.1])
mean_x = W @ z + mu
print(mean_x)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $Wz$ → `W @ z`
- $+\mu$ → `+ mu`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The code computes the Gaussian mean; covariance describes residual variation around it.

</details>

### Probabilistic PCA covariance

_Source slide(s): 38_

$$
\Sigma=\sigma^2I
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Sigma equals sigma squared times the identity matrix.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $\sigma^2$ — common residual variance.
- $I$ — identity matrix.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Restricts residual covariance to isotropic noise; the lecture identifies this as probabilistic PCA.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** $D=3$, $\sigma^2=0.5$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
sigma2 = 0.5
D = 3
Sigma = sigma2 * np.eye(D)
print(Sigma)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $I$ → `np.eye(D)`
- scalar multiplication → `sigma2 *`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

All observed dimensions have equal residual variance and zero residual covariance.

</details>

### PCA reconstruction

_Source slide(s): 39_

$$
\hat x=Wz+\mu
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$x$-hat equals $Wz$ plus mu.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $z$ — low-dimensional coordinate.
- $W$ — basis/mapping.
- $\mu$ — mean.
- $\hat x$ — reconstructed observation.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Maps a latent coordinate back into observation space.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** reconstruct a 3D point from a 2D latent vector.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
W = np.array([[1.0, 0.0], [0.0, 1.0], [0.5, 0.5]])
z = np.array([2.0, 1.0])
mu = np.array([0.1, 0.1, 0.1])
x_hat = W @ z + mu
print(x_hat)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $Wz$ → `W @ z`
- $+\mu$ → `+ mu`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The reconstruction lies on the learned linear subspace translated by the mean.

</details>


## Self-supervised prediction


### Proxy prediction

_Source slide(s): 40_

$$
\hat x_1=f(x_2;\theta)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$x$-hat sub one equals $f$ of $x$ sub two parameterized by theta.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $x_2$ — observed/context portion.
- $x_1$ — held-out portion to predict.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Creates a supervised-style prediction task from unlabeled data itself.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** estimate a hidden scalar from surrounding context.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def predict_hidden(context):
    return sum(context) / len(context)
print(predict_hidden([2.0, 4.0, 6.0]))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $f(x_2;\theta)$ → function applied to context

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The training target comes from the data rather than a human label.

</details>


## Reinforcement-learning policy


### Policy

_Source slide(s): 43_

$$
a=\pi(x)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Action $a$ equals policy pi applied to state $x$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $x$ — state.
- $\pi$ — policy.
- $a$ — selected action.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Defines the agent's state-to-action mapping.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** fire when an enemy is visible; otherwise move.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def policy(state):
    return "fire" if state["enemy_visible"] else "move"
print(policy({"enemy_visible": True}))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $x$ → `state`
- $\pi$ → `policy`
- $a$ → returned action

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The policy determines behavior; RL learns it from interaction and reward.

</details>


## Data representation, text, and missingness


### One-hot encoding

_Source slide(s): 51_

$$
\operatorname{onehot}(x)=
[I[x=1],\ldots,I[x=K]]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“One-hot of $x$ is the vector of indicators for whether $x$ equals each category from one through $K$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $K$ — number of categories.
- $I[\cdot]$ — indicator.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Represents a category numerically without imposing an artificial numeric ordering.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For category 2 of 3, the vector is $[0,1,0]$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
K = 3
x = 2
one_hot = [int(x == k) for k in range(1, K + 1)]
print(one_hot)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $I[x=k]$ → `int(x == k)`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Exactly one position identifies the selected category.

</details>

### Bag-of-words count

_Source slide(s): 52_

$$
\tilde x_{nv}=
\sum_{t=1}^{T}I[x_{nt}=v]
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The bag-of-words count for document $n$ and vocabulary term $v$ equals the sum over token positions of the indicator that the token equals $v$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $T$ — token positions.
- $v$ — vocabulary term.
- $\tilde x_{nv}$ — term count.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Counts occurrences of each vocabulary term while discarding order.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For `machine learning uses machine learning`, machine=2, learning=2, uses=1.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
from collections import Counter
doc = "machine learning uses machine learning".split()
print(Counter(doc))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- indicator-sum counting → `Counter`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The representation captures frequency but loses sequence/order information.

</details>

### Inverse document frequency

_Source slide(s): 53_

$$
IDF_i=
\log\frac{N}{1+DF_i}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“IDF for term $i$ equals the logarithm of $N$ divided by one plus document frequency $DF_i$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $N$ — number of documents.
- $DF_i$ — number of documents containing term $i$.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Downweights words that appear in many documents.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For $N=1000$, $DF_i=99$: $IDF_i=\log(10)\approx2.303$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import math
N = 1000
DF_i = 99
idf = math.log(N / (1 + DF_i))
print(idf)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\log$ → `math.log`
- fraction → `/`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Rarer terms receive larger IDF values.

</details>

### TF-IDF

_Source slide(s): 53_

$$
TFIDF_{ij}=
\log(TF_{ij}+1)\times IDF_i
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“TF-IDF for term $i$ in document $j$ equals log of term frequency plus one, multiplied by IDF for term $i$.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $TF_{ij}$ — count/frequency of term $i$ in document $j$.
- $IDF_i$ — inverse document frequency.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Balances local term frequency against corpus-wide commonness.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

For $TF=4$ and $IDF\approx2.303$, TF-IDF is about $3.706$.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import math
tf = 4
idf = math.log(1000 / (1 + 99))
tfidf = math.log(tf + 1) * idf
print(tfidf)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $\log(TF+1)$ → `math.log(tf + 1)`
- multiplication → `* idf`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A term scores highly when it appears in the document but is relatively uncommon across the corpus.

</details>

### Word embedding

_Source slide(s): 53_

$$
e_{nt}=Ex_{nt}\in\mathbb R^K,
\qquad
E\in\mathbb R^{K\times V}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Embedding $e$ sub $n t$ equals embedding matrix $E$ times one-hot vector $x$ sub $n t$, producing a $K$-dimensional real vector.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $V$ — vocabulary size.
- $K$ — embedding dimension.
- $E$ — embedding matrix.
- $x_{nt}$ — one-hot word vector.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Multiplying by a one-hot vector selects the corresponding dense embedding column.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** select the second of three vocabulary embeddings.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
E = np.array([[1.0, 0.2, 0.7],
              [0.1, 0.8, 0.4]])
x = np.array([0.0, 1.0, 0.0])
e = E @ x
print(e)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $Ex$ → `E @ x`
- $e$ → `e`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

A sparse vocabulary representation becomes a lower-dimensional dense vector.

</details>

### Document embedding

_Source slide(s): 53_

$$
e_n=\sum_t e_{nt}=E\tilde x_n
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Document embedding $e$ sub $n$ equals the sum of its token embeddings, equivalently $E$ times the bag-of-words vector.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $e_{nt}$ — token embedding.
- $\tilde x_n$ — bag-of-words vector.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Aggregates word embeddings into a simple document representation.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** multiply an embedding matrix by term counts.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
E = np.array([[1.0, 0.2, 0.7],
              [0.1, 0.8, 0.4]])
bow = np.array([2.0, 1.0, 0.0])
e_n = E @ bow
print(e_n)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $E\tilde x_n$ → `E @ bow`

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The document representation is a weighted sum of vocabulary embeddings.

</details>

### Embedded-text classifier

_Source slide(s): 53_

$$
p(y=c\mid x_n,\theta)=
\operatorname{softmax}_c(WE\tilde x_n)
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The probability that $y$ equals class $c$, given document $x_n$ and theta, is the class-$c$ softmax of $W E$ times the bag-of-words vector.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $E\tilde x_n$ — embedded document.
- $W$ — class-score weights.
- softmax — probability normalization.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Combines bag-of-words, embeddings, linear class scores, and softmax into one classifier.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** compute a two-class probability vector.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
import numpy as np
E = np.array([[1.0, 0.2, 0.7],
              [0.1, 0.8, 0.4]])
bow = np.array([2.0, 1.0, 0.0])
W = np.array([[1.0, -0.5],
              [-0.2, 0.9]])
logits = W @ (E @ bow)
exp_logits = np.exp(logits - np.max(logits))
probs = exp_logits / exp_logits.sum()
print(probs)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- $E\tilde x_n$ → `E @ bow`
- $W(...)$ → `W @ (...)`
- softmax → exponentiate and normalize

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The expression links several representation and classification ideas introduced earlier in the lecture.

</details>

### Missing-data indicator

_Source slide(s): 55_

$$M_{nd}=1\quad\text{if feature $d$ of example $n$ is missing}$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“$M$ sub $n d$ equals one when feature $d$ of example $n$ is missing.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $M$ — missingness indicators.
- $X_v$ — visible/observed values.
- $X_h$ — hidden/missing values.
- $Y$ — target.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The indicator records the missingness pattern.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** the code demonstrates the dependency structure conceptually.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
value = None
M_nd = int(value is None)
print(M_nd)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- conditional dependency in the equation → function arguments used by the probability model

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The indicator records the missingness pattern.

</details>

### MCAR

_Source slide(s): 55_

$$p(M\mid X_v,X_h,Y)=p(M)$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“The probability of missingness given visible features, hidden features, and the target equals the unconditional probability of missingness.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $M$ — missingness indicators.
- $X_v$ — visible/observed values.
- $X_h$ — hidden/missing values.
- $Y$ — target.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

Missingness is independent of the data.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** the code demonstrates the dependency structure conceptually.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
p_missing = 0.10
def p_M_mcar(X_v, X_h, Y):
    return p_missing
print(p_M_mcar(1, 100, 0))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- conditional dependency in the equation → function arguments used by the probability model

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Missingness is independent of the data.

</details>

### MAR

_Source slide(s): 55_

$$p(M\mid X_v,X_h,Y)=p(M\mid X_v,Y)$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: **“Missingness given visible features, hidden features, and target equals missingness given only visible features and target.”**

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

- $M$ — missingness indicators.
- $X_v$ — visible/observed values.
- $X_h$ — hidden/missing values.
- $Y$ — target.

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

After conditioning on observed information, missingness does not additionally depend on hidden missing values.

</details>


<details>
<summary><strong>🧮 Worked Example</strong></summary>

**Illustrative Example (not from lecture):** the code demonstrates the dependency structure conceptually.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def p_M_mar(observed_age, Y):
    return 0.15 if observed_age < 25 else 0.05
print(p_M_mar(20, 0))
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

- conditional dependency in the equation → function arguments used by the probability model

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

After conditioning on observed information, missingness does not additionally depend on hidden missing values.

</details>


### NMAR

_Source slide: 55_

The lecture states that under **NMAR**, missingness depends on the missing values themselves.

<details>
<summary><strong>📖 How to Read This Idea</strong></summary>

Read: **“Not missing at random: whether a value is missing can depend on the value that is itself unobserved.”**

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The missing-data mechanism cannot be ignored because the hidden value influences whether it becomes missing.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

```python
def p_missing_nmar(hidden_value):
    return 0.60 if hidden_value > 8 else 0.10

print(p_missing_nmar(9))
print(p_missing_nmar(3))
```

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The example deliberately makes missingness depend on the unobserved value, matching the lecture's conceptual definition of NMAR.

</details>
