---
type: concept
title: "Deadhead Ratio"
complexity: intermediate
domain: "fleet operations"
aliases:
  - "DH ratio"
created: 2026-04-15
updated: 2026-04-15
tags:
  - concept
  - road-intelligence-platform
  - fleet-metric
status: mature
related:
  - "[[Road Intelligence Platform]]"
  - "[[Route Optimization]]"
  - "[[Fully Loaded Hard Savings]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Deadhead Ratio

> [!important] Measured update (2026-04-16)
> Examples table below uses April 14 PDF estimates (24.9% fleet across 8 graders, MG-049 excluded, 367 days, 1.52M breadcrumbs). The Fabric pipeline on **2 years of GPS data (2.67M deduplicated breadcrumbs)** yields measured values: **grader deadhead 31.8%** across 9 graders, **fleet-wide 43.1%** across 38 devices. Per-grader range 14.0% (MG-047 Div 6) to 43.6% (MG-051 Div 1). See [[GPS Baseline Results 2026-04-16]].

## Definition

The deadhead ratio is the percentage of a grader's **active engine time** spent deadheading — traveling between work areas without grading. Active time is the sum of grading hours and deadheading hours; idle and engine-off time are excluded from the denominator.

$$\text{Deadhead Ratio} = \frac{\text{Deadhead Hours}}{\text{Grading Hours} + \text{Deadhead Hours}}$$

## How It Works

GPS breadcrumbs are classified into four states by speed and engine status:

- **GRADING**: 3 to 15 km/h, engine on (blade-down productive work)
- **DEADHEADING**: over 15 km/h, engine on (traveling between grading areas)
- **IDLE**: under 3 km/h, engine on (stationary with engine running)
- **OFF**: engine off (parked)

Only grading and deadheading count toward active time. Idling and parked hours are excluded — a grader sitting at a shop burning fuel doesn't inflate the deadhead ratio.

## Why It Matters

Deadhead fuel is a direct, measurable operating cost with no productive output. Every hour of deadhead is both a dollar of fuel burned and an hour of operator time unavailable for productive grading. Reducing deadhead translates to:

- Fuel cost savings (direct dollar impact)
- More productive grading hours without adding fleet time
- Reduced wear and tear from non-productive travel
- Better network coverage within the same shift budget

The metric also serves as a leading indicator for routing, depot placement, and scheduling inefficiency. A high deadhead ratio points to optimization opportunity elsewhere in the system.

## Examples

From the Fabric pipeline ([[GPS Baseline Results 2026-04-16]], 2 full years: 2024-03-06 to 2026-04-09, 2.67M deduplicated breadcrumbs, 5,653 shifts):

| Context | Deadhead Ratio |
|---|---|
| Grader fleet (9 GPS-equipped) | **31.8%** |
| All devices (38 total: graders + trucks + tractors + blade) | **43.1%** |
| MG-047 (Div 6, best) | 14.0% |
| MG-051 (Div 1, worst primary) | 43.6% |
| MG-046 (Div 2, second worst) | 42.7% |
| [[MG-048]] (Div 5) | 33.2% |
| MG-039 (spare) | 31.4% |
| MG-041 (spare, best spare) | 18.9% |
| MG-044 (spare, rotated out) | 23.4% |

Superseded: the April 14 PDF reported 24.9% fleet deadhead across 8 graders (MG-049 excluded) over 367 days / 1.52M breadcrumbs. The 2-year measured number is ~7 percentage points higher because the dataset is larger, MG-049 is included, and all 38 devices contribute to the fleet number. Seasonal swing analysis from the PDF (grading season 16.6-21.7%, winter 28.1-53.0%) has not yet been recomputed from the 2-year dataset.

## Seasonal Interpretation

The measured **31.8% grader deadhead ratio** in [[GPS Baseline Results 2026-04-16]] is a **2-year blended average** (March 2024 to April 2026) that includes winter months where:

- Graders are doing snow work (not gravel grading)
- Or sitting idle with occasional repositioning

Both activities register as high-deadhead or low-grading under the speed-based classifier, which inflates the blended ratio.

**The more meaningful number for the route optimization case is the grading-season ratio (April through October).** That is when the [[PyVRP]] optimizer actually runs, and it is the deadhead against which savings should be measured. The expected grading-season ratio is lower than the 31.8% blended number.

**Action**: The [[Fleet Efficiency Dashboard]] will add a season filter and report both the blended and the grading-season ratios.

## Connections

- [[Route Optimization]] — daily sequencing to minimize deadhead travel
- [[Facility Location]] — depot placement reduces start-of-shift deadhead
- [[Fully Loaded Hard Savings]] — translates deadhead reduction into dollars
- [[Road Intelligence Platform]] — the project using this metric as its core baseline

## Sources

- [[GPS Baseline Analysis]]
- [[Road Intelligence Platform Comprehensive Findings]]
