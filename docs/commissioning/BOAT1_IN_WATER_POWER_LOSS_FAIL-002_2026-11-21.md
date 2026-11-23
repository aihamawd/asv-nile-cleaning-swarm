# FAIL-002 / EXP-003 — Both onboard supply fuses opened during first in-water propulsion attempt

**Test:** 2026-11-21, morning (operator-reported)  
**Vessel:** inherited Boat 1; water flotation passed separately (EXP-002).  
**Operating condition:** boat floating in water, first motor start commanded through interim ESP32/NRF24 remote and Cytron MDD10A Rev2 dual brushed-motor driver.  
**Outcome:** after motors *just began moving*, the circuit suddenly lost power. The operator later diagnosed both installed fuses as blown/open: **3 A motor branch**, **1 A ESP/electronics branch**. No voltage/current scope trace or actual blow order available. No report of damage to other devices but their electrical integrity is not yet verified.

## Critical interpretation (suspicions, not proven root causes)

1. **Motor branch 3 A fuse under-sized for both startup currents** is plausible: two brushed motors have high start/stall current; the Cytron MDD10A can *handle up to 10 A continuous per channel*, but this is a *driver rating*, not measured motor draw and is not a fuse-sizing recommendation.
2. **The independent-looking 1 A ESP fuse opening requires separate diagnosis.** A motor startup surge alone does **not** explain both opens if their positive feed branches and return paths are truly properly separated. The 1 A fuse might have failed due to a short, water ingress, a buck input/inrush problem, unintentional motor current in electronics wiring, or a mistakenly shared fuse/power wiring path.
3. The earlier power/RF issue (FAIL-001) responded to *rearranging NRF24 and driver grounds*; exact grounding topology remains undocumented. This makes shared return wiring or misrouting a relevant hypothesis, **not evidence of the actual cause of this new fault**.
4. Two open fuses discovered after the event do **not** prove both opened simultaneously, which one blew first, or that either was definitively protecting all downstream hardware.

**No claim of successful in-water propulsion performance** is supported. Earlier basic flotation (EXP-002) remains a separate reported PASS; powered test is a STOP / FAIL.

## Immediate containment

- Leave battery isolated and **do not bypass or uprate either fuse**, attach improvised jumper wires, or repeatedly re-energize.
- Inspect for moisture, corrosion, wet connector paths, crossed polarity, damaged insulation, and motor leads touching hull hardware. Dry/repair as needed before any powered test. Check whether device grounds or signal paths have become inadvertent motor-current returns.
- With power removed, verify wiring diagram and motor vs buck branch fuse position, continuity/resistance from each branch positive to return and between branches; note that connected electronics/capacitors can distort resistance readings.
- Verify pack nominal voltage/series count, BMS current rating, fuse specifications including **fast/slow response and DC interrupt rating**, cable/gauge and power switch rating.
- In a dry, controlled, current-limited, human-supervised bench setup, *after fault isolation*, characterize power branches separately with a DC clamp/current meter appropriate for transient measurements. Instrument voltage at battery, DC-DC input/output, ESP receiver and NRF24 while starting motors one at a time at low duty. Verify radio emergency stop/failsafe before returning to water.
- **Choose protection only after verifying stall/start and running current plus minimum wire/connector ampacity.** A motor driver 10 A per channel rating alone does not justify a fuse increase.

## Most discriminating missing details

1. Exact **positive and negative power wiring**, showing placement of 3 A and 1 A fuses: battery -> branch -> MDD10A, and battery -> 1 A fuse -> buck IN or 4.9 V OUT -> ESP?
2. Fuse package/type and time-current characteristic (fast-blow vs time-delay), and whether one fuse is upstream of another.
3. Motor nameplate and measured start/stall/running current at safe rated voltage; dual start behavior from *current* Codex firmware.
4. Whether any part of the electronics enclosure, connector, motor joint, or battery housing got wet; whether the failure occurs dry with motors mechanically unloaded.
5. Result of unpowered continuity tests, electrical inspection, and verified battery state.

## Linked work

- [#17 — legacy boat baseline](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/17)
- [#25 — propulsion bench characterization](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/25)
- [#26 — battery/fuse/distribution](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/26)
- [#28 — interface and wiring review](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/28)
- [#56 — buoyancy/stability validation](https://github.com/aihamawd/asv-nile-cleaning-swarm/issues/56)

**Release state:** physical testing blocked pending electrical fault identification and safe re-verification. Documentation only; no motor commands, electrical changes or firmware flash issued.
