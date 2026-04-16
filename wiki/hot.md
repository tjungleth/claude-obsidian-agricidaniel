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
2026-04-16: Road Intelligence Platform fully ingested (6 concepts, 10 workstreams, 2 sources, anchor page)

## Road Intelligence Platform (Active Project)
- **Anchor**: [[Road Intelligence Platform]]
- **Status**: active, 24 files committed, pushed to origin
- **Source reports**: 2 PDFs dated 2026-04-14 (GPS Baseline Analysis + Comprehensive Findings), both `status: complete` in manifest
- **Sponsor**: [[Ryan Thomson]], Director, Public Works & Utilities
- **Key metric**: 24.9% fleet deadhead ratio, $55K-$65K/yr fuel, $140K-$165K/yr fully loaded
- **2026 projection**: $33K-$61K fuel / $80K-$150K fully loaded
- **Gold standard KPI**: road integrity duration after grading (quality of the grading itself)
- **Workstreams**: 3 Tier 1 (Route Planner, Spare Coordination, MG-048 Investigation), 3 Tier 2 (Div 1 Depot Staging, Demand-Driven Scheduling, Dust Control Coordination), 1 dashboard, 3 Tier 3 concept stubs
- **Entity pages on hold**: pending stakeholder meeting with Cody, Shawn, and Lee
- **Pending source material**: project folder on old laptop (to be ingested as `status: "historical"` when accessible)

## Plugin State
- **Version**: 1.4.1 (installed, enabled, user scope)
- **Hooks**: PostToolUse auto-commit is now **opt-in** via `CLAUDE_OBSIDIAN_AUTO_COMMIT=1` (changed 2026-04-15)
- **Skills**: 10 (wiki, wiki-ingest, wiki-query, wiki-lint, save, autoresearch, canvas, defuddle, obsidian-bases, obsidian-markdown)

## Key Lessons
1. **Verify every number against source before writing.** Summary paragraphs in reports can conflict with their own per-row data. Prefer granular data. Three wrong numbers in the first concept page's Examples table prompted this rule.
2. PostToolUse auto-commit hook was firing on every Write/Edit, sweeping unrelated files into commits. Fixed by gating on `CLAUDE_OBSIDAN_AUTO_COMMIT=1`. Old hook is cached for the session it was loaded in; fix takes effect on next session.
3. `pdftotext` (from MinGW) works for text extraction on Windows. `pdfplumber` and `pymupdf` now also installed.
4. Git squash workflow (Approach A): accept auto-commits during session, `git reset --mixed origin/main` at end, stage intended files only, commit with clean message.

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
