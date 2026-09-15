# Domain Types and Constraint Arity

**Source:** slides/pages 8–14.

## Definition / Core Idea
Domain type affects solver choice: finite discrete domains support general CSP propagation/search; infinite, continuous, and structured arithmetic domains can require specialized methods. Constraints may be unary, binary, ternary, n-ary, or global.

## Lecture Example
The lecture contrasts explicit finite domains, scheduling arithmetic, linear continuous constraints, 8-queens, and the global `Alldiff` constraint.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
