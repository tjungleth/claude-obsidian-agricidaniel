---
type: concept
title: "Demand-Driven Scheduling"
complexity: intermediate
domain: "fleet operations"
aliases: []
created: 2026-04-15
updated: 2026-04-15
tags:
  - concept
  - road-intelligence-platform
  - scheduling
status: mature
related:
  - "[[Route Optimization]]"
  - "[[PyVRP]]"
  - "[[Deadhead Ratio]]"
  - "[[Road Intelligence Platform]]"
sources:
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Demand-Driven Scheduling

## Definition

Demand-driven scheduling replaces fixed-rotation grading schedules with priority-based grading frequency. Instead of cycling through all road segments equally on a set rotation, segments are assigned priority levels (High, Medium, Low) based on traffic volume, road condition, and maintenance need. The route planner then schedules grading weighted by these priorities: high-demand segments are graded more frequently, low-demand segments less.

## How It Works

The approach requires two components:

1. **A GIS priority layer**: each gravel road segment is classified into priority tiers based on usage, condition, and maintenance requirements. This layer must be built and maintained as a prerequisite (Report 2, recommendation #5).
2. **Priority-aware routing**: the [[PyVRP]] solver weights segment visits by priority level when generating daily routes, concentrating grading time on the roads that need it most.

Under fixed rotation, a grader cycles through its entire division on a predictable schedule regardless of demand. Under demand-driven scheduling, the grader responds to where maintenance is most needed each cycle.

## Why It Matters

Fixed rotation treats all road segments equally, which means high-traffic roads degrade between visits while low-traffic roads get graded before they need it. Demand-driven scheduling directs limited grading hours toward the highest-need segments, improving road quality per grading hour without adding fleet time.

The value is reported as a "productivity gain" rather than a specific dollar figure (Report 2, Tier 2), because the benefit manifests as better road conditions for the same fleet effort rather than as direct cost reduction. It compounds with [[Route Optimization]] and [[Facility Location|depot optimization]].

## Connections

- [[Route Optimization]] — demand-driven scheduling feeds priority-weighted segments into the route optimizer
- [[PyVRP]] — the solver that generates priority-aware daily routes
- [[Deadhead Ratio]] — demand-driven routes may also reduce deadhead by concentrating work in priority clusters

## Sources

- [[Road Intelligence Platform Comprehensive Findings]] — "Replace fixed rotation with priority-based grading frequency" (Tier 2 table); "The planner needs High/Medium/Low segment priority to generate demand-driven routes instead of fixed rotations" (recommendation #5)
