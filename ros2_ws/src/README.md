# ROS 2 Workspace Source

Place project-owned ROS 2 Jazzy packages here. Do not commit generated `build/`, `install/` or `log/`.

## Planned package boundaries

- common messages/interfaces;
- vehicle bridge Pi ↔ STM32;
- perception (FloW-YOLO, range inputs);
- mission state machine;
- coverage planner;
- decentralized fleet/CBBA agent;
- dock/service client;
- logging/diagnostics.

LoRa is a compact fleet-state/task transport via STM32; do not route raw video, images or point clouds over it.

Package APIs must preserve robot ID, timestamps, coordinate frames, QoS and hardware/software revision traceability.
