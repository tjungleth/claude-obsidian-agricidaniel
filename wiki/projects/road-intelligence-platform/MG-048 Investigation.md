---
type: workstream
title: "MG-048 Investigation"
status: active
tier: 1
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "Sprint 1-4"
created: 2026-04-15
updated: 2026-04-15
tags:
  - workstream
  - road-intelligence-platform
  - tier-1
related:
  - "[[Route Planner]]"
  - "[[Spare Coordination]]"
  - "[[Deadhead Ratio]]"
  - "[[Facility Location]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# MG-048 Investigation

## Summary

[[MG-048]] (Division 5) is the fleet's most expensive single inefficiency. It deadheads more kilometres than it grades (55 km vs 36 km per shift) and burns fuel at 23.6 L/hr, the highest rate in the fleet. At 34.3% deadhead, it costs $7,872 per year in deadhead fuel alone.

Three factors stack together: Division 5 carries the heaviest gravel workload (324 km, 72% more than Division 3), MG-048 has the highest measured fuel rate, and route patterns may still be improvable. This workstream diagnoses how much of the problem is equipment, how much is terrain, and how much is routing.

Estimated value: $5,000 to $10,000 per year (Report 2, Tier 1).

## Deep Dive Metrics

From Report 2, §2 (MG-048 vs fleet):

| Metric | MG-048 | Fleet Avg |
|---|---|---|
| Shift duration | 8.9 hrs | — |
| Grading per shift | 3.7 hrs (42%) | — |
| Deadhead per shift | 1.9 hrs (21%) | — |
| Grading km per shift | 36 km | — |
| Deadhead km per shift | 55 km | — |
| Fuel rate | 23.6 L/hr | 21.1 L/hr |
| JD high-load engine time | 24% | 5-9% |

The 24% high-load profile is the most distinctive anomaly: other JD-equipped graders run 5-9% high-load, making MG-048 roughly 3 to 5 times the norm.

## Investigation Questions

From Report 1 (recommendation #2) and Report 2 (§2 recommended follow-up):

1. **Terrain**: is Division 5's topography inherently harder on equipment, or is the route structure driving unnecessary load?
2. **Operator technique**: does operator behavior (blade angle, speed, gear selection) contribute to the high fuel rate?
3. **Equipment condition**: is there a mechanical issue (hydraulic calibration, tire pressure, blade setup) driving the 24% high-load and 23.6 L/hr?

Report 2 recommends asking Fleet to check hydraulic calibration, tire pressure, and blade setup against MG-050 as the comparison unit (recommendation #2).

## Potential Outcomes

### Equipment fix

If the 24% high-load anomaly is equipment-driven, a mechanical fix reduces fuel rate toward the fleet average (21.1 L/hr), saving approximately $3,500 per year in fuel.

### MG-050/MG-048 swap

Moving MG-050 (most efficient at 18.9 L/hr) to Division 5 (heaviest workload) and MG-048 to a lighter division could save approximately $3,500 per year (Report 1, recommendation #4). This swap is gated on understanding whether MG-048's load profile is machine-driven or terrain-driven. If the issue is Division 5 terrain, the swap would just move the problem.

### Route improvement

Use the [[Route Planner]] to test whether daily sequencing can cut MG-048 deadhead materially during grading season (Report 2, §2 follow-up).

### Combined

These outcomes are not mutually exclusive. An equipment fix plus route optimization could deliver savings at both the fuel-rate and deadhead-ratio levels simultaneously.

## Estimated Value

From the Tier 1 opportunity assessment (Report 2):

| Metric | Range |
|---|---|
| Estimated value | $5,000 to $10,000/yr |

From the 2026 combined projection (Report 2, fuel only):

| Scenario | MG-048 Resolution (fuel) |
|---|---|
| Conservative | $3,000 |
| Moderate | $5,000 |

Note: the Tier 1 range ($5,000 to $10,000) is wider than the projection's conservative-to-moderate ($3,000 to $5,000), suggesting the Tier range includes upside scenarios or partially-loaded estimates.

## Timeline

- **Span**: Sprint 1 through Sprint 4 (the investigation runs across the project)
- **Gate**: the [[Route Planner]] pilot and MG-050/MG-048 swap evaluation both depend on understanding the high-load anomaly first

## Next Actions

- [ ] Request Fleet inspection: hydraulic calibration, tire pressure, blade setup vs MG-050 (Report 2, recommendation #2)
- [ ] Review JD telematics high-load detail for root cause indicators
- [ ] Schedule field team meeting (Cody, Shawn, Lee) for operational input on MG-048 Division 5 conditions
- [ ] After diagnosis: decide swap vs fix vs route improvement (or combination)

## Sources

- [[GPS Baseline Analysis]] — MG-048 at 34.3% deadhead, 23.6 L/hr, $7,872/yr fuel, 24% high-load vs 5-9% fleet (key finding #1); MG-050/MG-048 swap at ~$3,500/yr (recommendation #4); Division 5 has 324 km gravel road, 72% more than Division 3 (key finding #1)
- [[Road Intelligence Platform Comprehensive Findings]] — MG-048 deep dive: 55 km deadhead vs 36 km grading per shift, 8.9 hr shift (§2); investigation + resolution $5,000 to $10,000/yr, Sprint 1-4 (Tier 1); "Evaluate the MG-050/MG-048 swap after the high-load issue is understood" (§2 follow-up)
