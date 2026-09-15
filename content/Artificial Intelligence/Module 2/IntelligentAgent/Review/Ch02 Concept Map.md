---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
title: Chapter 2 - Concept Map
type: review
---

# Chapter 2 — Concept Map

``` text
Environment
   ↓ percepts
Sensors
   ↓
Percept → Percept Sequence
   ↓
Agent Function: P* → A
   ↓ implemented by
Agent = Architecture + Program
   ↓ judged by
Performance Measure
   ↓
Rationality = maximize expected performance
   ↓ design begins with
PEAS
   ↓ classify
Task Environment Properties
   ↓ constrain
Agent Architecture
   ├─ Simple Reflex
   ├─ Model-Based Reflex
   ├─ Goal-Based
   └─ Utility-Based → Expected Utility
            ↓
      can be augmented by
        Learning Agent
            ↓
Performance Element ↔ Learning Element
        ↑ critic     ↑ problem generator
            ↓
      modifies knowledge
            ↓
World Representation
Atomic → Factored → Structured
```

## Major Connections

**Partial observability → internal state.** If the current percept does
not reveal all action-relevant state, a simple reflex agent is
insufficient; model-based agents use transition and sensor models to
maintain an estimate.

**Sequential decisions → lookahead.** When present choices affect future
choices, goals and prediction become important.

**Uncertainty + trade-offs → utility.** Goals say whether a state
satisfies an objective; utility ranks outcomes and supports
probability-weighted decisions.

**Unknown environments → learning.** Learning reduces dependence on
incomplete prior knowledge and increases autonomy.

**Representation ↔ reasoning complexity.** More expressive state
representations can describe the world more compactly but make
reasoning/learning more complex.

## Navigation

[[quartz/content/Artificial Intelligence/Module 1/Chapter Home]] · [[Ch02 - Intelligent Agents]] ·
[[Ch02 Exam Cram]]
