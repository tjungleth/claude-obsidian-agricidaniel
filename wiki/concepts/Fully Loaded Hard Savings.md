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

> [!important] Measured update (2026-04-16)
> Baseline reference table below uses April 14 PDF estimates ($55-65K fuel / $140-165K fully loaded / $33-61K projection). The Fabric pipeline measures grader deadhead fuel at **$92,784 over 2 years ≈ $46K/yr**, which is ~**$115K/yr fully loaded** at 2.5x. Revised savings: graders $14K/yr at 30% reduction, $18.5K/yr at 40%, full fleet $40K-$55K/yr at 30-40%. See [[GPS Baseline Results 2026-04-16]].

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
| Grader deadhead fuel cost (measured) | **~$46,000/yr** ($92,784 over 2 yrs) | [[GPS Baseline Results 2026-04-16]] |
| Grader deadhead fully loaded cost (2.5x) | **~$115,000/yr** | derived from measured fuel |
| Full fleet deadhead ratio (including trucks) | 43.1% | [[GPS Baseline Results 2026-04-16]] |
| 2026 savings at 30% grader deadhead reduction | $14,000/yr fuel, $35,000/yr fully loaded | measured baseline × reduction |
| 2026 savings at 40% grader deadhead reduction | $18,500/yr fuel, $46,000/yr fully loaded | measured baseline × reduction |
| 2026 savings full fleet at 30-40% reduction | $40,000-$55,000/yr fuel | [[GPS Baseline Results 2026-04-16]] |
| Prior April 14 PDF estimate (superseded) | $55K-$65K fuel, $140K-$165K fully loaded | Report 1 headline |

## Connections

- [[Deadhead Ratio]] — the operational metric whose reduction produces the fuel savings input
- [[Route Optimization]] — the primary lever generating savings
- [[Road Intelligence Platform]] — the project reporting this metric to council

## Sources

- [[GPS Baseline Analysis]] — "The fully-loaded cost of deadheading (fuel + operator labor + equipment depreciation + maintenance) is approximately 2.5x the fuel cost. At fully-loaded rates, the fleet-wide deadhead cost is approximately $140,000-$165,000/year" (savings section)
- [[Road Intelligence Platform Comprehensive Findings]] — 2026 projection: $80,000 conservative / $150,000 moderate fully loaded (projection table); "roughly $150,000 in fully loaded value" (planning takeaway)
