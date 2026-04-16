---
type: source
title: "UK Winter Road Maintenance RL"
source_type: academic paper
author: "Xie, Xu, Beazley, Iida"
date_published: 2026-02-01
url: "https://arxiv.org/html/2602.24097"
confidence: high
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - academic
  - reinforcement-learning
  - winter-maintenance
  - multi-depot
status: current
related:
  - "[[Route Optimization]]"
  - "[[Facility Location]]"
  - "[[Road Intelligence Platform]]"
---

# Source: UK Winter Road Maintenance RL

## Summary

A 2026 paper applying reinforcement learning to large-scale winter road salt-spreading optimization on UK strategic motorways. Uses a bi-level framework: a PPO (Proximal Policy Optimization) agent assigns road segments to depots at the upper level, while a constraint-aware nearest-neighbor heuristic solves vehicle routing within each cluster at the lower level.

## Scale

- **Network**: 37,007 nodes, 71,505 directed edges (57.85 km), 1,515 treatment edges (543.5 km, 1,208.7 lane-km)
- **Depots**: 3 (Misterton, Pytchley, Rothersthorpe)
- **Vehicle capacity**: 166 km per lane; max route duration 120 min; max travel distance 630 km

## Key Results

Compared to KDTree + nearest-neighbor baseline:

| Metric | Baseline | RL-Optimized | Improvement |
|---|---|---|---|
| Makespan (max route time) | 122.14 min | 118.81 min | 2.7% |
| CO2 emissions | 3,386.63 kg | 3,220.95 kg | 4.9% |
| Vehicle utilization | 20 vehicles | 28 vehicles | Better constraint compliance |

## Relevance to Road Intelligence Platform

Two direct parallels:
1. **Depot-to-segment allocation**: the PPO agent's job (assigning road segments to depots) mirrors the RIP's division-to-camp assignment problem. The RL approach could inform future [[Facility Location]] work.
2. **Multi-objective optimization**: minimizing both makespan and emissions. The RIP currently optimizes for [[Deadhead Ratio]] (single objective); future iterations could add road integrity or emissions.

## Raw File

Web source: [arXiv](https://arxiv.org/html/2602.24097)
