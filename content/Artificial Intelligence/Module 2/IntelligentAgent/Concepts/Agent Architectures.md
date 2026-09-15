---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- agent-architecture
title: Agent Architectures
type: concept
---

# Agent Architectures

*Source slides: 34--53*

## Agent = Architecture + Program

The **program** implements the agent function. The **architecture** is
the physical computing device plus sensors/actuators on which it runs.
Program and architecture must be compatible.

## Why Table-Driven Agents Fail

A complete lookup table over percept histories is conceptually valid but
physically, manually, and learnably infeasible. See
[[Ch02 - Mathematics#Table-Driven Agent Size]].

## 1. Simple Reflex Agent

### Definition

Chooses actions only from the **current percept**, ignoring percept
history.

### Mechanism

``` text
Current percept → interpret current state → match condition-action rule → action
```

Example: `if car-in-front-is-braking then initiate-braking`.

### Limitation

Works when the correct decision is recoverable from the current percept.
Partial observability can make deterministic reflex behavior loop or
fail.

## 2. Model-Based Reflex Agent

### Definition

Maintains **internal state** to track aspects of the world not currently
observable.

### Required Knowledge

-   **Transition model:** how the world evolves and what the agent's
    actions do.
-   **Sensor model:** how world state produces percepts.

### Flow

``` text
old state + last action + current percept
              +
 transition model + sensor model
              ↓
        updated internal state
              ↓
      condition-action rule
              ↓
             action
```

The internal state is often a best estimate, not the exact hidden state.

## 3. Goal-Based Agent

### Definition

Adds explicit goals and uses predicted consequences to choose actions
that achieve desirable situations.

### Key Difference

Goal reasoning asks: **"What will happen if I do action A?"** This
explicit lookahead distinguishes it from reflex behavior.

### Advantage

Changing a destination can require only changing the goal; a reflex
system may require redesigning its rule set.

## 4. Utility-Based Agent

### Definition

Uses a utility function to compare degrees of desirability among
states/outcomes.

Goals are insufficient when: 1. goals conflict and trade-offs are
needed, 2. outcomes are uncertain and likelihood must be balanced
against importance.

See [[Ch02 - Mathematics#Expected Utility]].

### Caveats

Computing utility-maximizing behavior can itself be hard. Perfect
rationality is generally unattainable under real computational
constraints. Utility-based agents can also be **model-free**.

## Architecture Progression

``` text
Simple reflex
current percept
    ↓
Model-based reflex
+ internal state + models
    ↓
Goal-based
+ explicit goals + lookahead
    ↓
Utility-based
+ graded preferences + uncertainty trade-offs
```

> [!important] These are canonical design patterns, not mutually
> exclusive labels for all intelligent systems. Any can be augmented
> with learning.

## Connections

[[Agents and Rationality]] · [[Learning Agents]] · [[Task Environment Properties]]
