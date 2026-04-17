---
type: source
title: "GPS Baseline Analysis"
source_type: internal report
author: "Tony Jung"
date_published: 2026-04-14
raw_file: ".raw/projects/road-intelligence-platform/2026-04-14-gps-baseline-analysis-report.pdf"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - gps-data
  - fleet-analysis
status: superseded
related:
  - "[[Road Intelligence Platform]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Source: GPS Baseline Analysis

> [!warning] Superseded 2026-04-16
> The Fabric pipeline ([[GPS Baseline Results 2026-04-16]]) replaces this PDF's headline claims. Measured grader deadhead **31.8%** (vs 24.9% here), fleet-wide **43.1%**. Measured grader deadhead fuel **~$46K/yr** (vs $55-65K here), fully loaded **~$115K/yr** (vs $140-165K). Dataset is **2 years, 2.67M breadcrumbs** (vs 367 days, 1.52M). MG-046 is Div 2 (was Div 3). MG-049 is now included in the baseline. Per-grader numbers revised. Claims below preserved as historical record.

**Full title**: GPS Baseline Analysis / Grader Fleet Deadhead Report
**Prepared for**: [[Ryan Thomson]], Director, Public Works & Utilities
**Prepared by**: Tony Jung, Lead, Continuous Improvement
**Date**: April 14, 2026
**Data period**: April 7 2025 through April 8 2026 (367 days)
**Data**: 1.52 million GPS breadcrumbs from 9 Titan-equipped graders, 1,101 fuel fill-up records
**Pages**: 4

## Summary

Establishes the fleet deadhead baseline: 24.9% of active engine time is spent deadheading across 8 graders (MG-049 excluded). Quantifies the cost at $41,487/yr in measured fuel (7 tracked graders) and $55,000 to $65,000 fleet-wide. Introduces the fully loaded cost estimate of $140,000 to $165,000/yr (2.5x fuel). Provides per-grader ranking, seasonal analysis, fuel rate cross-validation, and five recommended next steps.

## Pages Created from This Source

- [[Road Intelligence Platform]] — fleet baseline table, executive summary, data quality notes
- [[Deadhead Ratio]] — definition, methodology (speed/engine classification), fleet examples, seasonal data
- [[Facility Location]] — Coaldale Shop 12.6 km from Div 1 demand centroid, 47% of roads >15 km
- [[Fully Loaded Hard Savings]] — 2.5x multiplier definition, $140,000-$165,000 fleet-wide cost
- [[PyVRP]] — "PyVRP solver with the road network cost matrix" (recommendation #3)
- [[Route Optimization]] — referenced as primary savings lever
- [[MG-048 Investigation]] — 34.3% deadhead, 23.6 L/hr, 24% high-load, $7,872/yr (key finding #1); swap evaluation ~$3,500/yr (recommendation #4)
- [[Spare Coordination]] — spare variability: MG-039 31.4%, MG-044 22.1%, MG-041 17.2% (key finding #4)
- [[Route Planner]] — "Build the daily route optimization tool" (recommendation #3)
- [[Division 1 Depot Staging]] — Coaldale Shop depot misalignment (key finding #2)
- [[Fleet Efficiency Dashboard]] — "Publish the Fleet Efficiency dashboard on Power BI" (recommendation #5)

## Key Findings

1. MG-048 (Division 5) has the highest deadhead in the fleet at 34.3%, with the highest fuel rate (23.6 L/hr) and 24% high-load engine time
2. Division 1 (Coaldale Shop) confirms depot misalignment: 12.6 km from demand centroid, 47% of roads >15 km from camp
3. Division 6 / MG-047 at 17.8% demonstrates what is achievable under good depot positioning
4. Spare graders show the widest spread (17.2% to 31.4%) due to no assigned territory
5. Seasonal pattern: grading season (May to September) ratios run 16.6% to 21.7%; winter (November to March) ratios span 28.1% to 53.0%

## Raw File

`.raw/projects/road-intelligence-platform/2026-04-14-gps-baseline-analysis-report.pdf`
