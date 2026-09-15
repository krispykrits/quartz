---
title: Beneficial Machines and Value Alignment
tags: [artificial-intelligence, value-alignment, ai-safety]
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: concept
---
# Beneficial Machines and Value Alignment
_Source slides: 11, 39_

## Standard Model
The standard model assumes a fully specified objective that the machine optimizes.

## Why It Is Incomplete
Real human objectives can be incomplete, context-sensitive, and inconsistent. A fixed objective can therefore create specification error and unintended behavior.

## Value Alignment
Machine objectives must align with human objectives.

## Safer Formulation
Let $	heta$ denote human preferences. A helpful machine reasons with $P(	heta\mid choices,context)$ and may learn, ask, defer, and preserve corrigibility.

## Long-Term Alignment
Slide 39 links human-level AI and superintelligence to the control problem and the King Midas problem: literal optimization of the wrong objective can create unwanted consequences.

## Assistance-Game Intuition
The human has utility $U_H$; the machine acts with uncertainty about $U_H$ given evidence. This uncertainty can create incentives to ask, defer, preserve options, and allow correction.

## Connections
[[Concepts/Rational Agents and Limited Rationality]] · [[Concepts/AI Capabilities Benefits and Risks]]
