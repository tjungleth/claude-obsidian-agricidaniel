---
type: source
title: "Road Intelligence Platform Build Plan (Original)"
source_type: historical build plan
author: "Tony Jung"
date_published: 2026-04-06
raw_file: ".raw/projects/road-intelligence-platform/historical/road_intelligence_platform_build_plan.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - build-plan
  - superseded
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[Road Intelligence Platform Refined Build Plan]]"
  - "[[Financial Rebase]]"
  - "[[PRD Road Intelligence Platform]]"
---

# Source: Original Build Plan (Superseded)

> [!note] Measured baseline available 2026-04-16
> This April 6 plan's assumptions were rebased April 10 (Financial Rebase) and are now measured (April 16). See [[GPS Baseline Results 2026-04-16]]: grader deadhead 31.8%, $46K/yr fuel, $14K-$18.5K/yr savings. Two-level optimization and solver stack decisions below remain valid.

**Full title**: Road Intelligence Platform — Build Plan
**Author**: Tony Jung
**Date**: April 6, 2026
**Status**: Historical. **Superseded by [[Road Intelligence Platform Refined Build Plan]] (April 14)**. Preserved for decision history and the "what changed and why" narrative.

## Summary

The project origin document. Ryan forwarded Graham White's PSD drivability export (March 11, 2026) and asked whether a Power BI dashboard was feasible. Analysis of 786 PSD rows revealed the larger opportunity: combining PSD + Titan GPS + ArcGIS + the existing Operations Intelligence lakehouse into a unified platform optimizing grader routes for fuel savings and tracking road-condition outcomes. Fuel savings chosen as Phase 1 for the hard dollar figure. Commits to PyVRP (over OR-Tools), two-level optimization (K-medoids territory + PyVRP route sequencing), empirical fuel cost model (Bektaş & Laporte 2011 Pollution-Routing Problem), and a build-on-Fabric / migrate-to-Databricks trajectory. Lists 7 open data gaps awaiting Ryan, Fleet, and Graham.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — project origin story
- [[PyVRP]] — solver choice rationale (Vidal 2012-2022)
- [[Route Optimization]] — medallion architecture, 08-14 notebook numbering (later extended to 15)
- [[Route Planner]] — original phase deliverable reference
- [[Fleet Efficiency Dashboard]] — original 4-page list

## Key Facts (Since Replaced)

- **Original fuel assumption**: 15 units × 1,350 hrs × 18 L/hr × $1.60/L = $544K (later rebased to $375K-$400K)
- **Original Year 1 savings**: $70K (later rebased to $40K-$75K combined)
- **Original 5-year cumulative**: $530K single point (later rebased to $345K-$535K range)
- **Solver choice**: PyVRP over OR-Tools (1-2% of optimal vs 5-10% gap)
- **Two-level optimization**: K-medoids (territory) + PyVRP (daily sequencing), LKH-3 post-processing, ALNS validation
- **Notebook numbering**: 08-14 (later extended to 15 for Grader Performance Score)
- **Platform path**: Fabric (Phases 1-3) → Databricks (Phase 4+)
- **Data gaps at plan time (7)**: Titan GPS sample, operator-to-equipment mapping, grader depot locations, current rotation schedule, PSD assessor-to-operator mapping, traffic volume, ArcGIS shapefile

## Why Superseded

Before GPS and telemetry arrived, savings were modeled from industry-typical deadhead ratios, engine hours came from spec sheets, and fuel rates were assumed flat at 18 L/hr. The April 10 Financial Rebase corrected these against telemetry. The April 14 Refined Build Plan added 5 sprints, the Grader Performance Score, Depot Analysis, 21-variable breakdown, and 5-level optimization stack. The plan evolves: April 6 → April 10 → April 14.

## Raw File

`.raw/projects/road-intelligence-platform/historical/road_intelligence_platform_build_plan.md`
