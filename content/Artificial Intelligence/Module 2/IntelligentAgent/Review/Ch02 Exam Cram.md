---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
title: Chapter 2 - Exam Cram
type: review
---

# Chapter 2 — Exam Cram

## Tier 1 — MUST KNOW ⭐⭐⭐

-   Agent, percept, percept sequence, agent function, agent program,
    architecture.
-   Formal definition of rational agent and the four dependencies of
    rationality.
-   Rationality vs. omniscience.
-   Performance-measure misspecification / vacuum reward-hacking
    example.
-   PEAS and the rule to specify the task environment first.
-   Seven task-environment dimensions.
-   Four canonical agent architectures and what each adds.
-   Four learning-agent components.
-   Atomic vs. factored vs. structured representation.
-   Expected utility.

## Tier 2 — VERY IMPORTANT ⭐⭐

-   Information gathering, exploration, learning, autonomy.
-   Transition model vs. sensor model.
-   Goal-based lookahead.
-   Utility for conflicting goals and uncertain outcomes.
-   Table-driven-agent infeasibility.
-   Known vs. observable as independent dimensions.
-   Localist vs. distributed representations.

## Tier 3 — SUPPORTING ⭐

-   Dung beetle and sphex wasp as fragility examples.
-   Randomization as an escape from loops and as rational
    anti-predictability in multiagent settings.
-   Model-free utility-based agents.
-   Turing's 1950 motivation for learning machines.

## Must-Memorize Lists

**Rationality depends on:** performance measure, prior knowledge,
actions, percept sequence.

**PEAS:** Performance, Environment, Actuators, Sensors.

**Environment dimensions:** observability, number of agents,
determinism, episodic/sequential, static/dynamic, discrete/continuous,
known/unknown.

**Agent programs:** simple reflex → model-based reflex → goal-based →
utility-based.

**Learning agent:** performance element, learning element, critic,
problem generator.

**Representations:** atomic → factored → structured.

## Equation Cheat Sheet

$$
f:P^*\to A
$$ Agent function: percept sequences → actions.

$$
\sum_{t=1}^T |P|^t
$$ Number of table entries for all percept sequences through lifetime
$T$.

$$
EU(a)=\sum_{s'}P(s'\mid a)U(s')
$$ Expected utility of an action.

Full teaching treatment: [[Mathematics/Ch02 - Mathematics]].

## Algorithm Cheat Sheet

**Simple reflex:** interpret current percept → match rule → action.\
**Model-based reflex:** update internal state using previous
state/action + percept + models → match rule → action.

## Common Confusions

-   Rationality ≠ omniscience.
-   Agent function ≠ agent program.
-   Performance measure ≠ utility function.
-   Known ≠ fully observable.
-   Stochastic ≠ merely nondeterministic.
-   Dynamic ≠ semidynamic.
-   Goal satisfaction ≠ utility maximization.
-   Factored ≠ structured.
-   Learning agent is not a fifth mutually exclusive base architecture;
    learning can augment the others.

## If You Only Remember 10 Things

1.  Agents perceive and act.
2.  The agent function maps percept histories to actions.
3.  Agent = architecture + program.
4.  Rationality maximizes expected performance given current evidence
    and prior knowledge.
5.  Performance measures can be badly specified and exploited.
6.  PEAS comes before agent design.
7.  Environment properties determine design difficulty.
8.  Reflex → model → goal → utility adds progressively richer decision
    information.
9.  Learning uses performance element + learning element + critic +
    problem generator.
10. Atomic → factored → structured increases expressive power but also
    reasoning complexity.

## ⚡ 5-Minute Pre-Exam Review

Recite PEAS, the seven environment dimensions, the four rationality
dependencies, the four agent architectures, and the four learning
components. Then explain expected utility aloud and contrast rationality
with omniscience.
