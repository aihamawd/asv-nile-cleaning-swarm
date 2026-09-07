# Contributing to ASV Nile Cleaning Swarm

**How to work on tasks, create issues, and submit pull requests.**

---

## Quick Start

1. **Create an issue** using the appropriate GitHub Issue Template (task, requirement, experiment, etc.)
2. **Assign an owner and reviewer** — typically one student per task
3. **Create a feature/fix branch** from main:
   ```bash
   git checkout -b feature/ID-number-brief-description
   # Examples:
   # feature/nav-014-state-estimator
   # feature/flt-006-task-reallocation
   # fix/elec-011-controller-timeout
   ```
4. **Work, commit, and push** with clear commit messages
5. **Open a pull request** referencing the issue
6. **Peer review and CI checks** before merge
7. **Merge to main** when approved

---

## Branch Naming Convention

**Format:**
```
{type}/{ID}-{brief-slug}
```

**Type:** `feature`, `fix`, `chore`, `docs`, `experiment`

**ID:** Use project ID or issue number
- `feature/nav-014-state-estimator` (ADR/design decision)
- `feature/SW-021-task-allocator` (Software task)
- `fix/elec-011-controller-timeout` (Bug fix)
- `experiment/exp-016-long-range-nav` (Experimental work)
- `chore/register-update` (Administrative)

---

## Commit Messages

**Format:**
```
{type}: {brief description}

{optional detailed explanation}

Related: #{issue-number}
```

**Examples:**
```
feat(nav): implement kalman filter state estimator

Implemented steady-state Kalman filter for INS/GPS fusion.
Threshold tuned empirically from lab trials (EXP-016).

Related: #42
```

```
fix(elec): add heatsink to motor controller

Controller overheating after 45 min continuous operation (FAIL-006).
Upgraded from 10mm to 20mm aluminum heatsink with thermal compound.
Tested in lab: 2hr sustained run without thermal shutdown.

Related: #38, RCA-003
```

---

## Pull Request Template

Every PR must complete the PR template in `.github/PULL_REQUEST_TEMPLATE.md`:

### Required Sections

1. **Related Issue(s):** Link to GitHub issue(s) this PR addresses
   ```
   Closes #42
   Related to #38, #41
   ```

2. **Engineering Purpose:** What problem does this solve? Why now?
   ```
   Implements Kalman filter for state estimation (ADR-003).
   Needed for single-vessel autonomous navigation (M4 gate).
   ```

3. **Changes Made:**
   ```
   - Added kalman_filter.cpp with steady-state tuning
   - Updated nav_stack.launch to enable EKF node
   - Added test suite for filter divergence detection
   ```

4. **Validation Performed:**
   ```
   - Unit tests: 12/12 pass
   - Lab trial (EXP-016): filter stable for 2hr continuous run
   - Peer review by Omar (code inspection)
   ```

5. **Evidence:** Where is the raw data/results?
   ```
   Raw data: Cloud Drive/Experiments/EXP-016/
   Test results: tests/state_estimator_tests.log
   Video: EVD reference pending
   ```

6. **Risks/Regressions:** Any edge cases or breaking changes?
   ```
   - Filter divergence risk if GPS drops >90 seconds (mitigation: dead-reckoning fallback, CHG-005)
   - Backward compatible with existing nav stack
   ```

7. **Reviewer:** Assign peer for review
   ```
   @omar (or @aiham)
   ```

8. **Checklist:**
   ```
   - [x] Code follows project style
   - [x] New functions documented
   - [x] CI tests pass
   - [x] Evidence linked
   - [x] Related issues updated
   ```

---

## Issue Creation Guidelines

**Always use Issue Templates.** Do not create blank issues.

### Available Templates

1. **Engineering Task** — Work item for feature/fix/component
2. **Requirement** — REQ specification or acceptance criteria
3. **Experiment** — EXP procedure and results capture
4. **Verification/Test** — TEST procedure or validation result
5. **Failure** — FAIL incident report
6. **Root Cause Analysis** — RCA investigation
7. **Engineering Change** — CHG request or approved modification
8. **Purchase** — PUR order or procurement request
9. **Risk/Safety** — RISK or SAFE procedure
10. **Design Decision** — ADR rationale and trade-offs
11. **Supervisor Meeting** — MIN meeting record
12. **Weekly Review** — WEEK status snapshot

### Minimum Fields (All Issues)

- **ID** — Project ID (REQ-007, EXP-016, etc.) or auto-assign
- **Owner** — Primary responsible student
- **Reviewer** — Peer reviewer for QA
- **Title** — Precise, descriptive
- **Description** — Problem statement, acceptance criteria, scope
- **Related Issues/Requirements** — Links for traceability
- **Evidence** — Cloud Drive location or link
- **Milestone** — Which M1–M11 gate?

---

## Code Review Standards

When reviewing a peer's PR:

1. **Correctness:** Does it solve the stated problem? Any logical errors?
2. **Traceability:** Is it linked to requirements/ADR/experiments?
3. **Evidence:** Are results/tests documented? Raw data location clear?
4. **Style:** Consistent with project conventions? Comments clear?
5. **Risk:** Any edge cases, potential regressions, or safety issues?
6. **Documentation:** Updated docstrings, README, or design docs?

**Approve with confidence** once satisfied. Flag concerns as requests for changes or suggestions.

---

## Workflow States

**GitHub Project statuses:**

- **BACKLOG** — Ideas, not yet started
- **READY** — Requirements clear, owner assigned, ready to start
- **IN PROGRESS** — Active work
- **BLOCKED** — Waiting for decision, external dependency, or peer
- **TESTING** — In validation (experiments, peer review)
- **REVIEW** — Awaiting supervisor approval (ADRs, scope changes)
- **DONE** — Complete with evidence linked

**Move issues** to reflect current status. Use issue comments to explain blocks/delays.

---

## Tips for Success

1. **Link early, link often.** Use issue comments to reference related work, decisions, evidence.
2. **One owner per executable task.** Both students may contribute, but make accountability clear.
3. **Small PRs.** Easier to review, faster merge, clearer history.
4. **Document assumptions.** If something is uncertain, flag it in the issue or PR.
5. **Use evidence links.** Always reference Cloud Drive raw data, not summaries.
6. **Weekly sync.** Attend supervisor meetings and complete weekly reviews.

---

**Last Updated:** 2026-09-07 (Bootstrap)
