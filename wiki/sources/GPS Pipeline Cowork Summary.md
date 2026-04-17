---
type: source
title: "GPS Pipeline Cowork Summary"
source_type: historical chat summary
author: "Tony Jung"
date_published: 2026-04-10
raw_file: ".raw/projects/road-intelligence-platform/historical/2026-04-10-gps-pipeline-cowork-summary.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - chat-summary
  - gps-pipeline
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[GPS Baseline Analysis]]"
  - "[[GPS Baseline Analysis Spec]]"
  - "[[Route Planner]]"
  - "[[Fleet Efficiency Dashboard]]"
  - "[[Shawn Ogertschnig]]"
  - "[[Jesse]]"
---

# Source: GPS Pipeline Cowork Summary

> [!note] Pipeline shipped, measured baseline landed 2026-04-16
> The pipeline built in this cowork session ran in Fabric on 2026-04-16 and produced the authoritative baseline. See [[GPS Baseline Results 2026-04-16]]: grader deadhead 31.8%, 5,653 shifts, gold tables `gold_fact_grading_activity` + `gold_fact_segment_visits` built.

**Session location**: Old laptop (pending recovery)
**Session date**: April 10, 2026 (approximate, confirm)
**Captured**: April 16, 2026
**Status**: Historical chat summary from a prior Claude Code cowork session. Captures pipeline implementation detail that produced the 2026-04-14 GPS Baseline Analysis report.

## Summary

Session built: `gps_baseline_analysis.py` (rewritten for Titan JSON structure with nested `raw_dumps/YYYY-MM-DD/{00-23}.json`, device-name parse `MG-050 - Div 4 - JD 772GP`, speed-based classification, shift detection, fuel cost estimation), `snap_to_segments.py` (GPS-to-LC_Roads matching, segment activity summaries), and three Fabric notebooks in the `finance_fabric` workspace (`10_bronze_gps`, `11_silver_gps_segments`, `12_gold_grading_activity`). 1.57 GB uploaded to the lakehouse at `Files/operations/gps/raw_dumps/`. Spark JSON read error resolved by replacing glob pattern with `recursiveFileLookup`. Shawn's handwritten operator maps received for all 7 divisions with March 2026 grading dates and mileage totals, providing ground-truth validation data.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — Data Pipeline section (medallion architecture, lakehouse layout)
- [[Deadhead Ratio]] — methodology (Titan JSON shape, device-name parse, speed classification, shift detection)
- [[Fleet Efficiency Dashboard]] — `12_gold_grading_activity` as upstream Power BI feed
- [[Route Planner]] — `snap_to_segments.py` against LC_Roads shapefile as upstream infrastructure
- [[Jesse]] — owns LC_Roads shapefile
- [[Shawn Ogertschnig]] — handwritten division maps as ground truth

## Key Facts

- **Titan JSON structure**: `raw_dumps/YYYY-MM-DD/{00-23}.json` (daily folder, 24 hourly files)
- **Device name parse**: e.g., `MG-050 - Div 4 - JD 772GP` yields unit ID, division assignment, make/model
- **Fabric workspace**: `finance_fabric`
- **Fabric notebooks created**:
  - `10_bronze_gps` (JSON ingestion with `explode(locations)`)
  - `11_silver_gps_segments` (classify + shifts)
  - `12_gold_grading_activity` (join to dims, gold facts for Power BI)
- **Lakehouse upload**: 1.57 GB to `Files/operations/gps/raw_dumps/`
- **Spark read fix**: replaced glob `*/*.json` with `recursiveFileLookup` option
- **Ground truth**: Shawn's handwritten maps, all 7 divisions, March 2026 grading dates + mileage totals

## Artifacts Referenced But Not Yet In Vault

- `gps_baseline_analysis.py` (exists in `.raw/.../historical/`; needs separate triage pass)
- `snap_to_segments.py` (exists in `.raw/.../historical/`; needs separate triage pass)
- Fabric notebooks (remote in `finance_fabric`, not exported to local)
- Shawn's handwritten division maps (photo or scan pending)

## Raw File

`.raw/projects/road-intelligence-platform/historical/2026-04-10-gps-pipeline-cowork-summary.md`
