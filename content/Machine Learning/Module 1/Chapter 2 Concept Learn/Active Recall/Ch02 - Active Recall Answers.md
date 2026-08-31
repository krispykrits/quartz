---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Active Recall Answers

1. Inferring a Boolean-valued function from training examples of its input and output.
2. $c:X\to\{0,1\}$.
3. The set of possible input instances.
4. The set of candidate hypotheses available to the learner.
5. Any value is acceptable at that attribute.
6. No value is acceptable; a hypothesis containing it rejects every instance.
7. A hypothesis that approximates the target well on a sufficiently large training set is expected to approximate it well on unobserved examples.
8. Every instance accepted by $h_k$ is also accepted by $h_j$.
9. It lets algorithms navigate H by generalization and specialization instead of enumerating every hypothesis.
10. The most specific hypothesis in H.
11. Negative examples.
12. $\langle Sunny,Warm,?,Strong,?,?\rangle$.
13. Negative examples can eliminate hypotheses that fit positives but wrongly accept negatives; FIND-S never uses that evidence.
14. A hypothesis is consistent with D if it agrees with every labeled example in D.
15. $VS_{H,D}=\{h\in H\mid Consistent(h,D)\}$.
16. The maximally specific consistent boundary.
17. The maximally general consistent boundary.
18. Every version-space hypothesis lies between some S member and some G member under the general-to-specific ordering.
19. Prune inconsistent G members and minimally generalize inconsistent S members.
20. Prune inconsistent S members and minimally specialize inconsistent G members.
21. $S=\{\langle Sunny,Warm,?,Strong,?,?\rangle\}$ and $G=\{\langle Sunny,?,?,?,?,?\rangle,\langle ?,Warm,?,?,?,?\rangle\}$.
22. When $S=G=\{h\}$.
23. No hypothesis in H is consistent with all observed data.
24. Either possible label can eliminate roughly half of the remaining hypotheses.
25. When every hypothesis in the current version space agrees on the classification.
26. If the target is not representable in H, enough data can eliminate every hypothesis in H.
27. For unseen instances, consistent hypotheses can still disagree on the label; the data alone cannot choose between them.
28. The extra assumptions beyond observed data that enable predictions on unseen instances.
29. Candidate Elimination assumes $c\in H$. FIND-S has that assumption plus a stronger preference reflected by treating unseen instances as negative unless positivity is entailed by its learned hypothesis.
30. Representation determines what can be expressed; ordering structures search; version spaces preserve remaining uncertainty; inductive bias provides the assumptions needed to generalize.
