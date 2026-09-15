---
title: Chapter 1 - Practice Questions
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: review
source: Mitchell 1997 Chapter 1 lecture
---
# Practice Questions
1. State Mitchell's definition of learning and identify T, P, and E.
2. For handwriting recognition on slide 8, identify T, P, and E.
3. Why can indirect feedback create a credit assignment problem?
4. Compare teacher-selected, self-selected, and externally generated experience at the level discussed by the lecture.
5. What is the self-play trade-off in checkers?
6. Compare `ChooseMove` and V. Why does the lecture choose V?
7. Read aloud: $V:X_{board}\to\mathbb R$.
8. Explain each symbol in $\hat V(b)=w_0+\cdots+w_6x_6$.
9. List and define the six board features.
10. Why is a linear representation a trade-off?
11. Read aloud: $V_{train}(b)\leftarrow\hat V(Successor(b))$.
12. Why can successor estimates propagate information backward?
13. Calculate $E$ for targets [10,5] and predictions [8,7].
14. With $w_i=.5,\eta=.1,V_{train}=10,\hat V=8,x_i=3$, perform one LMS update.
15. Explain why squared error is not an accuracy percentage.
16. Draw and explain the four-module architecture from slide 17.
17. What does the Critic produce? What does the Generalizer do?
18. Define hypothesis space H.
19. Distinguish hypothesis space from search strategy.
20. Name three of the open questions from slide 20.

## Multiple Choice
**21.** Which is P for the slide-8 checkers example? A) self-play games B) playing checkers C) % games won D) board features. **Answer:** C.

**22.** Which statement best matches slide 14? A) More features always guarantee learning B) Representation trades expressive power for learnability C) V is directly observed D) LMS selects training games. **Answer:** B.

## Long Answer
**23. Explain the complete checkers-learning design.**
Model outline: specify self-play experience → select V → approximate V with weighted features → create successor-based training values → use LMS → integrate Performance System, Critic, Generalizer, Experiment Generator → connect to hypothesis-space search.
