---
aliases:
- Atomic Factored Structured Representations
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- knowledge-representation
title: State Representations
type: concept
---

# State Representations

*Source slides: 60--66*

## Expressiveness Axis

``` text
Atomic → Factored → Structured
increasing complexity and expressive power →
```

## Atomic Representation

A state is an indivisible black box; only identity/difference is
visible. Example: represent a route state only by the current city name.

Used in the lecture by standard search/game-playing, hidden Markov
models, and Markov decision processes.

## Factored Representation

A state is a fixed collection of variables/attributes with values.
Example: GPS coordinates, fuel level, warning lights, toll money, radio
station.

Unlike opaque atomic states, factored states can share some attributes
while differing in others, enabling more direct reasoning about state
transformations.

## Structured Representation

The world is represented as **objects**, each with attributes and
relationships to other objects. The truck/cow/driveway example on slide
63 shows why a fixed attribute vector can become awkward when the
important content is relational.

## Side-by-Side Interpretation of Slide 64

-   **Atomic:** state = opaque black box.
-   **Factored:** state = vector of attribute values.
-   **Structured:** state = objects with attributes and relationships.

## Expressiveness Trade-off

A more expressive representation can encode everything a less expressive
representation can, often far more concisely. Slide 65 contrasts
chess-rule descriptions: roughly 1--2 pages in first-order logic,
thousands in propositional logic, and around $10^{38}$ pages as a
finite-state automaton.

> [!warning] Greater expressiveness usually makes reasoning and
> learning more complex. Real systems may use multiple representation
> levels simultaneously.

## Orthogonal Axis: Localist vs. Distributed

**Localist:** one-to-one mapping from concept to memory location;
fragile under bit corruption.\
**Distributed:** a concept is spread across many locations, while each
location participates in many concepts; the lecture describes this as
more robust to noise/information loss.

## Exam-Level Understanding

Be able to represent the *same* task in all three styles and state what
becomes easier or harder as expressiveness increases.

## Connections

[[Agent Architectures]] · [[Ch02 Comparisons and Distinctions]]
