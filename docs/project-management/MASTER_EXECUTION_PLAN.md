# Cooperative Autonomous Surface Vehicle Swarm for Nile Surface Cleaning — Master Execution Plan

**Project period:** August 2026 – June 2027  
**Architecture rebaseline:** 28 September 2026  
**Operating baseline:** 3–4 heterogeneous physical ASVs: one new fiberglass build + viable legacy retrofits.

## Execution rules

1. GitHub Issues are executable work; parent issues are milestone gates.
2. Evidence precedes design freeze and fabrication release.
3. Simulation/bench work may proceed autonomously; physical/irreversible work remains human-supervised.
4. Local navigation, hard safety, geofence, RC override and actuator interlocks remain onboard.
5. Fleet coordination is **decentralized by baseline**. No mandatory shore Fleet Manager.
6. Each main ASV uses a two-controller concept where feasible: role-sized Linux SBC for ROS 2/perception/mission + STM32/autopilot-class controller for real-time control/safety/I/O.
7. SX1262 LoRa connects directly to STM32; no ESP32 is required.
8. FloW image data is reused for YOLO; no new training dataset is planned.
9. Radar is outside the current baseline.
10. Hardware selection is reuse-first, role-specific and evidence-driven.

## Milestone gates

| ID | Milestone | Rebaselined window | Gate output |
|---|---|---|---|
| M1 | Requirements & Legacy Fleet Characterisation | 24 Aug–15 Oct 2026 | Verified fleet baseline + current requirements/metrics |
| M2 | Mechanical, Hull & Payload Readiness | 15 Sep 2026–15 Jan 2027 | Hydrostatics, fiberglass Robot A and retrofit/payload fabrication baseline |
| M3 | Power, Propulsion & Embedded Electrical Integration | 20 Sep 2026–15 Feb 2027 | Measured thrust/power, protected electrical architecture, PCB/interface baseline |
| M4 | Single-ASV Autonomy, Perception & Simulation | 1 Oct 2026–15 Mar 2027 | Repeatable navigation + FloW/ranging + MSS/VRX baseline |
| M5 | Collection, Pontederia Handling & Dock Prototype | 20 Sep 2026–15 Mar 2027 | Evidence-based collector/plant-handling/dock design freeze |
| M6 | Peer Communication & Common Fleet State | 15 Jan–1 Apr 2027 | Stable STM32-SX1262 transport, shared state and timeout behaviour |
| M7 | Decentralized Coverage, CBBA & Cooperation | 15 Feb–30 Apr 2027 | CBBA task ownership, coverage and cooperative payload behaviour |
| M8 | Fault-Aware Reallocation, Docking & Service | 15 Mar–10 May 2027 | Partition/rejoin, withdrawal, dock-token and service recovery evidence |
| M9 | Controlled Experimental Validation & AI/ML Ablation | 1 Apr–31 May 2027 | Quantified controlled tests and algorithm-vs-ML comparisons |
| M10 | Representative Nile-Environment Validation | 20 May–10 Jun 2027 | Approved field evidence package |
| M11 | Engineering Book, Report, Poster, Viva & Release | 24 Aug 2026–20 Jun 2027 | Defensible final submission and reproducible repository |

## Dependency spine

`M1 → M2/M3 → M4/M5 → M6 → M7 → M8 → M9 → M10 → M11`

M2–M5 overlap deliberately. M11 runs continuously.

## Current design decisions

### Fleet
- Robot A: new fiberglass hull.
- Robot B: inherited cleaning ASV, baseline before upgrade.
- Robot C: repurposed legacy ASV.
- Robot D: optional.

### Navigation/control
- GNSS + IMU + external compass.
- Low-level control stack remains a decision gate: ArduPilot Boat/Pixhawk-class vs custom STM32; PX4 considered only if marine support justifies it.
- Pi/SBC is not required to be Pi 5; selection is based on workload/latency/thermal performance.

### Perception
- FloW image-only YOLO baseline.
- ToF for close docking/clearance.
- 2D LiDAR conditional by role and demonstrated need.
- Radar outside the current baseline.

### Fleet communications and coordination
- STM32 ↔ SX1262 LoRa peer link.
- Compact fleet packets only; raw images/point clouds remain onboard.
- Decentralized fleet agent + CBBA-style assignment.
- Distributed dock token and task leases.
- Optional operator laptop for monitoring/configuration only.

### Mechanical mission systems
- Floating-waste collector and Pontederia subsystem are distinct.
- Intact Pontederia pickup preferred; cutting-assisted mode conditional.
- Cutter/feed motor sized from measured force/torque/duty.
- Dock/unloading is a first-class subsystem.

### Simulation
- SolidWorks + ANSYS Fluent/Mechanical.
- MATLAB/Simulink + MSS marine model.
- ROS 2 Jazzy + Gazebo Harmonic + VRX + ArduPilot SITL where selected.
- Current/wind disturbance estimation validated against known simulation disturbance and physical logs.

## Primary responsibility

- **Aiham:** electrical, embedded, power, propulsion sizing/control, custom PCB, navigation/control, sensors/compute, LoRa, simulation/control integration.
- **Omar:** fiberglass/hull/structure, hydrostatics, collector/Pontederia mechanics, dock mechanics, fabrication.
- **Both:** ROS 2, decentralized fleet software, perception integration, system testing, evidence and final delivery.

## Gate discipline

A parent milestone closes only when required sub-issues are complete/dispositioned, acceptance evidence exists, failures/risks are explicit, and downstream assumptions are updated.
