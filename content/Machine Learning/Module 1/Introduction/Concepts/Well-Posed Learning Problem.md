---
title: Well-Posed Learning Problem
tags: [machine-learning, chapter-1]
course: Machine Learning
chapter: 1
type: concept
source: Mitchell 1997 Chapter 1 lecture
---
_Source slides: 7–8_
# Well-Posed Learning Problem
## Definition
A program learns from experience **E** with respect to tasks **T** and performance measure **P** when its performance at T, as measured by P, improves with E.
## Technical Explanation
A learning problem is not fully specified until all three components are identified: **T** (task), **P** (performance measure), and **E** (training experience).
## Intuitive Explanation
Ask three questions: *What must the system do? How will I score it? What will it learn from?*
## Examples
| Problem | T | P | E |
|---|---|---|---|
| Checkers | Play checkers | % games won | Self-play games |
| Handwriting | Classify handwritten words | % correctly classified | Labeled handwritten-word database |
| Robot driving | Drive using vision | Average distance before human-judged error | Images + steering commands from human driver |
## Why It Matters
The framework prevents vague claims that a system “learns” without specifying observable improvement.
## Connections
[[Concepts/Training Experience]] · [[Concepts/Target Function]]
## Exam-Level Understanding
Given a scenario, identify T, P, and E and justify each choice.
