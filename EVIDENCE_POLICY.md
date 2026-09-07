# Evidence Management Policy

**Cooperative Autonomous Surface Vessel Swarm for Nile Surface Cleaning**

This policy establishes what lives in GitHub (records and links) versus Cloud Drive (native evidence vault).

---

## Principle

**GitHub = Traceable Records + Links**

**Cloud Drive = Evidence Vault (Binary, Large, Native)**

Every engineering claim in GitHub must be traceable to evidence. Evidence is indexed and referenced, not duplicated.

---

## What Goes in GitHub

### ✅ COMMIT TO GITHUB

**Text-based, reviewable, version-controlled:**

- Source code (ROS 2 nodes, embedded C++, firmware, simulation scripts)
- Configuration files (launch files, YAML parameters, hardware interfaces)
- Calculations and analysis (Jupyter notebooks, Python scripts for post-processing)
- Test procedures and acceptance criteria (markdown, code)
- Issue templates and project structure
- Registers and indices (CSV with headers and documentation)
  - cost-register.csv
  - failure-register.csv
  - experiment-index.csv
  - evidence-index.csv
  - risk-register.csv
  - requirements-traceability.csv
- Documentation and architecture (markdown, diagrams as SVG/PNG if small)
- Meeting notes and decision records (MIN, WEEK, ADR)
- Equipment datasheets and user guides (if <5 MB and actively referenced)
- References and citations (BibTeX, markdown links)

---

## What Goes in Cloud Drive

### 📁 STORE IN CLOUD DRIVE (Referenced from GitHub)

**Large, binary, native, or sensitive:**

- **CAD Models:** STEP, STL, SolidWorks files (mechanical, electrical schematics)
- **Raw Datasets:** Rosbags, CSV sensor logs, video recordings from experiments
- **Images & Video:** High-res photos, thermal imagery, experiment video
- **Invoices & Receipts:** Purchase documentation (may contain sensitive data)
- **Signed Documents:** Purchase orders, loan agreements, supplier contracts
- **Raw Experimental Data:** Unprocessed sensor data, oscilloscope captures
- **Large Test Logs:** Full CI/test artifacts, if not summarized in GitHub
- **Manufacturer Datasheets:** If >2 MB or dozens of PDFs

---

## Evidence Linking Convention

### GitHub Issue / PR Should Reference Cloud Drive

**Format in issue body or comment:**

```markdown
## Evidence

**Raw Data:** [Cloud Drive](https://drive.google.com/...) — Experiments/EXP-016/raw_data/
**CAD Model:** [Cloud Drive](https://drive.google.com/...) — Hardware/Main_Vessel_v3.step
**Video:** [Cloud Drive](https://drive.google.com/...) — Experiments/EXP-016/test_run_1.mp4
**Datasheet:** [Cloud Drive](https://drive.google.com/...) — Hardware/Motor_Spec_MaxonEC45.pdf
```

If the Cloud Drive link is not yet available, use placeholder:

```markdown
## Evidence

**Raw Data:** EVIDENCE_LINK_PENDING (will be uploaded to Cloud Drive after experiment)
**Video:** EVIDENCE_LINK_PENDING
```

**Do NOT leave evidence links pending indefinitely.** Update the issue once evidence is available.

---

## Evidence Index (EVD-###)

Maintain a searchable index of all major evidence:

**docs/project-data/evidence-index.csv**

```csv
EVD ID,Description,Type,Location,Related Issue,Date Created,Status
EVD-001,Baseline mechanical drawings - Main vessel v1,CAD,Cloud Drive/Hardware/Mechanical_v1/,MECH-001,2026-09-08,ARCHIVED
EVD-042,ROS bag from EXP-016 long-range navigation trial,Rosbag,Cloud Drive/Experiments/EXP-016/rosbag/,EXP-016,2026-09-15,CURRENT
EVD-051,Motor controller thermal test video,Video,Cloud Drive/Experiments/EXP-020/thermal_test.mp4,FAIL-006,2026-09-22,CURRENT
```

---

## Registers (CSV Format)

All registers stored in `project-data/` as CSV with headers.

Version-control the CSV files in GitHub.

### Cost Register

**project-data/cost-register.csv**

```csv
PUR ID,Supplier,Item Description,Baseline Budget (£),Committed Cost (£),Actual Cost (£),Failure/Rework Cost (£),Forecast Remaining (£),Forecast at Completion (£),Variance (£),Related Issues,Status,Invoice Link
PUR-001,RS Components,BlueRobotics T500 Thruster,1200,1200,1200,0,0,1200,0,EXP-016,DELIVERED,Cloud Drive/Invoices/PUR-001
PUR-018,Maxon Electronics,EC 45 brushless motor (qty 8),800,800,PENDING,0,0,PENDING,PENDING,MECH-003,ORDERED,Cloud Drive/Quotations/PUR-018
```

### Failure Register

**project-data/failure-register.csv**

```csv
FAIL ID,Component/System,Symptom,Operating Condition,Date,Trial/Experiment,Previous Occurrence,Failure Family,RCA Issue,RCA Status,Corrective Action (CHG),Cost Impact (£),Schedule Impact,Evidence Link
FAIL-006,Motor Controller (Maxon EC 45),Thermal shutdown after 45 min,6A continuous current in 25°C water,2026-09-22,EXP-020,None,Thermal management,RCA-003,COMPLETE,CHG-005,150,Minor delay,Cloud Drive/Experiments/EXP-020/
FAIL-012,GPS Receiver (U-blox),Loss of satellite lock in urban canyon,Dense buildings near test tank,2026-10-05,EXP-025,FAIL-008,Signal integrity,RCA-007,IN PROGRESS,PENDING,0,None,Cloud Drive/Experiments/EXP-025/
```

### Experiment Index

**project-data/experiment-index.csv**

```csv
EXP ID,Objective,Vehicle,Hardware Revision,Software Commit,Environment,Date,Result,Acceptance Criteria,Raw Data Location,Evidence (Video/Photos),Related Issues,Next Action
EXP-016,Test long-range autonomous navigation (5 km),Vessel 1 v2,MECH-002,main@abc123,Lab tank + outdoor pond,2026-09-15,PASS,Range 5+ km without intervention,Cloud Drive/Experiments/EXP-016/,EVD-042 (video),NAV-014 ADR-003,EXP-023 planned
EXP-020,Thermal performance under sustained load,Vessel 2 v1,ELEC-008,main@def456,Lab with external current load,2026-09-22,FAIL,No thermal shutdown <60 min,Cloud Drive/Experiments/EXP-020/,PENDING,FAIL-006 RCA-003,CHG-005 retest scheduled
```

### Risk Register

**project-data/risk-register.csv**

```csv
RISK ID,Description,Category,Probability (1-5),Impact (1-5),Risk Score,Mitigation Strategy,Mitigation Owner,Status,Related Issues,Review Date
RISK-008,Battery thermal runaway / fire,Safety,2,5,10,Battery monitoring with thermal cutoff; Li-ion with BMS,Aiham,ACTIVE,SAFE-012,2026-10-30
RISK-015,Nile field access denied by local authority,Schedule,3,4,12,Early liaison with authorities; fallback to lab/canal testing,Omar,ACTIVE,WEEK-008,2026-10-15
```

### Requirements Traceability Matrix

**project-data/requirements-traceability.csv**

```csv
REQ ID,Description,Assigned To,Design Decision (ADR),Implementation Issues,Verification Test (TEST),Experiment (EXP),Result,Evidence,Status
REQ-007,Float detection within 2 m range,Omar,ADR-005,SW-021 SW-022,TEST-012,EXP-018,PASS,EVD-045,VERIFIED
REQ-012,Multi-vessel task handoff <5 sec latency,Aiham,ADR-008,FLT-009 FLT-010,TEST-028,EXP-035,PARTIAL PASS,EVD-063 (video shows 6 sec edge case),UNDER INVESTIGATION
```

---

## Handling Sensitive Information

### Invoices with Personal Data

- **If not sensitive:** Attach to GitHub issue or commit to project-data/invoices/
- **If sensitive (personal addresses, credit card info):** Store ONLY in Cloud Drive (private folder)
  - Reference in issue as "Invoice on file (Cloud Drive)"
  - Do NOT commit to GitHub

### Student Logbooks

- Individual logbooks stored locally or in Cloud Drive (private)
- GitHub records the evidence (who authored, who reviewed, timestamps)
- Final logbook aggregates GitHub history + local notes

---

## Data Integrity

### ✅ DO

- Commit raw experimental data (CSV, JSON) to GitHub for traceability
- Version-control all analysis notebooks and processing scripts
- Link to Cloud Drive for large derivatives (videos, rosbags)
- Update evidence-index.csv when new evidence is added
- Archive old evidence with documented retention dates

### ❌ DON'T

- Commit large binary files (>10 MB) to GitHub
- Commit generated artifacts (build outputs, compiled binaries)
- Delete evidence or historical data (mark as archived instead)
- Invent missing data or measurements
- Modify raw data after experiment (always keep original)
- Store duplicate copies of the same evidence in multiple Cloud Drive locations

---

## Audit Trail

Every piece of evidence has a clear audit trail:

1. **GitHub issue/PR** documents the engineering claim
2. **Evidence link** points to Cloud Drive or GitHub artifact
3. **Timestamp** recorded in issue/PR metadata
4. **Owner** recorded in issue assignment
5. **Status** tracked in GitHub Project

At the end of the project:
- All major claims are traceable to evidence
- No "lost" experimental data
- Clear chain: Requirement → Design → Implementation → Verification → Evidence

---

## Cloud Drive Organization

**Recommended structure (reference, not mandatory):**

```
ASV Nile Cleaning Project/
├── Experiments/
│   ├── EXP-016/
│   │   ├── raw_data/
│   │   ├── rosbag/
│   │   ├── video/
│   │   └── analysis/
│   └── EXP-020/
├── Hardware/
│   ├── CAD/
│   ├── Mechanical_v1/
│   ├── Electrical/
│   └── Datasheets/
├── Invoices/
├── Vendor_Quotations/
├── Meeting_Notes/
└── Archive/
```

---

## Questions?

- **Is this too large for GitHub?** → Commit to Cloud Drive, reference in GitHub
- **Is this text/code?** → Commit to GitHub
- **Is this raw experimental data?** → Commit small CSVs to GitHub; large rosbags/videos to Cloud Drive
- **Is this sensitive?** → Cloud Drive (private); reference in GitHub as "on file"
- **Is this a design decision rationale?** → Commit ADR/design doc to GitHub; link to CAD/evidence in Cloud Drive

---

**Approved:** 2026-09-07 (Bootstrap)
**Review:** After M1 completion
