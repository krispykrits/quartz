---
title: "Chapter 1 Practice Questions"
type: practice
---

# Practice Questions

## Definitions / Concepts

1. State Mitchell's definition of ML using T, P, and E.
2. Why does the lecture adopt a probabilistic perspective?
3. Distinguish classification and regression.
4. Define empirical risk.
5. Define population risk.
6. Distinguish epistemic and aleatoric uncertainty.
7. What is a latent factor?
8. What is self-supervised learning?
9. What is the RL credit-assignment problem?
10. Distinguish MCAR, MAR, and NMAR.

## Mathematics

11. Read $\hat\theta=\arg\min_\theta L(\theta)$ aloud and explain what `arg min` returns.
12. A classifier makes 8 errors on 40 examples. Compute misclassification rate.
13. Compute softmax for logits $[1,2,3]$.
14. Given $w=[2,3]$, $x=[4,5]$, and $b=1$, compute $b+w^Tx$.
15. Compute MSE for $y=[1,3,5]$ and $\hat y=[2,3,7]$.
16. Explain why fixed-variance Gaussian MLE and least squares choose the same parameters.
17. If training risk is 0.03 and population risk is 0.18, compute the generalization gap.
18. For $N=1000$ and $DF_i=99$, compute IDF.
19. If term frequency is 4, use the previous IDF to compute TF-IDF.
20. Explain $e=Ex$ when $x$ is a one-hot word vector.

## Figures / Reasoning

21. What does the Iris pair plot show about class separability?
22. Explain the decision-tree figure's relationship between tree splits and feature-space regions.
23. Explain the degree-2/14/20 polynomial figure.
24. What does the PCA plane in the 3D Iris figure represent?
25. Explain LeCun's cake analogy.

## Scenarios

26. You have labeled records and must predict one of four categories. Which paradigm/task?
27. You have unlabeled sensor readings and want recurring operating regimes. Which lecture concept?
28. Training error approaches zero while validation error rises. Diagnose the problem.
29. Survey nonresponse depends on the hidden sensitive answer. Which missingness mechanism?
30. A game gives reward only after hundreds of actions. What problem does this create?

## Answers

11. “Theta-hat equals the value of theta that minimizes $L$ of theta.” `arg min` returns the parameter value, not the minimum loss.

12. $8/40=0.20$.

13. Approximately $[0.090,0.245,0.665]$.

14. $1+2(4)+3(5)=24$.

15. Residuals $[-1,0,-2]$, squares $[1,0,4]$, MSE $=5/3\approx1.667$.

16. Gaussian NLL is a positive scaling of MSE plus a parameter-independent constant when variance is fixed.

17. $0.18-0.03=0.15$.

18. $\log(1000/100)=\log10\approx2.303$.

19. $\log(5)(2.303)\approx3.706$.

20. Multiplying the embedding matrix by a one-hot vector selects the corresponding dense embedding.

26. Supervised multiclass classification.

27. Unsupervised learning, specifically clustering.

28. Overfitting.

29. NMAR.

30. Credit assignment.
