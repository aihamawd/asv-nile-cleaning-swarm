# Cooperative Autonomous Surface Vessel Swarm for Nile Surface Cleaning

**October University for Modern Sciences and Arts (MSA University)**  
**Mechatronics Systems Engineering | Final-Year Graduation Project | 2026/2027**

**Students:** Aiham Moustafa Awad · Omar Mohamed Bakr  
**Main Supervisor:** Assoc. Prof. Dr. Amgad M. Bayoumy Aly  
**Co-Supervisor:** Prof. Dr. Mostafa Zaki  

**Repository:** `asv-nile-cleaning-swarm`  
**GitHub:** https://github.com/kagetsu2/asv-nile-cleaning-swarm

---

## Project Vision

Design, fabricate, integrate, and experimentally validate a cooperative fleet of autonomous surface vessels (ASVs) for surface cleaning in representative Egyptian Nile environments.

The project continues a previous MSA autonomous water-surface-cleaning robot and extends it toward a common multi-vessel architecture with improved physical cleaning, environmental-disturbance handling, and mission-level cooperation.

### Current Fleet Baseline

**3–4 physical ASVs**

- **1 new vessel** designed and fabricated during the project.
- **2–3 inherited/legacy student vessels** assessed, restored where feasible, and retrofitted to a common cooperative fleet interface.

The number of operational vessels does not replace engineering quality as the primary objective. Additional vessels are integrated only when they contribute meaningful fleet-level functionality.

### Core System Goals

- Autonomous marine navigation using GNSS/IMU and a marine autopilot.
- ROS 2 based high-level mission execution and system integration.
- Floating-waste collection.
- Physical water-hyacinth cutting, handling, capture, and retention.
- Anti-entanglement and jam-aware mechanical/electrical design.
- Environmental-current and disturbance evaluation.
- Cooperative mission-level task allocation and reassignment.
- Fault-aware behaviour and recovery of unfinished work.
- Health, power, load, and communication-state monitoring.
- Repeatable experimental validation with traceable evidence.
- Progressive testing from subsystem level to representative field conditions.

### Control Architecture

The system separates **local vessel autonomy** from **fleet-level mission coordination**.

**Onboard each ASV**
- GNSS/IMU state estimation
- heading and speed control
- differential propulsion
- geofencing
- Hold / RTL
- local failsafes
- RC/manual override
- health monitoring
- ROS 2 mission client

**Shore Fleet Manager**
- mission planning
- cleaning-area decomposition
- shared task pool
- vessel-state monitoring
- task assignment/reassignment
- mission progress
- fleet logging

The Fleet Manager issues **mission-level tasks only**. It does not continuously command motors or replace onboard safety/autonomy.

---

# Team and Responsibility Split

The project uses clear subsystem ownership while keeping integration, fleet autonomy, testing, and final validation shared between both students.

## Aiham Moustafa Awad

### Electrical, Control & Integration Lead

Primary responsibility for:

#### Electrical & Power
- Legacy electrical-system assessment.
- Main power architecture.
- Battery selection and sizing.
- BMS integration.
- Fuse, isolation, and electrical protection.
- DC-DC conversion.
- Pack-level voltage/current/energy monitoring.
- Waterproof wiring and marine connectors.
- Electrical distribution and grounding.

#### Electronics & Embedded Systems
- Sensors and instrumentation.
- Leak detection.
- propulsion-current monitoring.
- cutter-current and jam detection.
- load/fill sensing electronics.
- auxiliary MCU integration where required.
- embedded interfaces between sensors, actuators, autopilot, and ROS 2.

#### Navigation & Control
- Marine autopilot integration.
- ArduPilot Rover/Boat configuration.
- GNSS/IMU integration.
- heading and speed control.
- differential-thrust configuration.
- geofence, Hold, RTL, and failsafe configuration.
- controller tuning.
- current/drift compensation experiments.
- navigation-performance evaluation.

#### Cutter Electrical Integration
- Cutter motor selection support.
- motor driver / ESC.
- current sensing.
- overload and jam protection.
- electrical interlocks.
- emergency shutdown interfaces.

#### Simulation & Integration
- ArduPilot SITL.
- ROS 2 / Gazebo integration support.
- electrical/control simulation.
- telemetry and logging.
- system-level integration troubleshooting.

---

## Omar Mohamed Bakr

### Mechanical, Collection & Fabrication Lead

Primary responsibility for:

#### Hull & Structure
- Legacy mechanical/CAD assessment.
- Robot hull and frame design.
- structural layout.
- material selection.
- buoyancy calculations.
- displacement.
- freeboard.
- stability.
- centre of gravity.
- trim.
- structural reinforcement.

#### Collection System
- floating-waste collection geometry.
- collection basket/net.
- guides and funnels.
- retention and anti-backflow mechanisms.
- payload accommodation.
- collection-system integration.

#### Water-Hyacinth Mechanical System
- cutter mechanical architecture.
- feeding/guide geometry.
- cutting mechanism.
- guards.
- anti-entanglement mechanical features.
- biomass capture and retention.
- mechanical jam-recovery considerations.
- serviceability.

Final cutter topology remains evidence-driven and is frozen only after calculations and prototype testing.

#### Propulsion Mechanical Integration
- thruster/motor mounting.
- propeller protection.
- anti-fouling geometry.
- structural hard points.
- shaft/mount alignment where applicable.

#### Fabrication & Mechanical Testing
- manufacturing drawings.
- fabrication coordination.
- machining requirements.
- mechanical waterproofing/enclosures.
- mechanical assembly.
- payload/stability testing.
- structure and deformation testing.
- cutter/collection mechanical testing.

---

## Shared Responsibilities

Aiham and Omar jointly own:

### ROS 2 & High-Level Software
- ROS 2 system integration.
- mission state machine.
- vessel fleet client.
- logging interfaces.
- perception integration.
- common message/interface definitions.

Neither student is treated as a dedicated software developer; existing packages and previous project software should be reused and adapted where technically appropriate.

### Fleet Coordination
- Shore Fleet Manager.
- geofenced cleaning-area decomposition.
- coverage strategy.
- shared task pool.
- task ownership.
- assignment and reassignment logic.
- communication heartbeat.
- stale-state handling.
- communication-loss behaviour.
- unfinished-work recovery.
- multi-vessel testing.

### Perception
- RGB camera integration.
- floating-waste detection.
- water-hyacinth perception.
- obstacle-sensing integration.
- evaluation of additional range/depth sensing where justified experimentally.

LiDAR, depth cameras, ToF, radar, RTK, and other advanced sensing are not assumed mandatory. They are introduced only when requirements or testing justify them.

### System Integration
- mechanical/electrical/software interface definition.
- fleet-wide hardware compatibility.
- common vessel interface.
- configuration management.
- debugging.
- integration testing.

### Experimental Validation
- bench testing.
- controlled float tests.
- propulsion testing.
- single-vessel autonomy.
- cleaning-system testing.
- water-hyacinth testing.
- disturbance/current experiments.
- multi-vessel communication.
- cooperative task allocation.
- fault/reallocation experiments.
- representative field testing.

### Project Engineering
- requirements.
- design reviews.
- procurement decisions.
- BOM.
- risk management.
- safety.
- experiment planning.
- evidence collection.
- engineering book.
- final report.
- poster.
- presentation.
- viva preparation.

---

# Operating Model

## GitHub = Complete Engineering Source of Truth

This repository is the project's complete engineering record and primary storage location.

It contains the documentation, source code, native engineering files, experimental evidence, procurement records, and project history required to reproduce, audit, continue, and defend the project.

Where practical, all project artifacts are stored directly in the repository. Large binary engineering files are tracked using **Git LFS**.

Examples include:

- CAD parts, assemblies, and drawings
- SolidWorks native files
- ANSYS models, setups, and relevant results
- MATLAB/Simulink models
- ROS 2 packages and configuration
- firmware and embedded software
- electrical schematics and PCB files
- BOMs and component records
- datasheets
- experimental datasets
- ROS bags
- photographs
- test videos
- supplier quotations
- invoices
- signed documents
- supervisor records
- reports
- presentations
- posters
- simulation inputs and relevant outputs

Every significant engineering artifact should be linked to the appropriate permanent project ID where applicable, such as **REQ-###**, **ADR-###**, **EXP-###**, **TEST-###**, or **EVD-###**.

### Large File Policy

Large binary files that are important to project reproducibility or evidence are stored using **Git LFS**.

Regenerable temporary data should not be committed unnecessarily.

Examples of files that may be excluded include:

- ANSYS temporary/cache directories
- compiler/build artifacts
- ROS 2 `build/`, `install/`, and `log/` directories
- temporary simulation files
- software caches
- duplicated exports
- automatically generated intermediate files

The rule is:

> **Preserve the engineering artifact, evidence, inputs, configurations, and relevant outputs. Exclude only files that can be regenerated without loss of engineering information.**

No external project-storage system is assumed. GitHub is the authoritative project memory.

---

# Engineering Principles

1. **Engineering quality before robot quantity.**
2. **Evidence before design freeze.**
3. **Maximum engineering time, minimum administrative burden.**
4. **No unnecessary rebuilding of previously solved work.**
5. **No engineering claim without traceable evidence.**
6. **No major hardware purchase without requirement or calculation basis.**
7. **Local safety remains onboard each vessel.**
8. **Fleet communication loss must not remove local autonomy.**
9. **Physical testing takes priority over simulation-only claims.**
10. **Failures are engineering evidence and must be recorded, not hidden.**

---

# Engineering Record ID Taxonomy

| Prefix | Category | Example |
|---|---|---|
| **REQ-###** | Requirement | REQ-007 |
| **SYS-###** | System architecture | SYS-003 |
| **ADR-###** | Architecture / design decision | ADR-005 |
| **MECH-###** | Mechanical | MECH-011 |
| **ELEC-###** | Electrical | ELEC-008 |
| **EMB-###** | Embedded | EMB-014 |
| **SW-###** | Software / ROS 2 | SW-021 |
| **NAV-###** | Navigation / control | NAV-006 |
| **VIS-###** | Vision / perception | VIS-004 |
| **FLT-###** | Fleet coordination | FLT-009 |
| **PUR-###** | Purchase | PUR-018 |
| **BOM-###** | Bill of materials | BOM-003 |
| **SUP-###** | Supplier | SUP-005 |
| **EXP-###** | Experiment | EXP-016 |
| **TEST-###** | Verification / validation | TEST-023 |
| **FAIL-###** | Failure | FAIL-006 |
| **RCA-###** | Root-cause analysis | RCA-003 |
| **CHG-###** | Engineering change | CHG-005 |
| **RISK-###** | Risk | RISK-008 |
| **SAFE-###** | Safety | SAFE-012 |
| **MIN-###** | Supervisor meeting | MIN-003 |
| **WEEK-###** | Weekly review | WEEK-007 |
| **EVD-###** | Evidence reference | EVD-042 |

IDs are permanent once issued.

---

# Repository Structure

```text
├── README.md
├── CONTRIBUTING.md
├── GOVERNANCE.md
├── EVIDENCE_POLICY.md
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── engineering-task.yml
│   │   ├── requirement.yml
│   │   ├── experiment.yml
│   │   ├── verification-test.yml
│   │   ├── failure.yml
│   │   ├── rca.yml
│   │   ├── engineering-change.yml
│   │   ├── purchase.yml
│   │   ├── risk-safety.yml
│   │   ├── design-decision.yml
│   │   ├── supervisor-meeting.yml
│   │   └── weekly-review.yml
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       ├── weekly-audit.yml
│       ├── gantt-generate.yml
│       └── ci.yml
│
├── docs/
│   ├── requirements/
│   ├── architecture/
│   ├── design-decisions/
│   ├── literature/
│   ├── risk/
│   ├── safety/
│   ├── test-plans/
│   ├── supervisor-notes/
│   ├── weekly-reviews/
│   ├── project-management/
│   │   ├── GITHUB_PROJECT_SETUP.md
│   │   └── gantt/
│   └── engineering-book/
│
├── ros2_ws/
│   └── src/
├── firmware/
├── simulation/
├── navigation/
├── perception/
├── fleet_coordination/
├── cleaning_system/
│
├── hardware/
│   ├── mechanical/
│   ├── electrical/
│   ├── interfaces/
│   └── bom/
│
├── experiments/
├── tests/
│
├── project-data/
│   ├── cost-register.csv
│   ├── failure-register.csv
│   ├── experiment-index.csv
│   ├── evidence-index.csv
│   ├── risk-register.csv
│   └── requirements-traceability.csv
│
├── tools/
│   ├── audit/
│   ├── gantt/
│   └── reporting/
│
└── reports/
    ├── proposal/
    ├── poster/
    └── final-report/
```

---

# Project Milestones

| ID | Milestone |
|---|---|
| **M1** | Requirements & Legacy Vessel Characterisation |
| **M2** | Fleet Mechanical Readiness |
| **M3** | Electrical & Propulsion Integration |
| **M4** | Single-Vessel Autonomous Navigation |
| **M5** | Cleaning / Water-Hyacinth Handling Prototype |
| **M6** | Multi-Vessel Communication |
| **M7** | Cooperative Task Allocation |
| **M8** | Fault-Aware Reallocation Behaviour |
| **M9** | Controlled Experimental Validation |
| **M10** | Representative Nile-Environment Validation |
| **M11** | Final Engineering Book, Report, Poster & Viva |

---

# Validation Philosophy

Development progresses through controlled gates:

```text
Bench
  ↓
Subsystem Test
  ↓
Controlled Float / Propulsion
  ↓
Single-Vessel Autonomous Operation
  ↓
Cleaning / Hyacinth Handling
  ↓
Multi-Vessel Communication
  ↓
Cooperative Task Allocation
  ↓
Fault / Reallocation Testing
  ↓
Representative Field Validation
```

Large fleet demonstrations do not substitute for subsystem reliability or quantitative experimental evidence.

---

# Getting Started

1. Read [`GOVERNANCE.md`](GOVERNANCE.md).
2. Read [`CONTRIBUTING.md`](CONTRIBUTING.md).
3. Read [`EVIDENCE_POLICY.md`](EVIDENCE_POLICY.md).
4. Review current requirements and open engineering issues.
5. Create work using the appropriate GitHub Issue template.
6. Link implementation, experiments, failures, changes, and evidence.
7. Preserve the digital thread from requirement to validation.

---

# Quick Links

- [Issues & Engineering Tasks](https://github.com/kagetsu2/asv-nile-cleaning-swarm/issues)
- [Pull Requests](https://github.com/kagetsu2/asv-nile-cleaning-swarm/pulls)
- [Project Board](https://github.com/kagetsu2/asv-nile-cleaning-swarm/projects)
- [Documentation](docs/)
- [Project Data](project-data/)
- [Engineering Book](docs/engineering-book/)

---

# Supervision

**Main Supervisor**  
Assoc. Prof. Dr. Amgad M. Bayoumy Aly

**Co-Supervisor**  
Prof. Dr. Mostafa Zaki

Major scope, budget, safety, and architecture changes are subject to supervisor review.

---

# Contact / Ownership

**Aiham Moustafa Awad**  
Electrical · Control · Embedded · Autopilot · Navigation · Power · System Integration

**Omar Mohamed Bakr**  
Mechanical · Hull · Structure · Collection · Hyacinth Mechanism · Fabrication

**Shared**  
ROS 2 · Fleet Coordination · Perception Integration · Testing · Procurement · Documentation · Final Validation

---

**Last updated:** 2026-09-07
