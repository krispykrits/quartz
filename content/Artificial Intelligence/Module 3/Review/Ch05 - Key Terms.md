# Chapter 5 Key Terms

**CSP:** Triple $\langle X,D,C\rangle$ of variables, domains, and constraints.  
**Assignment:** Set of variable/value bindings.  
**Partial solution:** Consistent partial assignment.  
**Solution:** Complete, consistent assignment.  
**Scope:** Variables participating in a constraint.  
**Relation:** Allowed tuples or predicate defining a constraint.  
**Support:** A neighboring value that satisfies the relevant binary constraint.  
**Node consistency:** Every domain value satisfies unary constraints.  
**Arc consistency:** Every value on a directed arc has support in the neighbor domain.  
**Path consistency:** Every consistent pair extends through a third variable.  
**k-consistency:** Any consistent assignment to k−1 variables extends to any kth variable.  
**Alldiff:** Global constraint requiring all participating variables to have distinct values.  
**Bounds consistency:** Maintain supported lower/upper endpoints rather than enumerating every value.  
**MRV:** Select unassigned variable with fewest legal values.  
**Degree heuristic:** Prefer tied variable constraining most unassigned neighbors.  
**LCV:** Prefer value eliminating fewest neighbor values.  
**Forward checking:** One-step domain pruning after assignment.  
**MAC:** Maintain arc consistency after decisions.  
**Conflict set:** Earlier variables implicated in a variable's failure.  
**No-good:** Assignment combination that cannot appear in any solution.  
**Min-conflicts:** Local repair by changing a conflicted variable to a minimum-conflict value.  
**Cycle cutset:** Variables whose removal leaves a forest.  
**Tree decomposition:** Tree of overlapping bags satisfying coverage, constraint coverage, and running intersection.  
**Tree width:** Largest bag size minus one.  
**Symmetry breaking:** Constraints that remove equivalent solutions while preserving representatives.
