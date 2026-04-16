---
type: concept
title: "Fully Loaded Hard Savings"
complexity: intermediate
domain: "financial analysis"
aliases:
  - "fully loaded cost"
  - "hard savings"
created: 2026-04-15
updated: 2026-04-15
tags:
  - concept
  - road-intelligence-platform
  - financial-metric
status: mature
related:
  - "[[Deadhead Ratio]]"
  - "[[Route Optimization]]"
  - "[[Road Intelligence Platform]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Fully Loaded Hard Savings

## Definition

Fully loaded hard savings is the success metric for the [[Road Intelligence Platform]]. It combines two ideas:

- **Fully loaded**: the all-in cost of a grader operation, not just direct fuel. Four components: fuel, operator labour, equipment depreciation, and maintenance. The fully loaded cost is approximately 2.5 times the fuel-only cost (Report 1, savings section).
- **Hard savings**: finance-recognizable cost reductions that can be reported to council as real budget impact, as opposed to soft savings like "time freed up" or "avoided future costs" that may or may not materialize.

## How It Works

The calculation starts from fuel savings (the most directly measurable output of route optimization and deadhead reduction), then applies the 2.5x multiplier to estimate total operational savings:

$$\text{Fully Loaded Savings} \approx \text{Fuel Savings} \times 2.5$$

The multiplier captures:

- **Fuel**: litres consumed at prevailing per-litre cost ($1.57/L UFA dyed diesel in the baseline period).
- **Operator labour**: burdened wages for the hours an operator spends deadheading instead of grading.
- **Equipment depreciation**: wear-and-tear cost allocated to non-productive travel hours.
- **Maintenance**: incremental maintenance cost from travel that produces no grading output.

## Why It Matters

Fuel savings alone understate the value of deadhead reduction. When a grader eliminates one hour of deadheading, the county saves not just the fuel for that hour but also the operator's wage, the equipment wear, and the maintenance cost. The 2.5x multiplier translates a modest fuel savings number into a more complete picture of operational value.

Baseline reference points from the reports:

| Metric | Value | Source |
|---|---|---|
| Fleet-wide deadhead fuel cost (current) | $55,000 to $65,000/yr | Report 1, headline |
| Fleet-wide deadhead fully loaded cost (current) | $140,000 to $165,000/yr | Report 1, savings section |
| 2026 combined projection (conservative, fuel) | $33,000 | Report 2, projection table |
| 2026 combined projection (conservative, fully loaded) | $80,000 | Report 2, projection table |
| 2026 combined projection (moderate, fuel) | $61,000 | Report 2, projection table |
| 2026 combined projection (moderate, fully loaded) | $150,000 | Report 2, projection table |

## Connections

- [[Deadhead Ratio]] — the operational metric whose reduction produces the fuel savings input
- [[Route Optimization]] — the primary lever generating savings
- [[Road Intelligence Platform]] — the project reporting this metric to council

## Sources

- [[GPS Baseline Analysis]] — "The fully-loaded cost of deadheading (fuel + operator labor + equipment depreciation + maintenance) is approximately 2.5x the fuel cost. At fully-loaded rates, the fleet-wide deadhead cost is approximately $140,000-$165,000/year" (savings section)
- [[Road Intelligence Platform Comprehensive Findings]] — 2026 projection: $80,000 conservative / $150,000 moderate fully loaded (projection table); "roughly $150,000 in fully loaded value" (planning takeaway)
