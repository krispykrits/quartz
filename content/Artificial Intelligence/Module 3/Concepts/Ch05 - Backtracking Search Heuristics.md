# Backtracking Search Heuristics

**Source:** slides/pages 31–36.

## Definition / Core Idea
CSP backtracking exploits commutativity: select one unassigned variable, try values, infer consequences, and backtrack on failure. MRV is fail-first, degree breaks ties by future impact, and LCV is fail-last.

## Lecture Example
After WA=red and NT=green, SA has only blue and MRV selects it. Initially, degree favors SA because it constrains five mainland neighbors.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
