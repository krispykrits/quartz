---
aliases:
- Intelligent Agents
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
tags:
- artificial-intelligence
- intelligent-agents
title: Chapter 2 - Intelligent Agents
type: lecture
---

# Chapter 2: Intelligent Agents

*Source: slides 1--71*

## 🎯 Big Picture

This lecture establishes the agent-centered framework used throughout
the course. An **agent** perceives an environment through sensors and
acts on it through actuators. The key abstraction is the
[[Agents and Rationality#Agent function|agent function]],
which maps an entire percept sequence to an action. That abstract
function is implemented by an agent program running on an architecture.

The lecture then asks what makes an agent's behavior *good*. The answer
is **rationality**: for each percept sequence, choose the action
expected to maximize the specified performance measure, given the
evidence perceived so far and the agent's prior knowledge. Rationality
is therefore not omniscience or guaranteed success. It is decision
quality under available information.

Before implementing an agent, the lecture requires a complete task
specification using [[PEAS and Task Environments|PEAS]]
and classification of the environment along seven dimensions. Those
properties determine what kinds of internal machinery the agent needs.
The lecture then develops four canonical program structures---simple
reflex, model-based reflex, goal-based, and utility-based---and shows
that any can be augmented with learning.

Finally, the lecture connects agent design to knowledge representation.
State can be represented atomically, as a vector of factors, or
structurally as objects and relations. Greater expressiveness can make
descriptions dramatically more concise, but also makes reasoning and
learning more complex.

## Lecture Roadmap

``` text
Agent + Environment
        ↓
Percepts / Percept Sequence
        ↓
Agent Function → Agent Program + Architecture
        ↓
Performance Measure
        ↓
Rationality
        ↓
PEAS Task Specification
        ↓
Environment Properties
        ↓
Agent Program Structure
   ↙       ↓       ↘
Reflex   Goal     Utility
   \       |       /
       Learning
          ↓
World Representation
Atomic → Factored → Structured
```

## What I Should Know After This Lecture

-   Define agent, percept, percept sequence, agent function, agent
    program, and architecture.
-   Explain why rationality maximizes **expected** performance rather
    than actual realized performance.
-   Diagnose reward-hacking failures caused by poorly specified
    performance measures.
-   Construct a PEAS description for a new task.
-   Classify a task environment along all seven dimensions and justify
    each classification.
-   Compare the four canonical agent program types and identify when
    each becomes insufficient.
-   Trace the four components of a learning agent.
-   Compare atomic, factored, and structured representations and explain
    the expressiveness/complexity trade-off.
-   Read and apply the two main mathematical expressions in the lecture:
    the agent function and expected utility.

## ⏱️ 60-Second Lecture Summary

An agent senses and acts. Its abstract behavior is an agent function
mapping percept histories to actions, while its program implements that
function on an architecture. A rational agent chooses actions expected
to maximize an externally defined performance measure using its percept
history and prior knowledge. Agent design begins with PEAS and the
environment's observability, agent count, determinism,
episodic/sequential nature, dynamism, discreteness, and known/unknown
status. Practical programs progress from simple reflex to model-based
reflex to goal-based to utility-based. Learning adds a performance
element, learning element, critic, and problem generator. Internal
states may be atomic, factored, or structured.

## 1. Agents and Environments

Slides 3--9 define an agent as anything viewed as perceiving through
**sensors** and acting through **actuators**. Human, robotic, and
software agents differ in implementation but share this loop.

The diagram on slide 4 shows the central feedback loop:

``` text
Environment → Sensors → Agent decision process → Actuators → Environment
                percepts                    actions
```

The "?" inside the agent is deliberate: the rest of the chapter fills in
increasingly sophisticated decision mechanisms.

A **percept** is what sensors perceive at one instant. A **percept
sequence** is the complete percept history. Action may depend on
built-in knowledge and the percept sequence so far, but not on
information never perceived.

See [[Agents and Rationality]] and [[Ch02 - Mathematics#Agent Function]].

### Vacuum-Cleaner World

Slides 7--8 use two squares, A and B. Each is clean or dirty. The agent
senses its location and local dirt status; actions are `Right`, `Left`,
`Suck`, and `NoOp`. A simple policy is: if dirty, suck; otherwise move
to the other square. The partial table demonstrates that different
agents correspond to different action choices for percept
histories---and that a complete table grows without bound.

## 2. Rationality and Performance Measures

Slides 10--20 define rationality consequentially: behavior is judged by
the sequence of environment states it causes. The **performance
measure** is the objective success criterion, not the agent's
self-assessment.

A central design danger is specifying a proxy instead of the desired
environmental outcome. Slide 12's vacuum agent rewarded for "amount of
dirt cleaned" can rationally dump dirt back onto the floor and
repeatedly clean it. The lecture's rule is to reward the state you
actually want achieved, not the behavior you imagine will achieve it.

Rationality depends on four things: 1. performance measure, 2. prior
knowledge, 3. available actions, 4. percept sequence to date.

The simple vacuum policy is rational only under the assumptions on slide
15. Slide 16 deliberately changes assumptions to show rationality is
contextual: movement penalties, recurring dirt, or unknown geography all
require different behavior.

> [!warning] **Rationality ≠ omniscience.** Slide 17 distinguishes
> maximizing expected performance from knowing the actual future
> outcome. A rational choice can have a bad realized outcome.

Slides 18--20 extend rationality to information gathering, exploration,
learning, and autonomy. Looking before crossing a busy road is itself a
rational action because it improves future percepts. An agent lacking
complete prior knowledge should learn from experience rather than remain
permanently dependent on designer assumptions.

## 3. PEAS and Task Environments

Slides 21--23 introduce [[PEAS and Task Environments|PEAS]]: - **P**erformance measure - **E**nvironment -
**A**ctuators - **S**ensors

The lecture's golden rule: **specify the task environment as fully as
possible before designing the agent.**

The automated taxi example makes the point that performance criteria can
conflict: safe, fast, legal, comfortable, profitable, and low-impact
driving cannot always be simultaneously maximized. Restricting the
environment can simplify the design problem.

## 4. Seven Environment Properties

Slides 24--33 classify environments by: 1. fully / partially /
unobservable, 2. single-agent / multiagent, 3. deterministic /
nondeterministic / stochastic, 4. episodic / sequential, 5. static /
dynamic / semidynamic, 6. discrete / continuous, 7. known / unknown.

See [[Task Environment Properties]] and [[Ch02 Comparisons and Distinctions]].

The hardest general case combines partial observability, multiple
agents, nondeterminism, sequential decisions, dynamics, continuity, and
unknown dynamics. Slide 33 emphasizes that classifications are modeling
choices and may not be perfectly cut-and-dried.

## 5. From Agent Function to Agent Structure

Slides 34--53 move from behavior to implementation. The lecture repeats:
```
agent = architecture + program
```

The program implements the agent function; the architecture supplies
the physical computational substrate, sensors, and actuators.

### Why table lookup fails

A table-driven program is conceptually valid but practically impossible
because the number of possible percept histories explodes. See
[[Ch02 - Mathematics#Table-Driven Agent Size]].

### Four canonical program types

See [[Agent Architectures]]. - **Simple reflex:** current
percept → condition-action rule. - **Model-based reflex:** internal
state + transition model + sensor model → rule. - **Goal-based:**
model + explicit goal + lookahead. - **Utility-based:** compare
desirability of outcomes, especially under trade-offs and uncertainty.

The diagrams on slides 39, 44, 48, and 52 form a progression: each
architecture adds information used in deciding "what action I should do
now."

## 6. Learning Agents

Slides 54--59 add learning to any base architecture. The diagram on
slide 55 contains four components: - **performance element** chooses
actions, - **learning element** changes knowledge, - **critic**
evaluates behavior against an external performance standard, - **problem
generator** proposes informative exploratory actions.

The learning element may modify state estimation, transition models,
sensor models, rules, goals, or utility. See [[Learning Agents]].

## 7. Representing States

Slides 60--66 introduce an expressiveness axis:

``` text
Atomic → Factored → Structured
```

Atomic states are opaque identities. Factored states expose a fixed
vector of attributes. Structured states expose objects, their
attributes, and relationships. Slide 65's chess example illustrates the
compression advantage of expressiveness, while warning that reasoning
and learning generally become more complex.

Slide 66 introduces a separate, orthogonal distinction: **localist
vs. distributed** representation. See [[State Representations]].

## 8. Professor Discussion Questions

The five explicit questions on slide 70 are preserved in
[[Review/Ch02 - Practice Questions#Professor Discussion Questions]]
with lecture-grounded answer guidance.

## Looking Ahead

Slide 71 explicitly connects this chapter to later material: - Chapters
3--4: search for goal-based agents using atomic representations. -
Chapter 5: constraint satisfaction with factored representations. -
Chapter 6: adversarial search in competitive multiagent settings. -
Chapter 11: planning. - Chapters 12--18: uncertainty and
utility/decision-theoretic agents. - Chapters 19, 21--23: learning
algorithms.

**Next lecture:** Solving Problems by Searching (Chapter 3).
