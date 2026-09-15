---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
title: Chapter 2 - Active Recall Answers
type: active-recall-answers
---

# Chapter 2 — Active Recall Answers

1.  Anything viewed as perceiving its environment through sensors and
    acting on that environment through actuators.
2.  A percept is sensor content at one instant; a percept sequence is
    the complete history of percepts.
3.  $f:P^*\to A$: all possible percept sequences to actions.
4.  The function is an abstract external behavioral mapping; the program
    is its concrete implementation on an architecture.
5.  Judge behavior by the desirability of the environment-state
    consequences it produces.
6.  An objective criterion for success that evaluates sequences of
    environment states.
7.  Performance measure, prior knowledge, available actions, and percept
    sequence to date.
8.  Rationality maximizes expected performance from available
    information; omniscience knows actual outcomes.
9.  Gathering information can improve future percepts and therefore
    increase expected performance.
10. An agent is more autonomous when it relies on its own percepts and
    learning rather than designer prior knowledge.
11. Performance measure, Environment, Actuators, Sensors.
12. Because the task---success, world, actions, and observations---must
    be defined before deciding how the agent should behave.
13. Observability; number of agents; determinism; episodic/sequential;
    static/dynamic; discrete/continuous; known/unknown.
14. Observability concerns access to current state; known/unknown
    concerns knowledge of action outcomes or outcome probabilities.
15. Stochastic explicitly quantifies probabilities; nondeterministic
    lists possibilities without probabilities.
16. Each episodic decision is independent, so the agent need not reason
    about future consequences of current actions.
17. The environment itself is stable with time, but the performance
    score changes with time.
18. The percept-history table grows explosively; it cannot realistically
    be stored, manually filled, or learned.
19. Only the current percept, after interpretation into a current-state
    description.
20. A transition model and a sensor model.
21. Explicit lookahead using goals: predicting what will happen if an
    action is taken and whether that reaches a desirable situation.
22. Goals provide a coarse achieved/not-achieved distinction; utility
    ranks outcomes and supports trade-offs weighted by uncertainty.
23. $EU(a)=\sum_{s'}P(s'\mid a)U(s')$: probability-weighted average
    utility over possible outcomes of action $a$.
24. Performance element, learning element, critic, problem generator.
25. It tells the learning element how well the agent is doing relative
    to a fixed external performance standard.
26. It proposes exploratory actions that can create informative
    experiences, even when temporarily suboptimal.
27. State estimation, transition model, sensor model, condition-action
    rules, goals, and utility function.
28. Atomic: opaque state identity. Factored: fixed vector of attributes.
    Structured: explicit objects with attributes and relationships.
29. Greater expressiveness can represent more, often more concisely, but
    reasoning and learning become more complex.
30. Atomic/factored/structured describes the logical structure of world
    states; localist/distributed describes how concepts map onto
    physical memory, an orthogonal axis.

Questions: [[Ch02 - Active Recall]]
