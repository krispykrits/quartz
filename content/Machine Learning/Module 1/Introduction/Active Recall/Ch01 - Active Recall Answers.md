---
title: Chapter 1 - Active Recall Answers
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: answer-key
source: Mitchell 1997 Chapter 1 lecture
---
# Active Recall Answers

1. Algorithms that improve automatically through experience.
2. A program learns from E with respect to T and P if its performance at T, as measured by P, improves with E.
3. The task(s) the program performs.
4. The performance measure used to evaluate it.
5. The training experience it learns from.
6. T: play checkers; P: percentage of games won against opponents; E: games played against itself.
7. Feedback type; control over the sequence of examples; match between training-example and evaluation distributions.
8. Under indirect feedback, deciding which earlier actions deserve credit or blame for a final outcome.
9. Self-play; it is unlimited and cheap but may differ from the distribution of play against human experts.
10. Training experience, target function, target-function representation, learning algorithm.
11. ChooseMove maps boards to moves; V maps boards to real-valued evaluations.
12. The lecture says V is far easier to learn.
13. Win 100; loss -100; draw 0.
14. Its recursive exact definition is not efficiently computable.
15. $\hat V(b)=w_0+w_1x_1+\cdots+w_6x_6$.
16. Black pieces, red pieces, black kings, red kings, black pieces threatened by red, red pieces threatened by black.
17. Expressive power for a small, learnable number of parameters.
18. $V_{train}(b)\leftarrow\hat V(Successor(b))$.
19. Errors can average out over games and values propagate backward from reliable end-game outcomes.
20. $E=\sum(V_{train}(b)-\hat V(b))^2$.
21. $w_i\leftarrow w_i+\eta(V_{train}(b)-\hat V(b))x_i$.
22. A small learning rate controlling update size.
23. Weights are nudged upward in proportion to feature contribution for positive features, scaled by eta and the error.
24. Performance System, Critic, Generalizer, Experiment Generator.
25. Performance plays; Critic labels traces; Generalizer updates V-hat via LMS; Experiment Generator chooses the next problem/opening board.
26. The set H of candidate hypotheses the learner searches.
27. The hypothesis space searched and the search strategy used.
28. Any three: algorithms/convergence; data sufficiency; prior knowledge; choosing next experience; reducing to function approximation; altering representation.
29. The linear weight vectors form H, and LMS is the strategy that adjusts/searches those weights using training examples.
30. “w sub i gets w sub i plus eta times V sub train of b minus V hat of b, times x sub i.”
