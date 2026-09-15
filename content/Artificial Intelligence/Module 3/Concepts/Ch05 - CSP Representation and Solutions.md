# CSP Representation and Solutions

**Source:** slides/pages 4–7.

## Definition / Core Idea
A CSP is the triple $\langle X,D,C\rangle$: variables, domains, and constraints. A solution is a complete, consistent assignment. The factored representation exposes variable interactions so one conflict can prune whole families of assignments.

## Lecture Example
Map coloring uses variables WA, NT, Q, NSW, V, SA, T with domains {red, green, blue} and binary inequality constraints for adjacent regions.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
