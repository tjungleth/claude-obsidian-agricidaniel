---
type: concept
title: "Facility Location"
complexity: intermediate
domain: "operations research"
aliases:
  - "depot placement"
  - "depot optimization"
created: 2026-04-15
updated: 2026-04-15
tags:
  - concept
  - road-intelligence-platform
  - operations-research
status: mature
related:
  - "[[Route Optimization]]"
  - "[[Deadhead Ratio]]"
  - "[[Road Intelligence Platform]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Facility Location

## Definition

The facility location problem asks: given a set of demand points (road segments needing service), where should service facilities (grader camps/depots) be placed to minimize total travel between depots and demand?

In the Lethbridge County context, grader camps are pre-existing infrastructure. The "optimization" is not relocating buildings but instead: (1) quantifying how well current depots serve their divisions, (2) using multi-day staging and overnight positioning to compensate for poor depot-demand alignment, and (3) informing long-term capital decisions about depot placement.

## How It Works

Two metrics from the Road Intelligence Platform baseline measure depot-demand alignment:

- **Average start distance**: how far from camp a grader typically begins its first grading pass. Ranges from 0.1 km (well-positioned) to 6.2 km ([[MG-051]], Coaldale Shop, Division 1).
- **Demand centroid distance**: the gap between a depot and the geographic center of its division's grading demand. Coaldale Shop is 12.6 km from Division 1's demand centroid, with 47% of the division's roads more than 15 km from camp.

When a depot is poorly positioned, every shift starts with a long deadhead drive before any productive grading begins. This raises the [[Deadhead Ratio]] structurally regardless of how well routes are optimized within the shift.

## Why It Matters

Depot placement is the foundation that [[Route Optimization]] builds on. A well-positioned depot (like Picture Butte Shop for Division 6, where MG-047 averages 0.5 km start distance) lets route optimization minimize within-shift deadhead. A poorly positioned depot (Coaldale Shop for Division 1) imposes a fixed deadhead penalty every shift that no route can eliminate.

The Division 1 depot staging workstream (Tier 2, $3,000 to $5,000 per year net) addresses this through multi-day plans and overnight positioning rather than capital relocation.

## Examples

Per-grader camp distances from the 2026 baseline (Report 2, §4):

| Grader | Division | Avg Start Distance | Same-Camp Return |
|---|---|---|---|
| MG-048 | Div 5 | 0.1 km | 99% |
| MG-047 | Div 6 | 0.5 km | 100% |
| MG-046 | Div 3 | 1.4 km | 95% |
| MG-041 | Spare | 3.2 km | 81% |
| [[MG-051]] | Div 1 | 6.2 km | 96% |

MG-051 is the clear outlier. All other primary graders start within 1.4 km of camp. The full 8-grader table is in Report 2, §4.

## Connections

- [[Route Optimization]] — depot position determines the start/end points the solver optimizes from
- [[Deadhead Ratio]] — poorly positioned depots inflate deadhead structurally
- [[MG-051]] — the grader most affected by depot misalignment

## Sources

- [[GPS Baseline Analysis]] — "Coaldale Shop is 12.6 km from the demand centroid of Division 1, with 47% of the division's roads more than 15 km from camp" (key finding #2)
- [[Road Intelligence Platform Comprehensive Findings]] — per-grader camp distance table (§4); Division 1 depot staging, $3,000 to $5,000 per year net (Tier 2)
