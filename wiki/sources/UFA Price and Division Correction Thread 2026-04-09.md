---
type: source
title: "UFA Price and Division Correction Thread 2026-04-09"
source_type: historical email thread
author: "Multiple (Tony, Shawn, Hailey, Tyler)"
date_published: 2026-04-09
raw_file: ".raw/projects/road-intelligence-platform/historical/2026-04-09-to-10-ufa-and-division-thread.md"
created: 2026-04-16
updated: 2026-04-16
tags:
  - source
  - road-intelligence-platform
  - historical
  - email-thread
  - fuel
  - division-assignments
  - corrections
status: historical
related:
  - "[[Road Intelligence Platform]]"
  - "[[Unit Fuel Rates Reconciliation]]"
  - "[[Shawn Ogertschnig]]"
  - "[[Hailey Pinksen]]"
  - "[[Sean MacRae]]"
  - "[[Tyler Reiter]]"
  - "[[Ryan Thomson]]"
---

# Source: UFA Price + Division Correction Thread (April 9-10, 2026)

**Subject**: UFA Fixed price / Re: UFA Fixed price
**Dates**: April 9-10, 2026
**Status**: Historical. Single reply-chain carrying two distinct decisions (UFA fuel lock-in + division assignment corrections).

## Summary

Thread started by Tyler Reiter (UFA Picture Butte) with a dyed-diesel price check. Shawn forwarded to Hailey, Ryan, and Tony confirming the lock-in would cover 75% of 2025 May-September usage for peak-season budget stability. Hailey asked about budget pressure. Tony's next-day reply turned the thread into a division assignment confirmation request (April 10, 8:18 AM), enumerating Titan's current labels. Shawn corrected: MG-046 is Div 2 (not Div 3, Titan label stale), MG-053 is Div 3 (no GPS), MG-042 and MG-052 are CAT 14M construction graders (no GPS by design).

## Pages Created or Enriched from This Source

- [[Road Intelligence Platform]] — UFA price detail, corrected division assignments, grader fleet roster (14 including 2 construction-only)
- [[Shawn Ogertschnig]] — title per signature (Manager, Public Operations); PRD said "Superintendent / Division Leads"
- [[Hailey Pinksen]] — new entity, internal, budget-aware (asked cost-pressure question on UFA lock-in)
- [[Sean MacRae]] — new entity, internal, on Tony's division-query distribution
- [[Tyler Reiter]] — new entity, UFA Picture Butte agent, external fuel-vendor contact
- [[Ryan Thomson]] — confirmed on both threads

## Key Facts

### UFA Fuel Lock-in (April 9, 2026)

| Fuel Type | Base (cents/L) | Gov't Tax | Total (cents/L) | Total ($/L) |
|---|---|---|---|---|
| Clear Diesel | 148.67 | 17.00 | 165.67 | $1.6567 |
| **Dyed Diesel** | 148.67 | **8.00** | **156.67** | **$1.5667** |

- Reference prices same day: Clear 162.19 cents/L, Dyed 153.19 cents/L
- **Coverage**: 75% of 2025 May-September usage
- **Purpose**: peak-season budget stability
- **Contract process**: 1-hour quote, Docusign required, 8-11 AM window
- **UFA vendor contact**: Tyler Reiter, UFA Picture Butte, 403-732-4224, Tyler.Reiter@agent.ufa.com

### Division Assignment Corrections (April 10, 2026)

| Division | Unit | Notes | Correction? |
|---|---|---|---|
| Div 1 | MG-051 | CAT 150 | OK |
| **Div 2** | **MG-046** | **CAT 150** | **Titan label said Div 3, stale** |
| **Div 3** | **MG-053** | **no GPS yet** | **Formally Div 3; earlier note "MG-053 replaced MG-044" was a Div 3 change** |
| Div 4 | MG-050 | JD 772GP | OK |
| Div 5 | MG-048 | JD 772GP | OK |
| Div 6 | MG-047 | JD 872GP | OK |
| Div 7 | MG-049 | JD 772GP (anomalous) | OK |
| Spares | MG-039, MG-041, MG-044 | | OK |
| Construction-only (no GPS by design) | **MG-042, MG-052** | **CAT 14M's** | **New info** |

### Downstream Implications

- Division-level fuel and deadhead aggregates using stale Titan labels are wrong for Div 2 and Div 3.
- MG-046's GPS and fuel data now correctly attributes to Div 2.
- Div 3 has **no GPS-equipped grader** (MG-053 carries no Titan). All Div 3 GPS aggregates should be null, not computed from MG-046 data.
- MG-042 and MG-052's absence from the grader baseline is by design (construction role), not a data quality problem. Update the 5-without-GPS narrative (was: MG-031, MG-042, MG-043, MG-045, MG-052, MG-053) to distinguish construction graders (MG-042, MG-052) from graders that simply lack GPS (MG-031, MG-043, MG-045, MG-053).

## Raw File

`.raw/projects/road-intelligence-platform/historical/2026-04-09-to-10-ufa-and-division-thread.md`
