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

From the Road Intelligence Platform 2026 baseline (April 7 2025 through April 8 2026, 367 days, 1.52M GPS breadcrumbs):

| Context | Deadhead Ratio |
|---|---|
| Fleet average (8 graders, MG-049 excluded) | 24.9% |
| [[MG-048]] (Division 5, worst primary) | 34.3% |
| MG-047 (Division 6, best primary) | 17.8% |
| Best grading month (September 2025) | 16.6% |
| Winter peak (December 2025) | 53.0% |

The seasonal swing is large. Grading season (May to September 2025) ratios run 16.6% to 21.7%, while winter (November 2025 through March 2026) ratios span 28.1% to 53.0% because graders still travel to check roads but do proportionally less grading.

## Connections

- [[Route Optimization]] — daily sequencing to minimize deadhead travel
- [[Facility Location]] — depot placement reduces start-of-shift deadhead
- [[Fully Loaded Hard Savings]] — translates deadhead reduction into dollars
- [[Road Intelligence Platform]] — the project using this metric as its core baseline

## Sources

- [[GPS Baseline Analysis]]
- [[Road Intelligence Platform Comprehensive Findings]]
