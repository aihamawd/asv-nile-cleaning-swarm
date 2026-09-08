# GitHub Project Configuration — ASV Swarm for Nile Cleaning

**Operational repository:** `aihamawd/asv-nile-cleaning-swarm`
**GitHub Project:** `ASV Swarm for Nile Cleaning` — user project #1

The Project is an execution view over repository Issues. It must not become a second independent task database.

## Current hierarchy

The repository contains **11 milestone/gate parent issues plus 58 engineering sub-issues (69 project items total)**.

Parent gates are intentionally unassigned; executable sub-issues carry the actual assignees.

## Live fields

- Title
- Assignees
- Status
- Start date
- Target date
- Parent issue
- Sub-issues progress
- Labels
- Linked pull requests
- Reviewers (built-in where applicable)

Start and Target dates are populated across all 69 project items.

## Live views

1. **Master Plan** — complete execution table.
2. **Execution Board** — status board.
3. **Current Queue** — `status:"In Progress"`.
4. **Roadmap** — Start/Target timeline.
5. **Aiham Tasks** — `assignee:aihamawd`.
6. **Omar Tasks** — `assignee:omaramer13`.
7. **Milestone Gates** — `no:assignee`.

## Assignment policy

GitHub Assignees are authoritative:

- `[Aiham]` → `@aihamawd`
- `[Omar]` → `@omaramer13`
- `[Both]` → both while the work is genuinely joint

The bracketed title marker is a visual planning cue; it does not replace the Assignees field.

For joint tasks that become predominantly one student's work, establish Primary Owner + Reviewer/Supporting Engineer when the task becomes active so individual contribution remains defensible.

## Status policy

The live Status field currently exposes:

`Todo · In Progress · Done`

Preferred mature workflow when the Project field can be safely extended:

`Todo → Ready → In Progress → Blocked / Testing / Review → Done`

Until the live field is extended, do not create duplicate status labels or a second status spreadsheet. Use the Issue/PR evidence and comments to explain a temporary blocker/test/review state while keeping the Project field authoritative.

## Initial execution state — 8 September 2026

- `#14 M1.1 [Both]` — In Progress — Aiham + Omar.
- `#15 M1.2 [Omar]` — In Progress — Omar.
- `#16 M1.3 [Aiham]` — In Progress — Aiham.
- `#17 M1.4` — next after relevant audit evidence.
- `#18 M1.5` — M1 gate-closure task.

## Project/PR integration

Visible views include **Linked pull requests** so an active engineering task can be traced directly to the reviewed repository change. Meaningful changes should use a feature/fix branch and PR under the protected `main` policy.

## Roadmap rule

GitHub Project Start/Target fields own the operational schedule. `project-data/gantt.csv` and rendered Gantt output are reporting/generated representations and must not diverge into a separate schedule.
