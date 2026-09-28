# Weekly AI/MCP Exception Audit

Report exceptions only.

## Checks

1. Closed/Done task without acceptance evidence.
2. Open task past current Gantt target.
3. Active task without an assignee.
4. Joint task with unclear Primary Owner/Reviewer after work begins.
5. Purchase without requirement/calculation basis, approval state or quotation/invoice evidence.
6. Purchase that duplicates usable legacy hardware without a documented reason.
7. Experiment/test without raw-data location, result or conclusion.
8. Failure without evidence, containment or next action.
9. Recurrent failure family without RCA.
10. Engineering change without required retest.
11. Requirement without planned/actual verification.
12. Evidence entry without valid source/location.
13. Supervisor action past target.
14. Schedule slip affecting downstream gate.
15. Budget variance from the EGP 40k baseline requiring review.
16. Any task/file still assuming mandatory shore Fleet Manager, ESP32 or funded radar.
17. Any claim that FloW requires a new training dataset.
18. Any ML function entering mission control without deterministic baseline/acceptance evidence.
19. Any physical ASV purchase/fabrication decision made before the relevant measurement gate.
20. Any current/wind result presented without clear distinction between simulated ground truth, measured environment and inferred disturbance.

## Rules

Do not infer measured values, costs, results or causes. Automatically fix only unambiguous administrative inconsistencies. Escalate baseline/scope, major failure closure, budget changes and final validation acceptance.
