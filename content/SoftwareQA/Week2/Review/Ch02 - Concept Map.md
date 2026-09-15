# Concept Map

```text
Software testing is too large for exhaustive testing
                    │
                    ▼
             Raise abstraction
                    │
         ┌──────────┴──────────┐
         ▼                     ▼
  Coverage Criteria        Human-Based Design
         │                     │
         ▼                     ▼
Test Requirements      Likely problem situations
         │
         ▼
   MDTD test design
Artifact → Model → Requirements → Input Values
                               │
                               ▼
                 Automation → Execution → Evaluation
                               │
                               ▼
                         Failure revealed?
                               │
                               ▼
                    Reach → Infect → Propagate → Reveal
```

## Development ↔ Testing
`Requirements ↔ Acceptance`  
`Architecture ↔ System`  
`Subsystem ↔ Integration`  
`Detailed design ↔ Module`  
`Implementation ↔ Unit`
