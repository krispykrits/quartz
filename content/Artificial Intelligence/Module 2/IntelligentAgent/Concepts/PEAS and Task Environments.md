---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- peas
- task-environment
title: PEAS and Task Environments
type: concept
---

# PEAS and Task Environments

*Source slides: 21--23*

## Definition

A **task environment** is the problem to which the rational agent is the
solution.

**PEAS** specifies: - **Performance measure** --- what counts as
success. - **Environment** --- what the agent operates in. -
**Actuators** --- how it can affect the environment. - **Sensors** ---
how it obtains percepts.

> [!important] The lecture's golden rule is to specify the task
> environment as fully as possible **before** designing the agent.

## Automated Taxi Example

  -----------------------------------------------------------------------
  PEAS element                        Lecture examples
  ----------------------------------- -----------------------------------
  Performance                         safe, fast, legal, comfortable
                                      trip; maximize profits; minimize
                                      impact on other road users

  Environment                         roads, traffic, police,
                                      pedestrians, customers, weather

  Actuators                           steering, accelerator, brake,
                                      signal, horn, display, speech

  Sensors                             cameras, radar, speedometer, GPS,
                                      engine sensors, accelerometer,
                                      microphones, touchscreen
  -----------------------------------------------------------------------

Multiple performance goals conflict, so trade-offs are unavoidable.
Restricting geography, weather, or driving conventions reduces the
design difficulty.

## Why It Matters

PEAS prevents premature implementation. It forces the designer to state
what success means, what world matters, what can be observed, and what
actions are physically/software-wise possible.

## More Lecture Examples

Medical diagnosis, satellite image analysis, part-picking robot,
refinery controller, and interactive English tutor show that PEAS
applies to both physical and software environments.

## Exam-Level Understanding

Given a new scenario, construct all four PEAS components and avoid
confusing: - **performance** with the agent's internal utility, -
**environment** with the entire universe, - **sensors** with internal
state, - **actuators** with desired outcomes.

## Connections

[[Agents and Rationality]] · [[Task Environment Properties]] · [[Agent Architectures]]
