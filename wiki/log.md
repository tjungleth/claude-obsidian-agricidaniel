---
type: meta
title: "Operation Log"
updated: 2026-04-16
tags:
  - meta
  - log
status: evergreen
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[overview]]"
  - "[[sources/_index]]"
---

# Operation Log

Navigation: [[index]] | [[hot]] | [[overview]]

Append-only. New entries go at the TOP. Never edit past entries.

Entry format: `## [YYYY-MM-DD] operation | Title`

Parse recent entries: `grep "^## \[" wiki/log.md | head -10`

---

## [2026-04-16] autoresearch | Municipal Fleet Route Optimization Case Studies

- Rounds: 2
- Searches: 7
- Sources found: 4 (Baltimore County, CMU SPRP, UK RL study, TAC gravel survey)
- Pages created: [[Baltimore County Fleet Telematics]], [[CMU Snow Plow Routing]], [[UK Winter Road Maintenance RL]], [[TAC Canadian Gravel Road Survey]], [[Capacitated Arc Routing]], [[Research Municipal Fleet Route Optimization Case Studies]]
- Synthesis: [[Research Municipal Fleet Route Optimization Case Studies]]
- Key finding: no grader-specific route optimization case study exists in the published literature. Grader routing is a CARP (arc routing) problem, not a standard VRP. The RIP may be the first GPS-based grader fleet optimization in a Canadian municipality.

## [2026-04-16] complete | Road Intelligence Platform — Full Ingestion

- Type: project ingest (complete)
- Source: `.raw/projects/road-intelligence-platform/` (2 PDFs, both now `status: complete` in manifest)
- **Pages created (20)**: 6 concepts ([[Deadhead Ratio]], [[Route Optimization]], [[PyVRP]], [[Demand-Driven Scheduling]], [[Facility Location]], [[Fully Loaded Hard Savings]]), 10 workstreams (3 Tier 1, 3 Tier 2, 1 dashboard, 3 Tier 3 stubs), 2 source pages, 1 anchor page ([[Road Intelligence Platform]])
- **Pages deleted (1)**: [[Grader Route Optimization]] stub (replaced by Road Intelligence Platform anchor)
- **Index updates**: wiki/index.md, wiki/concepts/_index.md, wiki/sources/_index.md, wiki/projects/_index.md
- **Infrastructure**: master manifest (`.raw/.manifest.json`), workstream template (`_templates/workstream.md`)
- Key data: 24.9% fleet deadhead baseline, $55K-$65K fuel, $140K-$165K fully loaded, 2026 projection $33K-$61K fuel / $80K-$150K fully loaded
- Gold standard KPI: road integrity duration after grading
- Entity pages (Ryan Thomson, Shawn, MG-048, MG-051) on hold pending stakeholder meeting with Cody, Shawn, Lee
- Pending: project folder on old laptop (to be ingested as `status: "historical"`)
- Vault health: 51 pages, zero orphans, 3 expected red links (held entity pages)

## [2026-04-15] session | Road Intelligence Platform — Setup and Interview Start

- Type: session
- Vault setup: CLAUDE.md user context, 5 project stubs, upstream remote added, git lessons (remotes, fetch vs pull, A..B range syntax)
- Auto-commit hook fix: PostToolUse gated on `CLAUDE_OBSIDIAN_AUTO_COMMIT=1` (default off)
- Interview approach started then abandoned: source PDFs already had executive-grade content, interview was wrong method
- Errors caught: 3 factual errors in Deadhead Ratio draft (wrong month, wrong seasonal ranges) from drafting off memory instead of re-reading source. Rule installed: verify every number against the source passage at write time.
- pdfplumber + pymupdf installed for future PDF extraction
## [2026-04-08] save | claude-obsidian v1.4 Release Session
- Type: session
- Location: wiki/meta/claude-obsidian-v1.4-release-session.md
- From: full release cycle covering v1.1 (URL/vision/delta tracking, 3 new skills), v1.4.0 (audit response, multi-agent compat, Bases dashboard, em dash scrub, security history rewrite), and v1.4.1 (plugin install command hotfix)
- Key lessons: plugin install is 2-step (marketplace add then install), allowed-tools is not valid frontmatter, Bases uses filters/views/formulas not Dataview syntax, hook context does not survive compaction, git filter-repo needs 2 passes for full scrub

## [2026-04-08] ingest | Claude + Obsidian Ecosystem Research
- Type: research ingest
- Source: `.raw/claude-obsidian-ecosystem-research.md`
- Queries: 6 parallel web searches + 12 repo deep-reads
- Pages created: [[claude-obsidian-ecosystem]], [[cherry-picks]], [[claude-obsidian-ecosystem-research]], [[Ar9av-obsidian-wiki]], [[Nexus-claudesidian-mcp]], [[ballred-obsidian-claude-pkm]], [[rvk7895-llm-knowledge-bases]], [[kepano-obsidian-skills]], [[Claudian-YishenTu]]
- Key finding: 16+ active Claude+Obsidian projects; 13 cherry-pick features identified for v1.3.0+
- Top gap confirmed: no delta tracking, no URL ingestion, no auto-commit

## [2026-04-07] session | Full Audit, System Setup & Plugin Installation
- Type: session
- Location: wiki/meta/full-audit-and-system-setup-session.md
- From: 12-area repo audit, 3 fixes, plugin installed to local system, folder renamed

## [2026-04-07] session | claude-obsidian v1.2.0 Release Session
- Type: session
- Location: wiki/meta/claude-obsidian-v1.2.0-release-session.md
- From: full build session — v1.2.0 plan execution, cosmic-brain→claude-obsidian rename, legal/security audit, branded GIFs, PDF install guide, dual GitHub repos


- Source: `.raw/` (first ingest)
- Pages updated: [[index]], [[log]], [[hot]], [[overview]]
- Key insight: The wiki pattern turns ephemeral AI chat into compounding knowledge — one user dropped token usage by 95%.

## [2026-04-07] setup | Vault initialized

- Plugin: claude-obsidian v1.1.0
- Structure: seed files + first ingest complete
- Skills: wiki, wiki-ingest, wiki-query, wiki-lint, save, autoresearch
