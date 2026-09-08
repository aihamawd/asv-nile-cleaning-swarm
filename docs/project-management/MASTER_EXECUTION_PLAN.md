# ASV Nile Cleaning Swarm — Master Execution Plan

**Project period:** August 2026 – June 2027  
**Repository:** `kagetsu2/asv-nile-cleaning-swarm`  
**Operating baseline:** 3–4 physical ASVs: one new-build vessel plus 2–3 inherited/legacy vessels where technically viable.

## Execution rules

1. GitHub Issues are the executable work items; milestone issues are parents and engineering tasks are sub-issues.
2. Requirements, design decisions, experiments, tests, failures and evidence retain permanent repository IDs (`REQ-###`, `ADR-###`, `EXP-###`, `TEST-###`, `FAIL-###`, `EVD-###`).
3. Evidence precedes design freeze. Major architecture, purchase and fabrication decisions require a traceable basis.
4. Simulation/bench work may proceed autonomously; physical fabrication, deployment and safety-critical actions require human approval and supervision.
5. Local vessel autonomy and safety remain onboard. The shore Fleet Manager issues mission-level tasks only.
6. The physical fleet target is 3–4 vessels, but engineering quality and repeatable evidence take priority over vessel count.

## Milestone gates

| ID | Milestone | Planned window | Gate output |
|---|---|---|---|
| M1 | Requirements & Legacy Vessel Characterisation | 24 Aug–30 Sep 2026 | Traceable requirements + verified legacy baseline |
| M2 | Fleet Mechanical Readiness | 15 Sep–15 Dec 2026 | Mechanically justified new-build/retrofit architecture |
| M3 | Electrical & Propulsion Integration | 20 Sep 2026–15 Jan 2027 | Safe, measured power/propulsion/electrical baseline |
| M4 | Single-Vessel Autonomous Navigation | 15 Oct 2026–15 Feb 2027 | Repeatable autonomous waypoint/coverage operation |
| M5 | Cleaning / Water-Hyacinth Handling Prototype | 20 Sep 2026–15 Feb 2027 | Evidence-based cutter/collection design freeze |
| M6 | Multi-Vessel Communication | 15 Jan–15 Mar 2027 | Stable common vessel interface and heartbeat behaviour |
| M7 | Cooperative Task Allocation | 15 Feb–15 Apr 2027 | Demonstrated shared task pool and cooperative coverage |
| M8 | Fault-Aware Reallocation Behaviour | 1 Mar–30 Apr 2027 | Demonstrated withdrawal/reallocation/recovery cases |
| M9 | Controlled Experimental Validation | 1 Apr–20 May 2027 | Quantified controlled test campaign |
| M10 | Representative Nile-Environment Validation | 10 May–5 Jun 2027 | Approved field-validation evidence package |
| M11 | Final Engineering Book, Report, Poster & Viva | 24 Aug 2026–20 Jun 2027 | Defensible final submission and reproducible repository |

## Dependency spine

`M1 → M2/M3 → M4/M5 → M6 → M7 → M8 → M9 → M10 → M11`

M2, M3, M4 and M5 intentionally overlap. Documentation and traceability under M11 run continuously rather than waiting until the end.

## Primary responsibility

- **Aiham:** electrical, control, embedded, autopilot/navigation, power, cutter electrical integration, system integration.
- **Omar:** mechanical, hull/structure, collection, cutter mechanics, fabrication.
- **Both:** requirements, ROS 2/high-level software, Fleet Manager, perception integration, tests, evidence, procurement, report and defence.

## Gate discipline

A milestone is complete only when its parent issue can be closed with:

- all required sub-issues complete or explicitly dispositioned;
- acceptance criteria met;
- evidence linked;
- unresolved failures/risks documented;
- downstream assumptions updated;
- no hidden physical action or unrecorded design change.
