# GitHub Project Configuration — ASV Swarm for Nile Cleaning

**Operational repository:** `aihamawd/asv-nile-cleaning-swarm`  
**Architecture rebaseline:** 28 September 2026

The Project is an execution view over repository Issues and must not become a second independent task database.

## Hierarchy

11 parent milestone/gate issues contain executable engineering sub-issues. Titles and bodies are rebaselined to the decentralized architecture.

## Current phase

Architecture freeze + pre-build engineering.

Current active focus:

- legacy fleet baseline;
- hydrostatics/fiberglass Robot A;
- propulsion sizing;
- low-level controller decision;
- collector/Pontederia mechanism trials;
- Pi/STM32/SX1262 interfaces;
- MSS + VRX current/wind baseline;
- FloW image-only perception pipeline.

## Status policy

If the Project UI still exposes only `Todo / In Progress / Done`, use Issue comments/body for Blocked/Testing/Review context rather than creating a competing status store.

## Assignment policy

- `[Aiham]` → @aihamawd;
- `[Omar]` → @omaramer13;
- `[Both]` → both while genuinely joint.

## Roadmap rule

`docs/project-management/GANTT.md` and `project-data/gantt.csv` contain the 28 Sep schedule rebaseline.

Project-v2 Start/Target fields should be updated to match these dates when the connector/API surface exposes writable Project fields. Do not invent a second date truth.

## Architecture reminders

- no mandatory shore Fleet Manager;
- no ESP32 requirement;
- SX1262 directly on STM32;
- FloW image-only YOLO, no new training dataset;
- no funded radar;
- LiDAR conditional by role;
- ToF for close docking;
- custom PCB intent;
- Robot A fiberglass build;
- performance-based procurement.
