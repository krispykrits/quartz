# Mathematics — Training Regression Models

**Source:** pp. 1–23. The equations below follow the lecture. Supplemental worked examples and Python snippets are explicitly labeled.

## RMSE — p. 2

$$RMSE(X,h)=\sqrt{\frac{1}{m}\sum_{i=1}^m(h(x^{(i)})-y^{(i)})^2}$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Root mean square prediction error: square each residual, average the squares, then take the square root.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $m$ | number of evaluated instances |
| $h(x^{(i)})$ | prediction for instance i |
| $y^{(i)}$ | true label |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> For errors 2 and -4, RMSE is sqrt((4+16)/2)=sqrt(10)≈3.162.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> np.sqrt(np.mean((y_pred - y)**2))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## MAE — p. 2

$$MAE(X,h)=\frac{1}{m}\sum_{i=1}^m|h(x^{(i)})-y^{(i)}|$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Mean absolute prediction error: take each residual magnitude and average them.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $|·|$ | absolute value / L1 norm |
| $m$ | number of instances |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> For errors 2 and -4, MAE=(2+4)/2=3.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> np.mean(np.abs(y_pred - y))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Linear Regression Prediction — p. 3

$$\hat y=w_0+w_1x_1+\cdots+w_nx_n=w^Tx$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: y-hat equals the bias plus the weighted features; in vector form, w transpose dot x.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $w_0$ | bias |
| $w_j$ | model parameter |
| $x_j$ | feature |
| $w^Tx$ | dot product |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> If x=(1,2), w=(4,3), then y-hat=4+3(2)=10.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> y_hat = w.T @ x
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## MSE — p. 3

$$MSE(w)=\frac{1}{m}\sum_{i=1}^m(w^Tx^{(i)}-y^{(i)})^2$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Average the squared differences between linear-model predictions and labels.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $w$ | parameter vector |
| $x^{(i)}$ | instance feature vector |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> For residuals 2 and -4, MSE=(4+16)/2=10.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> np.mean((X @ w - y)**2)
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Normal Equation — p. 3

$$\hat w=(X^TX)^{-1}X^Ty$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: w-hat equals the inverse of X-transpose X, times X-transpose, times y.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $X^T$ | transpose of X |
| $(X^TX)^{-1}$ | matrix inverse |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> Use the design matrix and targets to solve directly for the least-squares weights.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> w_hat = np.linalg.inv(X.T @ X) @ X.T @ y
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Batch GD Gradient — p. 7

$$\nabla_wMSE(w)=\frac{2}{m}X^T(Xw-y)$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: the gradient of MSE with respect to w equals two over m times X transpose times the residual vector.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $∇_w$ | gradient with respect to w |
| $Xw-y$ | residual vector |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> The gradient tells which direction increases MSE most rapidly; Gradient Descent moves opposite it.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> grad = (2/m) * X.T @ (X @ w - y)
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Gradient Descent Update — p. 8

$$w_{next}=w-\eta\nabla_wMSE(w)$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: next w equals current w minus learning rate eta times the MSE gradient.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $η$ | learning rate |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> If w=5, gradient=2, eta=.1, next w=4.8.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> w = w - eta * grad
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Polynomial Feature Count — p. 13

$$\binom{n+d}{n}=\frac{(n+d)!}{d!n!}$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: n plus d choose n; it counts the number of features after the stated polynomial transformation.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $n$ | original feature count |
| $d$ | polynomial degree |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> For n=2,d=2: 4!/(2!2!)=6 features, matching the lecture example.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> import math
count = math.factorial(n+d)//(math.factorial(d)*math.factorial(n))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Ridge Cost — p. 17

$$J(w)=MSE(w)+\alpha\sum_{i=1}^n w_i^2$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: Ridge cost equals MSE plus alpha times the sum of squared feature weights.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $α$ | regularization strength |
| $Σw_i²$ | L2 penalty |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> Larger alpha makes large weights more costly, producing flatter predictions in the lecture figure.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> J = mse + alpha * np.sum(w[1:]**2)
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Ridge Closed Form — p. 17

$$\hat w=(X^TX+\alpha I)^{-1}X^Ty$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: add alpha times the identity matrix to X transpose X before inversion.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $I$ | identity matrix |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> The added diagonal term penalizes large coefficients.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> w_hat = np.linalg.inv(X.T @ X + alpha*I) @ X.T @ y
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Lasso Cost — p. 18

$$J(w)=MSE(w)+\alpha\sum_{i=1}^n|w_i|$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: Lasso cost equals MSE plus alpha times the sum of absolute feature weights.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $Σ|w_i|$ | L1 penalty |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> The lecture emphasizes that this penalty can drive least-important weights exactly to zero.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> J = mse + alpha * np.sum(np.abs(w[1:]))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Elastic Net Cost — p. 19

$$J(w)=MSE(w)+r\alpha\sum_{i=1}^n|w_i|+\frac{1-r}{2}\alpha\sum_{i=1}^n w_i^2$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: MSE plus an r-weighted L1 penalty plus a one-minus-r weighted L2 penalty.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $r$ | mixing parameter |
| $α$ | overall regularization strength |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> r controls the balance between the Lasso-like and Ridge-like penalties.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> J = mse + r*alpha*np.sum(np.abs(w)) + ((1-r)/2)*alpha*np.sum(w**2)
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Sigmoid — p. 20

$$\sigma(t)=\frac{1}{1+\exp(-t)}$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: sigmoid of t equals one divided by one plus e raised to negative t.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $t$ | linear score |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> At t=0, sigma(0)=0.5, which explains the logistic decision threshold.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> p = 1 / (1 + np.exp(-t))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Logistic Probability — p. 20

$$\hat p=h_w(x)=\sigma(x^Tw)$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: predicted probability equals the sigmoid of the linear score x transpose w.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $p-hat$ | estimated probability |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> A positive score gives probability above .5; a negative score gives below .5.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> p_hat = 1/(1+np.exp(-(x.T @ w)))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Logistic Cost — p. 20

$$J(w)=-\frac{1}{m}\sum_{i=1}^m[y^{(i)}\log\hat p^{(i)}+(1-y^{(i)})\log(1-\hat p^{(i)})]$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: negative average binary log-likelihood over all training instances.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $y$ | binary target |
| $p-hat$ | predicted probability |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> Correct confident predictions have low cost; confident wrong predictions have high cost.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> J = -np.mean(y*np.log(p) + (1-y)*np.log(1-p))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Softmax Probability — p. 22

$$\hat p_k=\frac{\exp(s_k(x))}{\sum_{j=1}^K\exp(s_j(x))}$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: class-k probability is the exponential of its score divided by the sum of exponentiated scores for all classes.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $K$ | number of classes |
| $s_k$ | score for class k |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> The normalized probabilities sum to 1.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> p = np.exp(scores) / np.exp(scores).sum()
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Softmax Prediction — p. 23

$$\hat y=\arg\max_k\hat p_k=\arg\max_k s_k(x)$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: predict the class index with the largest probability, equivalently the largest score.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $arg max$ | argument/index producing the maximum |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> If scores are [1.2, 3.1, .4], predict class 2 (using one-based class naming).

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> y_hat = np.argmax(scores)
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>

## Softmax Cross Entropy — p. 23

$$J(w)=-\frac{1}{m}\sum_{i=1}^m\sum_{k=1}^K y_k^{(i)}\log(\hat p_k^{(i)})$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

Read: negative average, across instances, of target indicators times log predicted class probabilities.

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $y_k^{(i)}$ | 1 if instance i belongs to class k; otherwise 0 |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

This equation is used in the lecture's development of regression/classification training and evaluation.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use it in the setting identified by the section title and source page.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**  
> Only the true-class term contributes for one-hot targets.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
> ```python
> import numpy as np
> J = -np.mean(np.sum(Y * np.log(P), axis=1))
> ```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

The mathematical operations map directly to NumPy arithmetic, matrix multiplication (`@`), transposition (`.T`), summation, and elementwise functions as shown above.

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

Interpret the resulting scalar/vector according to the equation: as an error, parameter estimate, gradient/update, penalty, probability, or class decision.

</details>
