---
type: source
title: "GPS Baseline Analysis Spec"
source_type: historical technical spec
author: "Tony Jung"
date_published: 2026-04-10
raw_file: ".raw/projects/road-intelligence-platform/historical/GPS_BASELINE_ANALYSIS_SPEC.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - spec
  - gps-analysis
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[GPS Baseline Analysis]]"
  - "[[Deadhead Ratio]]"
  - "[[GPS Pipeline Cowork Summary]]"
---

# Source: GPS Baseline Analysis Spec

> [!note] Pipeline executed, measured baseline landed 2026-04-16
> The spec specified the April 14 PDF analysis. The Fabric pipeline ran on 2 years of data (2024-03-06 to 2026-04-09) and yielded measured values: grader deadhead **31.8%**, 2.67M breadcrumbs, 5,653 shifts. See [[GPS Baseline Results 2026-04-16]]. Methodology and data quality flags below remain the authoritative reference.

**Full title**: GPS Baseline Analysis — Implementation Spec
**Author**: Tony Jung
**Date**: April 10, 2026
**Status**: Historical technical spec. Defines `gps_baseline_analysis.py`, the script that produced the 2026-04-14 GPS Baseline Analysis report. Companion to the cowork-session summary.

## Summary

Specifies the pipeline that processes 367 days of Titan GPS breadcrumb data to calculate per-grader and per-division deadhead ratios. Defines the Titan record schema (deviceID, deviceName, eventTimeUTC, lat/lon, speedKph, headingDegrees, odometerHours/Km, exceptionEventType, insideLandmark, ignitionStatus). Commits to speed-based activity classification (GRADING 3-15 km/h, DEADHEADING >15 km/h, IDLE <3 km/h, OFF when ignitionStatus Off). Lists depot landmark names for 7 camps. Defines a five-step processing pipeline: load/filter, classify, shift aggregation, baseline metrics, snap-to-segment. Lists 7 data quality warnings including the MG-049 anomaly exclusion, the `isCurrLoc` API-artifact filter, and the weekend-baseline sanity check.

## Pages Created or Enriched from This Source

- [[GPS Baseline Analysis]] — upstream spec
- [[Deadhead Ratio]] — methodology, speed thresholds, classification logic, data quality flags
- [[Road Intelligence Platform]] — data quality warning catalog
- [[Route Planner]] — snap-to-segment 50m buffer, EPSG:26912 projection

## Key Facts

- **Data period**: 2025-04-07 to 2026-04-08 (367 days), ~609 MB, 1.52M breadcrumbs
- **Titan record schema** includes `insideLandmark` for depot-time calculation
- **Speed thresholds**: GRADING 3-15 km/h, DEADHEADING >15 km/h, IDLE <3 km/h
- **Spatial backbone**: LC_Roads EPSG:26912, 3,097 segments, 2,542 gravel. `segment_id` is the true unique key. `RS_GIS_ID` is not unique: 944 IDs map to 3,063 rows.
- **Grader camps**: 7 depots in LC_Grader_Camps.shp (EPSG:4326)
- **Fuel rates committed**: JD 21.3 L/hr working and 4.4 L/hr idle, CAT 18.2-22.7 L/hr, fleet 21 working / 4.5 idle average
- **Depot landmark names** (from Titan `insideLandmark`): `LC Coaldale Shop` (Div 1), `LC Picture Butte Shop` (Div 6 + main PW yard), `Barons Grader Camp` (Div 5); Readymade / Nolan Hill / Monarch / Iron Springs need confirmation
- **Exclusions**: MG-049 (3.4 km/h avg, no JD telematics, confirmed bad), MG-051 battery disconnects (929 events, GPS gaps)
- **Filters**: `isCurrLoc=true` records (API injection with future timestamps), `lat=0, lon=0` GPS signal loss, `Headingchange` events (`odometerHours=0`, use adjacent EngineInUse rows)

## Seven Data Quality Warnings

1. MG-049 exclusion from fleet averages (still usable for fuel fill data, 117 fills, 22,700L)
2. MG-051 battery disconnects (929 events, gaps)
3. `isCurrLoc=true` API artifacts with future timestamps
4. `HeartBeat` events (`ignitionStatus=N/A`), keep for timeline continuity not engine time
5. `Headingchange` events have `odometerHours=0`
6. Weekend baseline (~920 parked records) = zero-activity sanity check
7. Extraction summary only covers 240 days (Aug 11+); CSVs cover all 367 — CSVs are source of truth

## Pipeline Outputs

- `baseline_fleet_summary.csv` (per grader)
- `baseline_daily_summary.csv` (per grader per day)
- `baseline_monthly_summary.csv` (per grader per month)
- `baseline_report.md` (narrative for Ryan, became the 2026-04-14 Baseline Analysis report)
- Empirical fuel cost model (input for PyVRP cost matrix in Sprint 4)

## Technology Notes

- Python: pandas, geopandas, shapely, pyproj
- Memory: 609 MB CSVs. Load incrementally (one month at a time) or chunked.
- CRS: GPS WGS84 (EPSG:4326) reprojected to UTM Zone 12N (EPSG:26912) for spatial operations
- Distance: haversine between consecutive points, projected coordinates for snap-to-segment

## Raw File

`.raw/projects/road-intelligence-platform/historical/GPS_BASELINE_ANALYSIS_SPEC.md`
