# SYS-001 — Baseline System Architecture

**Status:** Baseline, subject to evidence-driven refinement

## System context

The project implements a mixed fleet of 3–4 physical autonomous surface vehicles for Nile surface cleaning. One vehicle is a new build; 2–3 vehicles are inherited platforms restored and retrofitted where feasible.

## Vehicle architecture

Each vehicle is expected to separate functions across three logical layers where hardware permits:

1. **Marine autopilot** — GNSS/IMU state estimation, heading/speed control, differential thrust, geofence, Hold/RTL, basic failsafes, RC/manual override.
2. **ROS 2 onboard computer** — mission state machine, perception, coverage/fleet client, logging, higher-level guidance and integration.
3. **Auxiliary embedded I/O** — collection/load sensing, leak sensing, cutter/gate interlocks, current/jam sensing and other local health I/O where required.

The exact electronics implementation may differ between legacy and new-build vehicles, provided the external fleet interface and safety behavior remain compatible.

## Fleet architecture

The shore Fleet Manager owns mission-level coordination only:

- geofenced mission definition;
- area decomposition;
- shared task pool;
- vehicle status monitoring;
- task assignment/reassignment;
- mission progress and logs;
- shore/service handoff arbitration where required.

It must not continuously command propulsion.

## Common vehicle state

The common fleet interface should be able to represent at minimum:

- vehicle ID and timestamp;
- pose/navigation state;
- velocity/speed;
- battery/energy state;
- collection load/fill state where available;
- health/fault state;
- communication freshness;
- current task and progress;
- operating mode.

## Communication-loss principle

Loss of shore communication does not remove onboard local autonomy. The vehicle should enter documented degraded behavior using onboard safety and mission logic; stale fleet tasks are only released after the defined heartbeat/timeout policy.

## Safety hierarchy

Local physical isolation and onboard failsafes take priority over remote software commands. RC/manual intervention has higher authority than mission-level autonomy.

## Open architecture decisions

The following are deliberately not frozen by SYS-001:

- exact autopilot model;
- exact SBC/MCU hardware;
- communication radio/transport;
- ROS 2 package decomposition;
- task-allocation algorithm;
- cutter topology;
- propulsion hardware;
- advanced sensing/RTK requirements.

These require requirements, tests, calculations, or design decisions before freeze.
