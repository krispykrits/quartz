---
title: "Chapter 1 Active Recall Answers"
type: answer-key
---

# Active Recall — Answer Key

1. Task, performance measure, and experience.
2. Unknown quantities are represented as random variables with probability distributions.
3. $f:\mathcal X\rightarrow\mathcal Y$.
4. $x$ is a feature/covariate/predictor; $y$ is a label/target/response.
5. Classification predicts discrete categories; regression predicts real values.
6. An $N\times D$ matrix with examples as rows and features as columns.
7. 1 if condition $e$ is true, otherwise 0.
8. Average loss on observed training examples.
9. The parameter/input value producing the minimum objective.
10. Because future/population performance is the objective; a model can overfit the training sample.
11. Lack of knowledge about the true mapping; model uncertainty.
12. Intrinsic irreducible stochasticity; data uncertainty.
13. An unconstrained class score before softmax.
14. It converts logits to nonnegative probabilities summing to one.
15. “Bias $b$ plus $w$ transpose $x$.”
16. Negative log-likelihood: negative average log probability assigned to observed outcomes.
17. Because $-\log p$ grows as $p$ becomes small.
18. Average squared residual.
19. Observed target minus predicted target.
20. With fixed variance, Gaussian NLL equals a positive scaling of MSE plus a constant.
21. Manually designing a feature transformation.
22. Low training risk but comparatively poor future/test performance.
23. Expected loss under the true data-generating distribution.
24. Population risk minus training risk.
25. Train fits parameters; validation selects model/complexity; test gives final unbiased evaluation.
26. No single model is best for every possible problem.
27. Unsupervised modeling is framed as $p(x)$; supervised prediction as $p(y\mid x)$.
28. Partitioning inputs into groups/regions of similar points.
29. Cluster count trades model complexity against fit; there need not be a uniquely correct answer.
30. An unobserved lower-dimensional variable explaining observed variation.
31. $\Sigma=\sigma^2I$.
32. Creating proxy prediction targets from unlabeled data itself.
33. Held-out NLL or downstream supervised-task performance.
34. “Action $a$ equals policy pi applied to state $x$.”
35. Determining which earlier actions caused later reward.
36. Represents a categorical value as an indicator vector.
37. Word order.
38. Corpus rarity based on document frequency.
39. Terms frequent in a document but comparatively uncommon across the corpus.
40. A learned dense vector representation of a word/token.
41. Out-of-vocabulary: a test-time word absent from the fixed vocabulary.
42. They exploit internal word structure rather than collapsing all unknown words to `UNK`.
43. MCAR: independent; MAR: depends on observed values; NMAR: depends on missing values.
44. MAR.
45. An optimizer exploits gaps in the specified objective rather than fulfilling the intended preference.
46. It exemplifies misalignment between what is optimized and what humans actually want.
47. Inferring reward from observed human behavior.
48. AI as a smart tool with a human in the loop, contrasted with autonomous AGI-style systems.
