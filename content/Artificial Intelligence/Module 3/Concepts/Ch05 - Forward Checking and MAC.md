# Forward Checking and MAC

**Source:** slides/pages 37–39.

## Definition / Core Idea
Forward checking removes values from unassigned neighbors of the latest assignment. Maintaining Arc Consistency (MAC) goes further by running arc-consistency propagation after each decision.

## Lecture Example
The lecture domain table reaches an empty SA domain after WA=R, Q=G, V=B. MAC can also detect contradictions between two unassigned singleton domains.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
