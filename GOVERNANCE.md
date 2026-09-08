# Engineering Governance

This repository is the authoritative engineering record for the 2026/2027 Nile ASV graduation project.

## 1. Change control

- `main` is the integration baseline.
- Engineering work should be traceable to a permanent project ID where practical.
- Design freezes require evidence, not preference alone.
- Physical/A3 actions (fabrication, irreversible hardware modification, energized testing, field deployment, purchasing commitments) require explicit human approval.
- Software, documentation, simulation, analysis, and repository maintenance may proceed autonomously when they remain reversible and within the approved project architecture.

## 2. Required digital thread

Use the repository ID taxonomy defined in `README.md`.

Minimum traceability for significant work:

`REQ -> ADR/design -> implementation -> TEST/EXP -> EVD -> result/change`

Failures are recorded as `FAIL-###`; root-cause work may create `RCA-###`; accepted corrective modifications may create `CHG-###`.

## 3. Design authority and boundaries

The current baseline is a mixed fleet of 3–4 physical ASVs: one new-build vessel and 2–3 inherited vessels where restoration/retrofit is technically justified.

Do not freeze prematurely:
- final payload/capacity;
- hull material and dimensions;
- cutter topology;
- propulsion hardware;
- RTK or advanced sensing;
- fleet allocation algorithm;
- exact solar contribution.

Fleet coordination is mission-level. Continuous motor control and safety-critical local autonomy remain onboard each vessel.

## 4. Evidence gates

Progression is expected through:

1. bench validation;
2. subsystem tests;
3. controlled float/propulsion tests;
4. single-vessel autonomous operation;
5. cleaning/hyacinth handling;
6. multi-vessel communication;
7. cooperative task allocation;
8. fault/reallocation tests;
9. representative field validation.

No later-stage demonstration substitutes for an unresolved safety-critical earlier gate.

## 5. Repository rules

- Never commit credentials, private keys, tokens, or passwords.
- Commit reproducible engineering inputs, source files, configuration, evidence, and relevant outputs.
- Use Git LFS for large binary engineering artifacts covered by `.gitattributes`.
- Do not commit ROS 2 `build/`, `install/`, or `log/` trees or other regenerable caches.
- Native files are preferred over screenshot-only evidence when the native source exists.
- Do not rewrite or delete historical evidence simply because a later design supersedes it.

## 6. Safety language

A communications-dependent shore stop is a software stop, not a hardware emergency stop. Physical isolation, onboard failsafes, RC/manual override, and software stop functions must be documented distinctly.

## 7. Completion rule

A task is not considered engineering-complete only because code or CAD exists. Completion requires the acceptance evidence stated by its issue/test/experiment record, or an explicit documented reason why validation is deferred.
