---
type: source
title: "Old Project CLAUDE Instructions"
source_type: historical project instructions
author: "Tony Jung"
date_published: 2026-04-14
raw_file: ".raw/projects/road-intelligence-platform/historical/CLAUDE.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - project-instructions
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[Road Intelligence Platform Refined Build Plan]]"
  - "[[GPS Baseline Analysis Spec]]"
---

# Source: Old Project CLAUDE Instructions

> [!note] Measured baseline available 2026-04-16
> The "immediate task" declared here (GPS baseline analysis) is complete. See [[GPS Baseline Results 2026-04-16]]: grader deadhead 31.8%, 2 years of data, 2.67M breadcrumbs. Fleet rosters below are authoritative for the April 14 period but division labels are stale (see callout below).

**Full title**: Road Intelligence Platform — Project Context (laptop `CLAUDE.md`)
**Author**: Tony Jung
**Date**: April 14, 2026 (inferred from cross-document references)
**Status**: Historical project instructions from the old laptop's Claude Code working directory. Compact index pointing at project data sources, planning docs, key numbers, and data quality warnings. Declares the Refined Build Plan as "START HERE".

## Summary

Project context file for the laptop's Claude Code sessions. Declares the project mission (route optimization for Lethbridge County's grader fleet, built by Tony for Ryan) and the current phase (Sprint 1: GPS Baseline Analysis). Indexes the project's data layout: 367 daily GPS CSVs, shapefile trio, fuel files, OEM telematics, scanned operator maps (`2148_001.pdf` February, `2215_001.pdf` March), drivability assessments, priority PDFs, operator manual, blade inventory, dust control and base stabilization records. Carries the immediate task pointer (implement GPS baseline per the spec), the key numbers block (9 tracked graders, 21.1 L/hr fleet avg, $1.57/L UFA, 20-30% deadhead expected), and the data quality warnings catalog.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — data layout, Fabric connection (workspace `finance_fabric`, F2 capacity, notebooks 08-14 continuing 01-07)
- [[Deadhead Ratio]] — data quality warnings list
- [[GPS Baseline Analysis Spec]] — confirms spec as the execution artifact

## Key Facts

> [!warning] Division assignment corrections from Shawn (2026-04-10)
> The old `CLAUDE.md` was written using Titan GPS division labels, which turned out to be stale. Per Shawn's April 10 email ([[UFA Price and Division Correction Thread 2026-04-09]]):
> - **MG-046 is Div 2** (CLAUDE.md says Div 3)
> - **MG-053 is Div 3** (CLAUDE.md noted Div 2 unclear; the "MG-053 replaced MG-044" earlier note was a Div 3 change, not Div 2)
> - **MG-042 and MG-052** are CAT 14M construction graders, no GPS by design. Listing them alongside other no-GPS units conflates two different situations.
>
> Per-unit fuel rates now available: see [[Unit Fuel Rates Reconciliation]].

- **"START HERE" pointer**: `REFINED_BUILD_PLAN.md` ([[Road Intelligence Platform Refined Build Plan]])
- **Immediate task at writing**: GPS baseline analysis
- **Graders active with GPS (9)**: MG-051 (Div 1, CAT 150, 146 active days, 3,390 hrs), MG-046 (Div 3, CAT 150, 180 days, 6,544 hrs), MG-050 (Div 4, JD 772GP, 231 days, 3,930 hrs), MG-048 (Div 5, JD 772GP, 170 days, 4,849 hrs), MG-047 (Div 6, JD 872GP, 234 days, 6,209 hrs), MG-049 (Div 7, JD 772GP, 235 days, 4,508 hrs, **anomalous**), MG-039 (spare, CAT 140M3, 96 days, 2,898 hrs), MG-041 (spare, JD 772GP, 78 days, 8,429 hrs), MG-044 (spare, JD 872GP, 138 days, 5,421 hrs)
- **Graders without GPS (6)**: MG-031, MG-042, MG-043, MG-045, MG-052, MG-053
- **Div 2 assignment**: unclear. MG-053 replaced MG-044 ~3 weeks before document date per Shawn.
- **Fabric connection**: `finance_fabric` workspace, F2 capacity, `gold_fact_equipment` and `gold_dim_equipment` as upstream dims for Road Intelligence pipeline
- **Downstream deliverables (3)**: Road Intelligence Dashboard, Route Planner (PyVRP-powered), Grader Performance Score (road durability)

## Data Inventory (pointer list)

- 367 daily GPS CSVs in `titan-gps-data-scrape/processed/locations/` (609 MB)
- `titan-gps-data-scrape/raw_dumps/` (24 hourly JSON × 367 days)
- `Route_Optimization_GIS/LC_Roads.shp` (3,097 segments, EPSG:26912)
- `Route_Optimization_GIS/LC_Grader_Camps.shp` (7 depots, EPSG:4326)
- `Route_Optimization_GIS/LC_Grader_Divisions.shp` (7 divisions + 2 rover areas)
- `fuel/` directory (JD telematics, CAT telematics, fill-up records)
- `FuelEconomyMain.xls` (1,101 fill records, 7 graders, May 2025 to April 2026)
- `2025IDLEHOURSREPORT-JOHN DEERE.csv` (8 JD graders, 2025 idle/load hours)
- `Fleet Utilization 01-01-2025 31-12-2025 09-04-2026.xlsx` (CAT graders runtime/idle/fuel)
- `2148_001.pdf` (Feb 2026 operator grading maps, all 7 divisions)
- `2215_001.pdf` (Mar 2026 operator grading maps, all 7 divisions)
- `Drivability Assessment.xlsx` (PSD Weeks 4-11 2026)
- `Grading/Grader Divisions Priority 2025.pdf` (10 pages, High/Med/Low per segment)
- `Grading/Gravel Road Maint_Procedures 2021 Final Copy.pdf` (17-page operator manual)
- `Grading/Grader Blade Inventory Tracker.xlsx` (blade types by unit)
- `Dust Control/Dust Control 2024.xlsx` (338 applications, $393K, 140 km)
- `Base Stabilization/` (MG-30 injection tracking, 2022-2026)

## Raw File

`.raw/projects/road-intelligence-platform/historical/CLAUDE.md`
