---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
title: Chapter 2 - Why and How
type: review
---

# Chapter 2 — Why and How

## Why isn't a rational agent required to be omniscient?

Because rationality is judged from the evidence available at decision
time. Omniscience would require knowledge of actual future outcomes,
which the lecture treats as impossible in reality.

## Why can information gathering itself be rational?

Because an action such as "look" changes future percepts and can improve
later decisions, thereby increasing expected performance.

## Why is performance-measure design dangerous?

A rational agent optimizes what is specified. If the measure rewards a
proxy---such as amount of dirt cleaned---it can produce unwanted but
measure-maximizing behavior such as re-dirtying the floor.

## Why does changing assumptions change rationality?

The optimal action depends on the performance measure, prior knowledge,
action set, and percept history. Movement penalties, recurring dirt, or
unknown geography alter the decision problem.

## Why specify PEAS before implementation?

Because rational behavior cannot be defined independently of success
criteria, environment, available actions, and percepts. PEAS makes those
design constraints explicit.

## Why does partial observability motivate model-based agents?

The current percept may not contain enough information to choose
correctly. Internal state integrates history with transition and sensor
models to estimate hidden state.

## Why are episodic tasks easier than sequential tasks?

In episodic tasks, a current decision does not affect later episodes.
The agent does not need to reason about long-term consequences.

## Why does a dynamic environment make deliberation harder?

The world may change while the agent is deciding. Delaying a decision is
effectively an action---doing nothing while the environment continues
evolving.

## Why are goals not enough?

Multiple plans may all reach a goal but differ in speed, safety,
reliability, or cost. Goals are essentially a coarse
satisfied/not-satisfied distinction; utility supports graded trade-offs.

## Why use expected utility?

Under uncertainty, a rational choice must account for both outcome
desirability and outcome likelihood.

## Why can perfect rationality be impractical?

The lecture notes that modeling, state tracking, and utility-maximizing
action selection can be computationally hard.

## Why does learning increase autonomy?

Learning allows experience to replace or correct designer-provided prior
knowledge, so behavior becomes less dependent on initial assumptions.

## Why have a critic if the agent already receives percepts?

Percepts describe what happened; they do not inherently say whether it
was good. The critic evaluates behavior against an external performance
standard.

## Why would a problem generator recommend a short-term suboptimal action?

Exploration can generate informative experiences that improve future
behavior.

## Why move from atomic to factored to structured representations?

Greater expressiveness can encode important regularities and
relationships much more concisely. The cost is increased reasoning and
learning complexity.

## What happens as $|P|$ or $T$ increases in a table-driven agent?

The table size $\sum_{t=1}^T |P|^t$ grows explosively. This is why exact
percept-history lookup is a conceptual baseline rather than a practical
architecture.
