---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- learning-agents
title: Learning Agents
type: concept
---

# Learning Agents

*Source slides: 54--59*

## Motivation

The lecture invokes Turing's 1950 insight: instead of laboriously
hand-programming intelligence, build machines that can learn and then
teach them. Any of the canonical agent architectures may be learning or
non-learning.

## Four Components

The diagram on slide 55 separates four roles.

### Performance Element

Takes percepts and selects actions---the component earlier treated as
"the agent."

### Learning Element

Uses feedback from the critic to determine how the performance element's
knowledge should change.

### Critic

Evaluates how well the agent is doing relative to a fixed external
performance standard. Raw percepts alone do not necessarily say whether
an outcome is good.

### Problem Generator

Suggests exploratory actions likely to produce informative experiences,
even if those actions are temporarily suboptimal.

## Information Flow

``` text
Sensors → Performance Element → Actuators
   │             ↑
   └→ Critic → Learning Element
                   │
              changes knowledge
                   ↓
           Performance Element
                   ↑
           Problem Generator
          (learning goals / exploration)
```

## What Can Be Learned?

The learning element may modify: - state estimation, - transition
model, - sensor model, - condition-action rules, - goals, - utility
function.

Successive observed states can reveal action effects and world dynamics.
Learning reflex behavior or utility requires feedback tied to the
external performance standard.

## Reward and Penalty

The performance standard can identify part of incoming percepts as
reward/penalty. Human reactions can also provide evidence about
preferences; the lecture's taxi example uses passenger reactions to
excessive horn use.

## Unifying Theme

**Learning modifies agent components to bring them into closer agreement
with available feedback, improving performance.**

## Connections

[[Agent Architectures]] · [[Agents and Rationality]] · [[State Representations]]
