# Comparisons and Distinctions

| Concept A | Concept B | Key distinction |
|---|---|---|
| Testing | Debugging | Testing observes execution; debugging finds a fault given a failure |
| Fault | Failure | Fault is the underlying defect; failure is incorrect behavior/result during execution |
| Reachability | Infection | Reach executes faulty location; infection creates incorrect state |
| Propagation | Revealability | Propagation carries incorrect state to final state/output; revealability requires observing it |
| Test design | Test automation | Design creates effective input values; automation embeds values in executable scripts |
| Test execution | Test evaluation | Execution runs/records; evaluation interprets/reports |
| Criteria-based | Human-based | Mathematical coverage goals vs. domain/user/problem intuition |
| Black-box | White-box | External descriptions vs. source internals; chapter prefers asking abstraction level |
| Unit | Module | Unit targets implementation units; module targets assembled related units/detailed design |
| Integration | System | Integration targets module interfaces/subsystems; system targets assembled system/architecture |
| Acceptance | System | Acceptance asks whether user/customer needs are met; system asks whether system meets specifications |
| MDTD | MBT | Strong overlap, but MDTD can derive abstract structures after implementation and directly from implementation artifacts |
