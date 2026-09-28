# Firmware

Baseline controller split:

- **Linux SBC:** ROS 2/perception/mission/fleet agent/logging.
- **STM32/autopilot-class controller:** real-time navigation/control, safety, auxiliaries, health I/O and SX1262 LoRa.

No ESP32 requirement.

## STM32 workflow

Use STM32CubeIDE / Programmer / Monitor where a custom STM32 target is selected. Instrument:

- propulsion/actuator commands;
- current/temperature/load/leak/jam;
- command age/sequence;
- failsafe reason/state;
- SX1262 packet counters and errors.

Low-level autopilot platform remains a design decision until the ArduPilot Boat/Pixhawk-class vs custom STM32 trade study closes.
