---
type: synthesis
title: "Research: Municipal Fleet Route Optimization Case Studies"
created: 2026-04-16
updated: 2026-04-16
tags:
  - research
  - fleet-optimization
  - case-studies
  - road-intelligence-platform
status: developing
related:
  - "[[Road Intelligence Platform]]"
  - "[[Route Optimization]]"
  - "[[Capacitated Arc Routing]]"
  - "[[PyVRP]]"
  - "[[Deadhead Ratio]]"
  - "[[Facility Location]]"
  - "[[Demand-Driven Scheduling]]"
sources:
  - "[[Baltimore County Fleet Telematics]]"
  - "[[CMU Snow Plow Routing]]"
  - "[[UK Winter Road Maintenance RL]]"
  - "[[TAC Canadian Gravel Road Survey]]"
---

# Research: Municipal Fleet Route Optimization Case Studies

## Overview

Web research across academic papers, trade publications, and government case studies to find precedents for the [[Road Intelligence Platform]]'s approach to grader fleet optimization. The research found strong case studies for GPS-based fleet optimization and snow plow routing, but **no published case study specifically addresses motor grader route optimization for gravel road maintenance**. The RIP appears to be breaking new ground.

## Key Findings

### 1. GPS-based fleet tracking delivers 25-40% fuel savings in municipal fleets

Industry benchmarks consistently show that municipal fleets implementing GPS tracking and route optimization achieve 25-40% fuel cost reductions and 30-35% decreases in overtime within the first six months. Government fleets waste an average of 25% of their fuel budget through inefficient routing alone. (Source: multiple trade publications)

### 2. Baltimore County: $354K savings in 6 months from GPS dispatch

The closest published case study to Lethbridge County's situation. Baltimore County, MD deployed GPS-based dispatch for public works and snow operations, resulting in 165,000 fewer miles driven, $79,000 fuel savings, and $354,000 total productivity savings in six months. Equipment costs were recouped in 3 months. (Source: [[Baltimore County Fleet Telematics]])

### 3. Grader routing is an arc routing problem, not a node routing problem

The most significant technical finding. Road maintenance operations (grading, plowing, sweeping) require vehicles to **traverse road segments** (arcs), not **visit point locations** (nodes). This makes grader routing a [[Capacitated Arc Routing]] problem, not a standard VRP. The [[Route Planner]]'s use of [[PyVRP]] with arc-to-node transformation is valid but approximate. CMU research showed that native CARP solutions produced routes 3% to 156% shorter than commercial VRP-based software. (Source: [[CMU Snow Plow Routing]])

### 4. Reinforcement learning shows promise for depot-to-segment allocation

A 2026 UK study used PPO (Proximal Policy Optimization) to assign road segments to depots, achieving 2.7% makespan reduction and 4.9% emissions reduction over static heuristic baselines. The depot-allocation problem mirrors the RIP's division-to-camp assignment. (Source: [[UK Winter Road Maintenance RL]])

### 5. 60% of Canada's public roads are unpaved, but no optimization case studies exist

A 2018 TAC survey of 97 Canadian municipalities managing ~40,000 km of gravel roads found that most lack a comprehensive gravel road management system. The survey recommends exactly what the RIP is building: data-driven condition assessment, prioritization, and budget planning. No surveyed municipality reported implementing GPS-based route optimization for graders. (Source: [[TAC Canadian Gravel Road Survey]])

### 6. Industry benchmarks for idle time and deadhead

Heavy equipment fleets typically find 20-30% of engine hours are spent idling. The RIP's **measured 31.8% grader [[Deadhead Ratio]]** (per [[GPS Baseline Results 2026-04-16]], superseding the April 14 PDF's 24.9% estimate) is slightly above the typical range, confirming the fleet sits at the upper end of the optimization opportunity. Fleet-wide (including trucks) the measured ratio is 43.1%.

## Key Concepts

- [[Capacitated Arc Routing]] (CARP): the problem class that best models grader routing (traverse arcs, not visit nodes)
- [[Route Optimization]]: the broader discipline; VRP is one formulation, CARP is another
- [[Facility Location]]: depot-to-demand alignment; the UK RL study offers an RL-based approach

## Contradictions

None found between sources. The case studies and academic papers are consistent: GPS visibility + route optimization = measurable savings. The main gap is the absence of grader-specific evidence, not conflicting evidence.

## Open Questions

1. **CARP vs VRP for the Route Planner**: would a native CARP solver produce materially better routes than the current PyVRP arc-to-node approach? The CMU paper's 3-156% range is wide. Testing with Lethbridge County data would answer this.
2. **No grader-specific benchmarks**: all case studies are snow plow, transit, or general fleet. The RIP's **measured 31.8% grader deadhead baseline** (per [[GPS Baseline Results 2026-04-16]]) may be the first published grader-specific measurement in a Canadian municipality.
3. **Road integrity as an optimization objective**: no case study optimizes for road durability after grading (Tony's gold standard KPI). This is genuinely novel and would be publishable if measured.
4. **Scalability of RL approaches**: the UK study's PPO agent worked on 1,515 treatment edges. Lethbridge County has 3,097 road segments. Would the approach scale?
5. **Calgary fleet management**: AssetWorks case study with City of Calgary exists but covers fleet/fuel management, not route optimization. Worth investigating for operational parallels.

## Sources

- [[Baltimore County Fleet Telematics]]: Government Fleet, 2013
- [[CMU Snow Plow Routing]]: van Hoeve et al., Carnegie Mellon University
- [[UK Winter Road Maintenance RL]]: Xie et al., arXiv 2602.24097, 2026
- [[TAC Canadian Gravel Road Survey]]: Rashedi et al., TAC Conference, 2018
