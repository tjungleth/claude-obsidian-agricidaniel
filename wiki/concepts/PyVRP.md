---
type: concept
title: "PyVRP"
complexity: advanced
domain: "operations research"
aliases:
  - "pyvrp"
created: 2026-04-15
updated: 2026-04-15
tags:
  - concept
  - road-intelligence-platform
  - operations-research
  - tooling
status: mature
related:
  - "[[Route Optimization]]"
  - "[[Deadhead Ratio]]"
  - "[[Road Intelligence Platform]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# PyVRP

## Definition

PyVRP is an open-source Python library for solving Vehicle Routing Problems (VRP). It implements the Hybrid Genetic Search (HGS) metaheuristic, which combines genetic algorithm population management with local search improvement.

In the [[Road Intelligence Platform]], PyVRP is the solver behind the Route Planner workstream: it takes a daily set of road segments, a road-network cost matrix, and grader camp locations, and produces fuel-minimized grading sequences.

## How It Works

The solver takes:

1. **A cost matrix**: travel distances (or times) between every pair of road segments and between segments and depots. For Lethbridge County, this is computed from the actual road network, not Euclidean distance.
2. **Depot locations**: grader camps where operators start and end their shifts.
3. **Demand nodes**: the set of road segments scheduled for grading that day.
4. **Constraints**: shift duration, single-vehicle-per-route (one grader per division), return-to-depot requirement.

HGS explores a population of candidate solutions, breeding and improving them over generations until converging on a near-optimal route sequence. The result is a daily route plan per grader that minimizes total [[Deadhead Ratio|deadhead travel]].

## Why It Matters

PyVRP is the mechanism through which route optimization delivers its projected $15,000 to $35,000 per year in fuel savings ($40,000 to $90,000 [[Fully Loaded Hard Savings|fully loaded]]). It replaces experience-based manual sequencing with algorithmic optimization that can adapt daily to changing segment priorities, weather, and equipment availability.

## Connections

- [[Route Optimization]] — the problem class PyVRP solves
- [[Deadhead Ratio]] — the metric the solver directly optimizes against
- [[Demand-Driven Scheduling]] — determines which segments feed into the solver each day
- [[Facility Location]] — depot placement sets the start/end points the solver works from

## Sources

- [[GPS Baseline Analysis]] — "The PyVRP solver with the road network cost matrix will produce routes that directly reduce the 24.9% deadhead ratio" (recommendation #3)
- [[Road Intelligence Platform Comprehensive Findings]] — "Route optimization (PyVRP) ... Optimized daily route sequencing within each division, minimizing deadhead travel" (Tier 1 table)
