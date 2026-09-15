# Chapter 5 Why and How

## Why does CSP representation help?
Because constraints expose interactions among variables, allowing one contradiction or unsupported value to eliminate entire families of assignments.

## Why re-enqueue incoming arcs in AC-3?
A deletion in $D_i$ can invalidate supports that values in neighboring domains previously relied on. Rechecking affected incoming arcs drives propagation to a fixed point.

## Why can arc consistency miss failure?
It reasons one directed edge at a time. A cycle can have support on every individual edge yet have no globally consistent assignment, as in the two-color triangle.

## Why use MRV and degree together?
MRV confronts the variable most likely to fail now; degree breaks ties by selecting the variable with the greatest impact on future choices.

## Why is LCV the opposite direction?
Every variable must eventually be assigned, so expose risky variables early; only one solution is needed, so try the value most likely to leave flexibility.

## How does forward checking fail to match MAC?
Forward checking stops after pruning neighbors of the assigned variable. MAC continues rechecking arcs affected by those deletions, exposing multi-step cascades.

## Why learn no-goods?
A contradiction can recur beneath many different irrelevant prefixes. A learned no-good prunes every recurrence of the same bad combination.

## Why can min-conflicts be effective?
When solutions are dense in complete-state space, small repairs can reach feasibility quickly. The lecture uses n-queens as the canonical example.

## Why do trees matter?
A rooted tree has no cycles, so directional arc consistency followed by supported forward assignment eliminates the need for backtracking.

## How do cutsets and tree width isolate hardness?
Cutset conditioning puts exponential work into a small cyclic core. Tree decomposition puts exponential work into bag size; bounded width yields polynomial dependence on the number of variables.
