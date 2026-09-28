# Current Execution Queue

**Architecture rebaseline:** 28 September 2026  
**Current state:** architecture freeze + pre-build engineering.

The project is still closing M1 evidence while selected M2–M5 design activities proceed in parallel where they do not depend on unknown legacy measurements.

## Execute now

1. **#14 — M1.1** Recover legacy assets and complete handover inventory.
2. **#15 — M1.2** Mechanical/CAD/hull integrity audit.
3. **#16 — M1.3** Electrical/control/software/compute/sensor legacy audit.
4. **#17 — M1.4** Restore/run at least one legacy platform as-is and record measured baseline.
5. **#20 — M2.2** Hydrostatics, buoyancy, payload, CG/CB, trim and stability.
6. **#25 — M3.2** Propulsion thrust/current sizing and bench characterisation.
7. **#29 — M4.1** Low-level control-stack trade study: ArduPilot Boat/Pixhawk-class vs custom STM32; PX4 only if justified.
8. **#35/#36** Collection/Pontederia requirements and mechanism trade study.
9. **#33** Establish MSS + VRX/Gazebo current/wind simulation baseline.
10. **#26/#27** Prepare FloW image-only YOLO pipeline and role-appropriate camera/ToF/LiDAR architecture.

## Next gate

Close **M1** only after the actual fleet inventory, baseline measurements, risks and open assumptions are explicit.

Immediately after that:

- freeze Robot A fiberglass hull envelope from hydrostatics;
- freeze propulsion purchase only after thrust/current evidence;
- freeze Pi/STM32/SX1262 interfaces;
- prototype collector/Pontederia handling and dock/unloading hardware;
- start controlled single-ASV navigation/perception testing.

## Do not freeze yet

Do not lock the following without evidence:

- exact Robot A dimensions before buoyancy/stability;
- exact thruster/motor before loaded thrust/current sizing;
- cutter topology/motor before contained cutting/feed tests;
- mandatory Pi 5 or identical SBC across the fleet;
- fleet-wide LiDAR;
- radar purchase;
- a mandatory shore Fleet Manager;
- custom PCB high-current power stage before interfaces/loads are proven.

## Gate rule

Exploration may run in parallel, but fabrication/purchase/field commitments must reference calculations, tests or an approved design decision.
