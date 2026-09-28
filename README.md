<div align="center">

# Cooperative Autonomous Surface Vehicle Swarm for Nile Surface Cleaning

### Autonomous navigation · Physical cleaning · Decentralized cooperation · Evidence-driven validation

**October University for Modern Sciences and Arts (MSA University)**  
**Mechatronics Systems Engineering · Final-Year Graduation Project · 2026/2027**

**Aiham Moustafa Awad · Omar Mohamed Bakr**

[![CI](https://github.com/aihamawd/asv-nile-cleaning-swarm/actions/workflows/ci.yml/badge.svg)](https://github.com/aihamawd/asv-nile-cleaning-swarm/actions/workflows/ci.yml)
![Status](https://img.shields.io/badge/Status-Architecture%20Freeze%20%2B%20Pre--Build-2ea44f)
![Fleet](https://img.shields.io/badge/Fleet-3--4%20Heterogeneous%20ASVs-0969da)
![ROS 2](https://img.shields.io/badge/ROS%202-Jazzy-22314E?logo=ros&logoColor=white)
![Gazebo](https://img.shields.io/badge/Gazebo-Harmonic-F58113)
![VRX](https://img.shields.io/badge/VRX-Multi--ASV%20Simulation-8250df)
![LoRa](https://img.shields.io/badge/Peer%20Link-SX1262%20LoRa-0a7ea4)

[Project Board](https://github.com/users/aihamawd/projects/1) · [Issues](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues) · [Pull Requests](https://github.com/aihamawd/asv-nile-cleaning-swarm/pulls)

</div>

---

## Current project baseline — 28 September 2026

The project targets a **mixed physical fleet of 3–4 ASVs**:

- **Robot A:** one new fiberglass ASV designed and fabricated from scratch.
- **Robot B:** inherited 2025/2026 MSA cleaning ASV, restored and measured before modification.
- **Robot C:** repurposed legacy platform selected after condition/capability audit.
- **Robot D:** optional fourth legacy platform only if technically viable and useful.

The fleet is intentionally **heterogeneous**. Vehicles do not need identical hulls, propulsion, compute, sensors or payloads. They share a minimum mission, health, navigation and communication contract.

### Current engineering position

**Architecture freeze + pre-build engineering.** Immediate priorities are:

1. finish legacy fleet inventory and measured baseline;
2. solve Robot A hydrostatics, displacement, CG/CB, trim, payload and fiberglass structure;
3. size propulsion from required loaded speed/current performance and bench thrust-current data;
4. bench-test floating-waste collection and Pontederia handling/cutter concepts before freezing mechanisms;
5. freeze the low-level control-stack decision (ArduPilot Boat/Pixhawk-class vs custom STM32; PX4 only if justified);
6. implement the Pi ↔ STM32 interface and STM32 ↔ SX1262 peer-radio path;
7. establish first MSS and VRX/Gazebo current/wind simulation baselines;
8. prepare the FloW image-only YOLO perception pipeline without creating a new training dataset.

## Core architecture

### Per operational ASV

**High-level computer (role-sized Linux SBC; Raspberry Pi family is one option, not a mandatory Pi 5):**

- ROS 2 Jazzy;
- FloW-trained YOLO camera perception where needed;
- mission state machine;
- local map/coverage logic;
- decentralized fleet agent and CBBA task bidding;
- advisory ML/AI functions only after deterministic baselines;
- rosbag2/MCAP logging and optional Wi-Fi maintenance/offload.

**Low-level real-time controller: STM32/autopilot-class controller:**

- GNSS + IMU + external compass state estimation;
- heading/speed/differential-thrust control;
- geofence, Hold/RTL/return and stale-command failsafes;
- RC/manual override and physical isolation path;
- collector/cutter/dock auxiliary I/O and hard interlocks;
- current, leak, load/fill and jam sensing;
- direct **SX1262 LoRa transceiver over SPI** for compact peer status/task traffic.

There is **no ESP32 requirement** in the baseline.

### Decentralized fleet

There is **no mandatory shore computer**. Each ASV maintains a local replicated mission/fleet view and exchanges compact peer messages over LoRa.

The baseline fleet logic includes:

- robot identity/capability vector;
- heartbeat and health state;
- pose, heading, speed and short intent;
- battery reserve and payload/full state;
- CBBA-style capability/energy/load-aware task bids;
- task ownership leases and stale-owner reconciliation;
- temporary leadership only when useful for a coalition or dock queue;
- unfinished-work recovery after bounded timeout/withdrawal;
- distributed dock token and staging waypoints.

An operator laptop may monitor/configure the fleet, but loss of that laptop is not a fleet-control failure.

## Mission payloads

### Floating waste collection

Robot B provides the inherited passive-net baseline. Candidate improvements include bow guides/funnel geometry, powered feed/conveyor where justified, retention/backflow control, fill/load estimation and a compatible unloading interface.

### Water hyacinth

Use the accepted name **water hyacinth (*Pontederia crassipes*; syn. *Eichhornia crassipes*)**.

The project prioritizes **intact mechanical removal where practical**. Cutting is assistance for dense mats, not the default goal. Candidate cutter/feed systems are selected from measured feedability, entanglement, cutting force, motor current, fragment escape, maintainability and safety.

No herbicide application is part of the ASV baseline.

### Docking and unloading

Docking is a first-class subsystem:

GNSS/compass coarse approach → AprilTag/ArUco relative alignment → ToF final range → guide rails/mechanical stop → contact/latch confirmation → unloading → optional guarded charging → token release.

## Perception

- **RGB camera + FloW image dataset + YOLO** is the floating-waste baseline.
- The project will **reuse FloW** rather than create a new training dataset.
- **2D LiDAR** is conditional and role-specific for obstacle/dock geometry.
- **ToF** is intended for close-range docking/clearance and must be characterized over water/sunlight.
- **Radar is not in the funded baseline.** Radar fusion may only be revisited if suitable 77 GHz hardware is borrowed or becomes economically reasonable; cheap presence radar is not treated as a substitute.

## Modelling, simulation and current/disturbance work

The engineering chain is deliberately multi-model:

- **SolidWorks / Motion:** hull, structure, mechanisms, mass properties, interference.
- **ANSYS Fluent:** resistance/drag, current-direction and draft/payload cases.
- **MATLAB/Simulink + Marine Systems Simulator (MSS):** 3-DOF marine dynamics, guidance/control reference, disturbance observer and energy models.
- **ROS 2 Jazzy + Gazebo Harmonic + VRX:** 3–4 ASV mission environment, dock, obstacles, current, wind, waves and fleet faults.
- **ArduPilot SITL / Mission Planner:** candidate low-level marine autopilot workflow and mode/failsafe testing where selected.
- **Foxglove / PlotJuggler / MCAP:** synchronized evidence and replay.
- **Wireshark / Serial Studio / PulseView:** network, UART and bus diagnostics.

Simulation does not replace water testing. MSS/VRX/Fluent results are calibrated or bounded with measured thrust, mass, speed, turning and field telemetry.

## AI/ML policy

No LLM or generative model is in the safety-critical control loop.

Deterministic control, interlocks, geofence, RC override and communication-loss behavior remain authoritative. Candidate advisory ML functions are tested only against deterministic baselines:

1. jam/prop-fouling detection;
2. remaining-energy prediction;
3. real-world dynamics residual learning;
4. hotspot prediction;
5. learned allocation-cost comparison;
6. health/fault scoring;
7. debris-drift/intercept prediction;
8. docking anomaly assistance;
9. optional water-quality outlier detection if sensors exist.

A model is allowed to influence mission logic only if measured benefit justifies it.

## Procurement philosophy

The project is **performance-based and reuse-first**, not best-in-class-by-default.

Buy the lowest-cost component that demonstrably meets the mission, safety and reliability threshold. Reuse serviceable legacy hardware. Richer compute/sensing is concentrated on the vehicle that needs it.

Current EGP 40,000 funding baseline:

| Area | Ceiling |
|---|---:|
| Propulsion + motor control | EGP 9,000 |
| Battery + protected power | EGP 5,000 |
| Compute + navigation + sensing + LoRa | EGP 6,000 |
| Robot A fiberglass hull + structural fabrication | EGP 5,500 |
| Collector + Pontederia cutter/feed mechanisms | EGP 4,500 |
| Custom PCB prototypes + waterproof electrical integration | EGP 4,000 |
| Docking + unloading prototype | EGP 2,500 |
| Testing, spares, transport and contingency | EGP 3,500 |
| **Total** | **EGP 40,000** |

These are **fleet-wide ceilings**, not automatic spend targets. Purchase follows measurement and reuse audit.

## Repository execution model

GitHub Issues are executable work. Parent issues are milestone gates; sub-issues are engineering tasks. GitHub is the operational source of truth; large/raw evidence may live in the configured evidence vault but must be indexed here.

See:

- [Current execution queue](docs/project-management/CURRENT_EXECUTION_QUEUE.md)
- [Master execution plan](docs/project-management/MASTER_EXECUTION_PLAN.md)
- [Gantt](docs/project-management/GANTT.md)
- [System architecture](docs/architecture/SYS-001_system-architecture.md)
- [Requirements baseline](docs/requirements/REQ-BASELINE.md)
- [Procurement baseline](docs/project-management/PROCUREMENT_BASELINE.md)
- [Operating architecture](docs/project-management/OPERATING_ARCHITECTURE.md)

## Milestone gates

| ID | Milestone |
|---|---|
| M1 | Requirements & Legacy Fleet Characterisation |
| M2 | Mechanical, Hull & Payload Readiness |
| M3 | Power, Propulsion & Embedded Electrical Integration |
| M4 | Single-ASV Autonomy, Perception & Simulation |
| M5 | Collection, Pontederia Handling & Dock Prototype |
| M6 | Peer Communication & Common Fleet State |
| M7 | Decentralized Coverage, CBBA & Cooperation |
| M8 | Fault-Aware Reallocation, Docking & Service |
| M9 | Controlled Experimental Validation & AI/ML Ablation |
| M10 | Representative Nile-Environment Validation |
| M11 | Engineering Book, Report, Poster, Viva & Release |

## Team split

- **Aiham:** electrical, power/protection, embedded, compute, custom PCB, navigation/control, propulsion electrical, sensing, communication, simulation/control integration.
- **Omar:** mechanical, hull/fiberglass/structure, hydrostatics/stability, collection, Pontederia mechanics, cutter/feed, dock mechanics, fabrication.
- **Both:** requirements, ROS 2 interfaces, decentralized fleet software, perception integration, procurement, validation, evidence and final academic delivery.

## Safety boundary

Repository changes, CI, simulation and code review do **not** authorize physical actuation. Fabrication, flashing/energizing hardware, propulsion/cutter testing and river deployment require explicit human supervision/approval.

---

**Last architecture rebaseline:** 2026-09-28
