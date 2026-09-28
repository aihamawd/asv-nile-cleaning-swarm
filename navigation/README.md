# Navigation & Control

## Minimum navigation inputs

- GNSS;
- IMU;
- external compass/magnetometer.

## Control baseline

Real-time heading/speed/differential-thrust control remains onboard the STM32/autopilot-class controller. Geofence, Hold/RTL/return, RC override and stale-command failsafe are local.

## Current/disturbance

Use MSS/MATLAB as classical model/GNC reference and VRX/Gazebo known current/wind as estimator ground truth. Real Nile logs validate model uncertainty.

Do not claim GNSS/IMU alone directly measures river current.

## Coverage

Deterministic boustrophedon/lawnmower and geofenced coverage precede learned allocation. CBBA allocates capability-compatible work at fleet level.
