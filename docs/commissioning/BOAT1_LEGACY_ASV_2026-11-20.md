# BOAT1 — inherited ASV propulsion commissioning checkpoint

**Engineering record:** TEST-001 / EXP-001 / FAIL-001 (initial records; identifiers checked against registers, which contained only headers before this update)  
**Bench testing reported:** 2026-11-20; **photographs supplied:** 2026-11-21 (image capture dates not established)  
**Vehicle:** “Boat 1”, existing/inherited surface-cleaning prototype; mapping to repository Robot B is **provisional** pending the formal fleet inventory.  
**Evidence basis:** operator's direct test observations reported in the commissioning conversation; five original photographs supplied in that conversation; local Windows handoff/logs. **Not an independently witnessed instrumented test**.  
**Firmware provenance:** RC2 and receiver sketches were subsequently updated using Codex; the actual latest source commit/hash has **not** been retrieved. Existing firmware is **not** modified by this documentation update.

## Purpose and scope

Restore the inherited electrical/propulsion setup just far enough to evaluate clear-water propulsion and **water-hyacinth (*Pontederia crassipes*) penetration and propeller entanglement**. The interim ESP32/NRF24, joystick remote and ESP32-CAM/TFT are *commissioning hardware*, not the final autonomous control/perception selection. Defer camera-screen optimization unless required for safe operation or experimental evidence.

## Photo-based physical inventory (visual only)

| Uploaded file | Supported observation | Limitation |
|---|---|---|
| `IMG_1381.jpeg` | Twin white PVC tube flotation/side structures; metal bow guide/funnel plates; central blue buoyant-looking blocks; clear central electronics enclosure; mechanical fasteners | No scale, draft, measured displacement, propulsion rating, or leak test |
| `IMG_1170.jpeg` | Handheld operator panel with two joystick positions and a color TFT; TFT visible in a connection/waiting state at the instant of photo | Does not establish continuous camera quality or live RF state |
| `IMG_1197.jpeg` | Open handheld electronics housing with two ESP32-style development modules, prototyping board, cylindrical cell, adjustable DC-DC module and wiring | Component roles, pinout, electrical protection and ratings not verified from photograph |
| `IMG_1196.jpeg` | Underside of handheld panel, joystick/mount and flat-cable connections, visible workmanship requiring strain-relief inspection | No continuity or mechanical-load test recorded |
| `IMG_1194.jpeg` | Overall dry bench layout showing PVC float frame, metal guide geometry, transparent electronics compartment and controller enclosure | No waterproofing, center-of-gravity or water-performance evidence |

Original images are not yet in the project's designated cloud evidence vault. **EVD-001 remains pending external archival and a stable link**. Do not equate the photo observations with proof of seaworthiness, waterproofing or hyacinth penetration.

## User-reported bench commissioning results

1. Receiver ESP32 (previous USB adapter: CP2102 COM12) and RC2 transmitter ESP32 (CH340 COM13) communicated using NRF24L01. The controller drove **both** propulsion motors through **Cytron MDD10A Rev2**. Bench motor rotation and remote control have been physically demonstrated by the operator; motor-current, thrust and steering performance have not been quantified.
2. With the receiver powered by **laptop USB**, RF communication worked with the motor driver connected. With the receiver powered from the **boat battery through a DC-DC buck**, RF initially failed whenever the MDD10A motor-power input was energized, before motor rotation.
3. Reported measurements: battery **11.1 V** at the time (pack chemistry/series count and claimed 10,400 mAh capacity **not independently verified**); buck output ~**4.9 V**; ESP32 power-input pins **4.73–4.74 V**; NRF24 supply **3.3 V** measured *some time after startup*. Startup transients, switching ripple, current and individual cell voltages were not measured.
4. Isolation outcomes: unplugging **MDD10A battery positive** restored RF while its battery negative, driver control GND and PWM/DIR remained connected. Reconnecting driver positive caused failure even with **both motors physically disconnected**. Disconnecting **all four PWM/DIR signals** also left the RF fault present. Disconnecting only the **MDD10A control-header GND** (keeping driver battery negative connected) restored RF.
5. Operator then **switched/rearranged the ground wires associated with the NRF24 and MDD10A**, after which RF worked with the receiver powered by the **single onboard boat power system**, without laptop USB. **Exact wiring correction, return current path, startup transients and underlying electrical root cause remain unverified**. The fix is reported functional; repeatability and under-load verification are still pending.
6. Interim joystick mapping correction: the **right joystick** is the one physically on **GPIO32/GPIO33**; VX/VY are reported shorted/correlated. Previous “left joystick” mapping is not trusted. Receiver arming and failsafe behavior must be regression-tested using current Codex firmware.
7. Earlier ESP32-CAM video appeared on the remote TFT but the image flickered. It is a **deferred**, non-blocking legacy issue for the current mission, conditional on an independent safe line-of-sight operating method.

## Status / acceptance evidence

| Requirement or test | Status as of 2026-11-21 |
|---|---|
| Inspect and revive inherited ASV electronics | **In progress**; significant bench recovery |
| NRF24 communications on a single onboard battery/buck supply | **User-reported successful after ground-wire correction** |
| Remote manual command drives both motors | **User-reported bench demonstration** |
| Driver/RF system endurance under repeated acceleration | **Not yet measured/confirmed** |
| Ground architecture, fuses, BMS, cell-count/charger, wire ratings, accessible cutoff | **Not verified** |
| Actual joystick pinout/calibration and loss-of-signal zero-thrust behavior with newest firmware | **Not yet re-verified** |
| Hull mass, trim, buoyancy, leak and secured enclosure check | **Not yet recorded** |
| Static thrust/current/power map, speed/turn, endurance | **Not yet measured** |
| Clear-water manoeuvring and recovery procedure | **Not yet performed** |
| Sparse/dense water-hyacinth entry, progress, fouling and recovery | **Not yet performed** |
| Final Pi/STM32/SX1262 autonomous controller integration | **Future architecture phase; no completion claim** |

### Follow-up validation order / safety gates

1. **Electronics integration gate:** document the *corrected* battery-negative/buck/ESP32/NRF24/MDD10A GND wiring, verify fuse/isolation path and pack rating, ensure low-current grounds cannot carry motor current, protect/secure cables, verify stable rails under both motors running, and exercise RF-loss → zero-thrust, neutral-start and emergency motor cutoff. Do not change known-working Codex firmware during this documentation task.
2. **Dry bench gate:** check motor direction and differential-thrust behavior at controlled duty values; log battery/buck voltages, current, motor temperature and any RF dropouts. The photographs do not establish that the electronics enclosure is sealed.
3. **Water-readiness gate (human-supervised):** inspect watertightness, buoyancy, trim, hull/guide fasteners, sharp edges, propeller clearance, access to cutoff and recovery tether/boat. Test in controlled shallow water with required permissions, not directly in a fast/currenting Nile location.
4. **Clear-water baseline:** log payload, water depth, battery voltage, power/current versus command, steady speed, stopping distance, turn response and leak checks.
5. **Hyacinth penetration trials:** start with sparse vegetation then denser mat under safe recovery conditions; record time, advance distance, propulsion current, commanded duty, estimated speed, steering authority, vegetation deflection/collection, propeller entanglement and any electrical/thermal fault. Do **not** infer success from unloaded motor speed. Prefer intact plant handling; avoid unmanaged fragmentation.

## Linked GitHub work

- [#17 — M1.4 inherited physical baseline](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/17)
- [#25 — M3.2 propulsion and motor-driver bench characterization](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/25)
- [#26 — M3.3 protected DC distribution](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/26)
- [#28 — M3.5 wiring/interface review](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/28)
- [#57 — M9.3 thrust/speed/power formal validation](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/57)

**Gate discipline:** no M1, M3 or M9 milestone closure from this checkpoint. This is a provisional progress log and failure-recovery record; objective validation must still be collected.

## Related local evidence

Historical technical handoff on operator Windows workstation:  
`F:\AIHAM\Downloads\Boat1_Engineering_Handoff_2026-11-20\`  
`Windows_Logs\BOAT1_COMMISSIONING_PROGRESS_2026-11-20.md`  
`Windows_Logs\MDD10A_POWER_RAIL_ISOLATION_2026-11-20.md`

Local paths are **not** externally accessible evidence-vault links. Archive the source files and photos in the approved vault and update EVD-001 when done.
