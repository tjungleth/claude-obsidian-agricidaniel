---
type: source
title: "GPS Baseline Results 2026-04-16"
source_type: pipeline output (authoritative)
author: "Tony Jung"
date_published: 2026-04-16
raw_file: ".raw/projects/road-intelligence-platform/2026-04-16-gps-baseline-results-fabric-pipeline.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - baseline
  - measured
  - authoritative
status: current
supersedes:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
related:
  - "[[Road Intelligence Platform]]"
  - "[[Deadhead Ratio]]"
  - "[[Unit Fuel Rates Reconciliation]]"
  - "[[UFA Price and Division Correction Thread 2026-04-09]]"
  - "[[Shawn Ogertschnig]]"
  - "[[Aaron Craig]]"
  - "[[Lee Martin]]"
  - "[[Hailey Pinksen]]"
  - "[[Tyler Reiter]]"
---

# Source: GPS Baseline Results (2026-04-16)

**Pipeline run**: Fabric `finance_fabric` workspace, 2026-04-16
**Notebooks**: `10_bronze_gps`, `11_silver_gps_segments`, `12_gold_grading_activity`
**Data range**: 2024-03-06 to 2026-04-09 (2 full years)
**Status**: Current, authoritative. Supersedes all prior estimates and the April 14 PDFs.

> [!important] Headline Numbers
> - **Grader deadhead ratio: 31.8%** (~$46K/yr)
> - **Fleet deadhead ratio: 43.1%** (all 38 devices)
> - **Best**: MG-047 Div 6 at 14.0%
> - **Worst**: MG-051 Div 1 at 43.6%, MG-046 Div 2 at 42.7%
> - **Savings (measured)**: $14K/yr at 30% grader reduction, $18.5K/yr at 40%, $40K-$55K/yr full fleet at 30-40%
> - **Fleet average fuel rate**: ~21 L/hr (pipeline used 22, within 5%)

> [!caution] 2-year blend caveat
> The 31.8% grader deadhead is a **2-year blended average** that includes winter months where graders do snow work or sit idle with occasional repositioning (both register as high-deadhead / low-grading). The **grading-season number (April-October)** is the meaningful one for the route optimization case, since that is when [[PyVRP]] actually runs. Expect the grading-season ratio to be lower than 31.8%. [[Fleet Efficiency Dashboard]] will add a season filter. See [[Deadhead Ratio]] "Seasonal Interpretation" for detail.

## Summary

All three GPS notebooks completed successfully in the Fabric lakehouse on April 16, 2026. From 8,798 JSON files across 2 full years of Titan GPS data: 2,666,866 deduplicated breadcrumbs across 38 devices, yielding 5,653 shifts and measured activity splits (1.27M GRADING / 756K DEADHEADING / 599K IDLE). Headline: the grader deadhead ratio is **31.8%**, ~7 percentage points higher than the April 14 PDF estimate of 24.9%. Measured grader deadhead fuel cost is $92,784 over two years (~$46K/yr). Savings projections recalibrate to $14K-$19K/yr for graders alone and $40K-$55K/yr when trucks are included.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — per-grader table replaced with measured numbers
- [[Deadhead Ratio]] — methodology becomes "measured"; 31.8% headline
- [[Fully Loaded Hard Savings]] — ~$115K/yr fully-loaded (2.5x $46K fuel)
- [[Fleet Efficiency Dashboard]] — per-grader measured table + idle %s
- [[Division 1 Depot Staging]] — MG-051 at 43.6% is the WORST grader; largest structural target
- [[MG-048 Investigation]] — measured 33.2% vs 34.3% PDF (close match)
- [[Spare Coordination]] — MG-039 31.4%, MG-041 18.9%, MG-044 23.4% (measured)
- [[Facility Location]] — MG-046 correctly attributed to Div 2
- [[Route Planner]] — priority targets: MG-046 (42.7%) and MG-051 (43.6%) carry the largest deadhead dollars

## Per-Grader Measured Results

| Unit | Division | Shifts | Grading Hrs | Deadhead Hrs | Deadhead % | Deadhead $ | Grading km |
|---|---|---|---|---|---|---|---|
| MG-039 | Spare | 141 | 629 | 287 | 31.4% | $6,317 | 4,194 |
| MG-041 | Spare | 95 | 365 | 85 | 18.9% | $1,876 | 2,337 |
| MG-044 | Spare (rotated out) | 211 | 1,266 | 386 | 23.4% | $8,483 | 8,881 |
| MG-046 | Div 2 | 203 | 1,974 | 1,471 | 42.7% | $32,326 | 6,225 |
| MG-047 | Div 6 | 212 | 1,505 | 245 | 14.0% | $5,393 | 9,085 |
| MG-048 | Div 5 | 169 | 681 | 338 | 33.2% | $7,430 | 6,127 |
| MG-049 | Div 7 | 114 | 579 | 292 | 33.5% | $6,425 | 4,262 |
| MG-050 | Div 4 | 224 | 1,210 | 450 | 27.1% | $9,884 | 8,781 |
| MG-051 | Div 1 | 235 | 862 | 667 | 43.6% | $14,650 | 5,946 |
| **GRADER TOTAL** | | **1,604** | **9,071** | **4,221** | **31.8%** | **$92,784** | **55,837** |

## Authoritative Fleet Mapping

Division assignments corrected by Shawn Ogertschnig's April 10 email ([[UFA Price and Division Correction Thread 2026-04-09]]):

| Unit | Division | Make/Model | GPS? | Notes |
|---|---|---|---|---|
| MG-051 | Div 1 | CAT 150 | Yes | |
| MG-046 | **Div 2** | CAT 150 | Yes | Titan label "Div 3" is stale |
| MG-053 | **Div 3** | unknown | **No** | Replaced MG-044 ~3 weeks ago |
| MG-050 | Div 4 | JD 772GP | Yes | |
| MG-048 | Div 5 | JD 772GP | Yes | |
| MG-047 | Div 6 | JD 872GP | Yes | |
| MG-049 | Div 7 | JD 772GP | Yes | |
| MG-039 | Spare | CAT 140M3 | Yes | |
| MG-041 | Spare | JD 772GP | Yes | |
| MG-044 | Spare | JD 872GP | Yes | Rotated out, replaced by MG-053 |
| MG-042 | **Construction** | CAT 14M | **No (by design)** | |
| MG-052 | **Construction** | CAT 14-15 | **No (by design)** | |
| MG-043 | ? | JD 872GP | No Titan, has JD telematics | |
| MG-045 | ? | JD 872GP | No Titan, has JD telematics | |

## Per-Unit Fuel Rates (three-source cross-validation)

| Unit | Division | CAT Telem | JD Fill-up | JD Telem | **Best** |
|---|---|---|---|---|---|
| MG-039 | Spare | 22.8 | - | - | **22.8** |
| MG-041 | Spare | - | - | 17.8 | **17.8** |
| MG-042 | Construction | 19.1 | - | - | **19.1** |
| MG-043 | ? | - | - | 15.7 | **15.7** |
| MG-044 | Spare | - | 23.1 | 19.7 | **23.1** |
| MG-045 | ? | - | - | 15.8 | **15.8** |
| MG-046 | Div 2 | 21.3 | 20.9 | - | **20.9** |
| MG-047 | Div 6 | - | 20.5 | 17.0 | **20.5** |
| MG-048 | Div 5 | - | 23.6 | 20.1 | **23.6** |
| MG-049 | Div 7 | - | 21.8 | - | **21.8** |
| MG-050 | Div 4 | - | 18.9 | 16.5 | **18.9** |
| MG-051 | Div 1 | 18.2 | 20.0 | - | **20.0** |
| MG-052 | Construction | 20.4 | - | - | **20.4** |

Cross-validation:
- MG-046: CAT 21.3 vs JD fill-up 20.9 = within 2%, strong agreement
- MG-051: CAT 18.2 vs JD fill-up 20.0 = 10% spread, use JD fill-up
- JD telematics consistently reads 2-4 L/hr lower than JD fill-ups (likely excludes idle fuel); fill-ups are the better ground truth

## Idle Percentages

- **JD units**: MG-041 24.2%, MG-043 24.1%, MG-044 17.7%, MG-045 26.5%, MG-047 17.5%, **MG-048 26.6% (highest active divisional)**, MG-050 18.8%
- **CAT units**: MG-039 12.9%, MG-046 13.2%, MG-051 13.7%. Construction: MG-042 29.9%, MG-052 28.0% (expected)

## Ground Truth Validation (March 2026)

Shawn's March 2026 grading maps, forwarded by Lee Martin. Monthly mileage per division:

| Division | GPS Unit | Operator-Reported Miles |
|---|---|---|
| Div 1 | MG-051 | 134 mi |
| Div 2 | **MG-046** | 131 mi |
| Div 3 | MG-053 (no GPS) | 116 mi |
| Div 4 | MG-050 | 72 mi |
| Div 5 | MG-048 | 49 mi |
| Div 6 | MG-047 | 76 mi |
| Div 7 | MG-049 | 99 mi |

Div 4 notes: Class 1: 32, Class 2: 10, Class 3: 12, haul routes 16, soft spots 8, blade changes 3,615.

Cross-validation target: compare each Div's March 2026 GPS-derived grading distance against the operator-reported mileage. Div 3 has no GPS cross-validation possible.

## Superseded Estimates

| Previous claim | Source | Measured (2026-04-16) |
|---|---|---|
| "24.9% fleet deadhead" | [[GPS Baseline Analysis]] PDF | **43.1% fleet, 31.8% graders** |
| "estimated 20-30% deadhead" | build plans | **31.8% graders** |
| "$108K-$163K addressable" | build plans | **~$46K/yr graders** |
| "$65K-$75K Year 1 savings" | build plans | **$14-19K/yr graders, $40-55K/yr full fleet** |
| "$140K-$165K/yr fully loaded" | GPS Baseline Analysis PDF | **~$115K/yr fully loaded** (2.5x $46K) |
| "1.86M records" / "1.52M breadcrumbs" | CLAUDE.md | **2,666,866 after dedup** |
| "367 days" | CLAUDE.md, spec | **2 years (2024-03-06 to 2026-04-09)** |
| "flat 22 L/hr grading" | pipeline default | **per-unit 15.7 to 23.6, fleet avg 21.0** |
| "MG-046 Div 3" | PDFs + Titan labels | **MG-046 is Div 2** |
| "5 graders without GPS" | old CLAUDE.md | Reclassify by cause (construction, replaced, non-Titan, unknown) |

## Gold Table Status

- `gold_fact_grading_activity`: 5,653 rows (shift-level) ✓ built
- `gold_fact_segment_visits`: 4,204 rows (daily grading per unit) ✓ built
- `gold_dim_road_segment`: **not yet built**. Blocked on shapefile upload (LC_Roads, LC_Grader_Divisions, LC_Grader_Camps still on local). Upload unlocks snap-to-segment enrichment.

## Related New Findings

- **Ryan Thomson** sent supporting email (April 16), urging cooperation. Aaron Craig CC'd.
- **Aaron Craig** (last name confirmed) still owes the road priority GIS layer. Critical path for [[Route Planner]].
- **Lee Martin** (last name confirmed) is separate from Cody and Cole Beck. Forwarded March 2026 grading maps to Shawn.

## Raw File

`.raw/projects/road-intelligence-platform/2026-04-16-gps-baseline-results-fabric-pipeline.md`
