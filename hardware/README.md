# Hardware

Hardware development follows the 2026-09-28 architecture rebaseline.

## Robot A

New fiberglass ASV. Before fabrication freeze record:

- displacement and reserve buoyancy;
- CG/CB, trim and stability;
- empty/normal/full-waste/wet-biomass load cases;
- propulsor immersion and sensor/dock height;
- collector/Pontederia/dock interfaces;
- manufacturing drawings and revision.

## Propulsion

Select from loaded resistance/current requirements and measured thrust-current maps. Premium marine thrusters are not mandatory if a cheaper solution passes the acceptance envelope.

## Payloads

Maintain separate design records for:

- floating-waste collector;
- Pontederia feed/intact pickup/cutting-assisted subsystem;
- anti-entanglement/propulsion protection;
- dock/unloading interface.

## Electronics

Custom PCB intent: STM32/SX1262/sensor/power-monitor/auxiliary interface and protection. Keep high-current propulsion power stages separate until explicitly justified.

See `docs/project-management/PROCUREMENT_BASELINE.md`.
