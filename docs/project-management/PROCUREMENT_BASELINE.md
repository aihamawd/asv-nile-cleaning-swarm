# Procurement Baseline — 28 September 2026

## Principle

The project buys **capability**, not premium labels. Use the lowest-cost component that demonstrably meets the required performance, safety and reliability threshold.

Reuse working legacy hardware first. Do not duplicate high-cost sensors/compute across all ASVs unless the role requires it.

## EGP 40,000 funding allocation

| Area | Fleet-wide ceiling | Scope |
|---|---:|---|
| Propulsion + motor control | EGP 9,000 | Selective thrusters/propulsors, ESCs/drivers, mounts, protection |
| Battery + protected power | EGP 5,000 | New packs only where legacy fails audit; BMS, fuses, DC-DC, wiring, charging, current sensing |
| Compute + navigation + sensing + LoRa | EGP 6,000 | Role-sized SBCs, GNSS/IMU/compass, STM32, SX1262, camera, ToF; LiDAR conditional |
| Robot A fiberglass hull + structural fabrication | EGP 5,500 | Fiberglass/resin, reinforcement, inserts, sealing, local fabrication |
| Collector + Pontederia cutter/feed | EGP 4,500 | Guides/feed/conveyor/cutter/gearmotor/transmission/bearings/current sensing |
| Custom PCB + waterproof electrical integration | EGP 4,000 | PCB revisions, connectors, glands, enclosures, protected interfaces |
| Docking + unloading prototype | EGP 2,500 | Guides/marker mount/contact sensing/unloader; charging optional |
| Testing/spares/transport/contingency | EGP 3,500 | Fixtures, replacement parts, transport, consumables |
| **Total** | **EGP 40,000** | |

## Purchase gates

### Propulsion
Do not buy by brand prestige. Require:
- loaded thrust/speed/current sizing;
- low-speed steering authority;
- positive upstream performance against representative design current;
- thermal/current headroom;
- serviceability and debris resistance.

### Compute
No mandatory Pi 5. A board must run its assigned ROS 2/perception workload at acceptable latency without sustained thermal throttling.

### Battery
Budget is fleet-wide. Test legacy packs first. Size each boat from Wh, discharge current and protected return reserve.

### Sensors
- camera where perception is needed;
- ToF for docking/clearance;
- LiDAR only where geometry benefit justifies cost;
- no funded radar.

### PCB
Prioritize common STM32/SX1262/sensor/power-monitor/interface boards. Keep high-current propulsion power stages commercial/separate unless a later design review justifies integration.
