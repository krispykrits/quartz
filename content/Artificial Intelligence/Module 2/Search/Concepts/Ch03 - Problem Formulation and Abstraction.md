# Problem Formulation and Abstraction

**Source:** pages 3-16

Search is the computational process by which a problem-solving agent considers action sequences that form paths to a goal. The chapter assumes episodic, single-agent, fully observable, deterministic, static, discrete, known environments and atomic states.

## Four-Phase Process

1. **Goal formulation:** choose an objective that limits relevant actions.
2. **Problem formulation:** construct an abstract model of states and actions.
3. **Search:** simulate action sequences until a solution is found or failure established.
4. **Execution:** perform the selected actions.

Open-loop execution is justified only under the chapter's strong assumptions. Uncertain or changing worlds call for closed-loop monitoring.

## Five Components of a Search Problem

- state space and an **initial state**;
- one or more **goal states**, or an `Is-Goal` test;
- `Actions(s)`;
- `Result(s,a)`;
- `Action-Cost(s,a,s') = c(s,a,s')`.

A path is an action sequence. A solution reaches a goal. An optimal solution has minimum additive path cost.

## Abstraction

The state “Arad” suppresses road condition, weather, companions, fuel, and other real details. A useful abstraction removes irrelevant detail while retaining distinctions needed for a valid, implementable, good solution. Too much detail makes search intractable; too little can produce unusable plans.

## Examples in the Lecture

- Romania route finding and touring
- grid and vacuum worlds ($n2^n$ states for an $n$-cell vacuum world)
- 8-puzzle
- Knuth's infinite numerical state space
- VLSI layout, robot navigation, assembly sequencing, protein design

## Exam-Level Understanding

Given a new problem, identify all five formal components and defend the abstraction boundary. Distinguish the real environment from its state-space model.

See [[Lectures/Ch03 - Solving Problems by Searching|Main Lecture Note]] and [[Review/Ch03 - Why and How|Why and How]].

