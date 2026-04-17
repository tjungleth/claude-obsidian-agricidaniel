---
type: workstream
title: "Spare Coordination"
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
  - "[[Route Planner]]"
  - "[[Route Optimization]]"
  - "[[Deadhead Ratio]]"
  - "[[MG-048 Investigation]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Spare Coordination

> [!important] Measured update (2026-04-16)
> Spare deadhead figures below are from the April 14 PDF. Measured values in the Fabric pipeline confirm within ~1.5 percentage points: MG-039 31.4% (confirmed), MG-044 23.4% (PDF 22.1%), MG-041 18.9% (PDF 17.2%). Table below updated. See [[GPS Baseline Results 2026-04-16]].

## Summary

Spare coordination is the second-highest-value Tier 1 workstream. 93% of multi-grader route overlap involves at least one spare grader. The core problem is not territory boundaries but dispatch coordination: spares sometimes re-grade roads the primary grader has already completed because there is no system to exclude already-graded segments from spare routes.

Estimated value: $5,000 to $15,000 per year in fuel savings (Report 2, Tier 1).

## Mechanism

The workstream has two components:

1. **Assign spares to highest unmet demand**: instead of sending a spare to a division based on ad hoc requests, use the route planner's knowledge of which segments are due for grading and which have already been completed.
2. **Exclude already-graded segments**: when generating a spare's daily route, filter out segments the primary grader has already visited that cycle.

Both components build on the [[Route Planner]] infrastructure: the same [[PyVRP]] solver and cost matrix, extended to coordinate spare assignments alongside primary grader routes.

## Overlap Analysis

From Report 2, §3 (2,542 total visited gravel segments, 2,017 touched by two or more graders):

| Overlap Category | Segments | % of Overlap | Actionable? |
|---|---|---|---|
| Involves at least one spare | 1,871 | 93% | Yes: spare coordination |
| ...of which: 2+ primaries + spare | 453 | 22% | Yes: territory + spare |
| ...of which: spare-only (no primary conflict) | 1,418 | 70% | Yes: spare scheduling |
| Pure primary-vs-primary (no spare) | 146 | 7% | Yes: territory boundaries |

The 79% headline overlap rate (2,017 of 2,542) looks alarming, but the breakdown shows most of it is addressable through better spare dispatch rather than redrawing division boundaries.

## Spare Grader Variability

From Report 1, key finding #4: spare deadhead ratios show the widest spread in the fleet because spares have no assigned territory:

| Grader | PDF Estimate | Measured (2026-04-16) |
|---|---|---|
| MG-039 | 31.4% | **31.4%** (confirmed) |
| MG-044 | 22.1% | **23.4%** |
| MG-041 | 17.2% | **18.9%** |

Without optimized deployment, a spare's deadhead depends on where it starts each day relative to where it is needed.

## Estimated Value

From the Tier 1 opportunity assessment (Report 2):

| Metric | Range |
|---|---|
| Fuel savings | $5,000 to $15,000/yr |

From the 2026 combined projection (Report 2, fuel only):

| Scenario | Spare Coordination (fuel) |
|---|---|
| Conservative | $5,000 |
| Moderate | $10,000 |

## Timeline

- **Target**: Sprint 4 (June 2026)
- Concurrent with [[Route Planner]] development: spare coordination extends the same infrastructure

## Dependencies

- [[Route Planner]] operational (same solver, same cost matrix)
- Real-time or daily knowledge of which segments the primary grader has already visited

## Next Actions

- [ ] Define spare assignment protocol with field team (Cody, Shawn, Lee)
- [ ] Extend Route Planner to generate spare routes excluding completed segments
- [ ] Validate spare deployment patterns with Shawn's field perspective (Report 2, recommendation #1)

## Sources

- [[GPS Baseline Analysis]] — spare grader variability: MG-039 (31.4%), MG-044 (22.1%), MG-041 (17.2%) (key finding #4)
- [[Road Intelligence Platform Comprehensive Findings]] — overlap analysis: 93% involves spares (§3); spare deployment coordination $5,000 to $15,000/yr, Sprint 4 (Tier 1); "Assign spares to highest unmet demand and exclude already-graded segments" (Tier 1 mechanism)
