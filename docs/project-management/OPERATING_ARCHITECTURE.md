# Final-Year Project Operating Architecture — v3

**Project:** Cooperative Autonomous Surface Vehicle Swarm for Nile Surface Cleaning  
**Students:** Aiham Moustafa Awad · Omar Mohamed Bakr  
**Operational repository:** `aihamawd/asv-nile-cleaning-swarm`  
**Rebaseline:** 28 September 2026

## 1. Source of truth

GitHub is the operational engineering source of truth. Issues are executable work; the GitHub Project is the execution view; repository files are controlled engineering records; large/raw evidence may be held externally only when indexed from GitHub.

Do not introduce a second independent task/schedule database.

## 2. Engineering baseline

The physical target is 3–4 heterogeneous ASVs:

- Robot A new fiberglass build;
- Robot B inherited MSA cleaning ASV;
- Robot C repurposed legacy platform;
- Robot D optional.

Common interfaces are standardized; hardware is role-specific where appropriate.

## 3. Controller and communications baseline

Per main ASV:

- high-level Linux SBC: ROS 2, perception, mission, decentralized fleet agent, advisory ML, logging;
- STM32/autopilot-class low-level controller: navigation/control, hard safety, auxiliaries, interlocks;
- SX1262 transceiver directly on STM32 for compact peer fleet traffic;
- GNSS + IMU + compass minimum navigation set.

No ESP32 requirement. No mandatory shore Fleet Manager.

## 4. Fleet execution model

Each Pi/SBC runs the same decentralized fleet agent.

Baseline behavior:

- replicated mission/task view;
- robot capability/health/energy/load state;
- CBBA-style bidding and ownership;
- lease/epoch timeout and stale-state rejection;
- bounded behavior under communication partition;
- temporary leader only for a local coalition/service sequence;
- distributed dock token;
- local Hold/RTL/return and RC override independent of fleet consensus.

The operator laptop is an optional HMI/diagnostic station.

## 5. Permanent IDs

`REQ` · `SYS` · `ADR` · `MECH` · `ELEC` · `EMB` · `SW` · `NAV` · `VIS` · `FLT` · `BOM` · `EXP` · `TEST` · `FAIL` · `RCA` · `CHG` · `RISK` · `SAFE` · `MIN` · `WEEK` · `EVD`.

## 6. Development principles

1. Evidence before freeze.
2. Reuse before replacement.
3. Role-specific hardware before fleet-wide duplication.
4. Deterministic safety before ML.
5. Physical validation before simulation-only claims.
6. Current/wind/disturbance must be measured or explicitly simulated with known ground truth.
7. Failures remain evidence.

## 7. Pull-request rule

Meaningful repository changes: branch → PR → review/CI → protected `main`.

A merged software change never authorizes physical actuation.

## 8. Event capture

- experiment/test → `EXP/TEST-###` + raw data + conclusion;
- failure → `FAIL-###` + containment + recurrence check;
- engineering change → `CHG-###` + re-verification;
- supervisor decision → `MIN-###` + affected requirement/task update.

## 9. Registers

Under `project-data/`:

- `requirements-traceability.csv`;
- `evidence-index.csv`;
- `gantt.csv`;
- `failure-register.csv`;
- `experiment-index.csv`.

## 10. Experiment standard

Record: question, vehicle/configuration, hardware revision, software commit, environment, procedure, measured variables, metrics, trials, raw-data location, result and conclusion.

“The boat worked” is not a test result.

## 11. Schedule

Issue hierarchy and current repository Gantt are the controlled plan. Historical dates are not silently rewritten. The 28 Sep rebaseline is explicitly documented in `GANTT.md`.

## 12. AI/ML authority

No generative/LLM component controls motors, cutter, geofence or emergency action.

Advisory ML is permitted only with a deterministic baseline and measured benefit. Hard current/temperature/leak/jam limits and local control remain authoritative.

## 13. Hardware authority

Simulation, analysis and repository edits can proceed without physical actuation. Fabrication release, flashing/energizing hardware, propulsion/cutter operation and river deployment require human supervision/approval.

## 14. Weekly operating loop

- Start: current queue + blockers.
- During work: capture tests/failures/changes.
- End of week: exception audit.
- Before supervisor meeting: evidence-backed progress brief.
- Before viva: final claims-to-evidence audit.
