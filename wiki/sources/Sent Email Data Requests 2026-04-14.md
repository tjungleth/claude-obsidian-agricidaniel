---
type: source
title: "Sent Email Data Requests 2026-04-14"
source_type: historical sent email
author: "Tony Jung"
date_published: 2026-04-14
raw_file: ".raw/projects/road-intelligence-platform/historical/2026-04-14-sent-email-data-requests.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - email
  - data-requests
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[PRD Road Intelligence Platform]]"
  - "[[Graham White]]"
  - "[[Jesse]]"
  - "[[Aaron Craig]]"
  - "[[Shawn Ogertschnig]]"
  - "[[Ryan Thomson]]"
---

# Source: Sent Email Data Requests (2026-04-14)

**Full title**: Road Intelligence Platform — Data Requests to Complete the Analysis
**From**: Tony Jung
**To**: All (broadcast to PW&U + GIS distribution)
**Date**: April 14, 2026 (approximate, confirm)
**Status**: Historical. Sent version of the data-requests email. Differs from the draft (`email_data_request.md`) on the laptop.

## Summary

Tony emails the PW&U and GIS distribution to report foundation status (367 days of GPS extracted, shapefiles loaded, fuel + telematics + PSD + dust control + base stabilization records integrated) and request five outstanding data items needed to complete the Route Planner by June. Items 1 and 2 (priority classification, base-stabilized segment IDs) broadcast to Graham, Jesse, Aaron, and Shawn. Item 3 (dust control geocoding) to Graham and Jesse. Item 4 (traffic / AADT) unassigned. Item 5 (dust control 2025/2026 list) to Aaron and Graham. The draft's sixth item (haul route designations) was dropped.

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — Pending Data Requests section
- [[Route Planner]] — upstream data dependencies
- [[Dust Control Coordination]] — geocoding + 2025/2026 list dependencies
- [[Graham White]] — primary recipient, owns priority layer + base stab IDs + geocoding + AADT
- [[Jesse]] — LC_Roads owner, dust control geocoding co-owner
- [[Aaron Craig]] — Base stabilization partner, dust control 2025/2026 list co-owner
- [[Shawn Ogertschnig]] — routing recipient on priority and base stab items

## Five Data Requests

1. **Road priority classification GIS layer** (Graham / Jesse / Aaron / Shawn): convert Grader Divisions Priority 2025 PDF to a joinable table or GIS field keyed by `RS_GIS_ID` or `segment_id`. Drives Route Planner prioritization.
2. **Base-stabilized segment IDs** (Graham / Aaron / Jesse / Shawn): map 2022-2026 base stabilization jobs to specific road segments. Lets Route Planner deprioritize stabilized roads.
3. **Dust control site geocoded coordinates** (Graham / Jesse): 338 application sites currently only carry Legal Land Descriptions. Geocoded coordinates enable CVRP optimization and grading-conflict overlay.
4. **Traffic volume / AADT data** (unassigned): partial data (haul routes, roads near hamlets) would calibrate the priority algorithm.
5. **Dust control 2025/2026 application list** (Aaron / Graham): pre-season list flags upcoming dust control roads so graders finish grading before calcium goes down.

## Delta vs Draft

| Change | Draft | Sent |
|---|---|---|
| Salutation | Named recipients | "Hi All" |
| Item count | 6 | 5 |
| Item 1 assignment | Graham / Jesse | Graham / Jesse / Aaron / Shawn |
| Item 2 assignment | Graham / Aaron | Graham / Aaron / Jesse / Shawn |
| Item 4 assignment | Graham | unassigned |
| Item 6 (haul routes) | Graham / Shawn | **dropped** |

The dropped haul-route request is worth re-raising with Graham and Shawn separately once baseline analysis is done, since haul route data is a priority-algorithm input for the Route Planner.

## Raw File

`.raw/projects/road-intelligence-platform/historical/2026-04-14-sent-email-data-requests.md`
