# Chapter 2 - Model-Driven Test Design

**Source:** textbook screenshots supplied by the user, Chapter 2, sections 2.1–2.7 and Figures 2.1–2.5.

## Big Picture
Software testing is inherently complicated. The chapter rejects the naive goal of proving software “correct” and instead asks whether its **behavior is acceptable** with respect to reliability, safety, maintainability, security, efficiency, and other concerns.

The chapter's central engineering response is **abstraction**. MDTD decomposes testing into smaller tasks, isolates those tasks, and lets designers work at a higher abstraction level using mathematical structures rather than implementation details.

## Roadmap
1. [[Concepts/Ch02 - RIPR Model|Software Testing Foundations and RIPR]]
2. [[Concepts/Ch02 - Software Testing Activities|Software Testing Activities]]
3. [[Concepts/Ch02 - Testing Levels and the V Model|Testing Levels]]
4. [[Concepts/Ch02 - Coverage Criteria|Coverage Criteria]]
5. [[Concepts/Ch02 - Criteria-Based and Human-Based Test Design|Model-Driven Test Design]]
6. Why MDTD matters

## Learning Objectives
After studying this chapter, you should be able to:
- distinguish testing, test failure, and debugging;
- explain why testing can demonstrate failures but not their absence;
- explain all four RIPR conditions;
- distinguish acceptance, system, integration, module, unit, and regression testing;
- explain why test design should occur throughout development;
- explain the purpose of coverage criteria and stopping rules;
- distinguish criteria-based and human-based test design;
- distinguish test design, automation, execution, and evaluation;
- trace the MDTD pipeline from software artifact to evaluated results;
- explain why MDTD raises the level of abstraction.

## 60-Second Chapter Summary
Testing cannot practically try all inputs, and finding all failures is undecidable. A useful test must do more than execute faulty code: under the [[Concepts/Ch02 - RIPR Model|RIPR model]], it must reach the fault, infect program state, propagate the bad state to output/final state, and reveal that incorrect portion to the tester. Testing work is divided into design, automation, execution, and evaluation. Tests also operate at levels tied to development artifacts: acceptance, system, integration, module, and unit testing. [[Concepts/Ch02 - Coverage Criteria|Coverage criteria]] provide systematic rules for selecting tests and deciding when enough tests have been designed. MDTD turns software artifacts into abstract structures, applies criteria to produce test requirements, refines those requirements into specifications/input values, executes tests, evaluates results, and feeds findings back into design.

# 2.1 Software Testing Foundations

Testing can show the **presence of failures**, not their absence. Finding all failures in a program is undecidable. A test is often considered successful/effective when it finds an error.

### Definitions
- **Testing:** evaluating software by observing its execution.
- **Test Failure:** execution of a test that results in a software failure.
- **Debugging:** the process of finding a fault given a failure.

A fault does not necessarily produce a visible failure for every input. The fault/failure relationship is explained by [[Concepts/Ch02 - RIPR Model|RIPR]].

### Figure 2.1 — RIPR Model
The figure shows a chain:

`Test → reaches faulty location → incorrect program state → propagates → incorrect portion of final state → revealed through observed portion`

The four conditions are:
1. **Reachability** — execution reaches the faulty location.
2. **Infection** — executing it produces an incorrect program state.
3. **Propagation** — the incorrect state affects the final state/output.
4. **Revealability** — the tester observes the incorrect part.

If the tester observes only a correct portion of final state, the failure is not revealed. The model also applies to faults of omission: when missing code should have executed, the program counter itself is part of an incorrect state.

# 2.2 Software Testing Activities

A **test engineer** is an IT professional responsible for one or more technical testing activities such as designing test inputs, producing test case values, running scripts, analyzing results, and reporting them.

Every engineer involved in development wears the “hat” of a test engineer at times because each software artifact should have associated test cases. The person best positioned to define those tests is often the artifact's designer.

### Figure 2.2 — Activities of Test Engineers
The figure separates:
- test design;
- instantiation into executable tests;
- execution on the computer/program;
- collection of output;
- evaluation of results;
- management/coordination by a test manager.

Formal coverage criteria are powerful because they guide **which inputs to use** and provide **stopping rules**.

# 2.3 Testing Levels Based on Software Activity

Testing levels correspond to development artifacts.

| Testing level | Assesses software with respect to |
|---|---|
| Acceptance testing | Requirements / users' needs |
| System testing | Architectural design and overall behavior |
| Integration testing | Subsystem design and interfaces |
| Module testing | Detailed design |
| Unit testing | Implementation |

### Figure 2.3 — The V Model
The left side descends through requirements analysis, architectural design, subsystem design, detailed design, and implementation. The right side ascends through unit, module, integration, system, and acceptance tests.

The important lesson is **not** to wait until implementation to design tests. Tests can be designed concurrently with development artifacts. Early test design can expose defects in design decisions before implementation, reducing the cost of correction.

### Acceptance Testing
Determines whether completed software meets customer needs captured during requirements analysis. It must involve users or people with strong domain knowledge.

### System Testing
Determines whether the assembled system meets its specifications. It assumes pieces work individually and asks whether the system works as a whole. It commonly targets design/specification problems and is an expensive place to find low-level faults.

### Integration Testing
Assesses whether module interfaces within a subsystem have consistent assumptions and communicate correctly. In this book, integration testing does **not** mean testing the entire integrated system.

### Module Testing
Tests individual modules in isolation, including interactions among component units and associated data structures. It is commonly developer testing.

### Unit Testing
Tests implementation-level units such as procedures/functions. It is the “lowest” testing level and is often performed by programmers/developers.

### Regression Testing
Performed after software changes to ensure updated software still possesses functionality it had before the updates.

### Object-Oriented Variation
The chapter notes:
- **intra-method testing** — individual methods;
- **inter-method testing** — pairs of methods in the same class;
- **intra-class testing** — an entire class, usually sequences of calls;
- **inter-class testing** — multiple classes, a form of integration testing.

# 2.4 Coverage Criteria

The essential problem is the **number of possible inputs**. Even a tiny method averaging three 32-bit integers has more than **80 octillion possible inputs** according to the chapter's example. Exhaustive testing is therefore impossible in practice.

This creates two problems:
1. **How do we search the input space?**
2. **When do we stop?**

[[Concepts/Ch02 - Coverage Criteria|Coverage criteria]] answer both by imposing structure on test selection and giving stopping rules. Good criteria seek broad coverage with relatively little redundant overlap.

Benefits described in the chapter include:
- more effective test generation with fewer tests;
- reduced redundancy;
- traceability from tests to software artifacts;
- support for regression-test decisions;
- an approximate stopping rule;
- suitability for automation.

A **test requirement** is a specific element of a software artifact that a test case must satisfy or cover. A **coverage criterion** is a rule or collection of rules that yields test requirements.

Examples:
- “cover every statement” → one requirement per statement;
- “cover every functional requirement” → one requirement per functional requirement.

The chapter argues that many apparently different coverage criteria reduce to a small number of mathematical structures: **input domains, graphs, logic expressions, and syntax descriptions (grammars).**

## Sidebar — Black-Box and White-Box Testing
See [[Concepts/Ch02 - Black-Box and White-Box Testing|Black-Box and White-Box Testing]]. The book argues that asking whether a criterion is black-box or white-box is often the wrong question. A better question is: **from what level of abstraction is the structure drawn?**

# 2.5 Model-Driven Test Design

**Test design** is the process of creating input values that will effectively test software.

The chapter divides test development into four tasks:
1. **Test design**
2. **Test automation**
3. **Test execution**
4. **Test evaluation**

These tasks demand different skills; assigning all of them to one person can waste expertise.

## 2.5.1 Test Design

### Criteria-Based Test Design
Creates test values that satisfy engineering goals such as coverage criteria. It is the most technical/mathematical testing task and relies on discrete mathematics, programming, and testing knowledge.

### Human-Based Test Design
Uses application-domain knowledge, testing knowledge, and user-interface knowledge. Designers deliberately seek stress conditions, boundary values, invalid values, and unusual user actions.

The chapter stresses that the two approaches are **complementary** rather than tied rigidly to unit vs. system testing.

See [[Concepts/Ch02 - Criteria-Based and Human-Based Test Design|Criteria-Based and Human-Based Test Design]].

## 2.5.2 Test Automation
Test automation embeds test values into executable scripts. Automated support for **test design** is not itself test automation under the chapter's definition.

Difficulty depends on the software under test. Low controllability or observability can make automation substantially harder.

## 2.5.3 Test Execution
Test execution runs tests and records results. With automation, execution can be trivial; without automation, it may become the most time-consuming activity.

## 2.5.4 Test Evaluation
Test evaluation interprets test results and reports them to developers. It can be harder than expected, particularly when expected outputs cannot be cleanly encoded in assertions.

## 2.5.5 Test Personnel and Abstraction
A shortage of highly technical test engineers motivates division of labor. A skilled criteria-based designer can support many people doing automation, execution, and evaluation.

### Figure 2.4 — Model-Driven Test Design
The figure separates a **design abstraction level** from an **implementation abstraction level**.

A software artifact is represented by a model/structure. Criteria produce test requirements, which may be refined into test specifications. These lead to input values/test cases, then scripts, results, and evaluation. Results can feed back into test design.

The core idea: **raise the level of abstraction** so a smaller number of specialized designers can perform the mathematical design work while others construct, execute, and evaluate tests.

### MDTD Pipeline
```text
Software artifact
      ↓
Abstract model / structure
      ↓
Coverage criterion
      ↓
Test requirements
      ↓
Refined test requirements / test specifications
      ↓
Input values / test cases
      ↓
Test scripts
      ↓
Execution / test results
      ↓
Test evaluation
      ↺ feedback into design
```

## Figure 2.5 — Java Method → CFG → Requirements → Test Paths
The textbook demonstrates the process on a small Java `indexOf()` method:
1. take the software artifact;
2. model it as a control-flow graph;
3. represent the graph abstractly using edges, initial node, and final nodes;
4. apply **edge-pair coverage**;
5. derive six test requirements;
6. choose complete test paths that collectively cover those requirements.

The example requirement **[3, 2, 3, 2]** means the subpath from node 2 to 3 and back to 2 must be executed.

The important point is the abstraction transition:
**source code → graph → coverage requirements → test paths**.

## Sidebar — MDTD and Model-Based Testing
See [[Concepts/Ch02 - MDTD and Model-Based Testing|MDTD and Model-Based Testing]]. The chapter says the approaches overlap substantially but are not identical.

# 2.6 Why MDTD Matters

MDTD represents years of thinking about the role of software testing. A key insight is that the **definitions and applications of test criteria are independent of testing level**. This abstraction greatly simplifies testing.

A second major insight is the separation of **human-based** and **criteria-based** design. The chapter rejects treating them as competing schools: both are needed.

A third insight is organizational: separating test design from construction/execution makes it possible to assign different activities to people with different skill sets.

The four mathematical structures introduced in Section 2.4 organize the later technical chapters:
- input domains;
- graphs;
- logic expressions;
- grammars.

The chapter connects these to RIPR:
- input-domain criteria mainly explore the input space;
- graph criteria emphasize **reachability**;
- logic criteria emphasize **reachability + infection**;
- grammar-based criteria can require **reachability + infection + propagation**.

## Ultimate Chapter 2 Takeaway
> **Testing becomes tractable when test design is treated as an engineering abstraction problem.**  
> We cannot test every input or prove the absence of failures through testing. Instead, MDTD models software artifacts mathematically, applies coverage criteria to derive explicit test requirements, and separates design from automation, execution, and evaluation. The RIPR model explains why merely executing faulty code is insufficient: the fault must be reached, infect state, propagate, and be revealed.
