---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- agents
- rationality
title: Agents and Rationality
type: concept
---

# Agents and Rationality

*Source slides: 3--20*

## Definition

An **agent** perceives its environment through sensors and acts on that
environment through actuators.

A **rational agent**, for every possible percept sequence, selects an
action expected to maximize its performance measure given the evidence
in that percept sequence and its built-in knowledge.

## Technical Explanation

A percept is instantaneous sensor content; a percept sequence is the
complete observation history. The agent's externally visible behavior is
characterized by an [[Ch02 - Mathematics#Agent Function|agent function]] from percept sequences to actions.

Rationality is evaluated by consequences through an external
**performance measure**. It is conditional on the information and
capabilities available at decision time. The same policy can therefore
be rational or irrational under different assumptions.

## Intuitive Explanation

Think of rationality as **making the best defensible decision with what
you know now**, not "always getting the best outcome." A lucky bad
decision is not made rational by luck, and an unlucky good decision is
not made irrational by a freak outcome.

## Performance-Measure Design

The vacuum reward-hacking example is central: rewarding "dirt cleaned"
encourages repeated re-dirtying and cleaning. Reward the desired
state---clean floors---rather than a behavioral proxy.

> [!important] Design the performance measure according to what you
> actually want achieved in the environment.

## Rationality Depends On

1.  Performance measure.
2.  Prior knowledge.
3.  Available actions.
4.  Percept sequence to date.

## Rationality vs. Omniscience

Omniscience requires knowing actual outcomes. Rationality uses expected
outcomes from available information. The Champs-Élysées example shows a
rational crossing decision can still end catastrophically because of an
unforeseeable event.

## Information Gathering, Learning, Autonomy

Information-gathering actions are rational when they improve future
decisions. Learning modifies prior knowledge using experience. An agent
is less autonomous to the extent that it depends on designer-provided
prior knowledge instead of its own percepts and learning.

## Assumptions / Limitations

Rationality cannot rescue a badly chosen performance measure. It also
does not imply perfect computation; later slides note that perfect
rationality is often computationally unattainable.

## Exam-Level Understanding

Be able to explain why: - rationality is relative to task assumptions, -
rationality differs from omniscience, - exploration can itself be
rational, - performance-measure misspecification can produce rational
but unwanted behavior, - autonomy increases as experience replaces
dependence on prior knowledge.

## Connections

[[PEAS and Task Environments]] · [[Agent Architectures]] · [[Learning Agents]] ·
[[Ch02 - Mathematics]]
