# Heuristics, Admissibility, and Consistency

**Source:** pages 40-47

A heuristic $h(n)$ estimates the cost of a cheapest path from node $n$ to a goal. By convention, $h(n)=0$ at a goal.

## Admissibility

$h$ is admissible when it never overestimates the true remaining cost: $0\le h(n)\le h^*(n)$. With an admissible heuristic, A* tree search is cost-optimal under the chapter's assumptions.

## Consistency

$h$ is consistent when $h(n)\le c(n,a,n')+h(n')$ for every successor. This triangle inequality makes $f=g+h$ nondecreasing along a path. Consistency implies admissibility and lets graph-search A* safely treat the first expansion of a state as using its best path.

## Search Contours

A* expands in contours of increasing $f$. It expands every reachable node whose path remains below $C^*$ in $f$ (“surely expanded”), may expand some nodes at $C^*$, and should not need nodes above $C^*$ before an optimal goal.

See [[Algorithms/Ch03 - A-Star Search|A* Search]] and [[Mathematics/Ch03 - Mathematics|Mathematics]].

