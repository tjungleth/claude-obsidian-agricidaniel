---
type: workstream
title: "Dust Control Coordination"
status: active
tier: 2
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "Sprint 4 (June 2026)"
created: 2026-04-16
updated: 2026-04-16
tags:
  - workstream
  - road-intelligence-platform
  - tier-2
related:
  - "[[Route Planner]]"
  - "[[Demand-Driven Scheduling]]"
sources:
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Dust Control Coordination

## Summary

Dust control coordination prevents wasted grading by synchronizing grader schedules with dust control treatment. When a grader grades a road that was recently treated with calcium chloride, the treatment is degraded or destroyed. When dust control is applied before scheduled grading, the application is wasted. Both scenarios burn budget with no net benefit.

Estimated value: $10,000 to $25,000 per year in avoided waste (Report 2, Tier 3 assessment).

This workstream was elevated from Tier 3 to active status because it has a concrete dollar estimate, a Sprint 4 timeline, and is operationally ready alongside the Route Planner deployment.

## Mechanism

Two coordination rules:

1. **Avoid grading dust-controlled roads after treatment**: if a road segment has been treated with calcium chloride, exclude it from the grading plan until the next treatment cycle, or flag it as low-priority for grading.
2. **Coordinate grading before calcium application**: schedule grading to complete before the dust control crew arrives, so the road surface is properly shaped before treatment is applied.

Both rules require the [[Route Planner]] to know which segments have been or are about to be treated. This can be as simple as a shared calendar or treatment schedule between grading and dust control crews.

## Estimated Value

From the Tier 3 opportunity assessment (Report 2):

| Metric | Range |
|---|---|
| Avoided waste | $10,000 to $25,000/yr |

From the 2026 combined projection (Report 2, fuel only):

| Scenario | Dust Control Coordination |
|---|---|
| Conservative | $5,000 |
| Moderate | $10,000 |

The value is primarily avoided waste (grading that doesn't need to be redone, treatment that isn't destroyed) rather than direct fuel savings. The projection table captures only the fuel component.

## Timeline

- **Target**: Sprint 4 (June 2026)
- Concurrent with [[Route Planner]] deployment: the same daily planning system can flag treatment-conflict segments

## Dependencies

- Dust control treatment schedule (when and where calcium is applied)
- [[Route Planner]] operational (to exclude or deprioritize treated segments)
- Coordination protocol between grading supervisors and dust control crew

## Next Actions

- [ ] Obtain current dust control treatment schedule and application plan
- [ ] Define segment-level conflict rules (post-treatment exclusion window, pre-treatment grading deadline)
- [ ] Integrate treatment schedule into Route Planner as a constraint layer

## Sources

- [[Road Intelligence Platform Comprehensive Findings]] — "Avoid grading dust-controlled roads after treatment and coordinate grading before calcium application" (Tier 3 mechanism); $10,000 to $25,000/yr avoided waste (Tier 3 estimated value)
