# GitHub Project Configuration — ASV Swarm for Nile Cleaning

The project should be limited operationally to `kagetsu2/asv-nile-cleaning-swarm`.

## One-time project import

After setting the Project's **Default repository** to `kagetsu2/asv-nile-cleaning-swarm`, use **Add item → Add from repository / search** and bulk-add:

```text
repo:kagetsu2/asv-nile-cleaning-swarm is:issue is:open
```

The repository currently contains the complete execution hierarchy: **11 milestone/gate parent issues plus 58 engineering sub-issues (69 open issues total)**.

Initial execution state on 8 September 2026:

- `#14 M1.1` — active now.
- `#15 M1.2` — active/ready as legacy hardware becomes available.
- `#16 M1.3` — active/ready as legacy electrical/software assets become available.
- `#17 M1.4` — next after the relevant audit evidence.
- `#18 M1.5` — M1 gate closure task.
- Later milestone tasks remain backlog until their dependencies are satisfied.

## Recommended fields

GitHub Project currently exposes `Status` and `Sub-issues progress`. Add these project fields in the UI when available:

| Field | Type | Recommended values/use |
|---|---|---|
| Status | Single select | Backlog · Ready · In Progress · Waiting/Blocked · Validation · Done |
| Workstream | Single select | Mechanical · Electrical/Power · Navigation/Control · Cleaning · ROS 2/Software · Fleet · Validation · Documentation/PM |
| Owner | Single select | Aiham · Omar · Both |
| Priority | Single select | P0 Critical · P1 High · P2 Normal · P3 Low |
| Start | Date | Planned start |
| Target | Date | Planned completion |
| Gate | Text/Single select | M1…M11 |
| Sub-issues progress | Built-in | Parent milestone completion |

## Recommended views

1. **Execution Board** — group by Status; filter repository to `kagetsu2/asv-nile-cleaning-swarm`.
2. **Milestones** — filter titles beginning `M1`…`M11`; show Sub-issues progress.
3. **Roadmap / Gantt** — use Start and Target fields.
4. **By Owner** — group by Owner.
5. **By Workstream** — group by Workstream.
6. **Validation Queue** — Status = Validation.
7. **Blocked / Waiting** — Status = Waiting/Blocked.

## Workflow policy

- New actionable issue: `Backlog`.
- Accepted for near-term execution: `Ready`.
- Actively worked: `In Progress`.
- External dependency, procurement, approval or unresolved blocker: `Waiting/Blocked`.
- Implementation complete but evidence/gate not yet accepted: `Validation`.
- Close issue only when acceptance criteria and evidence are satisfied: `Done`.

## Parent/sub-issue model

Each `M# — ...` issue is a milestone/gate parent. Engineering work is created as sub-issues so the built-in Sub-issues progress field gives a live completion indicator without duplicating work in a spreadsheet.

The milestone parent issues are:

- `#3` M1 — Requirements & Legacy Vessel Characterisation
- `#4` M2 — Fleet Mechanical Readiness
- `#5` M3 — Electrical & Propulsion Integration
- `#6` M4 — Single-Vessel Autonomous Navigation
- `#7` M5 — Cleaning / Water-Hyacinth Handling Prototype
- `#8` M6 — Multi-Vessel Communication
- `#9` M7 — Cooperative Task Allocation
- `#10` M8 — Fault-Aware Reallocation Behaviour
- `#11` M9 — Controlled Experimental Validation
- `#12` M10 — Representative Nile-Environment Validation
- `#13` M11 — Final Engineering Book, Report, Poster & Viva

## Project limitation

Repository issues, sub-issues, commits and planning files are authoritative. GitHub Projects-v2 UI fields/views are presentation and execution surfaces; they must not become a second independent task database.
