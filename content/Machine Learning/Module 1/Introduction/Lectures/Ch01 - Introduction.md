---
title: Chapter 1 - Introduction
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: lecture
source: Mitchell 1997 Chapter 1 lecture
---

# Machine Learning — Chapter 1: Introduction

_Source: slides 1–21; slides based on Tom M. Mitchell, **Machine Learning** (1997)._

## 🎯 Big Picture
Machine learning studies algorithms that **improve automatically through experience**. The lecture motivates ML by the growth of digital data, abundant computation/storage, tasks too complex for hand-coded rules, self-customizing software, and scientific interest in learning.

The organizing definition is Mitchell's **T–P–E framework**: a program learns from experience **E**, with respect to tasks **T** and performance measure **P**, when performance on T, measured by P, improves with E. [[Concepts/Well-Posed Learning Problem]] turns an informal desire to “learn” into a specified learning problem.

The checkers case study then makes system design concrete: choose the [[Concepts/Training Experience|training experience]], choose the [[Concepts/Target Function|target function]], choose a representation, and choose a learning algorithm. An exact board-value function is impractical to compute, so the learner uses [[Concepts/Function Approximation|function approximation]] and updates a linear approximation with [[Algorithms/Least Mean Squares|LMS]]. Finally, the lecture generalizes learning as search through a [[Concepts/Hypothesis Space|hypothesis space]].

## Lecture Roadmap
Why ML? → [[Concepts/Well-Posed Learning Problem|T–P–E]] → Checkers design

Training experience → Target function → Representation → LMS

↓

Performance System → Critic → Generalizer → Experiment Generator

↓

[[Concepts/Hypothesis Space|Learning as hypothesis-space search]]

## What I Should Know After This Lecture
- State and apply the T–P–E definition.
- Explain the four design choices in the checkers learner.
- Distinguish direct from indirect feedback and explain credit assignment.
- Explain why the exact value function is replaced by an approximation.
- Read, compute, implement, and interpret the linear board-value function and LMS update.
- Trace the four-module learning architecture on slide 17.
- Explain learning as search through a hypothesis space.

## ⏱️ 60-Second Lecture Summary
A learning problem specifies **what** to do (T), **how success is measured** (P), and **what experience drives improvement** (E). In checkers, self-play supplies experience. Rather than directly learning a move for every board, the learner approximates a board-value function with a weighted linear combination of six features. Successor-state estimates supply training values, and LMS adjusts the weights to reduce squared error. The resulting system cycles through performance, criticism, generalization, and experiment generation. More broadly, ML algorithms differ in the hypothesis spaces they search and the strategies used to search them.

## 1. Why Machine Learning? — slides 3–5
The lecture's examples include spoken-word recognition, patient recovery prediction, fraud detection, autonomous driving, and world-class backgammon. Slide 5 compares Samuel's checkers player, TD-Gammon, and ALVINN. Their common pattern is **task + performance measure + experience**, anticipating T–P–E.

## 2. Well-Posed Learning Problems — slides 6–8
See [[Concepts/Well-Posed Learning Problem]]. Slide 8 applies the framework to checkers, handwriting recognition, and robot driving.

## 3. Designing the Checkers Learner — slides 9–17
### Choice 1 — Training experience
See [[Concepts/Training Experience]]. The selected design uses self-play: unlimited and cheap, but potentially mismatched with the eventual distribution of human/expert opponents.

### Choice 2 — Target function
Two formulations are shown: `ChooseMove` maps board states to moves, whereas `V` maps board states to real-valued evaluations. The lecture chooses V because it is easier to learn. See [[Concepts/Target Function]] and [[Ch01 Mathematics#Exact board-value function]].

### Choice 3 — Representation
The approximation uses six board features and seven weights including the bias. See [[Concepts/Function Approximation]] and [[Ch01 Mathematics#Linear approximation of board value]].

### Choice 4 — Learning algorithm
Intermediate board values are not directly observed. The training-value rule bootstraps from the successor board's current estimate; LMS then adjusts weights to reduce squared error. See [[Algorithms/Least Mean Squares]] and [[Ch01 Mathematics]].

### Final architecture — slide 17
The diagram forms a learning loop:

Performance System → game history/trace → Critic → training examples → Generalizer

Generalizer → hypothesis V-hat → Experiment Generator → new problem/initial board → Performance System

- **Performance System:** plays using current V-hat.
- **Critic:** converts traces into training examples.
- **Generalizer:** updates V-hat using LMS.
- **Experiment Generator:** selects the next opening/problem to improve exploration/coverage.

> [!question]
> **Diagram-Based Exam Question:** If shown slide 17, explain what information flows between the four modules and why each module is necessary.

## 4. Perspectives and Issues — slides 18–20
See [[Concepts/Hypothesis Space]]. Slide 20 leaves six broad questions open: learning algorithms and convergence; sufficient training data; prior knowledge; choosing training experience; reducing learning to function approximation; and automatically changing representation.

## 5. Chapter Synthesis — slide 21
The chapter links T–P–E, four learning-system design choices, approximation plus LMS, and hypothesis-space search. The final slide explicitly frames later topics—concept learning, decision trees, neural networks, Bayesian methods, computational learning theory, instance-based methods, genetic algorithms, rule learning, analytical learning, and reinforcement learning—as variations in hypothesis space and search strategy.
