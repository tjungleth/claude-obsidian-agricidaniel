---
type: meta
title: "Wiki Index"
updated: 2026-04-16
tags:
  - meta
  - index
status: evergreen
related:
  - "[[overview]]"
  - "[[log]]"
  - "[[hot]]"
  - "[[dashboard]]"
  - "[[Wiki Map]]"
  - "[[concepts/_index]]"
  - "[[entities/_index]]"
  - "[[sources/_index]]"
  - "[[projects/_index]]"
  - "[[LLM Wiki Pattern]]"
  - "[[Hot Cache]]"
  - "[[Compounding Knowledge]]"
  - "[[Andrej Karpathy]]"
---

# Wiki Index

Last updated: 2026-04-16 | Total pages: ~85 | Sources ingested: 19 (incl. 10 historical + Fabric pipeline output)

Navigation: [[overview]] | [[log]] | [[hot]] | [[dashboard]] | [[Wiki Map]] | [[getting-started]]

---

## Concepts

- [[LLM Wiki Pattern]] — the pattern for building persistent, compounding knowledge bases using LLMs (status: mature)
- [[Hot Cache]] — ~500-word session context file, updated after every ingest and session (status: mature)
- [[Compounding Knowledge]] — why wiki knowledge grows more valuable over time, unlike RAG (status: mature)
- [[cherry-picks]] — prioritized feature backlog from ecosystem research; 13 features to add to claude-obsidian (status: current)
- [[Deadhead Ratio]] — percentage of active engine time spent traveling without grading (status: mature)
- [[Route Optimization]] — minimizing travel distance/time for vehicle routing problems (status: mature)
- [[PyVRP]] — Python Vehicle Routing Problem solver using Hybrid Genetic Search (status: mature)
- [[Demand-Driven Scheduling]] — priority-based grading frequency replacing fixed rotations (status: mature)
- [[Facility Location]] — depot-to-demand optimization for grader camp placement (status: mature)
- [[Fully Loaded Hard Savings]] — all-in cost metric: fuel + labour + depreciation + maintenance at 2.5x fuel (status: mature)
- [[Capacitated Arc Routing]] — arc-based counterpart to VRP; models grader/plow routing as segment traversal, not point visits (status: mature)

---

## Entities

- [[Andrej Karpathy]] — AI researcher, creator of the LLM Wiki pattern, former Tesla AI director (status: developing)
- [[Ar9av-obsidian-wiki]] — multi-agent compatible LLM Wiki plugin; delta tracking manifest (status: current)
- [[Nexus-claudesidian-mcp]] — native Obsidian plugin + MCP bridge; workspace memory, task management (status: current)
- [[ballred-obsidian-claude-pkm]] — goal cascade PKM; auto-commit hooks, /adopt command (status: current)
- [[rvk7895-llm-knowledge-bases]] — 3-depth query system, Marp slides, parallel deep research (status: current)
- [[kepano-obsidian-skills]] — official skills from Obsidian creator; defuddle, obsidian-bases (status: current)
- [[Claudian-YishenTu]] — native Obsidian plugin embedding Claude Code; plan mode, @mention (status: current)

### Road Intelligence Platform stakeholders

- [[Ryan Thomson]] — Director, Public Works & Utilities (sponsor)
- [[Shawn Ogertschnig]] — Manager, Public Operations (operational authority, source of division corrections + ground-truth maps)
- [[Graham White]] — Manager, Technical Services (GIS owner)
- [[Aaron Craig]] — Base Stabilization partner (owes road priority GIS layer, critical path)
- [[Jesse]] — GIS co-owner (LC_Roads, dust control geocoding)
- [[Cole Beck]] — CAO (informed, supportive)
- [[Hailey Pinksen]] — finance-adjacent (UFA budget-pressure question)
- [[Sean MacRae]] — on fuel / operational data distribution
- [[Lee Martin]] — forwarded March 2026 grading maps (distinct from Cody and Cole)
- [[Tyler Reiter]] — UFA Picture Butte agent (external)

> [!NOTE] Cody entity still on hold
> Entity pages for MG-048 / MG-051 / Cody remain to be written. The stakeholder meeting with Cody, Shawn, and Lee Martin is still pending. 9 stakeholder stubs were created 2026-04-16 based on available information; enrich as more context arrives.

---

## Sources

- [[claude-obsidian-ecosystem-research]] — 2026-04-08 | web research across 16+ repos | 8 wiki pages created
- [[GPS Baseline Results 2026-04-16]] — **authoritative measured baseline** | Fabric pipeline, 2 years, 2.67M breadcrumbs, grader deadhead 31.8%
- [[GPS Baseline Analysis]] — 2026-04-14 PDF | deadhead baseline (superseded by Fabric pipeline)
- [[Road Intelligence Platform Comprehensive Findings]] — 2026-04-14 PDF | Tier 1/2/3 opportunities (superseded)
- [[PRD Road Intelligence Platform]] — 2026-04-14 | 50 user stories, 6 personas, full architecture
- [[Road Intelligence Platform Refined Build Plan]] — 2026-04-14 | 5 sprints, 21 variables, 5-level stack
- [[Road Intelligence Platform Build Plan]] — 2026-04-06 | original plan (superseded by Refined)
- [[Financial Rebase]] — 2026-04-10 | UFA pricing + OEM telematics rebasing
- [[GPS Baseline Analysis Spec]] — 2026-04-10 | pipeline implementation spec
- [[GPS Pipeline Cowork Summary]] — 2026-04-10 | Fabric notebooks + lakehouse upload
- [[Old Project CLAUDE Instructions]] — 2026-04-14 | laptop project's CLAUDE.md
- [[Sent Email Data Requests 2026-04-14]] — 5 items to PW&U / GIS distribution
- [[UFA Price and Division Correction Thread 2026-04-09]] — fuel lock-in + division corrections
- [[Unit Fuel Rates Reconciliation]] — per-unit L/hr three-source cross-validation
- [[Baltimore County Fleet Telematics]] — 2013 | GPS dispatch for public works, $354K/6mo
- [[CMU Snow Plow Routing]] — academic | constraint programming CARP, 3-156% shorter routes
- [[UK Winter Road Maintenance RL]] — 2026 | RL + VRP for salt spreading
- [[TAC Canadian Gravel Road Survey]] — 2018 | 97 municipalities, 40,000 km gravel

---

## Questions

- [[How does the LLM Wiki pattern work]] — how the pattern works and why it outperforms RAG at human scale (status: developing)
- [[Research Municipal Fleet Route Optimization Case Studies]] — no grader-specific case studies exist; CARP vs VRP is the key technical finding (status: developing)

---

## Comparisons

- [[Wiki vs RAG]] — when to use a wiki knowledge base versus RAG; verdict: wiki wins at <1000 pages
- [[claude-obsidian-ecosystem]] — feature matrix of 16+ Claude+Obsidian projects; where claude-obsidian wins and gaps

---

## Projects

- [[Road Intelligence Platform]] — Lethbridge County grader fleet optimization, $80K-$150K projected fully loaded savings (status: active)
  - **Tier 1**: [[Route Planner]] | [[Spare Coordination]] | [[MG-048 Investigation]]
  - **Tier 2**: [[Division 1 Depot Staging]] | [[Demand-Driven Scheduling]] | [[Dust Control Coordination]]
  - **Dashboard**: [[Fleet Efficiency Dashboard]]
  - **Tier 3**: [[Weather-Responsive Scheduling]] | [[Grader Performance Score]] | [[Treatment Optimization]]
- [[Bank Reconciliation App]] — Lethbridge County (status: planning)
- [[Databricks Platform Implementation]] — Lethbridge County (status: planning)
- [[ERP Migration RFP]] — Lethbridge County (status: planning)
- [[SharePoint Migration]] — Lethbridge County (status: planning)

---

## Domains

<!-- Add domain entries here after scaffold -->
