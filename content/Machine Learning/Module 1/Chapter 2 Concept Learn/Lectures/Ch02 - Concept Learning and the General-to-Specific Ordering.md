---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Concept Learning and the General-to-Specific Ordering

_Source slides: 1-24_

## 🎯 Big Picture

This lecture develops the idea that **learning can be viewed as search through a hypothesis space**. The chapter focuses on concept learning, where the target is a Boolean-valued function and the learner must infer that target from labeled examples.

The EnjoySport example is used throughout the lecture to make the search process concrete. Hypotheses are conjunctions of constraints over six attributes. Because these hypotheses can be ordered from more specific to more general, learning algorithms can navigate the space without enumerating every possible hypothesis.

The lecture then contrasts [[Algorithms/FIND-S|FIND-S]] with [[Algorithms/Candidate Elimination|Candidate Elimination]]. FIND-S returns one maximally specific hypothesis that covers the positive examples, while Candidate Elimination maintains the entire [[Concepts/Consistency and Version Spaces|version space]] through the [[Concepts/S and G Boundaries|S and G boundaries]]. The final section introduces [[Concepts/Inductive Bias|inductive bias]] and argues that a learner cannot generalize beyond observed data without assumptions.

## Lecture Roadmap

Concept Learning  
↓  
Hypothesis Space $H$  
↓  
General-to-Specific Ordering  
↙　　　　　　　　　↘  
FIND-S　　　　　 Version Space  
　　　　　　　　　↓  
　　　　　　 S / G Boundaries  
　　　　　　　　　↓  
　　　　 Candidate Elimination  
　　　　　　　　　↓  
　　　　　 Active Queries  
　　　　　　　　　↓  
　　　　　 Inductive Bias

## What I Should Know After This Lecture

- Define concept learning and the target function $c:X\to\{0,1\}$.
- Explain the EnjoySport hypothesis representation.
- Read and interpret the more-general-than relation.
- Trace FIND-S on the EnjoySport data.
- Define consistency and version space.
- Explain the roles of the S and G boundaries.
- Trace Candidate Elimination through positive and negative examples.
- Explain how active queries can reduce the version space.
- Explain why an unrestricted hypothesis space does not remove the need for inductive bias.
- Compare the inductive biases of rote learning, Candidate Elimination, and FIND-S.

## ⏱️ 60-Second Lecture Summary

Concept learning learns a Boolean target $c:X\to\{0,1\}$ from labeled examples. The learner searches a hypothesis space $H$, and in EnjoySport the hypotheses are conjunctions of attribute constraints using specific values, `?`, or `∅`. The more-general-than relation imposes a partial ordering on $H$. FIND-S starts from the most specific hypothesis and minimally generalizes it to cover each positive example, ignoring negative examples. A version space contains every hypothesis consistent with the observed data. Candidate Elimination stores this space compactly through S, the maximally specific boundary, and G, the maximally general boundary. Positive examples generalize S; negative examples specialize G. Finally, the lecture argues that generalization requires inductive bias.

## 1. Concept Learning

See [[Concepts/Concept Learning|Concept Learning]].

The lecture defines concept learning as inferring a Boolean-valued function from training examples of its input and output.

$$
c:X\to\{0,1\}
$$

Training examples have the form:

$$
\langle x,c(x)\rangle
$$

The learner selects hypotheses from a hypothesis space $H$.

## 2. EnjoySport

See [[Concepts/EnjoySport Representation|EnjoySport Representation]].

| Ex. | Sky | AirTemp | Humidity | Wind | Water | Forecast | EnjoySport |
|---|---|---|---|---|---|---|---|
| 1 | Sunny | Warm | Normal | Strong | Warm | Same | Yes |
| 2 | Sunny | Warm | High | Strong | Warm | Same | Yes |
| 3 | Rainy | Cold | High | Strong | Warm | Change | No |
| 4 | Sunny | Warm | High | Strong | Cool | Change | Yes |

A hypothesis is a conjunction of six constraints. Each constraint may be:
- a specific value;
- `?`, meaning any value is accepted;
- `∅`, meaning no value is accepted.

Example:

$$
h=\langle Sunny, ?, ?, Strong, ?, Same\rangle
$$

## 3. The Inductive Learning Hypothesis

See [[Concepts/Inductive Learning Hypothesis|Inductive Learning Hypothesis]].

The lecture states that a hypothesis that approximates the target well over a sufficiently large set of training examples should also approximate the target over unobserved examples.

## 4. Concept Learning as Search

See [[Concepts/General-to-Specific Ordering|General-to-Specific Ordering]].

The lecture explicitly frames concept learning as search through a usually huge hypothesis space $H$.

For EnjoySport:

$$
5\cdot4\cdot4\cdot4\cdot4\cdot4=5120
$$

syntactically distinct hypotheses, but only

$$
1+(4\cdot3\cdot3\cdot3\cdot3\cdot3)=973
$$

semantically distinct hypotheses after hypotheses containing `∅` are merged by behavior.

The ordering is:

$$
h_j\ge_g h_k
\iff
\forall x\in X:[(h_k(x)=1)\to(h_j(x)=1)]
$$

## 5. FIND-S

See [[Algorithms/FIND-S|FIND-S]].

FIND-S starts at the most specific hypothesis and processes only positive examples. It minimally generalizes the current hypothesis whenever required to cover a new positive example.

Final EnjoySport result:

$$
\langle Sunny,Warm,?,Strong,?,?\rangle
$$

> [!warning]
> FIND-S ignores negative examples and does not show alternative hypotheses that may also be consistent with the data.

## 6. Version Spaces

See [[Concepts/Consistency and Version Spaces|Version Spaces]].

A hypothesis is consistent with $D$ if it classifies every training example correctly.

$$
VS_{H,D}
=
\{h\in H\mid Consistent(h,D)\}
$$

The naive [[Algorithms/List-Then-Eliminate|List-Then-Eliminate]] algorithm is correct but impractical for large $H$ because it requires exhaustive enumeration.

## 7. S and G Boundaries

See [[Concepts/S and G Boundaries|S and G Boundaries]].

- $G$: maximally general hypotheses in the version space.
- $S$: maximally specific hypotheses in the version space.

$$
VS_{H,D}
=
\{h\in H\mid
\exists s\in S,
\exists g\in G,
g\ge_g h\ge_g s\}
$$

The diagram on slide 17 places S at the bottom, G at the top, and the remaining consistent hypotheses between them. Its arrows point from specific toward more-general hypotheses.

## 8. Candidate Elimination

See [[Algorithms/Candidate Elimination|Candidate Elimination]].

Positive example:
- remove inconsistent members of G;
- minimally generalize inconsistent members of S.

Negative example:
- remove inconsistent members of S;
- minimally specialize inconsistent members of G.

After all four EnjoySport examples:

$$
S=
\{\langle Sunny,Warm,?,Strong,?,?\rangle\}
$$

$$
G=
\{
\langle Sunny,?,?,?,?,?\rangle,
\langle ?,Warm,?,?,?,?\rangle
\}
$$

Several hypotheses remain plausible, so more training examples or queries are required.

## 9. Choosing the Next Training Example

See [[Concepts/Active Learning and Query Selection|Active Learning and Query Selection]].

An active learner should request an instance that best discriminates among the remaining hypotheses. The lecture proposes choosing one satisfied by roughly half of the current version space. Either answer can then eliminate roughly half of the candidates.

## 10. Inductive Bias

See [[Concepts/Inductive Bias|Inductive Bias]].

A restricted $H$ may fail to represent the true concept. But using an unrestricted $H'$ containing every Boolean function does not solve generalization. The lecture argues that for unseen instances, the remaining hypotheses can still disagree evenly, so the data alone cannot determine a label.

> [!important]
> **A completely unbiased learner cannot generalize beyond observed examples.**

## Chapter Connections
- [[Mathematics/Ch02 - Mathematics|Mathematics]]
- [[Review/Ch02 - Concept Map|Concept Map]]
- [[Review/Ch02 - Exam Cram|Exam Cram]]
- [[Active Recall/Ch02 - Active Recall|Active Recall]]
