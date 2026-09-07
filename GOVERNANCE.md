# Project Governance

**Cooperative Autonomous Surface Vessel Swarm for Nile Surface Cleaning**

This document establishes decision authority, approval workflows, and accountability structures for the project.

---

## Decision Authority

### Engineering Design Approval

**Decision:** ADR (Architecture/Design Records), major component selection, significant scope changes

**Authority:** Supervisor (final)

**Process:**
1. Student submits ADR issue with:
   - Problem statement
   - Options considered
   - Recommended solution with justification
   - Trade-offs and risks
   - Cost/schedule impact
   - Evidence/references
2. Peer review by other student
3. Supervisor approval before implementation

**Fallback:** If supervisor unavailable, document decision with rationale and flag for post-decision review.

### Requirement Changes

**Decision:** Adding, removing, or significantly changing REQ

**Authority:** Supervisor (in consultation with students)

**Process:**
1. Document change request with justification
2. Impact analysis: scope, schedule, budget, risk
3. Supervisor approval
4. Update requirements traceability matrix

### Budget Changes

**Decision:** Baseline budget overages >10%, major purchase reallocations

**Authority:** Supervisor (may escalate to academic program lead)

**Process:**
1. Justify overage with evidence (quotes, unexpected costs)
2. Propose mitigation or reallocation
3. Supervisor approval before commitment

### Scope Baseline Changes

**Decision:** Fleet composition, vessel count, testing environment, major feature removal

**Authority:** Supervisor (after consultation with students)

**Process:**
1. Document rationale (technical, budget, schedule, risk)
2. Supervior decision with documented reasoning
3. Update milestone plan and project board

### Purchase Commitments

**Decision:** Individual orders >£500 or cumulative annual >£2000

**Authority:** Supervisor review

**Process:**
1. Create PUR issue with specifications, vendor, cost, delivery, risk
2. Attach quotation/invoice
3. Link to engineering requirement or experiment
4. Supervisor approval before placing order

### Failure/RCA Closure

**Decision:** Closing FAIL or RCA issues without corrective action or accepting unresolved risk

**Authority:** Supervisor (after student RCA)

**Process:**
1. Complete RCA with root cause evidence
2. Propose corrective action (CHG) or document acceptance of risk
3. Supervisor sign-off
4. Close issue with evidence link

### Experimental Validation / Pass/Fail

**Decision:** Accepting EXP result as PASS (meeting acceptance criteria)

**Authority:** Students (with peer review); Supervisor for gate-level decisions

**Process:**
1. Complete EXP with measured data, analysis, conclusion
2. Peer review confirms measurement integrity
3. For gate-level validation (e.g., M9), supervisor confirms
4. Link EXP to requirements/ADR for traceability

---

## Approval Workflow

### Pull Request Review

**Substantive Engineering Code / Documentation:**
- Requires peer review (other student)
- Requires passing CI/tests
- Supervisor spot-check for major architectural changes (ADRs, SYS decisions)

**Administrative/Data Updates:**
- Registers, indices, evidence links
- Issue templates, documentation clarifications
- May auto-merge if CI passes, with human audit in weekly review

### Issue Creation

**All Issues:**
- Use GitHub Issue Templates (do not create blank issues)
- Fill in required fields (ID, owner, acceptance criteria)
- Link to related requirements/issues
- Assign owner and reviewer

**Critical Issues (ADR, FAIL, RCA, RISK, major CHG):**
- Created by proposer
- Peer review before starting work
- Supervisor review before closure

---

## Accountability

### Task Ownership

Every executable task (issue, PR, experiment) must have:
- **Primary Owner:** Student responsible for delivery
- **Reviewer:** Other student for peer review
- **Acceptance Criteria:** Clear completion definition

**No ambiguous shared ownership.** Both students may contribute, but one is accountable.

### Evidence

Every completed task must reference:
- **Experiments:** Raw data location (Cloud Drive), measured results, analysis
- **Purchases:** Invoice, supplier, delivery confirmation
- **Design Decisions:** Rationale, alternatives considered, risk assessment
- **Failures:** Reproduction steps, root cause evidence, corrective action
- **Code/Documentation:** Link to PR, CI results, peer review

### Audit Trail

All decisions are traceable:
- Issue comments document rationale
- Git history shows who made changes and when
- GitHub Project tracks status and milestone
- Weekly review identifies exceptions

---

## Escalation

If a decision cannot be made within authority:

1. **Document the decision point** in the issue with options and uncertainty
2. **Set a decision deadline** (e.g., "decision needed by Friday end-of-day")
3. **Escalate to supervisor** with summary and recommended path forward
4. **Record supervisor decision** with rationale
5. **Update issue with outcome** and proceed

Do NOT proceed with engineering work awaiting a gated decision unless fallback is approved.

---

## Meeting Protocol

### Supervisor Meetings (MIN-###)

**Weekly checkpoint (recommended Fridays):**
- Agenda: exceptions, blocked work, scope/schedule/budget changes
- Duration: 30 min target
- Output: MIN issue with:
  - Decisions made
  - Actions assigned (with owner and deadline)
  - Risk flags
  - Next week priorities

### Weekly Review (WEEK-###)

**Every Friday or project cycle end:**
- Review project board status
- Audit registers for incomplete records
- Snapshot Gantt and frozen in docs/project-management/gantt/
- Generate weekly summary with:
  - Tasks completed
  - Blocked/overdue work
  - Risk/budget/schedule changes
  - Key decisions
  - Next week focus

---

## AI/MCP Authority

**AUTO-WRITE ALLOWED:**
- Create/update normal issues (using templates)
- Update issue metadata (labels, status, links)
- Create/update evidence indices
- Calculate costs from purchase records
- Generate summaries, audit reports, Gantt artifacts
- Create/merge administrative PRs (registers, indices, documentation)

**HUMAN-GATED (Supervisor approval required):**
- Create ADR / major design decisions
- Change baseline requirements
- Accept major scope changes
- Close FAIL/RCA without corrective action
- Accept final validation results (M9, M10)
- Merge substantive engineering code PRs

**NEVER AUTOMATIC:**
- Delete evidence or historical records
- Rewrite measured experimental results
- Invent missing data or calculations
- Alter invoices or raw datasets
- Silently change requirements
- Overwrite failure/RCA decisions

---

## Logbook Attribution

For Greenwich individual logbook requirements:

**Primary Owner** = Student completing the task (most logbook hours)
**Reviewer** = Peer review contributions (secondary hours)
**Git Author** = Code/documentation contributor
**Issue Author** = Issue creator

The weekly review and GitHub history together form the evidence for individual contribution.

---

**Approved:** 2026-09-07 (Bootstrap)
**Next Review:** After M1 completion
