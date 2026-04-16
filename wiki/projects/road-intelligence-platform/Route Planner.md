---
type: workstream
title: "Route Planner"
status: active
tier: 1
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "Sprint 4 (June 2026)"
created: 2026-04-15
updated: 2026-04-15
tags:
  - workstream
  - road-intelligence-platform
  - tier-1
related:
  - "[[Route Optimization]]"
  - "[[PyVRP]]"
  - "[[Capacitated Arc Routing]]"
  - "[[Deadhead Ratio]]"
  - "[[Spare Coordination]]"
  - "[[MG-048 Investigation]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Route Planner

## Summary

The Route Planner is the highest-value workstream in the [[Road Intelligence Platform]]. It generates fuel-minimized daily grading sequences for each division, replacing experience-based manual route selection. The focus is the May to October grading season, where demand is highest and absolute savings per shift are greatest.

Two solver approaches will be evaluated: [[PyVRP]] (node-based VRP with arc-to-node transformation) and a [[Capacitated Arc Routing|CARP solver]] (native arc routing). Both will be tested against the same input data to determine which produces shorter routes for grader operations.

Estimated value: $15,000 to $35,000 per year in fuel savings; $40,000 to $90,000 in [[Fully Loaded Hard Savings|fully loaded terms]] (Report 2, Tier 1).

## Mechanism

The planner builds optimized daily routes by:

1. Taking the day's priority road segments for a division (fed by [[Demand-Driven Scheduling]] once the GIS priority layer is available, or by the current divisional route map initially).
2. Computing a road-network cost matrix between all segment pairs and between segments and the grader's camp.
3. Running [[PyVRP]] to find the sequence that minimizes total [[Deadhead Ratio|deadhead travel]] while visiting all priority segments.
4. Producing a sequenced grading plan for the operator.

The solver accounts for the grader's start depot (camp), return-to-camp requirement, and shift duration constraint.

### Solver Comparison: PyVRP vs CARP

Grader routing is fundamentally an [[Capacitated Arc Routing|arc routing problem]]: graders traverse road segments (arcs), not visit point locations (nodes). The current approach uses [[PyVRP]] with an arc-to-node transformation (representing each road segment as a node at its centroid). This is standard practice and produces good results, but it is an approximation.

CMU research on snow plow routing ([[CMU Snow Plow Routing]]) showed that native CARP solutions produced routes **3% to 156% shorter** than VRP-based commercial software.

**Evaluation plan:**

| Approach | Solver | Problem class | Status |
|---|---|---|---|
| A (current) | [[PyVRP]] | VRP with arc-to-node transformation | Implementation in progress |
| B (evaluate) | CARP solver (Hexaly, custom, or open-source) | Native arc routing | To be evaluated against Approach A |

**Test protocol:**
1. Use the same input data for both: road segments, camp locations, shift constraints, cost matrix
2. Run both solvers on one division's daily workload
3. Compare: total deadhead km, total route time, fuel estimate
4. If CARP is materially better (>5% reduction in deadhead), adopt or offer as an alternative mode

The evaluation does not block Sprint 4 delivery. PyVRP launches first; CARP evaluation runs in parallel or immediately after the pilot.

## Estimated Value

From the Tier 1 opportunity assessment (Report 2):

| Metric | Range |
|---|---|
| Fuel savings | $15,000 to $35,000/yr |
| Fully loaded (approx 2.5x fuel) | $40,000 to $90,000/yr |

From the 2026 combined projection (Report 2, fuel only):

| Scenario | Route Optimization (fuel) |
|---|---|
| Conservative | $15,000 |
| Moderate | $25,000 |

## Timeline

- **Target**: Sprint 4 (June 2026)
- **Pilot approach**: start with one willing division and measure route adherence, fuel use, and grading coverage after rollout (Report 2, recommendation #4)

## Dependencies

- Road-network cost matrix (computed from GIS road data)
- GIS priority layer for [[Demand-Driven Scheduling]] (Report 2, recommendation #5): not required for initial launch (can use current divisional routes) but needed for priority-weighted routing
- GPS baseline data (complete: the two reports establish this)

## Next Actions

- [ ] Approve Route Planner pilot (Report 2, recommendation #4)
- [ ] Select pilot division
- [ ] Build road-network cost matrix from GIS data
- [ ] Request GIS priority layer (High/Medium/Low per segment)
- [ ] Schedule field team meeting (Cody, Shawn, Lee) for operational input
- [ ] Identify candidate CARP solver (Hexaly, open-source, or custom implementation)
- [ ] Run CARP vs PyVRP comparison on one division's daily workload
- [ ] Decision: adopt CARP, keep PyVRP, or offer both as modes

## Sources

- [[GPS Baseline Analysis]] — "Build the daily route optimization tool that generates fuel-minimized grading sequences for each operator, starting from their camp" (recommendation #3)
- [[Road Intelligence Platform Comprehensive Findings]] — Route optimization (PyVRP), $15,000 to $35,000/yr fuel, $40,000 to $90,000 fully loaded, Sprint 4 June (Tier 1 table); "Start with one willing division" (recommendation #4)
- [[CMU Snow Plow Routing]] — constraint programming CARP produced 3-156% shorter routes than commercial VRP software
- [[Research Municipal Fleet Route Optimization Case Studies]] — synthesis: CARP vs VRP is the key technical finding for grader routing
