# Weekly AI/MCP Exception Audit

Report exceptions only.

## Checks

1. Closed/Done task without acceptance evidence.
2. Open task past current Gantt target.
3. Active task without an assignee.
4. Joint task with unclear Primary Owner/Reviewer after work begins.
5. Experiment/test without raw-data location, result or conclusion.
6. Failure without evidence, containment or next action.
7. Recurrent failure family without RCA.
8. Engineering change without required retest.
9. Requirement without planned/actual verification.
10. Evidence entry without valid source/location.
11. Supervisor action past target.
12. Schedule slip affecting downstream gate.
13. Any task/file still assuming mandatory shore Fleet Manager or ESP32.
14. Any task/file treating radar as a required baseline sensor.
15. Any claim that FloW requires a new training dataset.
16. Any ML function entering mission control without deterministic baseline/acceptance evidence.
17. Any physical ASV fabrication decision made before the relevant measurement gate.
18. Any current/wind result presented without clear distinction between simulated ground truth, measured environment and inferred disturbance.

## Rules

Do not infer measured values, results or causes. Automatically fix only unambiguous administrative inconsistencies. Escalate baseline/scope changes, major failure closure and final validation acceptance.
