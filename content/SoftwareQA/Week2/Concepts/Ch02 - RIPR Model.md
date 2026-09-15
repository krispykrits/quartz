# RIPR Model
**Source:** Section 2.1, Figure 2.1.

## Definition
The RIPR model states four conditions needed for a fault to produce an observable test failure:
1. **Reachability**
2. **Infection**
3. **Propagation**
4. **Revealability**

## Technical Explanation
A test must first execute the faulty location. Execution must create an incorrect program state. That state must survive/affect later execution until it changes some final state or output. Finally, the tester must observe the incorrect portion.

## Intuitive Explanation
A bug can exist without a test exposing it. The test has to get to it, make something go wrong, carry that wrongness to something visible, and actually look at the right thing.

## Why It Matters
RIPR explains why code coverage alone does not guarantee fault detection.

## Figure 2.1 Exam Reading
`Test → Faulty Location → Incorrect Program State → Incorrect Final State → Observed Failure`

If any link fails, the test may pass even though a fault exists.

## Omission Faults
The chapter says RIPR also applies when code is missing. If execution reaches where the missing code should be, the program counter—part of program state—has the wrong value.

## Exam-Level Understanding
Be able to diagnose a non-revealing test by identifying which RIPR condition failed.
