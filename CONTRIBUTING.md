# Contributing

This repository is an engineering record, not only a source-code repository. Contributions should preserve traceability and reproducibility.

## Before starting

1. Read `README.md`, `GOVERNANCE.md`, and `EVIDENCE_POLICY.md`.
2. Identify the relevant permanent project ID or create a GitHub issue with the appropriate template.
3. Confirm the work does not bypass a required physical/safety approval.

## Branch and commit practice

- Prefer short-lived topic branches for substantive work.
- Suggested branch names: `mech/MECH-###-short-name`, `elec/ELEC-###-short-name`, `sw/SW-###-short-name`, `exp/EXP-###-short-name`, `docs/MIN-###-short-name`.
- Reference the permanent ID in commits when one exists.
- Keep commits coherent enough to audit or revert.

## Pull requests

A pull request should state:

- problem/objective;
- affected project IDs;
- files/subsystems changed;
- verification performed;
- evidence paths/IDs;
- known limitations;
- whether hardware, safety, procurement, or field-test approval is required.

Do not mark a change as validated when only compilation, simulation, or visual inspection was performed.

## Engineering files

- Commit native CAD/CAE/simulation source files when they are the engineering source of truth.
- Use Git LFS for configured large binary types.
- Do not commit regenerable build/cache directories.
- Record software/tool version when a result depends materially on it.

## Experiments and tests

Each significant experiment/test should record:

- ID and objective;
- configuration and revision;
- date/location when relevant;
- instruments/sensors and calibration context;
- procedure;
- raw evidence location;
- pass/fail or measured result;
- anomalies/failures;
- conclusion and next action.

## Safety

Never energize, fabricate, modify, purchase, or deploy hardware solely because a repository change says to do so. Physical actions require the appropriate human approval and local safety controls.
