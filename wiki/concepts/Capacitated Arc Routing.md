---
type: concept
title: "Capacitated Arc Routing"
complexity: advanced
domain: "operations research"
aliases:
  - "CARP"
  - "arc routing"
created: 2026-04-16
updated: 2026-04-16
tags:
  - concept
  - road-intelligence-platform
  - operations-research
status: mature
related:
  - "[[Route Optimization]]"
  - "[[PyVRP]]"
  - "[[Road Intelligence Platform]]"
sources:
  - "[[CMU Snow Plow Routing]]"
  - "[[UK Winter Road Maintenance RL]]"
---

# Capacitated Arc Routing

## Definition

The Capacitated Arc Routing Problem (CARP) is the arc-based counterpart to the [[Route Optimization|Vehicle Routing Problem (VRP)]]. Where VRP finds optimal routes to visit **locations** (nodes), CARP finds optimal routes to **traverse road segments** (arcs). Each arc has a service demand (e.g., km of road to grade), each vehicle has a capacity constraint (e.g., shift duration, fuel), and the objective is to minimize total travel cost while ensuring every required arc is serviced exactly once.

## Why It Matters for Grader Routing

Grader route optimization is fundamentally an arc routing problem:
- The "demand" is a road segment that needs grading, not a point location that needs visiting.
- The grader must traverse the full length of each segment, not just touch an endpoint.
- Travel between segments (deadhead) is the waste to minimize; travel along segments (grading) is the productive work.

Standard VRP solvers like [[PyVRP]] solve node-based problems. Applying them to arc-based problems requires an **arc-to-node transformation**: representing each road segment as a node (typically at its midpoint or centroid) and building a node-to-node distance matrix. This is the approach the [[Route Planner]] uses. It works, but it is an approximation. Pure CARP formulations can produce tighter solutions because they model the actual traversal geometry.

## How It Works

A CARP solver takes:
1. **A graph** of nodes and edges (the road network)
2. **Required edges** (road segments that need service, with demand quantities)
3. **Vehicle fleet** with capacity constraints (shift hours, fuel)
4. **Depot(s)** where vehicles start and end

The solver finds a set of routes that covers all required edges while minimizing total deadhead travel. Each required edge is assigned to exactly one vehicle route.

## CARP vs VRP

| Aspect | VRP (node routing) | CARP (arc routing) |
|---|---|---|
| Demand location | At nodes (points) | Along arcs (road segments) |
| Service action | Visit the node | Traverse the arc |
| Typical applications | Delivery, pickup, field service | Snow plowing, grading, street sweeping, waste collection |
| Solver examples | [[PyVRP]], OR-Tools | Hexaly CARP, custom heuristics |
| RIP approach | Arc-to-node transformation | Native formulation (not yet implemented) |

## Practical Implications for the Road Intelligence Platform

The current [[Route Planner]] uses [[PyVRP]] with an arc-to-node transformation. This is standard and produces good results. A future improvement path would be to evaluate a native CARP solver to see if it produces materially shorter routes. The CMU snow plow research ([[CMU Snow Plow Routing]]) showed constraint programming CARP routes were 3% to 156% shorter than a city's commercial routing software.

## Sources

- [[CMU Snow Plow Routing]] — constraint programming CARP approach, 3-156% improvement over commercial software
- [[UK Winter Road Maintenance RL]] — RL-based arc routing for salt spreading, multi-depot allocation
- DIMACS CARP benchmark: http://dimacs.rutgers.edu/programs/challenge/vrp/carp/
