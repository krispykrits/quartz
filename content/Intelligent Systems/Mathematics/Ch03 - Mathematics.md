# Chapter 3 - Mathematics
*Source: slides 21, 36, 39–42, 79, 86–92, 108.*

> [!note]
> Full formulas are reproduced only when exposed clearly by the lecture. Named equations whose full expression is not readable are not reconstructed from outside knowledge.

## Weighted Synaptic Summation
$$
s_i=\sum_j w_{ij}x_j
$$

<details><summary><strong>📖 How to Read This Formula</strong></summary>
The net input to neuron \(i\) is the sum of each incoming activity multiplied by its synaptic weight.
</details>

<details><summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| \(s_i\) | net input |
| \(w_{ij}\) | connection weight |
| \(x_j\) | incoming activity |

</details>

<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**
>
> \(x=[1,0,1]\), \(w=[0.8,-0.4,0.5]\) gives \(s=1.3\).

</details>

<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
```python
s = sum(wj*xj for wj, xj in zip(w, x))
```
</details>

## Basic Hebbian Update
$$
\Delta w_{ij}(t)=\eta y_j(t)y_i(t)
$$

<details><summary><strong>💡 Meaning & Purpose</strong></summary>
Co-activity strengthens the connection. The lecture warns that this form is dynamically unstable.
</details>

## Presynaptically Gated Hebbian Update
$$
\Delta w_{ij}(t)=\eta y_j(t)[y_i(t)-w_{ij}(t)]
$$

At convergence for binary activity:
$$
\bar w_{ij}
=
\frac{\langle y_jy_i\rangle}{\langle y_j\rangle}
=
\frac{p(y_i=1,y_j=1)}{p(y_j=1)}
=
p(y_i=1\mid y_j=1)
$$

<details><summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> **Illustrative Example - Not From Lecture**
>
> With \(\eta=0.1\), \(y_j=1\), \(y_i=1\), \(w=0.4\): \(\Delta w=0.06\), so \(w'=0.46\).

</details>

<details><summary><strong>🐍 Python Example</strong></summary>

> [!example]
> **Illustrative Python Example - Not From Lecture**
```python
w += eta * y_pre * (y_post - w)
```
</details>

## Postsynaptically Gated Hebbian Update
$$
\Delta w_{ij}(t)=\eta y_i(t)[y_j(t)-w_{ij}(t)]
$$
$$
\bar w_{ij}\approx p(y_j=1\mid y_i=1)
$$

## STDP Timing
$$
\Delta T=T_{post}-T_{pre}
$$
The lecture maps this timing difference to LTP/LTD but does not provide a full analytic curve.

## Electrical Membrane Model
$$
I_C=C\frac{dV_m}{dt}
$$
$$
I_{Na}=g_{Na}(V_m-V_{Na})
$$
$$
I_K=g_K(V_m-V_K)
$$
$$
I_{Cl}=g_{Cl}(V_m-V_{Cl})
$$

<details><summary><strong>💡 Meaning & Purpose</strong></summary>
Ionic current depends on conductance and the difference between membrane voltage and the ion's equilibrium/reversal voltage.
</details>

## Hodgkin-Huxley Conductances
$$
g_{Na}m^3h
$$
$$
g_Kn^4
$$

> [!note]
> Slide 79 names the Goldman-Hodgkin-Katz equation, but its complete expression is not recoverable from the exposed lecture text. Slide 108 similarly introduces transfer entropy without exposing a complete readable formula. Neither is invented here.
