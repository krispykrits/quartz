# Regularization

**Source:** pp. 17–19.

## Purpose
Regularization constrains model parameters to reduce overfitting. The lecture covers Ridge, Lasso, Elastic Net, and early stopping.

## Ridge (L2)
Adds $\alpha\sum w_i^2$. Larger $\alpha$ makes predictions flatter, reduces variance, and increases bias. Ridge shrinks weights rather than being presented as a feature-elimination method.

## Lasso (L1)
Adds $\alpha\sum|w_i|$. The lecture emphasizes that Lasso tends to set least-important weights to zero, automatically performing feature selection and producing a sparse model.

## Elastic Net
Combines L1 and L2 penalties using mixing parameter $r$. The lecture prefers Elastic Net to Lasso when $n>m$ or features are strongly correlated.

## Lecture Selection Guidance
- Avoid plain regression.
- Prefer Lasso or Elastic Net when only some features are suspected to be useful.
- Prefer Elastic Net to Lasso when $n>m$ or features are strongly correlated.

## Related
[[Algorithms/ChRW - Early Stopping|Early Stopping]] · [[Mathematics/ChRW - Mathematics|Mathematics]]
