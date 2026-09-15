# Node Arc Path and k-Consistency

**Source:** slides/pages 16–23.

## Definition / Core Idea
Consistency notions progressively strengthen local inference. Node consistency filters unary constraints; arc consistency requires a support in the neighboring domain; path consistency asks whether a consistent pair extends through a third variable; k-consistency generalizes extension to any kth variable.

## Lecture Example
The two-color WA–NT–SA triangle is arc-consistent edge-by-edge but path consistency exposes the cycle inconsistency.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
