# Hebbian Learning Rules
*Source: slides 35–41.*

## Basic Hebb Rule
$$
\Delta w_{ij}(t)=\eta y_j(t)y_i(t)
$$
**Intuition:** "Neurons that fire together wire together."  
**Lecture limitation:** dynamically unstable.

## Presynaptically Gated Rule
$$
\Delta w_{ij}(t)=\eta y_j(t)[y_i(t)-w_{ij}(t)]
$$
For binary activity:
$$
\bar w_{ij}\approx p(y_i=1\mid y_j=1)
$$

## Postsynaptically Gated Rule
$$
\Delta w_{ij}(t)=\eta y_i(t)[y_j(t)-w_{ij}(t)]
$$
For binary activity:
$$
\bar w_{ij}\approx p(y_j=1\mid y_i=1)
$$

## Why the Gated Rule Stabilizes
For small \(\eta\), the term \(y-w\) pulls the weight toward the bounded activity value rather than adding an unrestricted positive increment.

> [!example]
> **Illustrative Python Example - Not From Lecture**
```python
def pre_gated(w, y_pre, y_post, eta):
    return w + eta * y_pre * (y_post - w)
```
