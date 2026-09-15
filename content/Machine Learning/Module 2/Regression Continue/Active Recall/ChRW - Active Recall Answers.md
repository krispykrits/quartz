# Active Recall Answers

1. **The number of instances in the dataset on which the error is being measured.**
2. **The feature vector and desired label for training instance i.**
3. **The matrix containing feature values for all instances, one instance per row.**
4. **It is the prediction function/hypothesis.**
5. **RMSE squares residuals, averages, then takes a square root; MAE averages absolute residuals.**
6. ** $\hat y=w_0+w_1x_1+\cdots+w_nx_n=w^Tx$.**
7. **Find parameter values $w$ that minimize the error between predictions and targets.**
8. ** $\hat w=(X^TX)^{-1}X^Ty$.**
9. **It must invert an n×n matrix, with complexity stated as roughly $O(n^{2.4})$ to $O(n^3)$.**
10. **Iteratively tweak parameters to reduce a cost function by moving in the direction of descending gradient.**
11. **Convergence is slow and requires many iterations.**
12. **It may overshoot/miss the solution and can diverge.**
13. **Different scales elongate the cost surface and make convergence much slower.**
14. ** $\nabla_wMSE=\frac{2}{m}X^T(Xw-y)$.**
15. ** $w_{next}=w-\eta\nabla_wMSE(w)$.**
16. **Use a large iteration count but stop when the gradient norm falls below tolerance $\epsilon$.**
17. **For convex smooth MSE with fixed learning rate, the lecture states $O(1/iterations)$; dividing tolerance by 10 requires about 10× more iterations.**
18. **SGD computes each gradient from one random instance rather than the whole training set.**
19. **Its randomness can help it jump out of local minima.**
20. **A function that determines the learning rate at each iteration.**
21. **A round of m SGD iterations.**
22. **Mini-batch GD computes gradients on small random sets rather than one instance.**
23. **Add powers/interactions as new features, then train a linear model on the expanded features.**
24. **The number of features can grow as $\binom{n+d}{n}$, causing combinatorial explosion.**
25. **Training and validation errors plateau close together and fairly high.**
26. **Training error is much lower than validation error, creating a gap.**
27. **Bias: error from wrong model selection; variance: sensitivity to training variations; irreducible error: noise in data.**
28. **Variance increases and bias decreases.**
29. **Ridge uses L2 squared weights; Lasso uses L1 absolute weights and tends to zero least-important weights; Elastic Net mixes both.**
30. **Logistic uses sigmoid and threshold 0.5 (score 0); softmax computes normalized probabilities for multiple classes and predicts the argmax.**
