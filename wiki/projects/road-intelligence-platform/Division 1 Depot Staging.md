---
type: workstream
title: "Division 1 Depot Staging"
status: planning
tier: 2
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "Sprint 4 (June 2026)"
created: 2026-04-15
updated: 2026-04-15
tags:
  - workstream
  - road-intelligence-platform
  - tier-2
  - operational-considerations
related:
  - "[[Facility Location]]"
  - "[[Route Planner]]"
  - "[[Deadhead Ratio]]"
  - "[[Route Optimization]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Division 1 Depot Staging

> [!important] Measured update (2026-04-16)
> MG-051 measures **43.6% deadhead** in the Fabric pipeline — the worst in the grader fleet. The depot-misalignment thesis is confirmed and intensified: MG-051 is not just a depot outlier, it is the single largest routing inefficiency in the grader fleet. MG-051 deadhead fuel = $14,650 over 2 years ≈ **$7,325/yr**. See [[GPS Baseline Results 2026-04-16]].

## Summary

[[MG-051]] operates from Coaldale Shop, which is 12.6 km from the demand centroid of Division 1, with 47% of the division's roads more than 15 km from camp. This makes MG-051 the fleet's depot outlier at 6.2 km average start distance (next closest primary: MG-046 at 1.4 km).

Rather than relocating Coaldale Shop, this workstream uses multi-day planning and overnight staging to compensate: when MG-051 is scheduled to work the far western half of Division 1, it stages overnight near the work area instead of deadheading back to Coaldale Shop each day.

Estimated value: $3,000 to $5,000 per year net (Report 2, Tier 2).

## Mechanism

1. Identify multi-day work blocks in Division 1's western territory using the [[Route Planner]].
2. Pre-position MG-051 at or near the work area for consecutive shifts, avoiding the 12+ km round-trip deadhead to Coaldale Shop.
3. Coordinate staging logistics (overnight parking, operator transport if needed).

The value is "net" because staging has its own costs (operator commute, security of parked equipment). The estimate assumes these are outweighed by fuel and time savings.

## Estimated Value

From the Tier 2 opportunity assessment (Report 2):

| Metric | Range |
|---|---|
| Fuel savings (net) | $3,000 to $5,000/yr |

From the 2026 combined projection (Report 2, fuel only):

| Scenario | Depot Staging (fuel) |
|---|---|
| Conservative | $2,000 |
| Moderate | $3,000 |

## Timeline

- **Target**: Sprint 4 (June 2026)

## Dependencies

- [[Route Planner]] operational (to identify multi-day western work blocks)
- Field team input on staging logistics and feasibility (Cody, Shawn, Lee)

## Next Actions

- [ ] Map Division 1 western territory work patterns from GPS data
- [ ] Identify candidate staging locations
- [ ] Get field team input on overnight staging feasibility and logistics

## Operational Considerations

### How Overnight Staging Works

Grader parks at a strategic location (intersection, pullout, county yard) near the start of next day's route instead of returning to the home depot. Operator needs separate transport to/from the staging point. Three options:

- **Crew truck shuttle**: supervisor drops off/picks up the operator at the staging point.
- **Personal vehicle**: operator drives their own vehicle to the staging point.
- **Two-up staging**: two operators carpool, each takes their grader from the staging point.

### The Math

Every km of avoided deadhead saves 85-90% of that km's fuel cost (grader burns ~30 L/hr at travel speed vs near-zero for a parked machine).

MG-051 example: currently deadheads ~45 min each way from Coaldale yard. Staging near Picture Butte could cut 30+ min of deadhead per shift, roughly 15L of fuel saved per day. Crew truck shuttle adds ~$15-20 in fuel per round trip vs ~$45-60 in grader fuel saved: net positive even with the shuttle.

### Barriers to Address

- **Equipment security**: graders left overnight need secure, visible locations. County yards preferred, but not always available near optimal staging points.
- **Cold starts**: winter staging means the grader sits unplugged overnight. Block heater access matters; a cold-soaked grader in -30C takes 30+ min to warm up, eating into the time savings.
- **Operator comfort**: some operators will not want to leave "their" machine somewhere overnight. This is a change management issue, not a logistics one.
- **Insurance/liability**: confirm county policy on equipment left at non-county locations overnight.

### Decision Framework

Overnight staging makes sense when: deadhead exceeds 20 min one-way, a secure staging location exists within 10 min of route start, and block heater access is available in winter. It does not make sense for short deadheads or routes that already start near the home depot.

See also: [[Route Optimization]], [[Facility Location]].

## Sources

- [[GPS Baseline Analysis]] — "Coaldale Shop is 12.6 km from the demand centroid of Division 1, with 47% of the division's roads more than 15 km from camp" (key finding #2)
- [[Road Intelligence Platform Comprehensive Findings]] — MG-051 at 6.2 km avg start distance, depot outlier (§4); Division 1 depot staging $3,000 to $5,000/yr net, Sprint 4 (Tier 2)
