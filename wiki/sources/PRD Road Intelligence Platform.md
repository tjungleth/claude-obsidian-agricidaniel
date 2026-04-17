---
type: source
title: "PRD: Road Intelligence Platform"
source_type: historical PRD
author: "Tony Jung"
date_published: 2026-04-14
raw_file: ".raw/projects/road-intelligence-platform/historical/PRD_Road_Intelligence_Platform.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - prd
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
  - "[[Road Intelligence Platform Refined Build Plan]]"
---

# Source: PRD — Road Intelligence Platform

> [!note] Measured baseline available 2026-04-16
> This historical PRD's estimates are superseded by measured values from the Fabric pipeline. See [[GPS Baseline Results 2026-04-16]] for grader deadhead 31.8% / fleet 43.1% from 2 years of GPS data, $46K/yr grader fuel, $14K-$18.5K/yr savings at 30-40% reduction. Division correction: MG-046 is Div 2 (not Div 3). User stories and architectural decisions below remain relevant.

**Full title**: PRD: Road Intelligence Platform
**Author**: Tony Jung, Lead Continuous Improvement
**Date**: April 14, 2026
**Status**: Historical. Master requirements document written alongside the Refined Build Plan. Carries detail the two April 14 PDF reports do not.

## Summary

Defines the Road Intelligence Platform as a unified data and optimization system on Microsoft Fabric that turns GPS telemetry, road condition scores, fuel records, weather, and operational data into measurable fuel savings, better road conditions, and a defensible business case for Council. Identifies six systemic problems (deadhead travel, division workload imbalance, depot misalignment, program uncoordination, no grading-quality measurement, stale boundaries) and lays out a six-part solution (measure, optimize, provide tools, measure quality, coordinate programs, compound via ML). Maps 50 user stories across six personas. Commits to a PyVRP + ALNS + LKH-3 solver stack, notebook numbering 08-15 continuing the existing Fabric Ops Intelligence pipeline, a vehicle-agnostic extensible silver schema, and role-based Grader Performance Score visibility.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] (anchor) — problem framing, architecture, six-problem list, 50-story persona map, 5-year projection
- [[Ryan Thomson]] — 12 director user stories
- [[Shawn Ogertschnig]] — 16 superintendent user stories, full last name confirmed
- [[Graham White]] — GIS manager, 5 user stories, spatial data ownership
- [[Cole Beck]] — CAO, informed/supportive stance
- [[Aaron Craig]] — Base Stabilization partner on pending data requests
- [[Jesse]] — GIS co-owner, LC_Roads + dust control geocoding owner
- [[Deadhead Ratio]] — methodology references
- [[Route Planner]] — multi-week feature list from stories 13-28
- [[Fleet Efficiency Dashboard]] — 4-page dashboard spec
- [[Grader Performance Score]] — composite score definition (RID 50% / coverage 25% / fuel 25%)
- [[Dust Control Coordination]] — 338 applications, $393K program, CVRP routing

## Key Facts

- **Fleet**: 14 graders, 1,810 km of gravel road across 7 divisions + 2 rover areas
- **Fuel budget**: ~$500K-$550K/yr grader-only (14 units, extrapolated from 7 tracked at $377,438/yr)
- **Division imbalance**: Div 5 (324 km) vs Div 3 (189 km), 1.7x
- **Depot misalignment**: Div 1 Coaldale Shop 12.6 km from demand centroid, 47% of roads >15 km from camp
- **Dust control program**: $393K/yr, 140 km, 338 applications (grading and dust control are not coordinated today)
- **Base stabilization program**: ~$150K+/yr (MG-30 calcium chloride injection)
- **Division boundaries**: last updated January 12, 2021 (5 years stale)
- **PSD baseline**: 786 assessments, 722 unique segments, 91 roads (Weeks 4-11, 2026)
- **Solver stack**: PyVRP (Vidal Hybrid Genetic Search) + ALNS validation (Ropke & Pisinger 2006) + LKH-3 post-processing (Helsgott 2023)
- **Notebooks reserved**: 08-15 continuing existing 01-07 Ops Intelligence series
- **Route generation cadence**: scheduled 5:00 AM daily cron, pre-generated before crew arrival. "Regenerate" button available for mid-day re-optimization (not primary workflow).
- **Delivery**: Power BI Route Planner page + paginated print-ready operator route sheets

## 50 User Stories by Persona

- **Ryan Thomson (Director, PW&U)**: stories 1-12. Fleet deadhead visibility, monthly summaries, weather-normalized year-over-year comparisons, audit-grade numbers, fully-loaded cost, Council-ready reports.
- **Shawn Ogertschnig (PRD: Superintendent / Division Leads; per email signature April 2026: Manager, Public Operations)**: stories 13-28. Pre-generated routes by 6 AM, color-coded division map, grader availability toggles, priority overrides, printed operator sheets, overnight staging recommendations, dust control overlay, weekly division review, operator scorecards, three-territory scenario comparison (A/B/C), multi-day plans, base-stabilized road deprioritization.
- **Grader Operators**: stories 29-35. Printed route sheet like an improved paper map, road names + from-to + estimated time + passes, GPS auto-logging, own monthly scorecard, "your roads lasted X days" framing, dust control markers, radio-feedback flagging routed through Shawn/GIS.
- **Graham White (Manager, Technical Services)**: stories 36-40. LC_Roads + RS_GIS_ID as primary spatial key, road condition GIS layer, coverage gap analysis, PSD assessor calibration visibility, segment-level exportable data.
- **Dust Control Crew**: stories 41-44. Clustered application route, tank-capacity refill logic, grading-first sequencing, print-ready crew route sheet.
- **System / Platform**: stories 45-50. Weekly CSV ingestion, Delta + OneLake portable to Databricks, vehicle-agnostic silver schema, `bridge_grading_assessment` table, Environment Canada weather join, versioned solver outputs.

## Implementation Decisions

- **Medallion architecture on Microsoft Fabric** (workspace: `finance_fabric`, F2 capacity). Bronze / silver / gold Delta on OneLake.
- **Extensible schema**: `unit_prefix` (`MG` = grader, `TR` = truck, etc.) enables vehicle-agnostic analytics.
- **Snap-to-segment**: 50m buffer against LC_Roads; reproject GPS EPSG:4326 to UTM Zone 12N (EPSG:26912).
- **Three-level solver decomposition**: P-median facility location (Level 0) → K-medoids territory assignment (Level 1) → PyVRP daily route sequencing (Level 2).
- **ALNS independent validation**: target solution cost agreement within 2%.
- **LKH-3 post-processing**: +0.5-1% refinement per route.
- **Cost matrix**: segment-to-segment fuel cost from empirical GPS-derived L/hr per unit per activity type. Paved corridors priced at 60-70% of gravel deadhead cost.
- **Grader Performance Score**: composite 0-100. RID (primary, 50%) + coverage efficiency in grading-km per engine hour (25%) + fuel efficiency via deadhead ratio (25%). GPS revisit interval serves as RID proxy when PSD assessment frequency drops in peak season.
- **Effective-km-days**: system-level metric. Grading-km multiplied by RID. 30 km/day at 20-day RID = 600 effective-km-days, more productive than 40 km/day at 12-day RID = 480.
- **Role-based score visibility**: Ryan and Shawn see all scores. Operator visibility (own score only, or division comparison) is a configurable setting pending Ryan's decision.

## Out of Scope (workstream boundary reference)

- Winter plow route optimization — deferred to Phase 3 (Fall 2026 - Winter 2027)
- Full fleet analysis (trucks, tractors) — schema supports, 2026 scope is graders + dust control truck only
- Public Council portal — internal dashboards only
- Real-time GPS streaming — weekly batch only, Fabric F2 capacity constraint
- Operator mobile app — print workflow first, mobile deferred until print adoption validated
- Automated dispatch — Shawn reviews and distributes; no push-to-operator bypass of supervisor
- Road reconstruction budgeting — separate capital process
- Fabric capacity upgrade — known risk, budgetary decision for Ryan
- Gravel supply chain optimization — separate operational domain
- Cross-municipality shared services — architectural support possible, inter-municipal agreements out of scope

## Pending Data Requests (as of 2026-04-14)

The PRD lists six items. The companion draft (`email_data_request.md`) carried all six. The **actually sent** email (see [[Sent Email Data Requests 2026-04-14]]) dropped item 6 (haul routes) and broadened the distribution on items 1-2.

PRD-listed items:

1. Road priority classification as GIS layer or joinable table (Graham / Jesse)
2. Base-stabilized segment IDs mapped to RS_GIS_ID (Graham / Aaron)
3. Dust control site geocoded coordinates (Graham / Jesse)
4. Traffic volume / AADT data for gravel roads (Graham)
5. Dust control 2025/2026 application list (Aaron / Graham)
6. Haul route designations as GIS layer or list (Graham / Shawn) — **dropped from sent email; re-raise separately**

## Sprint Timeline

| Sprint | Dates | Deliverable |
|---|---|---|
| 1 | Apr 14-25 | GPS baseline analysis, deadhead ratio, report for Ryan |
| 2 | Apr 28-May 9 | Spatial analysis, depot optimization, cost matrix, territory recommendations |
| 3 | May 12-30 | Fabric lakehouse deployment, Road Intelligence Dashboard (4 pages) |
| 4 | June | Route Planner (PyVRP/ALNS/LKH-3), territory optimization, dust control CVRP |
| 5 | Jul-Oct | Grader Performance Score, continuous measurement, end-of-season Council report |

## 5-Year Financial Projection

| Year | Combined Value | Cumulative |
|---|---|---|
| 2026 | $50,000-$110,000 | $50,000-$110,000 |
| 2027 | $75,000-$130,000 | $125,000-$240,000 |
| 2028 | $90,000-$145,000 | $215,000-$385,000 |
| 2029 | $100,000-$150,000 | $315,000-$535,000 |
| 2030 | $100,000-$150,000 | $415,000-$685,000 |

## Raw File

`.raw/projects/road-intelligence-platform/historical/PRD_Road_Intelligence_Platform.md`
