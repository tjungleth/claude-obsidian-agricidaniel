---
type: concept
title: "Route Optimization"
complexity: intermediate
domain: "operations research"
aliases:
  - "route planning"
  - "vehicle routing"
created: 2026-04-15
updated: 2026-04-15
tags:
  - concept
  - road-intelligence-platform
  - operations-research
status: mature
related:
  - "[[Deadhead Ratio]]"
  - "[[PyVRP]]"
  - "[[Facility Location]]"
  - "[[Demand-Driven Scheduling]]"
  - "[[Road Intelligence Platform]]"
sources:
  - "[[GPS Baseline Analysis]]"
  - "[[Road Intelligence Platform Comprehensive Findings]]"
---

# Route Optimization

## Definition

Route optimization is the class of problems where one or more vehicles must visit a set of locations in a sequence that minimizes an objective (total distance, travel time, fuel consumption) subject to constraints (vehicle count, time windows, capacity, start/end depots).

In the Lethbridge County context, the problem is: given a set of gravel road segments that need grading, a grader starting from its camp, and a return-to-camp requirement, find the daily grading sequence that minimizes [[Deadhead Ratio|deadhead travel]].

## How It Works

A route optimization solver takes three inputs:

1. **Locations to visit**: the set of road segments scheduled for grading that day.
2. **Cost matrix**: the travel time or distance between every pair of locations (and between each location and the depot). For Lethbridge County, this is built from the road network, not straight-line distance.
3. **Constraints**: start depot (grader camp), end depot (same camp), shift length, equipment limitations.

The solver produces a sequenced route that minimizes total deadhead travel. The specific solver chosen for the [[Road Intelligence Platform]] is [[PyVRP]], a Python implementation of modern Vehicle Routing Problem heuristics.

## Why It Matters

Manual route selection by operators relies on experience and local knowledge, which produces workable but sub-optimal sequences. The 24.9% fleet [[Deadhead Ratio|deadhead ratio]] is the measurable gap between current routing and what a solver can achieve.

Route optimization is the single highest-value lever in the Road Intelligence Platform, estimated at $15,000 to $35,000 per year in fuel savings and $40,000 to $90,000 in [[Fully Loaded Hard Savings|fully loaded terms]] (Report 2, Tier 1). It targets the May to October grading season, where demand is highest and absolute savings per shift are greatest.

## Examples

- **Traveling Salesman Problem (TSP)**: one vehicle, visit all locations, minimize distance. The simplest form.
- **Vehicle Routing Problem (VRP)**: multiple vehicles, each starting from a depot, collectively serving all locations.
- **Lethbridge County application**: one grader per division, starting from its camp, serving that day's priority road segments, returning to camp. Solved via [[PyVRP]] with a road-network cost matrix.

## Connections

- [[PyVRP]] — the solver implementation
- [[Deadhead Ratio]] — the metric route optimization directly reduces
- [[Facility Location]] — depot placement determines the starting point that route optimization works from
- [[Demand-Driven Scheduling]] — determines which segments enter the daily route
- [[Fully Loaded Hard Savings]] — translates reduced deadhead into dollar savings

## Sources

- [[GPS Baseline Analysis]]
- [[Road Intelligence Platform Comprehensive Findings]]
