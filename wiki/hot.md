---
type: meta
title: "Hot Cache"
updated: 2026-04-16
tags:
  - meta
  - hot-cache
status: evergreen
related:
  - "[[index]]"
  - "[[log]]"
  - "[[Wiki Map]]"
  - "[[getting-started]]"
  - "[[Road Intelligence Platform]]"
---

# Recent Context

Navigation: [[index]] | [[log]] | [[overview]]

## Last Updated
2026-04-16: Measured baseline landed ([[GPS Baseline Results 2026-04-16]]), laptop historical folder fully ingested (660 files triaged, 10 source pages), 9 entity stubs created, cascade edits applied across 12 analytical pages + 9 source callouts.

## Road Intelligence Platform (Active Project)
- **Anchor**: [[Road Intelligence Platform]]
- **Authoritative baseline**: [[GPS Baseline Results 2026-04-16]] — Fabric pipeline, 2 years of data (2024-03-06 to 2026-04-09), 2.67M deduplicated breadcrumbs, 5,653 shifts, 38 devices
- **Headline (measured)**: grader deadhead **31.8%**, fleet-wide **43.1%**, ~$46K/yr grader deadhead fuel, ~$115K/yr fully loaded
- **Savings (revised)**: $14K-$18.5K/yr graders at 30-40% reduction, $40K-$55K/yr full fleet
- **Sponsor**: [[Ryan Thomson]], Director, Public Works & Utilities
- **Gold standard KPI**: road integrity duration after grading (quality, not cost)
- **Worst graders (biggest routing targets)**: [[MG-051]] Div 1 at 43.6% ($7,325/yr fuel), MG-046 Div 2 at 42.7% ($16,163/yr fuel)
- **Best grader**: MG-047 Div 6 at 14.0% (compact territory)

## Division Corrections (authoritative, from Shawn 2026-04-10)
- **MG-046 is Div 2** (Titan label "Div 3" is stale)
- **MG-053 is Div 3** (no GPS, replaced MG-044 ~3 weeks ago)
- **MG-042 & MG-052 are CAT 14M construction graders** — no GPS by design, not "missing"

## Superseded (April 14 PDFs marked `status: superseded`)
- Old baseline: 24.9% fleet (8 graders, MG-049 excluded, 367 days, 1.52M breadcrumbs)
- Old projection: $33K-$61K fuel / $80K-$150K fully loaded
- Fabric pipeline on 2-year dataset gives ~7 percentage points higher deadhead because larger dataset + MG-049 included + all 38 devices contribute to fleet figure

## Key People (Road Intelligence Platform)
- **[[Shawn Ogertschnig]]**, Manager, Public Operations. NOT "Superintendent" despite PRD; email sig is authoritative. Source of division corrections + March 2026 ground-truth maps.
- **[[Graham White]]**, Manager, Technical Services. GIS owner.
- **[[Aaron Craig]]** (last name confirmed). Base Stabilization partner. **Owes road priority GIS layer — critical path** for Route Planner.
- **[[Jesse]]**, GIS co-owner (LC_Roads shapefile, dust control geocoding). Last name unknown.
- **[[Cole Beck]]**, CAO. Informed / supportive.
- **[[Hailey Pinksen]]**, finance-adjacent (budget question on UFA thread).
- **[[Sean MacRae]]**, on fuel / operational data distribution.
- **[[Lee Martin]]** (last name confirmed; distinct from Cody and Cole). Forwarded Shawn's March 2026 grading maps.
- **[[Tyler Reiter]]**, UFA Picture Butte agent (external). Provided $1.5667/L dyed diesel lock-in.

## Fabric State (Road Intelligence Platform)
- **Workspace**: `finance_fabric`, F2 capacity
- **Gold tables built**: `gold_fact_grading_activity` (5,653 rows), `gold_fact_segment_visits` (4,204 rows)
- **Gold tables pending**: `gold_dim_road_segment` — blocked on shapefile upload (LC_Roads, LC_Grader_Divisions, LC_Grader_Camps still on local machine)
- **UFA lock-in**: $1.5667/L dyed diesel (75% of 2025 May-Sep usage) via Tyler Reiter

## Workstreams
- **Tier 1**: [[Route Planner]], [[Spare Coordination]], [[MG-048 Investigation]]
- **Tier 2**: [[Division 1 Depot Staging]] (MG-051 is THE worst grader now, strong case), [[Demand-Driven Scheduling]], [[Dust Control Coordination]]
- **Dashboard**: [[Fleet Efficiency Dashboard]]
- **Tier 3**: [[Weather-Responsive Scheduling]], [[Grader Performance Score]], [[Treatment Optimization]]

## Historical Laptop Material (ingested 2026-04-16)
- Folder: `.raw/projects/road-intelligence-platform/historical/` (660 files from old laptop)
- 10 source wiki pages: [[PRD Road Intelligence Platform]], [[Road Intelligence Platform Refined Build Plan]], [[Road Intelligence Platform Build Plan]], [[Financial Rebase]], [[GPS Baseline Analysis Spec]], [[GPS Pipeline Cowork Summary]], [[Old Project CLAUDE Instructions]], [[Sent Email Data Requests 2026-04-14]], [[UFA Price and Division Correction Thread 2026-04-09]], [[Unit Fuel Rates Reconciliation]]
- Tier B/C archives (Base Stabilization 2017-2022, Dust Control RFPs 2017-2025, Grading division maps, src/tests Python project, Route_Optimization_GIS shapefiles) are in `.raw/` but not individually pageified. Available for reference.

## Plugin State
- **Version**: 1.4.1 (installed, enabled, user scope)
- **Hooks**: PostToolUse auto-commit is opt-in via `CLAUDE_OBSIDIAN_AUTO_COMMIT=1`
- **Skills**: 10

## Autoresearch: Municipal Fleet Route Optimization (2026-04-16)
- No grader-specific route optimization case study exists in the published literature
- Closest: Baltimore County ($354K/6mo from GPS dispatch), CMU snow plow CARP (3-156% shorter routes)
- **CARP vs VRP**: grader routing is arc routing, not node routing. PyVRP arc-to-node transformation works but is approximate.
- Synthesis: [[Research Municipal Fleet Route Optimization Case Studies]]

## Key Lessons
1. **Verify every number against source before writing.**
2. PostToolUse auto-commit hook is opt-in via env var.
3. `pdftotext`, `pdfplumber`, `pymupdf` installed.
4. Git squash workflow for clean commits.
5. **Measured values can materially differ from recent PDF estimates**: April 14 PDFs reported 24.9% fleet deadhead. April 16 Fabric pipeline on 2-year dataset showed 31.8% grader / 43.1% fleet — ~7 percentage points higher. Always re-run the pipeline on full data before quoting numbers to Council.
6. **Nested git repo in `.raw/`**: the laptop project folder carries its own `.git/`. Add to vault `.gitignore` before next commit to avoid submodule issues.

## Style Preferences (Saved to Memory)
- **No em dashes** (U+2014) or `--` as punctuation anywhere. Use periods, commas, colons, or parentheses. Hyphens in compound words are fine.
- Keep responses short and direct. No trailing summaries.
- Diff before every write to vault config/meta files.
- Briefly teach Obsidian/Markdown idioms when using new syntax.
- One file per write. Pause between clusters for review.

## Repo Locations
- Working vault: `C:\Users\tjung\Documents\vault`
- Public: https://github.com/tjungleth/claude-obsidian-agricidaniel
- Upstream: https://github.com/AgriciDaniel/claude-obsidian
