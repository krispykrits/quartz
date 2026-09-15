# Concept Map

```mermaid
flowchart TD
  A[Problem-solving agent] --> B[Problem formulation]
  B --> C[State-space graph]
  C --> D[Search tree]
  D --> E[Frontier and reached]
  E --> F[Best-first framework]
  F --> G[Uninformed search]
  F --> H[Informed search]
  G --> I[BFS / UCS / DFS / ID / Bidirectional]
  H --> J[Greedy / A* / Memory-bounded]
  J --> K[Heuristic quality]
  K --> L[Relaxation / PDB / Landmarks / Learning]
```

## Core Relationships

- A problem definition determines the state-space graph.
- Search generates a tree of paths over that graph.
- The frontier ordering determines which node is expanded next.
- `reached` controls redundant paths and affects memory.
- $f$ specializes best-first search: depth, $g$, $h$, or $g+h$.
- Heuristic conditions determine A* guarantees; heuristic quality determines practical effort.
- Memory-bounded algorithms preserve A*-like guidance while trading storage for regeneration.

Return to [[00 - Chapter Home|Chapter Home]].

