# Why and How

## Why can't testing prove the absence of failures?
The chapter states that testing can show the presence of failures, not their absence, and that finding all failures is undecidable.

## Why can a test execute faulty code and still pass?
Because one or more RIPR conditions may fail. Execution may not infect state, the bad state may not propagate, or the tester may not observe the incorrect part.

## Why use abstraction?
Implementation detail creates overwhelming complexity. Abstract mathematical structures let designers reason about testing at a simpler level.

## How do coverage criteria help?
They structure the search through the input space and provide stopping rules.

## Why design tests during development?
Tests derived from requirements/design can expose defects before implementation, when they are cheaper to correct.

## How does MDTD transform an artifact into tests?
Artifact → abstract structure → coverage criterion → test requirements → refined specifications → input values/test cases → scripts → execution → results → evaluation.

## Why separate testing tasks?
Test design, automation, execution, and evaluation require different skills. Division of labor allows scarce highly technical designers to support more testers.

## Why are criteria-based and human-based testing complementary?
Criteria-based design gives systematic mathematical coverage; human-based design targets domain-specific, unusual, boundary, invalid, and stress situations that formal criteria may miss.
