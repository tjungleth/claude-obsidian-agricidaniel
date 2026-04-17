---
type: source
title: "Unit Fuel Rates Reconciliation"
source_type: historical analysis memo
author: "Tony Jung"
date_published: 2026-04-10
raw_file: ".raw/projects/road-intelligence-platform/historical/2026-04-10-unit-fuel-rates-reconciliation.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - fuel-rates
  - analysis
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[UFA Price and Division Correction Thread 2026-04-09]]"
  - "[[GPS Baseline Analysis]]"
  - "[[Deadhead Ratio]]"
---

# Source: Unit Fuel Rates Reconciliation

**Memo origin**: Cowork session analysis, April 10, 2026 (approximate)
**Status**: Historical. Cross-validates per-unit L/hr against three independent sources, confirms fleet-average ~21 L/hr, captures Shawn's division-assignment corrections from the same day.

## Summary

Three-source cross-validation of per-unit grader fuel rates: FuelEconomyMain fill records (1,101 fills), JD telematics (2025 idle/load hours), CAT telematics (Fleet Utilization 2025). Pipeline used a flat 22 L/hr estimate for all units. Actual per-unit rates vary from 18.9 (MG-050) to 23.6 (MG-048). Fleet average ~21 L/hr, making the 22 L/hr estimate close but slightly high. Pipeline fuel-cost numbers land within 5% of reality. Per-unit rates are ready to plug into `UNIT_FUEL_RATES` in the notebooks for a precision pass.

## Pages Created or Enriched from This Source

- [[Deadhead Ratio]] — per-unit L/hr methodology table
- [[Road Intelligence Platform]] — corrected per-unit fuel rates
- [[Fleet Efficiency Dashboard]] — per-unit rates as precision input

## Per-Unit Fuel Rates

| Unit | Division | Make | Actual L/hr | Pipeline Used | Delta |
|---|---|---|---|---|---|
| MG-039 | Spare | CAT | 22.8 | 22.0 | +0.8 |
| MG-044 | Spare | JD | 23.1 | 22.0 | +1.1 |
| MG-046 | **Div 2** | CAT | 20.9 | 22.0 | -1.1 |
| MG-047 | Div 6 | JD | 20.5 | 22.0 | -1.5 |
| MG-048 | Div 5 | JD | 23.6 | 22.0 | +1.6 |
| MG-049 | Div 7 | JD | 21.8 | 22.0 | -0.2 |
| MG-050 | Div 4 | JD | 18.9 | 22.0 | -3.1 |
| MG-051 | Div 1 | CAT | 20.0 | 22.0 | -2.0 |

**Fleet average**: ~21 L/hr
**Pipeline accuracy**: within 5%

## Implications

- **MG-050 (Div 4, JD 772GP)** is the most fuel-efficient grader at 18.9 L/hr.
- **MG-048 (Div 5, JD 772GP)** at 23.6 L/hr is the highest rate. Drives the Refined Build Plan's proposed MG-050/MG-048 swap (~$3,500/yr savings by pairing most-efficient grader with heaviest workload, 324 km Div 5).
- **MG-044 (spare, JD 872GP)** at 23.1 L/hr is the second-highest. Spare deployment should consider rate-workload pairing.
- **MG-046's 20.9 L/hr** now correctly attributes to Div 2 (Titan label was stale). All Div 2 and Div 3 fuel aggregates need recomputation.

## Corrections Cascade

Downstream pages needing updates in Cluster 4 (enrichment):

1. [[Road Intelligence Platform]] anchor: per-grader table (MG-046 Div 3 → Div 2)
2. [[Facility Location]] concept: MG-046 camp-distance row (Div 3 → Div 2)
3. [[Division 1 Depot Staging]]: verify MG-046 reference context
4. Sources [[GPS Baseline Analysis]] and [[Road Intelligence Platform Comprehensive Findings]]: add correction callouts noting PDFs carry stale Titan labels
5. Div 2 and Div 3 aggregates: recompute with MG-046 attributed to Div 2; Div 3 has no GPS-equipped unit so no GPS-derived aggregates

## Raw File

`.raw/projects/road-intelligence-platform/historical/2026-04-10-unit-fuel-rates-reconciliation.md`
