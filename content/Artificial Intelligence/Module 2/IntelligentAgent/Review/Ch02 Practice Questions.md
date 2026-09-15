---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
title: Chapter 2 - Practice Questions
type: review
---

# Chapter 2 — Practice Questions

## Definitions and Short Answer

1.  Define an agent using the lecture's sensor/actuator framing.
2.  Distinguish a percept from a percept sequence.
3.  What is the difference between an agent function and an agent
    program?
4.  State the four things rationality depends on.
5.  Define autonomy as used in the lecture.
6.  Expand PEAS and explain why it should precede implementation.
7.  Define transition model and sensor model.
8.  Why is a goal-based agent fundamentally different from a reflex
    agent?
9.  What is a utility function?
10. Name and explain the four learning-agent components.

## Compare / Contrast

11. Rationality vs. omniscience.
12. Deterministic vs. stochastic vs. nondeterministic.
13. Known vs. fully observable.
14. Episodic vs. sequential.
15. Static vs. dynamic vs. semidynamic.
16. Simple reflex vs. model-based reflex.
17. Goal-based vs. utility-based.
18. Atomic vs. factored vs. structured.
19. Localist vs. distributed.

## Diagram Interpretation

20. In the slide 44 model-based reflex diagram, explain how state, "how
    the world evolves," "what my actions do," and the current percept
    contribute to "what the world is like now."
21. In the slide 55 learning-agent diagram, trace feedback from
    sensors/critic through the learning element to changes in the
    performance element.

## Mathematics

22. Read aloud: $f:P^*\to A$. What does each symbol mean?
23. If $|P|=3$ and $T=2$, calculate $\sum_{t=1}^T|P|^t$. Interpret the
    result.
24. Read aloud: $EU(a)=\sum_{s'}P(s'\mid a)U(s')$.
25. An action has outcomes `(p=0.7, U=90)` and `(p=0.3, U=10)`. Compute
    expected utility and explain what the result does **not** guarantee.

## Application

26. A warehouse robot cannot see behind shelves and must remember where
    obstacles were observed. Which base architecture is motivated, and
    why?
27. A navigation agent has three routes that all reach the goal but
    differ in risk and time. Why is utility useful?
28. A chess agent deliberately varies openings to avoid predictability.
    How does the lecture justify randomization in multiagent settings?
29. Construct a performance measure that could produce unintended
    behavior, then redesign it to target the desired environment state.
30. Classify a real-world task of your choice across all seven
    environment dimensions and justify each choice.

## Multiple Choice

31. Which is a property of the agent/designer's knowledge rather than
    the environment itself?\
    A. Dynamic B. Known/unknown C. Continuous D. Multiagent\
    **Answer:** B.

32. Which component evaluates behavior against an external performance
    standard?\
    A. Performance element B. Problem generator C. Critic D. Sensor
    model\
    **Answer:** C.

33. Which architecture explicitly asks what the world will be like after
    an action?\
    A. Simple reflex B. Goal-based C. Table-driven D. Localist\
    **Answer:** B.

## True / False

34. A rational agent must always achieve the best actual outcome.
    **False.**
35. A fully observable environment must also be known. **False.**
36. Any canonical agent type can be augmented with learning. **True.**
37. More expressive representations always make reasoning easier.
    **False.**

## Long Answer

38. Explain the lecture's full argument from performance measure →
    rationality → PEAS → architecture choice.\
    **Model outline:** define external success; explain
    expected-performance rationality; specify task via PEAS; classify
    environment; show how properties motivate internal
    state/goals/utility/learning.

39. Explain why the table-driven agent is conceptually correct yet
    practically useless.\
    **Model outline:** it can implement the desired agent function;
    table contains action for every percept sequence; size grows as
    $\sum |P|^t$; impossible storage/design/learning.

## Professor Discussion Questions

*Source slide: 70*

40. Give a PEAS description for an agent that plays online chess
    anonymously against unknown opponents. Classify each environment
    property.\
    **Lecture-grounded guidance:** use the PEAS framework and the
    environment-property definitions. Chess is multiagent, sequential,
    discrete, and deterministic under the rules; "unknown opponents"
    introduces knowledge uncertainty about the opponent rather than
    changing the rules themselves. Exact classification should be
    justified from the stated task.

41. Construct an example of a performance measure that is easy to state
    but leads to unintended reward-hacking behavior.\
    **Guidance:** mirror the vacuum example's structure: identify a
    proxy that can be maximized without producing the desired
    environment state, then propose a state-based measure.

42. Why is a rational agent not required to be omniscient? Give a new
    real-world example.\
    **Guidance:** rationality uses expected performance from available
    evidence; omniscience requires actual future outcomes. Clearly label
    your example as your own.

43. For an email spam-filtering agent, sketch the four learning-agent
    components.\
    **Guidance:** identify action selection (performance element),
    modification process (learning element), external success feedback
    (critic), and informative exploration (problem generator).

44. Compare atomic, factored, and structured representations for one
    task. What is gained and lost?\
    **Guidance:** show increasing internal structure/expressiveness and
    the corresponding increase in reasoning/learning complexity.
