---
type: workstream
title: "Weather-Responsive Scheduling"
status: concept
tier: 3
parent: "[[Road Intelligence Platform]]"
owner: "Tony Jung"
timeline: "Phase 2"
created: 2026-04-16
updated: 2026-04-16
tags:
  - workstream
  - road-intelligence-platform
  - tier-3
related:
  - "[[Route Planner]]"
  - "[[Demand-Driven Scheduling]]"
  - "[[Deadhead Ratio]]"
sources:
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Weather-Responsive Scheduling

> [!NOTE] Concept stage
> This workstream is identified in the Tier 3 assessment but has no active sprint work. It compounds on top of Tier 1 and Tier 2 results.

## Summary

Weather-responsive scheduling adjusts grading timing based on weather conditions: grade after rain when the road surface is moist and pliable, defer during extended dry spells when grading produces a less durable result.

The value is not measured in fuel savings but in **road integrity duration**: a road graded under the right moisture conditions maintains its surface longer between maintenance cycles. This is the gold standard KPI for grading quality. Over multiple seasons, weather-responsive scheduling compounds: each grading pass lasts longer, reducing the total number of passes needed per year.

Estimated value: longer road integrity, compounding over seasons (Report 2, Tier 3). No dollar figure assigned.

## Mechanism

1. Incorporate historical weather data (precipitation, temperature, soil moisture) into the [[Route Planner]] as a scheduling input.
2. When conditions are favorable (post-rain, adequate soil moisture), prioritize grading on segments that benefit most from wet-condition grading.
3. When conditions are unfavorable (extended dry spell, frozen ground), defer non-urgent grading or shift to inspection/travel-only schedules.

This extends [[concepts/Demand-Driven Scheduling|Demand-Driven Scheduling]] from priority-based to condition-and-priority-based routing.

## Connection to Road Integrity

Grading effectiveness depends on moisture. A gravel road graded when moist compacts better, sheds water more evenly, and holds its shape longer. A road graded when dry produces loose material that ruts and washboards faster. Weather-responsive scheduling targets grading to the window when the work produces the most durable result.

## Timeline

- **Phase 2** (post-initial grading season): requires a season of correlated weather + grading + road condition data to calibrate the model

## Sources

- [[Road Intelligence Platform Comprehensive Findings]] — "Grade after rain and defer during dry spells for better durability" (Tier 3 mechanism); estimated value: longer road integrity, compounds over seasons
