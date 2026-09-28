# SYS-001 — Baseline System Architecture

**Status:** Rebaselined 2026-09-28; evidence-driven refinement remains allowed.

## 1. System context

Mixed fleet of 3–4 physical ASVs for Nile floating-waste collection and water-hyacinth (*Pontederia crassipes*) handling.

- Robot A: new fiberglass build.
- Robot B: inherited cleaning ASV.
- Robot C: repurposed legacy ASV.
- Robot D: optional.

## 2. Per-vehicle architecture

Where practical, each main ASV uses two processing layers:

### High-level Linux SBC

Role-sized compute selected by measured workload rather than a mandatory Pi 5.

Responsibilities:

- ROS 2 Jazzy;
- camera perception and FloW-trained YOLO where needed;
- mission state machine;
- coverage/local map;
- decentralized fleet agent / CBBA;
- advisory ML;
- MCAP logging;
- optional Wi-Fi maintenance/offload.

### Low-level STM32/autopilot-class controller

Responsibilities:

- GNSS + IMU + external compass state estimation;
- heading/speed and differential-thrust control;
- actuator outputs and auxiliary I/O;
- hard geofence/failsafe/interlock behavior;
- RC/manual override;
- leak/current/load/jam monitoring;
- direct SX1262 LoRa peer link.

The low-level software stack is not frozen: ArduPilot Boat/Pixhawk-class, custom STM32 or another justified marine-capable approach must pass a documented trade study.

## 3. Fleet architecture

No mandatory shore Fleet Manager.

Each vehicle maintains a local fleet/mission state and exchanges compact peer messages:

- ID/time/pose/velocity/heading;
- capability vector;
- battery/energy reserve;
- payload/full state;
- health/fault;
- current task/progress;
- bid/ownership/lease epoch;
- dock token/service state;
- short intent/trajectory.

Baseline allocation is decentralized CBBA-style consensus. Temporary local leadership is allowed for a coalition/dock sequence but is not a permanent master.

## 4. Communication

Baseline: SX1262 LoRa transceiver connected directly to STM32 over SPI.

LoRa carries compact state/task/fault traffic only. Raw images, LiDAR and MCAP stay onboard and are offloaded separately.

Communication partition must not remove local safety. Stale ownership is released only under explicit lease/timeout policy.

## 5. Perception

- RGB camera + FloW image dataset + YOLO baseline.
- No new training dataset required.
- ToF for final docking/close clearance.
- 2D LiDAR conditional by role and demonstrated need.
- Radar excluded from the current baseline.

## 6. Payload architecture

### Floating waste
Guide/funnel → capture/feed → retention/bin → fill/load state → unload.

### Pontederia
Intact pickup preferred. Cutting-assisted handling is conditional on dense-mat tests. Design includes feed/retention, anti-wrap, current/jam detection and escaped-fragment measurement.

### Dock/service
GNSS coarse approach → marker pose → ToF final range → mechanical guides/contact → unload → optional charge → token release.

## 7. Modelling/simulation

- SolidWorks / Motion;
- ANSYS Fluent / Mechanical;
- MATLAB/Simulink + MSS;
- ROS 2 + Gazebo Harmonic + VRX;
- ArduPilot SITL where selected;
- QGIS/Sentinel mission mapping;
- Foxglove/PlotJuggler/MCAP evidence.

Known simulated current/wind is used to evaluate estimators; real logs validate generalization.

## 8. Safety hierarchy

Physical isolation / RC override / local interlock > low-level control > high-level mission > fleet suggestion > advisory ML.

No ML or remote fleet agent may weaken local hard limits.

## 9. Open design decisions

Still evidence-driven:

- final Robot A dimensions;
- exact fiberglass layup;
- exact propulsion hardware;
- exact battery sizes per boat;
- low-level autopilot/controller platform;
- exact SBC by role;
- final collector/cutter/feed topology;
- final dock/unloader;
- whether any boat justifies LiDAR;
- custom PCB partitioning and revision;
- advanced ML functions.
