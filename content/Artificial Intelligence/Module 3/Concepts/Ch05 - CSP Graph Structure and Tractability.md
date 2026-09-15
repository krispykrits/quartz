# CSP Graph Structure and Tractability

**Source:** slides/pages 49–55.

## Definition / Core Idea
Constraint graph structure can collapse exponential search. Independent components solve separately; tree CSPs admit an exact $O(nd^2)$ two-pass algorithm; small cutsets isolate cyclic cores; tree width controls dynamic-programming cost.

## Lecture Example
Australia has disconnected Tasmania. Conditioning on SA breaks mainland cycles. A tree decomposition uses overlapping bags satisfying coverage, constraint coverage, and running intersection.

## Why It Matters
The lecture's central theme is that internal structure is computational leverage: modeling choices expose support, conflicts, and graph structure that general-purpose inference can exploit.

## Connections
- [[Lectures/Ch05 - Constraint Satisfaction Problems|Main Lecture Note]]
- [[Mathematics/Ch05 - Mathematics|Mathematics]]
- [[Review/Ch05 - Comparisons and Distinctions|Comparisons]]

## Exam-Level Understanding
Be able to define the concept using the lecture terminology, apply it to the Australia/Sudoku/8-queens examples where relevant, and explain what pruning or complexity benefit it provides.
