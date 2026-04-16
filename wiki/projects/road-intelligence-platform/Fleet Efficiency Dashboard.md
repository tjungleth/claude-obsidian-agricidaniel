---
type: workstream
title: "Fleet Efficiency Dashboard"
status: active
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "May 2026"
created: 2026-04-16
updated: 2026-04-16
tags:
  - workstream
  - road-intelligence-platform
  - deliverable
related:
  - "[[Deadhead Ratio]]"
  - "[[Route Planner]]"
  - "[[Spare Coordination]]"
  - "[[MG-048 Investigation]]"
  - "[[Fully Loaded Hard Savings]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Fleet Efficiency Dashboard

## Summary

The Fleet Efficiency Dashboard publishes grader fleet metrics on Power BI with a weekly cadence so that deadhead ratios, route overlap, and improvement are visible to operations and management. It is the visibility layer that makes all other workstreams measurable and accountable.

This is a cross-cutting deliverable, not a tier'd optimization opportunity. Its value comes from behavior change (operators and supervisors responding to visible metrics) rather than direct operational savings.

Timeline: May 2026 (Report 1, recommendation #5).

## Metrics to Display

From the two baseline reports, the dashboard should track:

- **[[Deadhead Ratio]]** per grader and per division (weekly)
- **Route overlap** (segments touched by multiple graders per cycle)
- **Improvement against baseline** (24.9% fleet average as the reference point)
- **Fuel consumption** per grader (L/hr and total litres)
- **Grading hours vs deadhead hours** per unit

## Estimated Value

From the 2026 combined projection (Report 2):

| Scenario | Visibility / Behavior Change (fuel) |
|---|---|
| Conservative | $3,000 |
| Moderate | $8,000 |

The value is indirect: visible metrics drive behavior change (operators self-correcting inefficient patterns, supervisors prioritizing high-deadhead units for route improvement). The dollar estimate reflects the fuel savings attributable to visibility alone, separate from the solver-driven Route Planner savings.

## Timeline

- **Target**: May 2026 (ahead of Sprint 4 Route Planner deployment)
- Publishing the dashboard first establishes baseline visibility before optimization changes are introduced, providing a clean before/after comparison

## Dependencies

- GPS baseline data (complete: the two reports establish this)
- Power BI access and publishing permissions
- Agreement on which metrics and at what cadence (weekly recommended by both reports)

## Next Actions

- [ ] Approve dashboard deployment (Report 2, recommendation #3)
- [ ] Define metric definitions and refresh cadence with Ryan Thomson
- [ ] Build Power BI report from GPS baseline dataset
- [ ] Publish and communicate to operations team

## Sources

- [[GPS Baseline Analysis]] — "Publish the Fleet Efficiency dashboard on Power BI so deadhead ratios are visible weekly and improvement can be tracked against this baseline" (recommendation #5, May target)
- [[Road Intelligence Platform Comprehensive Findings]] — "Publish the metrics on a weekly cadence so the fleet can track deadhead, overlap, and improvement against baseline" (recommendation #3)
