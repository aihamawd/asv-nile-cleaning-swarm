# Requirements Baseline — Rebaseline 2026-09-28

| ID | Requirement | Verification intent |
|---|---|---|
| REQ-001 | Support cooperative operation of 3–4 heterogeneous physical ASVs where viable: one new fiberglass build plus inherited/repurposed platforms. | Inspection + fleet demo |
| REQ-002 | Each operational ASV shall retain local navigation and safety independent of a shore computer or continuous remote motor commands. | Architecture + comm-loss test |
| REQ-003 | Fleet task allocation/reallocation shall operate peer-to-peer using replicated mission state and bounded ownership/lease rules; no permanent master is required. | Multi-ASV simulation + physical test |
| REQ-004 | Navigation shall use GNSS + IMU + compass with a marine-capable real-time controller/autopilot architecture. | Calibration + controlled navigation |
| REQ-005 | At least one ASV shall physically demonstrate floating-waste collection, retention and service/unloading. | Collection + dock experiment |
| REQ-006 | The project shall demonstrate a measured *Pontederia crassipes* handling system; intact removal is preferred and cutting is used only where justified. | Handling/cutter experiment |
| REQ-007 | Propulsion shall be sized from loaded thrust/current/current-disturbance requirements and validated by bench/water measurements. | Thrust/current + speed test |
| REQ-008 | Robot A shall have verified displacement, freeboard, CG/CB, trim, stability and safe payload states before final fabrication freeze. | Calculation + flotation test |
| REQ-009 | Communication baseline shall use compact peer traffic over STM32-connected SX1262 LoRa or an evidence-approved replacement; no ESP32 is required. | RF bench + range test |
| REQ-010 | Communication loss/partition shall invoke documented local degraded behavior and stale-task reconciliation without removing onboard safety. | Partition/fault test |
| REQ-011 | Floating-waste perception shall use the published FloW image dataset as the baseline training source; a new training dataset is not a project requirement. | Reproducible training/evaluation |
| REQ-012 | Radar shall not be required for the funded baseline. | Architecture/procurement review |
| REQ-013 | ToF shall support close-range docking/clearance where fitted; LiDAR is conditional by role/budget. | Sensor characterization |
| REQ-014 | Docking/unloading shall be treated as a system subsystem with approach, alignment, contact confirmation and service cycle evidence. | Dock cycle test |
| REQ-015 | Safety-critical stop/interlock functions shall distinguish physical isolation, RC/manual override, low-level failsafe and high-level software requests. | Safety review + test |
| REQ-016 | Custom PCB development shall be limited to interfaces/protection/instrumentation justified by wiring, reliability and repeatability; high-current power stages remain separate unless validated. | Design review |
| REQ-017 | Current/wind/disturbance effects shall be evaluated using known VRX/Gazebo disturbances and physical measurements; GNSS/IMU alone shall not be claimed as direct current measurement. | Sim + field A/B |
| REQ-018 | MSS/MATLAB marine dynamics shall provide the classical modelling/GNC reference used for controller and residual-learning comparisons. | Model review + replay |
| REQ-019 | ML/AI functions shall remain advisory unless they demonstrate measurable benefit over deterministic baselines and shall not bypass hard safety. | A/B/ablation |
| REQ-020 | Procurement shall be reuse-first, role-specific and performance-based rather than best-in-class-by-default. | Purchase/design audit |
| REQ-021 | Significant engineering claims shall be traceable to calculations, tests, experiments or evidence. | Traceability audit |

Numeric acceptance thresholds are introduced only when legacy/site/subsystem data justify them.
