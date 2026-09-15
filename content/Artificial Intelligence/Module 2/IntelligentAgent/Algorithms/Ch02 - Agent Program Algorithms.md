---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- algorithms
- agents
title: Chapter 2 - Agent Program Algorithms
type: algorithms
---

# Chapter 2 — Agent Program Algorithms

*Source slides: 40, 45*

## SIMPLE-REFLEX-AGENT

### Purpose

Select an action from the current percept using condition-action rules.

### Inputs

Current percept.

### Output

Action.

### Steps

1.  Interpret the current percept into an abstract state description.
2.  Match that state against the rule set.
3.  Select the first matching rule.
4.  Return the rule's action.

``` text
SIMPLE-REFLEX-AGENT(percept)
persistent: rules

state  ← INTERPRET-INPUT(percept)
rule   ← RULE-MATCH(state, rules)
action ← rule.ACTION
return action
```

### Intuition

Compress the current sensory input into the features relevant to a
decision, then react immediately.

### Limitation / Failure Mode

The lecture states this works only when the correct action is
determinable from the current percept. It fails under important forms of
partial observability.

### Computational Consideration

The lecture does not give a formal time complexity. "Rules" and
"matching" are conceptual and could be implemented by a Boolean circuit
or neural network.

------------------------------------------------------------------------

## MODEL-BASED-REFLEX-AGENT

### Purpose

Choose reflex actions while maintaining an internal estimate of hidden
world state.

### Inputs

Current percept plus persistent state and previous action.

### Persistent Knowledge

-   state,
-   transition model,
-   sensor model,
-   rules,
-   most recent action.

### Steps

1.  Fuse old state, previous action, current percept, transition model,
    and sensor model.
2.  Produce an updated state estimate.
3.  Match that state to a condition-action rule.
4.  Store and return the chosen action.

``` text
MODEL-BASED-REFLEX-AGENT(percept)
persistent: state, transition_model, sensor_model, rules, action

state  ← UPDATE-STATE(state, action, percept,
                      transition_model, sensor_model)
rule   ← RULE-MATCH(state, rules)
action ← rule.ACTION
return action
```

### Intuition

When the current percept is incomplete, remember enough history and use
models to infer what is probably true now.

### Assumption / Limitation

The exact state of a partially observable environment is seldom
recoverable. The internal state may represent a best guess or multiple
possible guesses.

## Comparison

  -----------------------------------------------------------------------
  Feature                 Simple Reflex           Model-Based Reflex
  ----------------------- ----------------------- -----------------------
  Uses current percept    Yes                     Yes

  Uses percept history    No                      Yes, through internal
  indirectly                                      state

  Transition model        No                      Yes

  Sensor model            No                      Yes

  Handles partial         Poorly                  Designed to address it
  observability                                   

  Final action mechanism  Rule matching           Rule matching on
                                                  estimated state
  -----------------------------------------------------------------------

## Connections

[[Agent Architectures]] · [[Task Environment Properties]]
