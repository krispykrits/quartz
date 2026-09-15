# Conflict Sets Backjumping and No-Goods

**Source:** slides/pages 40–42.

## Definition / Core Idea
Conflict-directed methods record why a branch fails. Backjumping skips irrelevant recent decisions; conflict-directed backjumping propagates causes; no-goods turn a discovered contradiction into a learned pruning constraint.

## Lecture Example
If SA fails because of Q, NSW, and V while T is irrelevant, jump to V rather than chronologically reconsidering T.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
