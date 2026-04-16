---
type: source
title: "Road Intelligence Platform Comprehensive Findings"
source_type: internal report
author: "Tony Jung"
date_published: 2026-04-14
raw_file: ".raw/projects/road-intelligence-platform/2026-04-14-road-intelligence-platform-comprehensive-findings.pdf"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - fleet-analysis
  - optimization
status: current
related:
  - "[[Road Intelligence Platform]]"
  - "[[GPS Baseline Analysis]]"
---

# Source: Road Intelligence Platform Comprehensive Findings

**Prepared for**: [[Ryan Thomson]]
**Prepared by**: Tony Jung
**Date**: April 14, 2026
**Data**: 1.52M GPS breadcrumbs, 9 graders, 367 days. 1,101 fuel fill records. 3,097 road segments. 7 grader camps.
**Pages**: 7

## Summary

Builds on the GPS Baseline Analysis with deeper investigation: MG-048 deep dive, route overlap analysis (93% involves spare graders), depot proximity assessment, network coverage (98.3%), and a ranked Tier 1/2/3 opportunity table. Introduces the combined 2026 projection ($33,000 to $61,000 fuel, $80,000 to $150,000 fully loaded) and five immediate recommendations.

## Pages Created from This Source

- [[Road Intelligence Platform]] — executive summary, workstreams table, 2026 projection, immediate recommendations, data quality notes
- [[Deadhead Ratio]] — seasonal breakdown, per-grader ranking
- [[Route Optimization]] — Tier 1 value estimate ($15,000-$35,000 fuel, $40,000-$90,000 fully loaded)
- [[PyVRP]] — "Route optimization (PyVRP)" Tier 1 entry, Sprint 4 June timeline
- [[Demand-Driven Scheduling]] — "Replace fixed rotation with priority-based grading frequency" (Tier 2); GIS priority layer requirement (recommendation #5)
- [[Facility Location]] — per-grader camp distance table, MG-051 at 6.2 km outlier
- [[Fully Loaded Hard Savings]] — 2026 projection: $80,000 conservative / $150,000 moderate
- [[MG-048 Investigation]] — deep dive §2: 55 km deadhead vs 36 km grading per shift, 8.9 hr shift, 24% high-load; Tier 1 $5,000-$10,000/yr
- [[Spare Coordination]] — overlap analysis §3: 2,017 of 2,542 segments with multi-grader contact, 1,871 (93%) involve a spare; Tier 1 $5,000-$15,000/yr
- [[Route Planner]] — Tier 1 entry, Sprint 4 June, $15,000-$35,000 fuel; pilot recommendation #4
- [[Division 1 Depot Staging]] — Tier 2, $3,000-$5,000/yr net, Sprint 4
- [[Dust Control Coordination]] — Tier 3 assessment, $10,000-$25,000/yr avoided waste; "Avoid grading dust-controlled roads after treatment"
- [[Fleet Efficiency Dashboard]] — recommendation #3: "Publish the metrics on a weekly cadence"
- [[Weather-Responsive Scheduling]] — Tier 3: "Grade after rain and defer during dry spells for better durability"
- [[Grader Performance Score]] — Tier 3: "Identify operators producing the most durable results and support peer learning"
- [[Treatment Optimization]] — Tier 3: "Allocate grading, dust control, and stabilization budgets segment by segment"

## Key Findings

1. 93% of multi-grader route overlap involves at least one spare grader: the core issue is dispatch coordination, not territory boundaries
2. MG-048 deep dive: deadheads 55 km per shift but grades only 36 km; 24% high-load engine time vs 5-9% fleet norm
3. Network coverage is 98.3% (2,500 of 2,542 gravel segments visited): the issue is not under-coverage but the cost of achieving coverage
4. Tier 1 opportunities (route optimization + spare coordination + MG-048 investigation) carry the highest near-term value
5. 2026 combined projection: conservative $33,000 fuel / $80,000 fully loaded; moderate $61,000 fuel / $150,000 fully loaded
6. Five immediate recommendations: share with Shawn, investigate MG-048, approve dashboard, approve Route Planner pilot, request GIS priority layer

## Raw File

`.raw/projects/road-intelligence-platform/2026-04-14-road-intelligence-platform-comprehensive-findings.pdf`
