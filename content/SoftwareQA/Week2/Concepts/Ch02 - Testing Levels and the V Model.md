# Testing Levels and the V Model
**Source:** Section 2.3 and Figure 2.3.

| Development artifact/activity | Testing level |
|---|---|
| Requirements analysis | Acceptance testing |
| Architectural design | System testing |
| Subsystem design | Integration testing |
| Detailed design | Module testing |
| Implementation | Unit testing |

## Key Insight
The V model pairs testing with the artifact from which tests are derived. Tests should be **designed concurrently** with development activities even though execution may wait for implementation.

## Regression Testing
Performed after changes to ensure previously possessed functionality remains.

## Why Early Design Matters
Designing tests early can reveal defects in requirements/design before those defects become expensive implementation faults.
