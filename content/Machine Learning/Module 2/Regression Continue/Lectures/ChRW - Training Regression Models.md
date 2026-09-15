# Training Regression Models

**Source pages:** 1–23  
**Author:** Anca Ralescu, University of Cincinnati

## Big Picture
The lecture develops regression training from notation and linear regression through optimization, polynomial regression, learning curves, regularization, and finally logistic/softmax regression. A central theme is learning a parameter vector $w$ that minimizes an error or cost function while controlling computational cost and generalization.

## Roadmap
1. Notation and error measures (pp. 1–2)
2. Linear regression and the Normal Equation (pp. 2–4)
3. Gradient Descent and its variants (pp. 5–11)
4. Polynomial regression and learning curves (pp. 12–15)
5. Bias, variance, and regularization (pp. 15–19)
6. Logistic regression, decision boundaries, and softmax (pp. 20–23)

## Learning Objectives
- Interpret $x^{(i)}$, $y^{(i)}$, $X$, $h$, $w$, MSE, RMSE, and MAE.
- Express linear regression in scalar and vectorized forms.
- Explain the Normal Equation and its computational tradeoffs.
- Explain learning rate, convergence, scaling, and Batch/SGD/Mini-batch GD.
- Recognize underfitting and overfitting from learning curves.
- Explain Ridge, Lasso, Elastic Net, and early stopping.
- Explain logistic decision boundaries and softmax multiclass prediction.

## 60-Second Lecture Summary
Linear regression predicts with a weighted sum of features and can be trained either by a closed-form Normal Equation or iterative Gradient Descent. Gradient Descent requires careful learning-rate choice and feature scaling; Batch, Stochastic, and Mini-batch variants trade stable updates against speed. Polynomial features let linear models represent nonlinear relationships but can cause overfitting. Learning curves expose under/overfitting, while Ridge, Lasso, Elastic Net, and early stopping regularize models. Logistic regression converts a linear score to a probability with the sigmoid function; softmax generalizes this idea to multiple classes.

## 1. Notation and Error Measures — pp. 1–2
The data is divided into **training, validation, and test sets**. $m$ is the number of instances in the dataset on which an error is measured. $x^{(i)}$ is the feature vector for instance $i$, $y^{(i)}$ its desired output, and $X$ is the matrix whose rows are the transposed feature vectors. The prediction function is $h$, with predicted output $\hat y^{(i)}=h(x^{(i)})$.

The lecture introduces RMSE and MAE. See [[Mathematics/ChRW - Mathematics|Mathematics]] for formula reading and worked examples.

## 2. Linear Regression — pp. 2–4
The simple model is
$$	ext{life satisfaction}=w_0+w_1	imes 	ext{GDP per capita}.$$
The general model is
$$\hat y=w_0+w_1x_1+\cdots+w_nx_n,$$
and, after extending each $x$ with a leading 1,
$$\hat y=h_w(x)=w^T\cdot x.$$
Training means finding $w$ so the error between predictions and labels is minimized.

### Normal Equation
The lecture gives the closed-form solution
$$\hat w=(X^TX)^{-1}X^Ty.$$
The inverse involves an $n	imes n$ matrix and costs roughly $O(n^{2.4})$ to $O(n^3)$, making it slow when the feature count is very large, while scaling linearly with the number of training instances. See [[Algorithms/ChRW - Normal Equation|Normal Equation]].

## 3. Gradient Descent — pp. 5–11
Gradient Descent iteratively changes $w$ to decrease the cost function. It starts with random parameter values and moves opposite the gradient.

### Learning rate $\eta$ — pp. 5–8
A small learning rate takes many iterations. A learning rate that is too large can overshoot or diverge. **Figure 8 (p. 8)** contrasts $\eta=0.02$, $0.1$, and $0.5$: the first progresses slowly, the middle converges quickly, and the last diverges.

> [!important]
> The lecture emphasizes feature scaling: if features have very different scales, the MSE bowl becomes elongated and Gradient Descent takes longer to converge (Figure 6, p. 6).

### Convexity and pitfalls
For linear-regression MSE, convexity and a continuous slope mean Gradient Descent can approach the global minimum when the learning rate is not too high. **Figure 7 (p. 7)** additionally illustrates general Gradient Descent pitfalls on irregular cost surfaces: local minima and plateaus.

> [!question]
> **Professor Question (p. 8):** How should the number of iterations be set?
>
> **Lecture answer:** Set a very large number but stop when the gradient norm becomes smaller than a small tolerance $\epsilon$.

### Batch Gradient Descent
$$
abla_w\mathrm{MSE}(w)=rac{2}{m}X^T(Xw-y),$$
$$w_{next}=w-\eta
abla_w\mathrm{MSE}(w).$$
It uses the entire training set at each step: slow for very large $m$, but it scales well with many features. See [[Algorithms/ChRW - Batch Gradient Descent|Batch Gradient Descent]].

### Stochastic Gradient Descent — pp. 9–10
SGD uses one random training instance per step. It is fast and memory-efficient but its cost bounces around the minimum. The lecture recommends gradually reducing the learning rate using a **learning schedule**, analogous to simulated annealing. See [[Algorithms/ChRW - Stochastic Gradient Descent|Stochastic Gradient Descent]].

### Mini-batch Gradient Descent — pp. 10–11
Mini-batch GD computes gradients on small random sets. It benefits from optimized matrix operations and is less erratic than SGD. **Figure 10 (p. 11)** shows Batch GD stopping at the minimum while SGD and Mini-batch continue walking around it. See [[Algorithms/ChRW - Mini-batch Gradient Descent|Mini-batch Gradient Descent]].

### Lecture comparison table — p. 11
| Algorithm | Large $m$ | Large $n$ | Hyperparameters | Scaling? |
|---|---|---|---|---|
| Normal Equation | fast | slow | 0 | No |
| Batch GD | slow | fast | 2 | yes |
| Stochastic GD | fast | fast | $\ge 2$ | yes |
| Mini-batch GD | fast | fast | $\ge 2$ | yes |

## 4. Polynomial Regression — pp. 12–13
Nonlinear data can be modeled with a linear model by adding powers and interaction terms as features. For one original feature, a quadratic expansion produces $(1,x_1,x_1^2)$. For two original features, the lecture shows $(1,x_1,x_2,x_1^2,x_2^2,x_1x_2)$.

> [!warning]
> `PolynomialFeatures(degree=d)` can create $inom{n+d}{n}=rac{(n+d)!}{d!n!}$ features. The lecture warns about combinatorial feature explosion.

**Figure 13 (p. 14)** compares degree 300, degree 2, and degree 1. The degree-300 curve wiggles around the samples and severely overfits; the straight line underfits; the quadratic model best matches the data-generating structure described in the lecture.

## 5. Learning Curves, Bias, and Variance — pp. 14–16
Learning curves plot training and validation performance against training-set size. **Figure 14 (p. 14)** shows underfitting: both curves plateau close together at relatively high error. **Figure 15 (p. 15)** shows a 10th-degree polynomial with lower training error and a gap to validation error, indicating overfitting.

The lecture decomposes generalization concerns into **bias**, **variance**, and **irreducible error**. Increasing model complexity tends to increase variance and decrease bias. See [[Concepts/ChRW - Learning Curves and Bias-Variance|Learning Curves and Bias–Variance]].

## 6. Regularization — pp. 17–19
The lecture presents three approaches: **Ridge**, **Lasso**, and **Elastic Net**.

### Ridge
$$J(w)=\mathrm{MSE}(w)+lpha\sum_{i=1}^n w_i^2.$$
Increasing $lpha$ produces flatter, less extreme predictions, reducing variance while increasing bias (Figure 16, p. 17).

### Lasso
$$J(w)=\mathrm{MSE}(w)+lpha\sum_{i=1}^n|w_i|.$$
Lasso tends to set the least important feature weights exactly to zero, automatically performing feature selection and creating a sparse model (p. 18).

### Elastic Net
$$J(w)=\mathrm{MSE}(w)+rlpha\sum_{i=1}^n|w_i|+rac{1-r}{2}lpha\sum_{i=1}^n w_i^2.$$
The lecture calls Elastic Net a middle ground between Ridge and Lasso and recommends it over Lasso when $n>m$ or features are strongly correlated.

### Early stopping
**Figure 18 (p. 19)** illustrates stopping training when validation error reaches its minimum; after that point validation error rises as overfitting begins. See [[Algorithms/ChRW - Early Stopping|Early Stopping]].

## 7. Logistic Regression — pp. 20–22
Logistic regression estimates probabilities:
$$\hat p=h_w(x)=\sigma(x^Tw),\qquad \sigma(t)=rac{1}{1+e^{-t}}.$$
The predicted class is 1 when $\hat p\ge0.5$, equivalently when $x^Tw\ge0$.

**Figure 21 (p. 21)** uses iris petal width. The lecture places the decision boundary around 1.6 cm, where the two probabilities are 0.5. Above it, the classifier predicts Iris-Virginica; below it, not Iris-Virginica. **Figure 22 (p. 22)** extends the boundary to petal-length/petal-width space.

## 8. Softmax Regression — pp. 22–23
Softmax generalizes logistic regression to multiple classes. Each class $k$ receives a score
$$s_k(x)=x^Tw^{(k)},$$
then probability
$$\hat p_k=rac{e^{s_k(x)}}{\sum_{j=1}^K e^{s_j(x)}}.$$
Prediction selects the class with the largest probability/score. Training uses cross entropy.

## Connections
- [[Concepts/ChRW - Linear Regression|Linear Regression]]
- [[Concepts/ChRW - Learning Curves and Bias-Variance|Learning Curves and Bias–Variance]]
- [[Concepts/ChRW - Regularization|Regularization]]
- [[Concepts/ChRW - Logistic and Softmax Regression|Logistic and Softmax Regression]]
- [[Mathematics/ChRW - Mathematics|Mathematics]]
- [[Review/ChRW - Exam Cram|Exam Cram]]
