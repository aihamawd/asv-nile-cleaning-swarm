# Project Gantt

The roadmap below is the schedule baseline. Dates are planning targets and are re-baselined only with a documented engineering reason; historical dates are not silently rewritten.

## Milestone roadmap

```mermaid
gantt
    title ASV Nile Cleaning Swarm — 2026/2027 Master Roadmap
    dateFormat  YYYY-MM-DD
    axisFormat  %b %Y

    section Grad I — Baseline & Design
    M1 Requirements + legacy characterisation :m1, 2026-08-24, 2026-09-30
    M2 Fleet mechanical readiness             :m2, 2026-09-15, 2026-12-15
    M3 Electrical + propulsion integration    :m3, 2026-09-20, 2027-01-15
    M4 Single-vessel autonomous navigation    :m4, 2026-10-15, 2027-02-15
    M5 Cleaning + hyacinth prototype          :m5, 2026-09-20, 2027-02-15

    section Grad II — Fleet Integration
    M6 Multi-vessel communication             :m6, 2027-01-15, 2027-03-15
    M7 Cooperative task allocation            :m7, 2027-02-15, 2027-04-15
    M8 Fault-aware reallocation               :m8, 2027-03-01, 2027-04-30

    section Validation
    M9 Controlled experimental validation     :m9, 2027-04-01, 2027-05-20
    M10 Representative Nile validation        :m10, 2027-05-10, 2027-06-05

    section Documentation
    M11 Engineering book/report/poster/viva   :m11, 2026-08-24, 2027-06-20
```

## Responsibility roadmap

```mermaid
gantt
    title Workstream Responsibility Roadmap
    dateFormat  YYYY-MM-DD
    axisFormat  %b %Y

    section Omar — Mechanical Lead
    Legacy mechanical audit + hydrostatics    :2026-08-24, 2026-10-15
    Hull/frame/CAD + retrofit design           :2026-09-15, 2026-12-15
    Cutter/collection mechanics               :2026-09-20, 2027-02-15
    Fabrication + mechanical integration       :2027-01-15, 2027-04-15
    Mechanical validation                      :2027-04-01, 2027-06-05

    section Aiham — Electrical/Control Lead
    Legacy electrical/control baseline        :2026-08-24, 2026-09-30
    Power/propulsion/electronics architecture  :2026-09-20, 2027-01-15
    Autopilot/navigation/control               :2026-10-15, 2027-02-15
    Cutter electrical + health monitoring      :2026-10-01, 2027-02-15
    Disturbance/control validation             :2027-02-01, 2027-06-05

    section Shared
    ROS 2 + system interfaces                  :2026-10-15, 2027-03-15
    Fleet Manager + cooperation                :2027-01-15, 2027-04-30
    Experimental validation                    :2027-04-01, 2027-06-05
    Engineering book/report/evidence           :2026-08-24, 2027-06-20
```

## Schedule control

- Dates are targets, not substitutes for technical gate evidence.
- M10 cannot begin field activity without site/safety/permission readiness.
- Physical fleet quantity may be reduced if a legacy vessel is not technically viable; the decision must be documented rather than hidden.
- A milestone may overlap another when the dependency required for a specific subtask is already satisfied.
