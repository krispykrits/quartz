# Chapter 2 Mathematics

Chapter 2 contains little equation-heavy mathematics, but it introduces the quantitative reason exhaustive testing fails and the abstract structures that later chapters formalize.

## Size of the Input Space

For three independent 32-bit integer inputs, each variable has:

$$
2^{32}
$$

possible bit patterns/values. Therefore the number of possible triples is:

$$
(2^{32})^3 = 2^{96}
$$

<details>
<summary><strong>📖 How to Read This Formula</strong></summary>

“Two to the thirty-second possibilities for each of three inputs, giving two to the ninety-sixth possible input combinations.”

</details>

<details>
<summary><strong>🔣 Notation & Symbols</strong></summary>

| Symbol | Meaning |
|---|---|
| $2^{32}$ | number of possible 32-bit patterns |
| $3$ | three independent input variables |
| $2^{96}$ | total number of input triples |

</details>

<details>
<summary><strong>💡 Meaning & Purpose</strong></summary>

The calculation illustrates why exhaustive testing is infeasible even for a tiny method. The chapter describes the result as more than 80 octillion possible inputs.

</details>

<details>
<summary><strong>🧭 When / Why to Use It</strong></summary>

Use input-space size calculations to understand why testing requires selection strategies such as coverage criteria instead of exhaustive enumeration.

</details>

<details>
<summary><strong>🧮 Worked Example</strong></summary>

> [!example]
> Illustrative Example - Not From Textbook

For two 8-bit inputs:

$$
(2^8)^2 = 2^{16} = 65{,}536
$$

Even reducing each variable to one byte quickly multiplies the number of combinations.

</details>

<details>
<summary><strong>🐍 Python Example</strong></summary>

> [!example]
> Illustrative Python Example - Not From Textbook

```python
values_per_int = 2**32
number_of_inputs = 3
combinations = values_per_int ** number_of_inputs
print(combinations)
```

</details>

<details>
<summary><strong>🔗 Math → Python Mapping</strong></summary>

| Mathematics | Python |
|---|---|
| $2^{32}$ | `2**32` |
| $(2^{32})^3$ | `(2**32)**3` |
| $2^{96}$ | `2**96` |

</details>

<details>
<summary><strong>🎯 Interpretation</strong></summary>

The lesson is not the exact number; it is that combinatorial growth makes exhaustive input testing impractical. This motivates [[Concepts/Ch02 - Coverage Criteria|Coverage Criteria]].

</details>

## Mathematical Abstraction in MDTD
Chapter 2 identifies four recurring structures:
- input domains;
- graphs;
- logic expressions;
- syntax descriptions/grammars.

These structures are the mathematical basis for later criteria. Figure 2.5 previews graph abstraction by converting a Java method into a control-flow graph and deriving edge-pair requirements.
