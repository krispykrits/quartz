---
title: "Chapter 1 Why and How"
type: review
---

# Why and How

### Why use probability?

It gives a principled framework for uncertainty and a common mathematical language across ML and related fields.

### Why isn't training error enough?

Because the real objective is expected future loss. Flexible models can memorize or interpolate training observations without generalizing.

### Why softmax?

Raw logits are unrestricted real numbers. Softmax turns them into a valid categorical probability distribution.

### Why NLL?

It makes high probability on the observed outcome inexpensive and low probability expensive.

### Why does Gaussian MLE equal least squares?

For fixed variance, Gaussian NLL is MSE multiplied by a positive constant plus a theta-independent constant.

### Why can high-degree polynomials overfit?

More degrees of freedom allow increasingly exact training fits, including interpolation, while predictions between/away from observations can become unstable.

### Why validation and test?

Validation influences model selection. The test set must remain separate so it can estimate final performance without selection bias.

### Why no free lunch?

No model is universally best; performance depends on whether inductive bias matches the problem.

### Why is unsupervised evaluation hard?

There may be no provided target defining the uniquely correct discovered structure.

### Why self-supervision?

The data can create its own proxy targets, allowing useful representation learning without manual labels.

### Why is RL harder than ordinary supervised feedback?

Reward can be sparse and delayed, so the learner must solve credit assignment.

### Why TF-IDF?

Common corpus-wide words carry less discriminative information, so IDF downweights them.

### Why subwords?

They preserve internal structure of novel words rather than mapping every unseen word to the same `UNK` symbol.

### Why does missingness matter?

Different missing-data mechanisms imply different dependencies. Under NMAR, missingness depends on the hidden values themselves and must be modeled.
