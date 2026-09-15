# Why and How

## Why does feature scaling matter for Gradient Descent?
Different feature scales elongate the MSE cost surface, making the path toward the minimum slower. The lecture recommends similar feature scales, e.g. `StandardScaler`.

## Why can learning rate be too small or too large?
Too small means slow convergence; too large can overshoot the solution or diverge.

## How does Batch Gradient Descent update parameters?
It computes the gradient using all training instances and subtracts $\eta$ times that gradient from $w$.

## Why use SGD?
It avoids computing a full-data gradient at every step, making updates much faster and allowing huge datasets to be trained with little data in memory per iteration.

## Why reduce SGD's learning rate over time?
Large early steps help progress/escape local minima; smaller later steps reduce bouncing near the minimum.

## Why can polynomial regression overfit?
High-degree feature expansion gives the model many degrees of freedom, allowing it to follow training noise.

## How do learning curves diagnose underfitting?
Training and validation errors plateau close together at relatively high values.

## How do they diagnose overfitting?
Training error is much lower than validation error, leaving a gap.

## Why does Ridge reduce variance?
Its L2 penalty discourages large weights; the lecture shows larger alpha producing flatter predictions, trading lower variance for higher bias.

## Why does Lasso perform feature selection?
The lecture states that its L1 penalty tends to drive least-important weights completely to zero.

## Why use Elastic Net?
It provides a middle ground between Ridge and Lasso; the lecture prefers it to Lasso when $n>m$ or features are strongly correlated.

## How does early stopping regularize?
Training is stopped at the minimum validation error, before validation performance worsens from overfitting.

## How does logistic regression make a class decision?
It applies sigmoid to $x^Tw$ and predicts class 1 when probability is at least 0.5, equivalent to $x^Tw\ge0$.

## How does softmax support multiple classes?
It computes one score per class, normalizes the exponentials of those scores into probabilities, and chooses the largest.
