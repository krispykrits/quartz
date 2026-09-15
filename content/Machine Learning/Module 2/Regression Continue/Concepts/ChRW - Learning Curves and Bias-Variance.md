# Learning Curves and Bias–Variance

**Source:** pp. 13–16.

## Learning Curves
Plots of training and validation performance versus training-set size. The lecture uses them to diagnose underfitting and overfitting.

### Underfitting
Figure 14: training and validation curves plateau close together and fairly high. Adding more examples will not fix an underfitting model; the lecture says to use a more complex model or better features.

### Overfitting
Figure 15: training error is much lower and a gap remains between training and validation error. More training data can bring the curves closer.

## Bias
Error due to wrong model selection; the lecture's example is assuming linear structure when the relationship is quadratic. High bias contributes to underfitting.

## Variance
Error from excessive sensitivity to variations in training data. Models with many degrees of freedom can have high variance and overfit.

## Irreducible Error
Error caused by data noise. The lecture points to fixing data sources or detecting/removing outliers.

> [!important]
> Increased complexity ⇒ variance increases and bias decreases.
