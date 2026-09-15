# Exam Cram

## Tier 1 — MUST KNOW ⭐⭐⭐
- RIPR: Reachability → Infection → Propagation → Revealability.
- Testing ≠ debugging.
- Testing can reveal failures; it cannot establish their absence.
- Coverage criteria answer **how to search** and **when to stop**.
- MDTD pipeline: artifact → model → criterion → requirements → tests → execution → evaluation.
- Four test tasks: design, automation, execution, evaluation.
- Testing levels: acceptance, system, integration, module, unit.
- Criteria-based and human-based test design are complementary.

## Tier 2 — VERY IMPORTANT ⭐⭐
- V-model mappings.
- Regression testing.
- Four mathematical structures: input domains, graphs, logic, grammars.
- Test requirement vs. coverage criterion.
- Black-box/white-box distinction and the chapter's abstraction-level critique.
- MDTD vs. model-based testing.

## Tier 3 — SUPPORTING ⭐
- OO testing variations: intra-method, inter-method, intra-class, inter-class.
- Personnel/division-of-labor argument.
- Low controllability/observability can make automation harder.

## Equation Cheat Sheet
$$
(2^{32})^3 = 2^{96}
$$
Three 32-bit inputs already create an enormous input space.

## Process Cheat Sheet
`Artifact → Structure → Criterion → Test Requirements → Test Specification → Input Values → Test Cases → Scripts → Results → Evaluation`

## Common Confusions
- **Coverage ≠ exhaustive testing.**
- **Automation ≠ test design.**
- **Executing the fault ≠ revealing the failure.**
- **Integration testing ≠ whole-system testing** in this textbook's terminology.
- **Criteria-based ≠ unit-only** and **human-based ≠ system-only**.

## If You Only Remember 10 Things
1. Testing observes execution.
2. Debugging locates a fault after failure.
3. Testing cannot prove no failures exist.
4. RIPR explains fault revelation.
5. Reach the fault.
6. Infect program state.
7. Propagate the bad state.
8. Reveal the incorrect result.
9. Coverage criteria systematically select tests and provide stopping rules.
10. MDTD raises abstraction and separates test design from construction/execution/evaluation.

## 5-Minute Pre-Exam Review
Recite RIPR, redraw the V model mappings, define coverage criterion/test requirement, list the four testing tasks, and trace Figure 2.4's MDTD pipeline.
