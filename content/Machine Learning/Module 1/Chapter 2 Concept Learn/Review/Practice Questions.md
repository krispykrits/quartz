---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Practice Questions

1. Define concept learning.
2. What do $X$, $c$, $h$, and $H$ mean?
3. What does `?` mean in an EnjoySport hypothesis?
4. What does `∅` mean?
5. State the inductive learning hypothesis.
6. Read aloud the general-to-specific ordering equation.
7. Explain what $h_j\ge_g h_k$ means.
8. Why are there fewer semantic than syntactic EnjoySport hypotheses?
9. Trace FIND-S through all four EnjoySport examples.
10. Why is the third example ignored by FIND-S?
11. What concerns does the lecture raise about FIND-S?
12. Define consistency.
13. Define the version space.
14. Why is List-Then-Eliminate impractical?
15. Define S and G.
16. State the version-space representation theorem in words.
17. What does a positive example do to S and G?
18. What does a negative example do to S and G?
19. What are the final S and G boundaries after the four EnjoySport examples?
20. Explain the slide 17 version-space diagram.
21. When can a new instance be classified confidently?
22. Why request an instance that splits the version space approximately in half?
23. Give a concept that the conjunction-only H cannot represent.
24. Why can Candidate Elimination reach an empty version space?
25. Why does $H'=\mathcal P(X)$ not eliminate the need for bias?
26. Define inductive bias.
27. Compare the biases of the rote learner, Candidate Elimination, and FIND-S.
28. True or False: A consistent hypothesis must be the true concept.
29. True or False: FIND-S specializes its hypothesis after a negative example.
30. Long answer: Explain why inductive bias is logically necessary for generalization.

## Model Answer Outline for Question 30
- Observed data constrains only observed instances.
- An unrestricted hypothesis space contains consistent hypotheses that disagree on unseen instances.
- The data alone therefore cannot determine unseen labels.
- Extra assumptions are required to choose among those hypotheses.
- Those assumptions constitute inductive bias.
