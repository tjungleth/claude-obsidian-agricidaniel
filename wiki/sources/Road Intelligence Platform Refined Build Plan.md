---
type: source
title: "Road Intelligence Platform Refined Build Plan"
source_type: historical build plan
author: "Tony Jung"
date_published: 2026-04-14
raw_file: ".raw/projects/road-intelligence-platform/historical/REFINED_BUILD_PLAN.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - build-plan
  - master-plan
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[PRD Road Intelligence Platform]]"
  - "[[Road Intelligence Platform Build Plan]]"
  - "[[Financial Rebase]]"
  - "[[GPS Baseline Analysis Spec]]"
  - "[[GPS Baseline Analysis]]"
---

# Source: Refined Build Plan

> [!note] Measured baseline available 2026-04-16
> This historical plan's estimates are superseded by measured values. See [[GPS Baseline Results 2026-04-16]] for grader deadhead 31.8%, $46K/yr fuel, $14K-$18.5K/yr savings. Sprint schedule, architecture, 5-level optimization stack, and 21-variable analysis below remain the master plan.

**Full title**: Road Intelligence Platform — Refined Build Plan
**Author**: Tony Jung, Lead Continuous Improvement
**Date**: April 14, 2026
**Status**: Historical. The laptop project's "START HERE" master plan. Builds on the April 6 build plan and the April 10 financial rebase. 989 lines. Most execution-detail-rich document in the historical set.

## Summary

Grounds the original plan in verified data (367 days of GPS extracted, fuel rates from 1,101 fill records, OEM telematics in hand, operator maps received). Articulates a design philosophy ("analytics alone don't save fuel; tools do") with two deliverables for two audiences: the Road Intelligence Dashboard for Ryan and Shawn's weekly review, the Route Planner for Shawn's daily morning routine. Adds the Grader Performance Score as the grading-quality metric missing from the original plan. Breaks Phase 1 into 5 sprints spanning Apr 14 to October. Adds a full Depot Location Analysis, a 21-variable optimization breakdown across 6 tiers, a 5-level optimization stack (Level 0 capital allocation through Level 5 quality feedback), and a systems-level "three-program triangle" showing how grading, dust control, and base stabilization interact.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — design philosophy, 5-sprint plan, 5-level stack, 21 variables, capacity equation, three-program triangle
- [[Route Planner]] — Sprint 4 spec, PyVRP config, multi-depot start/end, Shawn's interface
- [[Fleet Efficiency Dashboard]] — Sprint 3 4-page spec
- [[Grader Performance Score]] — RID definition, 50/25/25 composite, operator framing, feedback loop into priority
- [[Dust Control Coordination]] — Parallel May-June track, CVRP config, $10-25K/yr estimate
- [[Division 1 Depot Staging]] — $3,300-$5,500/yr single-division savings
- [[Demand-Driven Scheduling]] — replacing fixed rotation
- [[Deadhead Ratio]] — capacity equation (5pp reduction = +550 hrs = +4,400 km/yr)
- [[Facility Location]] — 7-camp table with camp-to-centroid distances

## Key Facts

- **Sprint schedule**: S1 Apr 14-25 (baseline), S2 Apr 28-May 9 (spatial + depot), S3 May 12-30 (lakehouse + dashboard), S4 June (Route Planner), S5 Jul-Oct (Performance Score + measurement + Council report)
- **Fleet tracked fuel**: $377,438/yr (7 units, 240,407 L, $1.57/L UFA)
- **Fleet engine hours**: ~11,060/yr across 7 tracked graders
- **Road network**: 1,810 km gravel, 3,097 segments, 2,542 gravel, 2,491 connect (one large graph), 158 km paved corridors, 16 dead-ends totaling 8 km
- **Segment micro-geography**: 52% of gravel segments <500m, 38% take <2 min to grade at 8 km/h
- **Depot table** (all 7 camps by camp-to-centroid): Barons (4.1 km), Iron Springs (4.0), Readymade (4.5), Nolan Hill (5.4), Monarch (7.3, 23% roads >15km), Picture Butte (9.0, 20% roads >15km), Coaldale Shop (12.6, **47% roads >15km**)
- **Reassignment optimization**: current 6-way fleet cost $299,354/yr, optimal $293,669/yr = $5,685/yr. MG-050/MG-048 swap alone = ~$3,500/yr.
- **Capacity equation**: every 5 percentage-point deadhead reduction frees ~550 grading hours = 4,400 km/yr additional road graded
- **Multi-day staging**: Div 1 alone 3-day staged plan saves $2,950/yr gross, fleet-wide $4,000-$6,000/yr net after pickup truck logistics
- **5-year projection**: $50K-$110K (2026) compounding to $415K-$685K cumulative by 2030

## Six Optimization Tiers (21 Variables)

1. **Structural**: depot locations / staging, division sizing, grader-to-division reassignment, segment grouping into "grading runs", spare/rover deployment
2. **Fleet & Equipment**: MG-048 high-load anomaly (24% vs 5-9% for other JDs), per-unit fuel variability, idle patterns (13-28%)
3. **Temporal & Scheduling**: shift duration amortization, demand-driven scheduling (vs fixed rotation), weather-responsive grading, seasonal demand patterns
4. **Operational / Technique**: grading speed optimization (3-15 km/h range), number of passes, deadhead speed curve, dead-end segment handling
5. **Quality & Effectiveness**: operator technique variance, assessor calibration (0.58-point spread), road surface sub-type interaction
6. **Economic**: fully-loaded cost ($100-120/hr vs $33 fuel-only), cost of road failure ($30-40/km grading vs $200-500/km emergency repair)

## Five-Level Optimization Stack

| Level | Question | Method | Frequency |
|---|---|---|---|
| 0. Capital Allocation | Stabilization vs dust control vs grading per segment? | NPV per segment per treatment | Annual budget |
| 1. Facility Location | Optimal camp and staging point placement | P-median, K-medoids | Annual / on infra change |
| 2. Fleet Assignment | Which grader in which territory at which camp? | Joint optimization | Seasonal |
| 3. Weekly Planning | Priority segments and sequencing | PyVRP + ALNS + LKH-3 | Weekly |
| 4. Daily Operations | Today's route, overnight staging | PyVRP daily multi-depot | Daily |
| 5. Quality Feedback | RID and operator performance | Grader Performance Score | Monthly, continuous |

## Three-Program Triangle

Grading ($500K/yr fuel), Dust Control ($393K/yr calcium), and Base Stabilization ($150K+/yr) interact directly. Today they step on each other: graders destroy dust control treatments, base-stabilized roads get graded on fixed rotation when they need less, dust control applies to roads about to be graded. With the platform: grade before dust control (calcium bonds to fresh surface), deprioritize stabilized roads, drop priority on dust-controlled roads, calculate per-segment NPV across the three treatments. Phase 3 joint optimization, data foundations built in 2026.

## Risks (updated from original plan)

- **Mitigated**: GPS data quality (three-source cross-validation, MG-049 flagged)
- **Active**: operators won't use Route Planner (UX critical, pilot with willing lead first); PSD program momentum loss (Dashboard Program Health page is early warning); surveillance perception (framing matters)
- **Known**: assessor calibration variance (0.58-point spread), design for it
- **Low risk**: Fabric F2 capacity (schedule around Ops pipeline), Titan GPS access (CSV export fallback)

## Raw File

`.raw/projects/road-intelligence-platform/historical/REFINED_BUILD_PLAN.md`
