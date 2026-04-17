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
  - "[[GPS Baseline Results 2026-04-16]]"
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
  - "[[PRD Road Intelligence Platform]]"
  - "[[Road Intelligence Platform Refined Build Plan]]"
  - "[[Financial Rebase]]"
  - "[[Unit Fuel Rates Reconciliation]]"
  - "[[UFA Price and Division Correction Thread 2026-04-09]]"
---

# Road Intelligence Platform

> [!important] Measured baseline landed 2026-04-16
> The Fabric pipeline ([[GPS Baseline Results 2026-04-16]]) replaces the April 14 PDF estimates with measured values from 2 years of GPS data (2024-03-06 to 2026-04-09, 2.67M deduplicated breadcrumbs, 5,653 shifts across 38 devices).
>
> Headline: **grader deadhead 31.8%** (fleet-wide 43.1%), measured deadhead fuel ~$46K/yr. Savings revised to $14K-$18.5K/yr graders / $40K-$55K/yr full fleet at 30-40% reduction. Division correction: MG-046 is Div 2 (not Div 3, Titan label stale).

## Executive Summary

The Road Intelligence Platform uses GPS baseline data from the Lethbridge County grader fleet to identify and act on operational inefficiencies. The **measured grader deadhead ratio is 31.8%** across 9 GPS-equipped graders over 2 years. Fleet-wide (all 38 devices: graders + trucks + tractors + blade) the ratio is 43.1%. Measured grader deadhead fuel cost is ~$46,000/yr ($92,784 over the 2-year period), or ~$115,000/yr in [[Fully Loaded Hard Savings|fully loaded terms]] (approximately 2.5x fuel).

The fleet is covering the network: 98.3% of gravel segments were visited per the April 14 PDF analysis (2,500 of 2,542). The opportunity is to cover it with less travel, less overlap, and better daily sequencing.

Revised 2026 savings: $14K-$18.5K/yr in grader fuel at 30-40% deadhead reduction, $40K-$55K/yr full fleet. The prior April 14 PDF headline ($55K-$65K fuel / $140K-$165K fully loaded / $33K-$61K combined fuel projection) is superseded. See [[GPS Baseline Results 2026-04-16]].

**Gold standard KPI**: the ultimate measure of success is not just cost reduction but **how long a road maintains its integrity after grading**. The quality of grading, the conditions under which it happens, and the operator's technique all affect durability. Tier 3 workstreams ([[Weather-Responsive Scheduling]], [[Grader Performance Score]], [[Treatment Optimization]]) target this KPI directly.

**Sponsor**: [[Ryan Thomson]], Director, Public Works & Utilities.

## Fleet Baseline

Data period: **2024-03-06 through 2026-04-09 (2 full years)**. Source: 2,666,866 deduplicated Titan GPS breadcrumbs across 38 devices (9 graders + 2 spare GPS + 6 field tractors + 20 trucks + 1 blade), 5,653 shifts, 1,101 fuel fill-up records at $1.57/L UFA dyed diesel, per-unit fuel rates from three-source cross-validation (CAT telematics, JD fill-ups, JD telematics). See [[GPS Baseline Results 2026-04-16]] for full pipeline output.

**Grader per-unit results (measured, ranked by deadhead %):**

| Rank | Grader | Division | Deadhead % | Grading Hrs | Deadhead Hrs | Deadhead $ (2 yrs) | Grading km |
|---|---|---|---|---|---|---|---|
| 1 (worst) | [[MG-051]] | Div 1 | **43.6%** | 862 | 667 | $14,650 | 5,946 |
| 2 | MG-046 | **Div 2** | 42.7% | 1,974 | 1,471 | $32,326 | 6,225 |
| 3 | MG-049 | Div 7 | 33.5% | 579 | 292 | $6,425 | 4,262 |
| 4 | [[MG-048]] | Div 5 | 33.2% | 681 | 338 | $7,430 | 6,127 |
| 5 | MG-039 | Spare | 31.4% | 629 | 287 | $6,317 | 4,194 |
| 6 | MG-050 | Div 4 | 27.1% | 1,210 | 450 | $9,884 | 8,781 |
| 7 | MG-044 | Spare (rotated out) | 23.4% | 1,266 | 386 | $8,483 | 8,881 |
| 8 | MG-041 | Spare | 18.9% | 365 | 85 | $1,876 | 2,337 |
| 9 (best) | MG-047 | Div 6 | **14.0%** | 1,505 | 245 | $5,393 | 9,085 |
| | **GRADER TOTAL** | | **31.8%** | **9,071** | **4,221** | **$92,784** | **55,837** |

**Fleet-wide** (all 38 GPS devices including trucks, tractors, a blade): **43.1% deadhead ratio**, **$271,180** deadhead fuel cost over 2 years.

**Division corrections from [[Shawn Ogertschnig]] (April 10, 2026):** MG-046 is Div 2 (Titan label "Div 3" is stale); MG-053 is Div 3 (no GPS yet, replaced MG-044); MG-042 and MG-052 are CAT 14M construction graders (no GPS by design). MG-049 is now included in the measured baseline (PDF excluded it). See [[UFA Price and Division Correction Thread 2026-04-09]] and [[Unit Fuel Rates Reconciliation]].

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

**Revised against measured baseline** ([[GPS Baseline Results 2026-04-16]]). Grader deadhead fuel ~$46K/yr. Fleet-wide (incl trucks) ~$135K/yr.

| Lever | Conservative | Moderate | Notes |
|---|---|---|---|
| [[Route Planner|Route optimization]] (graders, fuel) | $8,000 | $14,000 | Portion of grader $14K-$18.5K/yr at 30-40% reduction |
| [[Spare Coordination]] | $3,000 | $5,000 | Revised from PDF $5-10K |
| [[MG-048 Investigation|MG-048 resolution]] | $2,000 | $4,000 | MG-048 measured $3,715/yr, not $7,872/yr as in PDF |
| [[Division 1 Depot Staging|Depot staging (Div 1)]] | $2,000 | $3,500 | MG-051 measured $7,325/yr deadhead fuel, the single largest per-unit lever |
| [[Dust Control Coordination]] | $5,000 | $10,000 | Same as PDF; not directly touched by GPS baseline |
| [[Fleet Efficiency Dashboard|Visibility / behavior change]] | $3,000 | $8,000 | Same as PDF |
| **2026 Total (graders, fuel)** | **$23,000** | **$44,500** | |
| **[[Fully Loaded Hard Savings|Fully loaded]] (2.5x)** | **$57,500** | **$111,250** | |
| Full fleet target (trucks included) | $40,000 | $55,000 | [[GPS Baseline Results 2026-04-16]] |

Superseded: April 14 PDF projection was $33K-$61K fuel / $80K-$150K fully loaded.

## Stakeholders

- **Sponsor**: [[Ryan Thomson]], Director, Public Works & Utilities
- **Project lead**: Tony Jung, Lead, Continuous Improvement
- **Field validation / operational authority**: [[Shawn Ogertschnig]], Manager, Public Operations (corrected title per email signature; PRD said "Superintendent"). Source of authoritative division mapping.
- **GIS / data**: [[Graham White]] (Manager, Technical Services, road priority layer owner); [[Jesse]] (LC_Roads shapefile, dust control geocoding co-owner); [[Aaron Craig]] (Base Stabilization partner, still owes the road priority GIS layer — critical path for Route Planner).
- **Finance / budget**: [[Hailey Pinksen]] (asked budget-pressure question on UFA fuel lock-in).
- **Executive**: [[Cole Beck]], CAO (informed, supportive).
- **Distribution**: [[Sean MacRae]] on operational / fuel data queries.
- **Logistics support**: [[Lee Martin]] (forwarded Shawn's March 2026 grading maps; distinct from Cody and Cole Beck).
- **External vendor**: [[Tyler Reiter]], UFA Picture Butte agent (fuel lock-in).

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

- **MG-049 (Division 7)**: April 14 PDF excluded MG-049 from fleet averages (no JD telematics, anomalous 3.4 km/h average GPS speed). The April 16 Fabric pipeline includes MG-049 (measured 33.5% deadhead, 21.8 L/hr JD fill-up rate). GPS anomaly investigation still recommended. Fuel fill records (117 fills, 22,700 L) are usable.
- **MG-051 battery disconnects**: 929 disconnect events in GPS data creating coverage gaps. Fill-record engine hours (1,520 hrs) are more reliable than GPS-derived hours (1,059 hrs).
- **Data cleaning**: 8,755 isCurrLoc API artifact records filtered out; 5,376 exact duplicates removed across the fleet.
- **Data provenance**: all figures are derived from measured GPS breadcrumbs and verified fuel fill-up records, not estimates or industry benchmarks.

> [!QUESTION] Open questions
> - **Baseline period**: which reference period anchors cost comparisons? (Recommended: 3-year average with fuel price normalization)
> - **Measurement scope**: which divisions and fleet units are in scope for the initial pilot?
> - **Pilot division**: which division runs the Route Planner first?
> - **MG-048 diagnosis**: terrain, operator technique, or equipment condition? (Investigation in progress)
> - **Shapefile upload to Fabric**: LC_Roads, LC_Grader_Divisions, LC_Grader_Camps still on local machine. `gold_dim_road_segment` awaits upload, Route Planner blocked from spatial enrichment until then.
> - **Road priority GIS layer**: still owed by [[Aaron Craig]] per the April 14 data-requests email. Critical path for [[Route Planner]].
> - **Shawn's March 2026 grading maps**: forwarded via [[Lee Martin]]; monthly mileages per division available as GPS cross-validation ground truth.

## Artifacts

| Source | Location | Status |
|---|---|---|
| **GPS Baseline Results (2026-04-16, authoritative)** | `.raw/projects/road-intelligence-platform/2026-04-16-gps-baseline-results-fabric-pipeline.md` | current |
| GPS Baseline Analysis PDF (2026-04-14) | `.raw/projects/road-intelligence-platform/` | superseded |
| Comprehensive Findings PDF (2026-04-14) | `.raw/projects/road-intelligence-platform/` | superseded |
| PRD, Refined Build Plan, Build Plan, Financial Rebase, GPS Spec, Old CLAUDE | `.raw/projects/road-intelligence-platform/historical/` | historical |
| UFA + Division correction email thread | `.raw/projects/road-intelligence-platform/historical/` | historical |
| Unit Fuel Rates Reconciliation memo | `.raw/projects/road-intelligence-platform/historical/` | historical |
| Sent email data requests | `.raw/projects/road-intelligence-platform/historical/` | historical |
| GPS pipeline cowork summary | `.raw/projects/road-intelligence-platform/historical/` | historical |
| Laptop project folder (Base Stab, Dust Control, Grading, code) | `.raw/projects/road-intelligence-platform/historical/` | ingested (inventory), not all files individually manifested |
| Fabric gold tables | `finance_fabric` workspace (remote) | `gold_fact_grading_activity` ✓, `gold_fact_segment_visits` ✓; `gold_dim_road_segment` pending shapefile upload |
| Master manifest | `.raw/.manifest.json` | update pending (Cluster 7) |

## Sources

- **Authoritative**: [[GPS Baseline Results 2026-04-16]]
- **Historical (superseded)**:
  - [[GPS Baseline Analysis]] (April 14 PDF)
  - [[Road Intelligence Platform Comprehensive Findings]] (April 14 PDF)
- **Historical (decision history)**:
  - [[PRD Road Intelligence Platform]]
  - [[Road Intelligence Platform Refined Build Plan]]
  - [[Road Intelligence Platform Build Plan]] (April 6, superseded by Refined)
  - [[Financial Rebase]]
  - [[GPS Baseline Analysis Spec]]
  - [[GPS Pipeline Cowork Summary]]
  - [[Old Project CLAUDE Instructions]]
  - [[Sent Email Data Requests 2026-04-14]]
  - [[UFA Price and Division Correction Thread 2026-04-09]]
  - [[Unit Fuel Rates Reconciliation]]
