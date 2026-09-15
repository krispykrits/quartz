---
title: Symbolic AI and Expert Systems
tags: [artificial-intelligence, symbolic-ai, expert-systems]
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: concept
---
# Symbolic AI and Expert Systems
_Source slides: 26, 28-31_

## Symbolic Problem Solving
Logic Theorist and General Problem Solver suggested symbolic search could model problem solving. Lisp and Advice Taker emphasized explicit symbolic knowledge and reasoning.

## Microworlds
```text
Tiny world → explicit symbols/rules → feasible search/planning → impressive but narrow demo
```

## Scale Failure
Search grows roughly as $O(b^d)$. More objects, actions, and plan depth create combinatorial explosion.

## Expert Systems
Expert systems replaced blind/weak general search with domain-specific knowledge.

### DENDRAL
Infers molecular structure from mass-spectrum data; chemists' pattern knowledge prunes generate-and-test search.

### MYCIN
Diagnoses blood infections and recommends treatment using hundreds of rules and an uncertain-evidence calculus.

## Limitations
- knowledge acquisition bottleneck,
- maintenance as domains change,
- uncertainty and exceptions,
- little learning from experience.

## Historical Effect
Commercial success raised expectations; brittleness contributed to disillusionment and AI winter.
