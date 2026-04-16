---
type: workstream
title: "Demand-Driven Scheduling"
status: planning
tier: 2
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "Sprint 4 (June 2026)"
created: 2026-04-15
updated: 2026-04-15
tags:
  - workstream
  - road-intelligence-platform
  - tier-2
related:
  - "[[concepts/Demand-Driven Scheduling]]"
  - "[[Route Planner]]"
  - "[[PyVRP]]"
sources:
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Demand-Driven Scheduling (Workstream)

## Summary

This workstream replaces the current fixed-rotation grading schedule with priority-based grading frequency. Roads that carry more traffic or degrade faster get graded more often; low-demand roads get graded less. The concept is defined in [[concepts/Demand-Driven Scheduling|Demand-Driven Scheduling]].

Estimated value: productivity gain (Report 2, Tier 2). No specific dollar figure is attributed because the benefit manifests as better road conditions for the same fleet effort rather than direct fuel savings. Its value compounds with the [[Route Planner]]: demand-driven inputs make optimized routes target the right roads, not just the nearest ones.

## Mechanism

1. **Build the GIS priority layer**: classify every gravel segment as High, Medium, or Low priority based on traffic volume, road condition, and maintenance need (Report 2, recommendation #5).
2. **Feed priorities into the Route Planner**: the [[PyVRP]] solver weights segment visits by priority when generating daily routes. High-priority segments appear more frequently in the grading plan.
3. **Replace the fixed rotation**: operators follow priority-weighted plans instead of cycling through all segments equally.

## Prerequisites

The GIS priority layer is the critical dependency. Without High/Medium/Low classification per segment, the Route Planner falls back to treating all segments equally (still valuable for deadhead reduction, but missing the demand-weighting benefit).

Report 2, recommendation #5: "The planner needs High/Medium/Low segment priority to generate demand-driven routes instead of fixed rotations."

## Timeline

- **Target**: Sprint 4 (June 2026)
- **Dependency**: GIS priority layer must be requested and built before demand-driven routing is possible

## Next Actions

- [ ] Request GIS priority layer from GIS team (Report 2, recommendation #5)
- [ ] Define priority criteria (traffic counts, road condition scores, maintenance history)
- [ ] Integrate priority layer into Route Planner solver inputs

## Sources

- [[Road Intelligence Platform Comprehensive Findings]] — "Replace fixed rotation with priority-based grading frequency" (Tier 2); "The planner needs High/Medium/Low segment priority to generate demand-driven routes instead of fixed rotations" (recommendation #5)
