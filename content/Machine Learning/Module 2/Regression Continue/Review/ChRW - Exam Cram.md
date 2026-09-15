# Exam Cram

## Tier 1 — MUST KNOW ⭐⭐⭐
- Linear prediction: $\hat y=w^Tx$.
- Normal Equation and its feature-count complexity limitation.
- Gradient Descent update $w_{next}=w-\eta\nabla MSE$.
- Effects of too-small vs too-large learning rate.
- Feature scaling requirement for Gradient Descent.
- Batch vs SGD vs Mini-batch.
- Underfitting vs overfitting learning curves.
- Ridge (L2), Lasso (L1), Elastic Net.
- Logistic sigmoid and 0.5 decision threshold.
- Softmax probability and argmax prediction.

## Tier 2 — VERY IMPORTANT ⭐⭐
- Bias vs variance vs irreducible error.
- Polynomial feature explosion $\binom{n+d}{n}$.
- SGD learning schedules and epochs.
- Early stopping.
- Cross entropy.

## Tier 3 — SUPPORTING ⭐
- Normal Equation complexity range $O(n^{2.4})$–$O(n^3)$.
- Figure-based interpretations: learning-rate paths, learning curves, iris decision boundary.

## Equation Cheat Sheet
$$RMSE=\sqrt{\frac1m\sum(\hat y-y)^2}$$
$$MSE=\frac1m\sum(w^Tx-y)^2$$
$$\hat w=(X^TX)^{-1}X^Ty$$
$$\nabla MSE=\frac2mX^T(Xw-y)$$
$$w_{next}=w-\eta\nabla MSE$$
$$J_{Ridge}=MSE+\alpha\sum w_i^2$$
$$J_{Lasso}=MSE+\alpha\sum|w_i|$$
$$\sigma(t)=\frac1{1+e^{-t}}$$
$$\hat p_k=\frac{e^{s_k}}{\sum_j e^{s_j}}$$

## Common Confusions
- Polynomial regression is nonlinear in features but still linear in weights.
- Lasso is the regularizer explicitly described as setting some weights to zero.
- Batch GD's “batch” means the full training set, not a mini-batch.
- Logistic regression is used here for classification probabilities despite its name.

## If You Only Remember 10 Things
1. Training finds $w$ that minimizes error.
2. Normal Equation is direct but expensive with many features.
3. Gradient Descent moves opposite the gradient.
4. Learning rate controls step size.
5. Scale features for Gradient Descent.
6. SGD trades smoothness for speed.
7. High complexity lowers bias but raises variance.
8. Ridge shrinks; Lasso can zero weights.
9. Early stopping uses validation error.
10. Logistic/softmax convert linear scores into class probabilities.

## 5-Minute Pre-Exam Review
Recite the GD update, compare the three GD variants, sketch underfit/overfit learning curves, state Ridge/Lasso/Elastic penalties, and explain why sigmoid's threshold corresponds to $x^Tw=0$.
