---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- task-environment
title: Task Environment Properties
type: concept
---

# Task Environment Properties

*Source slides: 24--33*

## Seven Dimensions

### 1. Fully Observable vs. Partially Observable vs. Unobservable

**Fully observable:** sensors provide the complete decision-relevant
state.\
**Partially observable:** sensor noise/inaccuracy or missing information
hides relevant state.\
**Unobservable:** no sensors.

### 2. Single-Agent vs. Multiagent

The subtle test is whether another entity is best modeled as maximizing
a performance measure whose value depends on this agent's behavior.
Chess is competitive; taxi driving mixes cooperation and competition.

### 3. Deterministic vs. Nondeterministic vs. Stochastic

**Deterministic:** next state is completely determined by current state
and actions.\
**Nondeterministic:** multiple outcomes are possible without quantified
probabilities.\
**Stochastic:** probabilities are explicitly attached to outcomes.

### 4. Episodic vs. Sequential

**Episodic:** each decision episode is independent of prior actions.\
**Sequential:** current actions can affect future decisions and
outcomes.

### 5. Static vs. Dynamic vs. Semidynamic

**Static:** environment does not change during deliberation.\
**Dynamic:** environment can change while the agent deliberates.\
**Semidynamic:** world state is stable, but performance changes with
time.

### 6. Discrete vs. Continuous

Can apply independently to state, time, percepts, and actions.

### 7. Known vs. Unknown

A property of the agent/designer's knowledge. In a known environment,
action outcomes or their probabilities are given; in an unknown one, the
agent must learn them.

> [!warning] **Known/unknown ≠ observable/unobservable.** Solitaire
> can be known but partially observable. A new video game can be fully
> observable but initially unknown.

## Hardest General Case

Partially observable + multiagent + nondeterministic + sequential +
dynamic + continuous + unknown.

## Lecture Classification Table

  ----------------------------------------------------------------------------------------------
  Task           Observable   Agents     Dynamics        Episodes     Time          Values
  -------------- ------------ ---------- --------------- ------------ ------------- ------------
  Crossword      Fully        Single     Deterministic   Sequential   Static        Discrete

  Chess with     Fully        Multi      Deterministic   Sequential   Semidynamic   Discrete
  clock                                                                             

  Poker          Partially    Multi      Stochastic      Sequential   Static        Discrete

  Backgammon     Fully        Multi      Stochastic      Sequential   Static        Discrete

  Taxi driving   Partially    Multi      Stochastic      Sequential   Dynamic       Continuous

  Medical        Partially    Single     Stochastic      Sequential   Dynamic       Continuous
  diagnosis                                                                         

  Image analysis Fully        Single     Deterministic   Episodic     Semidynamic   Continuous

  Part-picking   Partially    Single     Stochastic      Episodic     Dynamic       Continuous
  robot                                                                             

  Refinery       Partially    Single     Stochastic      Sequential   Dynamic       Continuous
  controller                                                                        

  English tutor  Partially    Multi      Stochastic      Sequential   Dynamic       Discrete
  ----------------------------------------------------------------------------------------------

The lecture warns these classifications are modeling judgments rather
than absolute facts.

## Why It Matters

Environment properties constrain architecture. Partial observability
motivates internal state; sequential tasks motivate lookahead;
uncertainty motivates utility/decision-theoretic reasoning; unknown
environments motivate learning.

## Connections

[[PEAS and Task Environments]] · [[Agent Architectures]] · [[Learning Agents]]
