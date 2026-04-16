---
type: project
title: "Road Intelligence Platform"
status: active
owner: "Tony Jung"
sponsor: "[[Ryan Thomson]]"
started: 2026-04-14
updated: 2026-04-16
tags:
  - project
  - lethbridge-county
  - road-intelligence-platform
related:
  - "[[projects/_index]]"
  - "[[Deadhead Ratio]]"
  - "[[Route Optimization]]"
  - "[[Fully Loaded Hard Savings]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Road Intelligence Platform

## Executive Summary

The Road Intelligence Platform uses GPS baseline data from the Lethbridge County grader fleet to identify and act on operational inefficiencies. The fleet spends 24.9% of its active engine time [[Deadhead Ratio|deadheading]]: traveling between work areas without grading. This non-productive travel costs an estimated $55,000 to $65,000 per year in fuel across the fleet, and $140,000 to $165,000 in [[Fully Loaded Hard Savings|fully loaded terms]] (fuel + labour + depreciation + maintenance, approximately 2.5 times fuel cost).

The fleet is covering the network: 98.3% of gravel segments are visited (2,500 of 2,542). The opportunity is to cover it with less travel, less overlap, and better daily sequencing.

A combined 2026 projection estimates $33,000 to $61,000 in annual fuel savings and $80,000 to $150,000 fully loaded when route optimization, spare coordination, mechanical follow-up, and visibility changes are combined.

**Gold standard KPI**: the ultimate measure of success is not just cost reduction but **how long a road maintains its integrity after grading**. The quality of grading, the conditions under which it happens, and the operator's technique all affect durability. Tier 3 workstreams ([[Weather-Responsive Scheduling]], [[Grader Performance Score]], [[Treatment Optimization]]) target this KPI directly.

**Sponsor**: [[Ryan Thomson]], Director, Public Works & Utilities.

## Fleet Baseline

Data period: April 7 2025 through April 8 2026 (367 days). Source: 1.52 million GPS breadcrumbs from 9 Titan-equipped graders, 1,101 fuel fill-up records at $1.57/L UFA dyed diesel, 3,097 road segments, 7 grader camps.

| Rank | Grader | Division | Deadhead Ratio | Grading Hrs | Deadhead Hrs | Deadhead Fuel |
|---|---|---|---|---|---|---|
| 1 (worst) | [[MG-048]] | Div 5 | 34.3% | 628 | 327 | $7,872 |
| 2 | MG-039 | Spare | 31.4% | 451 | 206 | $4,438 |
| 3 | MG-050 | Div 4 | 27.9% | 1,005 | 388 | $7,489 |
| 4 | [[MG-051]] | Div 1 | 26.2% | 660 | 234 | $4,787 |
| 5 | MG-044 | Spare | 22.1% | 1,015 | 288 | $6,804 |
| 6 | MG-046 | Div 3 | 21.4% | 666 | 182 | $3,866 |
| 7 | MG-047 | Div 6 | 17.8% | 1,081 | 233 | $4,878 |
| 8 (best) | MG-041 | Spare | 17.2% | 302 | 63 | $1,353 |
| | **Fleet** | | **24.9%** | **5,809** | **1,922** | **$41,487** |

MG-049 (Division 7) excluded due to confirmed data quality issues (no JD telematics, anomalous GPS patterns).

## Workstreams

| Workstream | Tier | Estimated Value (fuel) | Timeline | Status |
|---|---|---|---|---|
| [[Route Planner]] | 1 | $15,000-$35,000/yr | Sprint 4 (June) | active |
| [[Spare Coordination]] | 1 | $5,000-$15,000/yr | Sprint 4 | active |
| [[MG-048 Investigation]] | 1 | $5,000-$10,000/yr | Sprint 1-4 | active |
| [[Division 1 Depot Staging]] | 2 | $3,000-$5,000/yr net | Sprint 4 | planning |
| [[Demand-Driven Scheduling]] | 2 | Productivity gain | Sprint 4 | planning |
| [[Dust Control Coordination]] | 2 | $10,000-$25,000/yr | Sprint 4 | active |
| [[Fleet Efficiency Dashboard]] | — | $3,000-$8,000/yr | May 2026 | active |
| [[Weather-Responsive Scheduling]] | 3 | Longer road integrity | Phase 2 | concept |
| [[Grader Performance Score]] | 3 | Compounds over seasons | Phase 2-3 | concept |
| [[Treatment Optimization]] | 3 | Capital allocation | Phase 3 | concept |

Workstream pages: `wiki/projects/road-intelligence-platform/`

## 2026 Projection

| Lever | Conservative | Moderate |
|---|---|---|
| [[Route Planner|Route optimization]] (fuel) | $15,000 | $25,000 |
| [[Spare Coordination]] | $5,000 | $10,000 |
| [[MG-048 Investigation|MG-048 resolution]] | $3,000 | $5,000 |
| [[Division 1 Depot Staging|Depot staging (Div 1)]] | $2,000 | $3,000 |
| [[Dust Control Coordination]] | $5,000 | $10,000 |
| [[Fleet Efficiency Dashboard|Visibility / behavior change]] | $3,000 | $8,000 |
| **2026 Total (fuel)** | **$33,000** | **$61,000** |
| **[[Fully Loaded Hard Savings|Fully loaded]]** | **$80,000** | **$150,000** |

## Stakeholders

- **Sponsor**: [[Ryan Thomson]], Director, Public Works & Utilities
- **Project lead**: Tony Jung, Lead, Continuous Improvement
- **Field validation**: Shawn (pending stakeholder meeting for full context)

> [!NOTE] Entity pages pending
> Entity pages for Ryan Thomson, Shawn, MG-048, and MG-051 are on hold pending a stakeholder meeting with Cody, Shawn, and Lee to gather org context.

## Timeline

| Phase | Target | Workstreams |
|---|---|---|
| Dashboard | May 2026 | [[Fleet Efficiency Dashboard]] |
| Sprint 4 | June 2026 | [[Route Planner]], [[Spare Coordination]], [[Division 1 Depot Staging]], [[Demand-Driven Scheduling]], [[Dust Control Coordination]] |
| Sprint 1-4 | Ongoing | [[MG-048 Investigation]] |
| Phase 2 | Post-season | [[Weather-Responsive Scheduling]] |
| Phase 2-3 | Post-season | [[Grader Performance Score]] |
| Phase 3 | 2027+ | [[Treatment Optimization]] |

## Immediate Recommendations

From Report 2, §6:

- [ ] Share findings with Shawn for field perspective validation
- [ ] Investigate MG-048: hydraulic calibration, tire pressure, blade setup vs MG-050
- [ ] Approve [[Fleet Efficiency Dashboard]] deployment (weekly cadence)
- [ ] Approve [[Route Planner]] pilot (one willing division)
- [ ] Request GIS priority layer (High/Medium/Low per segment) for [[Demand-Driven Scheduling]]
- [ ] Schedule field team meeting (Cody, Shawn, Lee) for operational input

## Data Quality Notes

- **MG-049 (Division 7)**: excluded from all fleet averages. No JD telematics data, anomalous 3.4 km/h average GPS speed. Fuel fill records (117 fills, 22,700 L) are usable but GPS activity data is unreliable. Recommend investigating the GPS unit.
- **MG-051 battery disconnects**: 929 disconnect events in GPS data creating coverage gaps. Fill-record engine hours (1,520 hrs) are more reliable than GPS-derived hours (1,059 hrs).
- **Data cleaning**: 8,755 isCurrLoc API artifact records filtered out; 5,376 exact duplicates removed across the fleet.
- **Data provenance**: all figures are derived from measured GPS breadcrumbs and verified fuel fill-up records, not estimates or industry benchmarks.

> [!QUESTION] Open questions
> - **Baseline period**: which reference period anchors cost comparisons? (Recommended: 3-year average with fuel price normalization)
> - **Measurement scope**: which divisions and fleet units are in scope for the initial pilot?
> - **Pilot division**: which division runs the Route Planner first?
> - **MG-048 diagnosis**: terrain, operator technique, or equipment condition? (Investigation in progress)
> - **Additional source material**: project folder on old laptop contains decision history and early analysis not captured in the two PDF reports. To be ingested as `status: "historical"` when accessible.

## Artifacts

| Source | Location | Manifest Status |
|---|---|---|
| GPS Baseline Analysis (2026-04-14) | `.raw/projects/road-intelligence-platform/` | pending |
| Comprehensive Findings (2026-04-14) | `.raw/projects/road-intelligence-platform/` | pending |
| Project folder (old laptop) | not yet accessible | planned |
| Master manifest | `.raw/.manifest.json` | complete |

## Sources

- [[GPS Baseline Analysis]]
- [[Road Intelligence Platform Comprehensive Findings]]
