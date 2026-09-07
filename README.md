# Cooperative Autonomous Surface Vessel Swarm for Nile Surface Cleaning

**October University for Modern Science and Arts Mechatronics Engineering | Final-Year Graduation Project**

- **Students:** Aiham, Omar
- **Repository:** asv-nile-cleaning-swarm
- **Project GitHub:** Operational source of truth for all engineering decisions, hardware, software, experiments, failures, and project history

---

## Vision

Design, fabricate, and validate a cooperative fleet of autonomous surface vessels (ASVs) capable of autonomous navigation and coordinated water-hyacinth removal from representative Egyptian Nile environments.

- **Fleet:** 3–4 autonomous surface vessels
  - 1 newly designed and fabricated from first principles
  - 2–3 legacy student vessels retrofitted for cooperative architecture
- **System Goals:** Robust distributed task allocation, fault recovery, cooperative cleaning, traceable engineering evidence
- **Scope:** From concept through controlled laboratory validation and representative field testing

---

## Operating Model

### GitHub = Project Memory

This repository is **not merely code storage**. It is the:
- **Operational source of truth** for all engineering decisions, procurement, experiments, failures, and root-cause analysis
- **Traceable digital thread** linking requirements → design decisions → implementation → testing → evidence
- **Project memory** ensuring no engineering knowledge is lost between milestones or semesters

### Cloud Drive = Evidence Vault

Large/native evidence (CAD models, ROS bags, raw datasets, videos, invoices, datasheets, signed documents) is stored on the project Cloud Drive. **GitHub records reference this evidence rather than duplicate it.**

### Key Principles

1. **Maximum engineering time, minimum administrative burden**
2. **Zero loss of traceability or evidence**
3. **Concise, technically precise documentation** — avoid corporate bureaucracy
4. **Permanent IDs** for all major engineering artifacts (requirements, decisions, components, experiments, failures)
5. **Every engineering claim traceable to evidence**

---

## ID Taxonomy

All major engineering records use permanent IDs for traceability:

| Prefix | Category | Example |
|--------|----------|---------|
| **REQ-###** | Requirement | REQ-007 (float detection) |
| **SYS-###** | System architecture | SYS-003 (three-layer stack) |
| **ADR-###** | Architecture/design decision | ADR-005 (LiDAR over sonar) |
| **MECH-###** | Mechanical | MECH-011 (hull reinforcement) |
| **ELEC-###** | Electrical | ELEC-008 (power distribution) |
| **EMB-###** | Embedded | EMB-014 (sensor fusion) |
| **SW-###** | Software/ROS 2 | SW-021 (task allocator node) |
| **NAV-###** | Navigation/control | NAV-006 (state estimator) |
| **VIS-###** | Vision/perception | VIS-004 (hyacinth detector) |
| **FLT-###** | Fleet coordination | FLT-009 (handoff protocol) |
| **PUR-###** | Purchase order | PUR-018 (motor supply) |
| **BOM-###** | Bill of materials | BOM-003 (main vessel BOM) |
| **SUP-###** | Supplier | SUP-005 (Maxon Electronics) |
| **EXP-###** | Experiment | EXP-016 (long-distance navigation) |
| **TEST-###** | Verification/validation | TEST-023 (cutting efficiency) |
| **FAIL-###** | Failure | FAIL-006 (motor controller overheat) |
| **RCA-###** | Root-cause analysis | RCA-003 (inadequate heatsink) |
| **CHG-###** | Engineering change | CHG-005 (upgrade heatsink) |
| **RISK-###** | Risk | RISK-008 (battery fire) |
| **SAFE-###** | Safety | SAFE-012 (emergency tether) |
| **MIN-###** | Supervisor meeting | MIN-003 (weekly checkpoint) |
| **WEEK-###** | Weekly review | WEEK-007 (week of Sept 8) |
| **EVD-###** | Evidence reference | EVD-042 (ROS bag from EXP-016) |

---

## Repository Structure

```
├── README.md                          (this file)
├── CONTRIBUTING.md                    (Git/PR workflow)
├── GOVERNANCE.md                      (decision authority, approvals)
├── EVIDENCE_POLICY.md                 (GitHub vs. Drive split)
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── engineering-task.yml
│   │   ├── requirement.yml
│   │   ├── experiment.yml
│   │   ├── verification-test.yml
│   │   ├── failure.yml
│   │   ├── rca.yml
│   │   ├── engineering-change.yml
│   │   ├── purchase.yml
│   │   ├── risk-safety.yml
│   │   ├── design-decision.yml
│   │   ├── supervisor-meeting.yml
│   │   └── weekly-review.yml
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       ├── weekly-audit.yml
│       ├── gantt-generate.yml
│       └── ci.yml
│
├── docs/
│   ├── requirements/                   (REQ specifications & traceability)
│   ├── architecture/                   (SYS documentation)
│   ├── design-decisions/               (ADR records)
│   ├── literature/                     (references, state of the art)
│   ├── risk/                           (RISK & mitigation strategy)
│   ├── safety/                         (SAFE procedures)
│   ├── test-plans/                     (TEST procedures & protocols)
│   ├── supervisor-notes/               (meeting records)
│   ├── weekly-reviews/                 (WEEK snapshots)
│   ├── project-management/
│   │   ├── GITHUB_PROJECT_SETUP.md     (manual setup if needed)
│   │   └── gantt/                      (frozen Gantt artifacts)
│   └── engineering-book/               (final comprehensive documentation)
│
├── ros2_ws/
│   └── src/
├── firmware/
├── simulation/
├── navigation/
├── perception/
├── fleet_coordination/
├── cleaning_system/
│
├── hardware/
│   ├── mechanical/
│   ├── electrical/
│   ├── interfaces/
│   └── bom/
│
├── experiments/
├── tests/
├── project-data/
│   ├── cost-register.csv
│   ├── failure-register.csv
│   ├── experiment-index.csv
│   ├── evidence-index.csv
│   ├── risk-register.csv
│   └── requirements-traceability.csv
│
├── tools/
│   ├── audit/
│   ├── gantt/
│   └── reporting/
│
└── reports/
    ├── proposal/
    ├── poster/
    └── final-report/
```

---

## Milestones

1. **M1** — Requirements & Existing Vessel Characterisation
2. **M2** — Fleet Mechanical Readiness
3. **M3** — Electrical & Propulsion Integration
4. **M4** — Single-Vessel Autonomous Navigation
5. **M5** — Cleaning / Hyacinth Handling Prototype
6. **M6** — Multi-Vessel Communication
7. **M7** — Cooperative Task Allocation
8. **M8** — Fault / Reallocation Behaviour
9. **M9** — Controlled Experimental Validation
10. **M10** — Representative / Nile Environment Validation
11. **M11** — Final Engineering Book, Report, Poster & Viva

---

## Getting Started

1. **Read** [GOVERNANCE.md](GOVERNANCE.md) for decision authority and approval workflows
2. **Read** [CONTRIBUTING.md](CONTRIBUTING.md) for branch/PR policy and issue creation
3. **Read** [EVIDENCE_POLICY.md](EVIDENCE_POLICY.md) for GitHub vs. Cloud Drive guidelines
4. **Create issues** using GitHub Issue Templates for tasks, requirements, experiments, failures, etc.
5. **Maintain digital thread** by linking issues to PRs, experiments, and evidence

---

## Quick Links

- **Issues & Tasks:** [GitHub Issues](https://github.com/kagetsu2/asv-nile-cleaning-swarm/issues)
- **Pull Requests:** [GitHub PRs](https://github.com/kagetsu2/asv-nile-cleaning-swarm/pulls)
- **Project Board:** [GitHub Projects](https://github.com/kagetsu2/asv-nile-cleaning-swarm/projects)
- **Documentation:** [docs/](docs/)
- **Project Data:** [project-data/](project-data/)

---

## Contact

- **Aiham** — Primary contact for mechanical systems
- **Omar** — Primary contact for software and autonomous systems
- **Supervisor** — Review authority for scope, budget, and major design changes

---

**Last updated:** 2026-09-07 (Bootstrap Day 1)
