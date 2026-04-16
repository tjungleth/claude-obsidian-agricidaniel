---
type: meta
title: "Road Intelligence Platform Ingestion Session"
created: 2026-04-16
updated: 2026-04-16
tags:
  - meta
  - session
  - road-intelligence-platform
status: current
related:
  - "[[Road Intelligence Platform]]"
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Road Intelligence Platform Ingestion Session

**Dates**: 2026-04-15 to 2026-04-16
**Scope**: Full project ingestion from two executive PDF reports into a structured wiki knowledge base.

## What Was Built

From 2 PDF reports (11 pages combined), the session produced:

- **6 concept pages**: [[Deadhead Ratio]], [[Route Optimization]], [[PyVRP]], [[Demand-Driven Scheduling]], [[Facility Location]], [[Fully Loaded Hard Savings]]
- **10 workstream pages**: 3 Tier 1, 3 Tier 2, 1 dashboard, 3 Tier 3 concept stubs
- **2 source pages**: [[GPS Baseline Analysis]], [[Road Intelligence Platform Comprehensive Findings]]
- **1 anchor page**: [[Road Intelligence Platform]] with fleet baseline table, workstream routing, 2026 projection
- **1 master manifest**: `.raw/.manifest.json` with delta tracking (status enum: pending, partial, complete, stale, historical)
- **1 workstream template**: `_templates/workstream.md`

Total: 21 new wiki pages, 51 pages in the vault overall, zero orphans.

## Key Decisions

1. **Project renamed**: "Grader Route Optimization" to "Road Intelligence Platform" (umbrella, not single workstream)
2. **Interview approach abandoned**: source PDFs already had executive-grade content; ingesting reports was more accurate than cold interview
3. **Dust Control Coordination elevated**: moved from Tier 3 stub to active Tier 2 workstream ($10K-$25K/yr concrete estimate, Sprint 4 timing)
4. **MG-050/MG-048 Swap folded**: into MG-048 Investigation as "Potential Outcomes" section (conditional on investigation results, not a parallel initiative)
5. **Entity pages deferred**: Ryan Thomson, Shawn, MG-048, MG-051 pages held until stakeholder meeting with Cody, Shawn, and Lee
6. **Gold standard KPI defined**: road integrity duration after grading, not just cost reduction. Tier 3 workstreams target this directly.

## Operational Enrichment Pattern

After the report-sourced ingestion was complete, Tony contributed **field-level operational knowledge** to [[Division 1 Depot Staging]] that the PDFs did not contain:

- Three transport options for overnight staging (crew truck shuttle, personal vehicle, two-up staging)
- The math: $15-20 shuttle fuel vs $45-60 grader fuel saved per round trip
- Barriers: equipment security, cold starts at -30C (block heater access), operator change management, insurance/liability for non-county overnight locations
- Decision framework: staging makes sense when deadhead exceeds 20 min one-way, a secure location exists within 10 min, and block heater access is available in winter

This establishes the pattern for future sessions: **reports provide the analytical foundation; field knowledge enriches workstream pages with operational reality that analysis alone cannot capture.**

## Process Lessons

1. **Verify every number at write time.** Three factual errors in the first concept page draft (wrong month, wrong seasonal ranges) came from drafting off memory instead of re-reading the source passage. Rule: grep the source for every figure before it enters the vault.
2. **Auto-commit hook interference.** The PostToolUse hook fired on every Write, producing 35 junk auto-commits with swept-in noise. Fixed by gating on `CLAUDE_OBSIDIAN_AUTO_COMMIT=1` (opt-in). Squash workflow: accept auto-commits during session, `git reset --mixed origin/main` at end, stage intended files only.
3. **Build order matters.** Concepts first (no dependencies), then workstreams (link to concepts), then anchor last (links to everything). Leaves-first, trunk-last.
4. **pdftotext table extraction is unreliable.** Installed pdfplumber + pymupdf for future use. Always reconstruct table alignment logically (sum checks, set membership) rather than trusting visual layout from pdftotext.

## Pending

- Entity pages (after Cody/Shawn/Lee meeting)
- Old laptop project folder (to ingest as `status: "historical"` when accessible)
- 4 other project stubs (Bank Reconciliation App, Databricks, ERP Migration, SharePoint) untouched
