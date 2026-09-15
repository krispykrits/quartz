# Comparisons and Distinctions

| Topic | Key distinction |
|---|---|
| RMSE vs MAE | RMSE squares residuals before averaging/root; MAE averages absolute residuals. |
| Normal Equation vs GD | Normal Equation is closed-form; GD is iterative. |
| Batch vs SGD | Batch uses all training instances per update; SGD uses one random instance. |
| Mini-batch vs SGD | Mini-batch uses small random sets and is less erratic. |
| Underfitting vs overfitting | Underfitting: train/validation errors high and close; overfitting: low train error with a validation gap. |
| Bias vs variance | Bias comes from wrong model assumptions; variance from sensitivity to training-data variation. |
| Ridge vs Lasso | Ridge uses squared weights; Lasso uses absolute weights and tends to zero out least-important features. |
| Lasso vs Elastic Net | Elastic Net mixes L1 and L2 and is preferred by the lecture when n>m or features are strongly correlated. |
| Linear vs logistic regression | Linear regression predicts numeric values; logistic regression estimates class probabilities. |
| Logistic vs softmax | Logistic section handles binary classification; softmax directly supports multiple classes. |

## Gradient Descent Comparison
| Algorithm | Data per update | Path | Lecture tradeoff |
|---|---|---|---|
| Batch | Full set | Smooth | Slow for large training sets |
| SGD | One instance | Erratic | Fast; can escape local minima |
| Mini-batch | Small batch | Between Batch and SGD | Hardware-friendly matrix operations |
