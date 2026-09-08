# Final-Year Project Operating Architecture — v2

**Project:** Cooperative Autonomous Surface Vehicle Swarm for Nile Surface Cleaning  
**Students:** Aiham Moustafa Awad · Omar Mohamed Bakr  
**Operational repository:** `aihamawd/asv-nile-cleaning-swarm`  
**Baseline:** 8 September 2026

## 1. Main rule

The students' job is **engineering execution**: design, calculations, CAD, electronics, embedded systems, ROS 2/software, control, fabrication, integration, testing, experiments, analysis and engineering decisions.

Administration must be captured once and then reused. The operating chain is:

```text
Aiham + Omar
    ↓ engineering events
AI / MCP administrative layer
    ↓ structured records
GitHub + Cloud Drive evidence vault
    ↓
Generated schedule / cost / weekly audit / Engineering Book
```

**GitHub is the operational source of truth. Cloud Drive is the heavy/raw evidence vault. The GitHub Project is the execution view. The AI/MCP layer is the administrative workforce.**

Do not introduce Odoo, Jira, Microsoft Project or another task database unless an academic requirement specifically requires it.

## 2. Authority hierarchy

| Layer | Authoritative for |
|---|---|
| GitHub repository | engineering documents, code, configuration, registers, traceability and version history |
| GitHub Issues | committed engineering work and permanent engineering records |
| GitHub Project | live execution state, assignment, dates and Roadmap |
| Pull Requests | reviewed change history and individual contribution |
| Discussions | unresolved engineering conversation; not final decisions |
| Wiki | navigation/explanation; not an independent engineering record |
| Cloud Drive | native CAD, video, photos, invoices, quotations, ROS bags, raw datasets, signed/formal files and other large evidence |
| `project-data/` | machine-readable indexes/registers linking GitHub records to evidence |

If two locations disagree, resolve the discrepancy rather than maintaining two competing truths.

## 3. Canonical terminology

**ASV means Autonomous Surface Vehicle.** Use **vehicle / ASV**, not “vessel”, in project documentation and planning.

Current physical fleet baseline: **3–4 ASVs** — one new-build ASV plus 2–3 inherited ASVs where restoration/retrofit is technically justified. Engineering quality and evidence take priority over vehicle count.

## 4. Permanent ID taxonomy

`REQ` requirement · `SYS` system architecture · `ADR` design decision · `MECH` mechanical · `ELEC` electrical · `EMB` embedded · `SW` software/ROS 2 · `NAV` navigation/control · `VIS` perception · `FLT` fleet coordination · `PUR` purchase · `BOM` bill of materials · `SUP` supplier · `EXP` experiment · `TEST` verification test · `FAIL` failure · `RCA` root-cause analysis · `CHG` engineering change · `RISK` risk · `SAFE` safety · `MIN` supervisor meeting · `WEEK` weekly review · `EVD` evidence.

Do not create vague records when a permanent engineering record is appropriate.

## 5. GitHub execution model

The repository uses **11 parent milestone/gate issues plus executable sub-issues**. Parent gates provide hierarchy and sub-issue progress; they are not duplicate executable tasks.

The live Project views are:

- **Master Plan** — complete execution table.
- **Execution Board** — status-oriented board.
- **Current Queue** — active items only.
- **Roadmap** — Start/Target timeline.
- **Aiham Tasks** — assignment view for Aiham.
- **Omar Tasks** — assignment view for Omar.
- **Milestone Gates** — unassigned parent gate overview.

The live Project currently uses `Todo`, `In Progress`, and `Done`. The preferred mature workflow is `Todo → Ready → In Progress → Blocked/Testing/Review → Done`; extend the Project Status field when the interface permits it. Until then, do **not** create a second status database or duplicate status labels.

## 6. Ownership and individual contribution

GitHub **Assignees** are the machine-readable task allocation.

- `[Aiham]` task → Aiham assigned.
- `[Omar]` task → Omar assigned.
- `[Both]` task → both assigned while joint work is genuinely required.

For a `[Both]` task that becomes predominantly one student's work, identify a **Primary Owner** and make the other student the **Reviewer / Supporting Engineer** when the task becomes active. Do not silently claim equal ownership where the contribution is not equal.

Trace where relevant: primary owner, reviewer, commit author, PR reviewer, experiment operator, ADR author and test lead.

## 7. Pull-request rule

Meaningful repository changes follow:

```text
feature/fix branch → Pull Request → review/CI → main
```

`main` is protected. Passing CI or merging software does **not** authorize physical fabrication, energized testing, propulsion/cutter operation, purchase commitments or field deployment.

## 8. Event capture instead of daily paperwork

Students should report important engineering events briefly:

- “We bought …” → `PUR-###` + cost register + evidence link.
- “We tested …” → `EXP-###`/`TEST-###` + raw evidence + result/conclusion.
- “This failed …” → `FAIL-###` + recurrence check + RCA gate if needed.
- “We changed …” → `CHG-###` linked to evidence and re-verification.
- “Supervisor decided …” → `MIN-###` and related requirement/ADR/schedule updates.

The AI/MCP layer performs the repetitive structuring and calculations; it must never invent measured values, dates, costs, results, evidence or root causes.

## 9. Operational registers

Machine-readable project registers live under `project-data/`:

- `requirements-traceability.csv`
- `evidence-index.csv`
- `gantt.csv`
- `cost-register.csv`
- `failure-register.csv`
- `experiment-index.csv`

These files are indexes, not replacements for the richer Issue/ADR/experiment records. The ID links the register row to the detailed record and evidence.

## 10. Evidence vault

Large/raw evidence belongs in the Cloud Drive structure defined in [`EVIDENCE_VAULT.md`](EVIDENCE_VAULT.md). GitHub retains the index, metadata, scripts/configuration required for reproducibility, and links to the evidence location.

Raw evidence must be preserved where practical. Processed plots/screenshots do not replace raw data.

## 11. Failure → RCA → change → retest chain

```text
FAIL-###
   ↓
RCA-###
   ↓
CHG-###
   ↓
EXP-/TEST-###
   ↓
PASS or new FAIL
```

Repeated failure families must trigger root-cause review rather than repeated replacement without analysis.

## 12. Experiment rule

Every meaningful experiment records the engineering question, vehicle/configuration, hardware revision, software commit/version, environment, procedure, measured variables, metrics, trials, raw-data location, result and conclusion.

A test is not complete because “the boat worked.” Completion requires a metric, result and evidence sufficient to defend the engineering claim.

## 13. Schedule rule

GitHub Project Start/Target fields and the parent/sub-issue hierarchy own the operational schedule. `project-data/gantt.csv` and rendered Gantt material are generated/reporting representations of the same plan.

Historical dates are not silently rewritten. Re-baselining requires a documented reason.

## 14. Weekly exception audit

Run the audit defined in [`WEEKLY_AUDIT.md`](WEEKLY_AUDIT.md). Students should receive **exceptions**, not an administrative diary.

Typical exceptions include DONE without evidence, overdue work, unowned work, purchases without evidence, experiments without conclusions/raw data, recurrent failures without RCA, corrective actions without retest, requirements without validation evidence and unresolved supervisor actions.

## 15. AI/MCP authority

**Auto-write allowed:** normal issue creation/update, labels, evidence links, register maintenance, calculated costs, schedule fields, summaries, indexes and documentation PRs.

**Human-gated:** baseline requirement changes, engineering design approval, major scope change, budget baseline change, closure of a major failure/RCA, acceptance of final validation results, substantive engineering-code merge and all physical/irreversible actions.

**Never automatic:** delete evidence, rewrite history, alter measured values, invent missing values/results/causes, delete failure history or silently change requirements.

## 16. Engineering Book

The Engineering Book is built continuously from the digital thread, not reconstructed from memory at the end.

```text
Requirement
   ↓
Design / ADR
   ↓
Task / implementation / PR
   ↓
Experiment or test
   ↓
Failure / RCA / change if applicable
   ↓
Evidence
   ↓
Engineering conclusion
```

The final report is a curated academic argument based on this audited project history. The viva is the students' ability to defend it.

## 17. Daily operating experience

- Morning: **What should we execute today?**
- During work: **We bought / tested / failed / changed / decided …**
- End of day: **Is anything important from today undocumented?**
- End of week: **Run the project audit and show only exceptions.**
- Before supervisor meeting: **Prepare the evidence-backed progress brief.**
- Before viva: **Show every final claim without adequate evidence.**

**Objective: maximum engineering time, minimum administrative burden, zero loss of traceability or evidence.**
