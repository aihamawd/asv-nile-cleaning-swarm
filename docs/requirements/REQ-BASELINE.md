# Initial Requirements Baseline

This file captures the currently agreed high-level requirements without freezing unresolved design choices.

| ID | Requirement | Verification intent |
|---|---|---|
| REQ-001 | The project shall support cooperative operation of a mixed fleet of 3–4 physical ASVs where technically feasible, including one new-build vehicle and inherited vehicles restored/retrofitted as justified. | Inspection + fleet demonstration |
| REQ-002 | Each operational ASV shall retain onboard local navigation and safety behavior independent of continuous shore motor commands. | Architecture review + comms-loss test |
| REQ-003 | The fleet manager shall issue mission-level assignments and support reassignment of unfinished work when a vehicle becomes unavailable or reaches an operational limit. | Multi-vehicle functional test |
| REQ-004 | The system shall support autonomous GNSS/IMU-based navigation using a marine-autopilot-oriented architecture. | Controlled navigation test |
| REQ-005 | At least one vehicle shall physically demonstrate floating-waste collection. | Collection experiment |
| REQ-006 | At least one vehicle shall physically demonstrate a water-hyacinth cutting/handling subsystem selected through calculation and prototype evidence. | Cutter/handling experiment |
| REQ-007 | The project shall measure and evaluate environmental-disturbance/current effects rather than relying only on simulation claims. | Controlled/field A/B test |
| REQ-008 | Communication loss shall not directly remove onboard basic autonomy; degraded behavior and timeout/recovery policy shall be documented and tested. | Comms-loss test |
| REQ-009 | The system shall provide health/energy/collection-state information sufficient for fleet-level mission decisions where sensors are installed. | Interface inspection + functional test |
| REQ-010 | Safety-critical stop mechanisms shall distinguish local physical isolation, onboard failsafes, RC/manual override, and remote software stop. | Safety review + test |
| REQ-011 | Significant engineering claims shall be traceable to tests, experiments, calculations, or other repository evidence. | Traceability audit |
| REQ-012 | Final payload, vehicle dimensions, hull material, cutter topology, propulsion hardware, advanced sensing, and task-allocation algorithm shall remain open until justified by engineering evidence or approved constraints. | Design-review audit |

## Notes

These are project-level requirements, not final acceptance thresholds. Numeric performance thresholds should be introduced only after legacy-vehicle characterization, site/user constraints, and subsystem capability are measured.
