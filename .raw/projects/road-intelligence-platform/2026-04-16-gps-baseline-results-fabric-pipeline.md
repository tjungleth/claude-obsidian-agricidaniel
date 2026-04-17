---
type: pipeline-results
project: Road Intelligence Platform
source_system: Microsoft Fabric (finance_fabric workspace)
notebooks: ["10_bronze_gps", "11_silver_gps_segments", "12_gold_grading_activity"]
run_date: 2026-04-16
data_range: 2024-03-06 to 2026-04-09
captured: 2026-04-16
status: current
supersedes:
  - ".raw/projects/road-intelligence-platform/2026-04-14-gps-baseline-analysis-report.pdf"
  - ".raw/projects/road-intelligence-platform/2026-04-14-road-intelligence-platform-comprehensive-findings.pdf"
  - "Estimates in PRD / REFINED_BUILD_PLAN / FINANCIAL_REBASE / GPS_BASELINE_ANALYSIS_SPEC"
---

# GPS Baseline Results — Fabric Pipeline Output (April 16, 2026)

All three GPS notebooks (`10_bronze_gps`, `11_silver_gps_segments`, `12_gold_grading_activity`) completed in the Fabric `finance_fabric` workspace on 2026-04-16. These are measured numbers from two full years of Titan GPS data and supersede all prior estimates in the PRD, Refined Build Plan, Financial Rebase, GPS Baseline Analysis Spec, and the April 14 PDFs.

## Bronze (`10_bronze_gps`)

- 8,798 JSON files loaded from nested folders (`raw_dumps/YYYY-MM-DD/{00-23}.json`)
- 3,070,155 raw breadcrumbs, 2,666,866 after dedup
- 38 devices total: 9 graders, 2 spare GPS, 6 field tractors, 20 trucks, 1 blade
- Date range: 2024-03-06 to 2026-04-09 (2 full years)
- Quality filters: 15,415 bad coords / 796 outside bounds / 111,460 excluded events / 334,324 `isCurrLoc` filtered

## Silver (`11_silver_gps_segments`)

- 2,623,732 classified breadcrumbs after quality filters
- Activity: 1,268,093 GRADING / 756,263 DEADHEADING / 599,376 IDLE
- 5,653 shifts detected
- **Fleet deadhead ratio: 43.1%** (all 38 devices)
- Fleet deadhead fuel cost: $271,180 over 2-year period

## Grader-Specific Results

| Unit | Division | Shifts | Grading Hrs | Deadhead Hrs | Deadhead % | Deadhead $ | Grading km |
|---|---|---|---|---|---|---|---|
| MG-039 | Spare | 141 | 629 | 287 | 31.4% | $6,317 | 4,194 |
| MG-041 | Spare | 95 | 365 | 85 | 18.9% | $1,876 | 2,337 |
| MG-044 | Spare (rotated out) | 211 | 1,266 | 386 | 23.4% | $8,483 | 8,881 |
| MG-046 | Div 2 | 203 | 1,974 | 1,471 | 42.7% | $32,326 | 6,225 |
| MG-047 | Div 6 | 212 | 1,505 | 245 | 14.0% | $5,393 | 9,085 |
| MG-048 | Div 5 | 169 | 681 | 338 | 33.2% | $7,430 | 6,127 |
| MG-049 | Div 7 | 114 | 579 | 292 | 33.5% | $6,425 | 4,262 |
| MG-050 | Div 4 | 224 | 1,210 | 450 | 27.1% | $9,884 | 8,781 |
| MG-051 | Div 1 | 235 | 862 | 667 | 43.6% | $14,650 | 5,946 |
| **GRADER TOTAL** | | **1,604** | **9,071** | **4,221** | **31.8%** | **$92,784** | **55,837** |

- **Grader deadhead ratio: 31.8%** (~$46K/year over the 2-year period)
- **Best**: MG-047 Div 6 at 14.0% (compact territory)
- **Worst**: MG-051 Div 1 at 43.6%, MG-046 Div 2 at 42.7% (largest territories)

## Savings Recalculated (measured)

- 30% grader deadhead reduction: ~$14,000/yr
- 40% grader deadhead reduction: ~$18,500/yr
- Full fleet (trucks included) at 30-40%: $40,000-$55,000/yr

## Gold Tables

- `gold_fact_grading_activity`: 5,653 rows (shift-level)
- `gold_fact_segment_visits`: 4,204 rows (daily grading per unit)
- `gold_dim_road_segment`: not yet built. Blocked on shapefile upload (LC_Roads, LC_Grader_Divisions, LC_Grader_Camps still on local). After upload, this dim unlocks snap-to-segment joins.

## Authoritative Fleet Mapping (from Shawn Ogertschnig)

Corrected via Shawn's April 10 email:

| Unit | Division | Make/Model | GPS? | Notes |
|---|---|---|---|---|
| MG-051 | Div 1 | CAT 150 | Yes | |
| MG-046 | Div 2 | CAT 150 | Yes | Titan label says "Div 3" (stale) |
| MG-053 | Div 3 | unknown | No | Replaced MG-044 ~3 weeks ago |
| MG-050 | Div 4 | JD 772GP | Yes | |
| MG-048 | Div 5 | JD 772GP | Yes | |
| MG-047 | Div 6 | JD 872GP | Yes | |
| MG-049 | Div 7 | JD 772GP | Yes | |
| MG-039 | Spare | CAT 140M3 | Yes | |
| MG-041 | Spare | JD 772GP | Yes | |
| MG-044 | Spare | JD 872GP | Yes | Rotated out, replaced by MG-053 |
| MG-042 | Construction | CAT 14M | No (by design) | |
| MG-052 | Construction | CAT 14-15 | No (by design) | |
| MG-043 | ? | JD 872GP | No Titan, has JD telematics | |
| MG-045 | ? | JD 872GP | No Titan, has JD telematics | |

Fuel cost: $1.57/L dyed diesel (UFA lock-in, Tyler Reiter UFA Picture Butte, confirmed April 9, 2026. Clear $1.6567/L, dyed $1.5667/L. Covers 75% of 2025 May-September usage.)

## Per-Unit Fuel Rates (three-source cross-validation)

| Unit | Division | Make | CAT Telem L/hr | JD Fill-up L/hr | JD Telem L/hr | Best Rate |
|---|---|---|---|---|---|---|
| MG-039 | Spare | CAT | 22.8 | - | - | 22.8 |
| MG-041 | Spare | JD | - | - | 17.8 | 17.8 |
| MG-042 | Construction | CAT | 19.1 | - | - | 19.1 |
| MG-043 | ? | JD | - | - | 15.7 | 15.7 |
| MG-044 | Spare | JD | - | 23.1 | 19.7 | 23.1 |
| MG-045 | ? | JD | - | - | 15.8 | 15.8 |
| MG-046 | Div 2 | CAT | 21.3 | 20.9 | - | 20.9 |
| MG-047 | Div 6 | JD | - | 20.5 | 17.0 | 20.5 |
| MG-048 | Div 5 | JD | - | 23.6 | 20.1 | 23.6 |
| MG-049 | Div 7 | JD | - | 21.8 | - | 21.8 |
| MG-050 | Div 4 | JD | - | 18.9 | 16.5 | 18.9 |
| MG-051 | Div 1 | CAT | 18.2 | 20.0 | - | 20.0 |
| MG-052 | Construction | CAT | 20.4 | - | - | 20.4 |

Fleet average: ~21.0 L/hr (pipeline used 22.0, within 5%, fuel cost numbers valid).

Cross-validation highlights:
- MG-046: CAT 21.3 vs JD fill-up 20.9 = within 2%, strong agreement
- MG-051: CAT 18.2 vs JD fill-up 20.0 = 10% spread, use JD fill-up as more granular
- JD telematics consistently reads 2-4 L/hr lower than JD fill-ups (likely excludes idle fuel); fill-ups are the better ground truth

## Idle Percentages

JD (from telematics):
- MG-041 24.2%, MG-043 24.1%, MG-044 17.7%, MG-045 26.5%, MG-047 17.5%, MG-048 26.6% (highest active divisional grader), MG-050 18.8%

CAT (from telematics):
- MG-039 12.9%, MG-046 13.2%, MG-051 13.7%. Construction: MG-042 29.9%, MG-052 28.0% (expected)

## Ground Truth Validation (March 2026)

Shawn Ogertschnig sent March 2026 grading maps from all 7 division operators (scanned PDFs, handwritten grading dates, forwarded via Lee Martin). Monthly mileages:

| Division | GPS-tracked Unit | March 2026 Miles (operator-reported) |
|---|---|---|
| Div 1 | MG-051 | 134 mi |
| Div 2 | **MG-046** | 131 mi |
| Div 3 | MG-053 (no GPS) | 116 mi |
| Div 4 | MG-050 | 72 mi |
| Div 5 | MG-048 | 49 mi |
| Div 6 | MG-047 | 76 mi |
| Div 7 | MG-049 | 99 mi |

Div 4 notes include: Class 1: 32, Class 2: 10, Class 3: 12, haul routes 16, soft spots 8, blade changes 3,615.

With the division correction, Div 2 (131 miles) maps to MG-046, not MG-053.

## Superseded Estimates Catalog

| Previous claim | Source | Measured |
|---|---|---|
| "24.9% fleet deadhead" | GPS Baseline Analysis PDF | **43.1% fleet, 31.8% graders** (large correction) |
| "estimated 20-30% deadhead" | build plans | **31.8% graders** |
| "$108K-$163K addressable" | build plans | **~$46K/yr graders** (from $92,784 over 2 yrs) |
| "$65K-$75K Year 1 savings" | build plans | **$14-19K/yr graders, $40-55K/yr full fleet** |
| "$140K-$165K/yr fully loaded" | GPS Baseline Analysis PDF | **~$115K/yr fully loaded** (2.5x $46K) |
| "1.86M records" / "1.52M breadcrumbs" | CLAUDE.md / spec | **2,666,866 after dedup** |
| "367 days" | CLAUDE.md / spec | **2 full years (2024-03-06 to 2026-04-09)** |
| "$544K annual grader fuel" | original build plan | already rebased to $375K, confirmed |
| "9 of 14 graders" | PDFs | confirmed with Shawn's authoritative mapping |
| "flat 22 L/hr grading" | pipeline default | **per-unit 15.7 to 23.6, fleet avg 21.0** |
| "MG-046 Div 3" | PDFs + Titan labels | **MG-046 is Div 2** |
| "5 graders without GPS" | old CLAUDE.md | Reclassify: MG-042/MG-052 construction-only (no GPS by design), MG-053 Div 3, MG-043/MG-045 JD telematics only, MG-031 unknown |

## Additional Context

- **Ryan Thomson** sent email (April 16) backing Tony's work, emphasizing fuel cost urgency, asking team for cooperation. Aaron Craig CC'd.
- **Aaron Craig** (last name confirmed) still owes the road priority GIS layer (High/Medium/Low classification joinable by RS_GIS_ID). Critical path for Route Planner.
- **Lee Martin** (last name confirmed) forwarded the grading maps to Shawn. Separate person from Cody and Cole Beck.
- **Shapefiles** (LC_Roads, LC_Grader_Divisions, LC_Grader_Camps) on local machine, not yet in Fabric lakehouse. `gold_dim_road_segment` awaits this upload.
- **Shawn's title**: Manager, Public Operations (per signature, not "Superintendent" as in PRD).
- **Hailey Pinksen** on the UFA fuel price thread, asked about budget pressure from lock-in vs budget rates.
- **Tyler Reiter**: UFA Picture Butte rep, provided lock-in pricing, 403-732-4224.
