# GitHub Project Configuration — ASV Swarm for Nile Cleaning

The project should be limited operationally to `kagetsu2/asv-nile-cleaning-swarm`.

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

## Project limitation

Repository issues, sub-issues, commits and planning files are authoritative. GitHub Projects-v2 UI fields/views are presentation and execution surfaces; they must not become a second independent task database.
