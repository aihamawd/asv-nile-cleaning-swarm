# Weekly AI/MCP Exception Audit

Run once per week and report **exceptions only**. The purpose is to protect traceability without creating a weekly administrative burden for the students.

## Checks

1. `Done`/closed task without acceptance evidence.
2. Open task past Target date.
3. Active task without an assignee.
4. `[Both]` active task whose actual Primary Owner/Reviewer split is still ambiguous after execution has materially begun.
5. Purchase without technical purpose, approval status or invoice/quotation evidence.
6. Experiment/test without raw-data location, result or conclusion.
7. Failure without evidence, containment or next action.
8. Recurrent failure family without RCA.
9. RCA without corrective action or verification plan.
10. Engineering change without required retest/re-verification.
11. Requirement without a planned/actual verification link.
12. Evidence entry without a valid source record or location.
13. Supervisor action past target date or not linked to affected work.
14. Schedule slip that affects a downstream gate.
15. Budget/committed-cost variance requiring review.
16. Cloud Drive evidence not indexed in GitHub.

## Output format

```text
WEEK-### EXCEPTIONS

1. EXP-### — conclusion missing.
2. PUR-### — invoice/quotation evidence missing.
3. FAIL-### — recurrence detected; RCA required.
4. NAV-### — target missed; downstream gate impact requires review.
```

No exception means no administrative action is required beyond the normal weekly record.

## Rules

- Do not infer missing measured values or evidence.
- Do not silently change historical dates or results.
- Automatically fix only administrative inconsistencies that are unambiguous and within AI/MCP authority.
- Escalate engineering judgement, baseline/scope changes, major failure closure, budget baseline changes and final validation acceptance to the students.
