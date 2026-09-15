# Chapter 2 - Model-Driven Test Design

## 📚 Chapter Navigation

### Core
- [[Lectures/Ch02 - Model-Driven Test Design|Main Lecture Note]]
- [[Mathematics/Ch02 - Mathematics|Mathematics]]
- [[Review/Ch02 - Concept Map|Concept Map]]
- [[Review/Ch02 - Comparisons and Distinctions|Comparisons]]
- [[Review/Ch02 - Key Terms|Key Terms]]
- [[Review/Ch02 - Why and How|Why and How]]
- [[Review/Ch02 - Exam Cram|Exam Cram]]
- [[Review/Ch02 - Practice Questions|Practice Questions]]
- [[Active Recall/Ch02 - Active Recall|Active Recall]]
- [[Active Recall/Ch02 - Active Recall Answers|Answer Key]]

### Concepts
- [[Concepts/Ch02 - RIPR Model|RIPR Model]]
- [[Concepts/Ch02 - Software Testing Activities|Software Testing Activities]]
- [[Concepts/Ch02 - Testing Levels and the V Model|Testing Levels and the V Model]]
- [[Concepts/Ch02 - Coverage Criteria|Coverage Criteria]]
- [[Concepts/Ch02 - Criteria-Based and Human-Based Test Design|Criteria-Based and Human-Based Test Design]]
- [[Concepts/Ch02 - Black-Box and White-Box Testing|Black-Box and White-Box Testing]]
- [[Concepts/Ch02 - MDTD and Model-Based Testing|MDTD and Model-Based Testing]]

## 🎯 Chapter Theme
**Designers are more efficient and effective if they can raise their level of abstraction.**

Chapter 2 argues that completely correct software is effectively unreachable as a testing goal. Testing therefore focuses on **software behavior** and uses abstraction, mathematical structures, and coverage criteria to design a manageable set of tests that are likely to reveal important failures.

## Ultimate Chapter 2 Takeaway
> **Good software testing is not exhaustive input checking. It is disciplined test design.**  
> Model-Driven Test Design (MDTD) raises testing from implementation details to abstract models, derives test requirements from coverage criteria, and then turns those requirements into executable tests. A test reveals a fault only when the RIPR conditions hold: it **reaches** the fault, **infects** program state, the incorrect state **propagates**, and the failure is **revealed** to the tester.
