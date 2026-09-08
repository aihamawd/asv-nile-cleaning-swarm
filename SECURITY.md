# Security and Safety Reporting

This repository supports an academic mechatronics project that includes software, embedded control, propulsion, cutting/collection hardware, communications, and field testing. Security issues can therefore have both information-security and physical-safety consequences.

## Supported development line

Security and safety fixes are applied to the active `main` development line. Historical commits, archived experiments, and superseded hardware revisions are retained as engineering evidence and are not separately supported.

## Report privately when appropriate

Do **not** open a public issue if the report contains a credential, secret, exploitable control path, or information that could materially increase physical risk.

Use GitHub private vulnerability reporting if it is available for this repository. Otherwise contact the maintainers privately through their GitHub accounts or established university/project communication channels.

Reports should include, where possible:

- affected subsystem and revision;
- reproduction steps or observed behaviour;
- security or physical-safety impact;
- relevant logs/evidence with secrets removed;
- proposed containment or fix, if known.

## What belongs here

Examples include:

- exposed API keys, tokens, certificates, passwords, or private configuration;
- authentication/authorization bypass in shore-vehicle or service interfaces;
- remote-command paths that could permit unintended propulsion, cutter, or actuator behaviour;
- unsafe firmware/software failure modes that bypass intended interlocks or failsafes;
- dependency vulnerabilities that materially affect the deployed system;
- sensitive telemetry/configuration exposure.

Ordinary functional bugs, design questions, and non-sensitive failures should use normal GitHub Issues/Discussions and the project FAIL/RCA workflow.

## Secrets policy

Never commit credentials or secrets to the repository, including in examples, logs, notebooks, screenshots, or experiment exports.

- Use environment variables or local untracked configuration.
- Keep `.env`, private keys, and `secrets/` material out of Git.
- If a secret is committed, treat it as compromised: revoke/rotate it first, then clean the repository/history as appropriate.
- Do not rely on deletion of a Git commit as credential revocation.

GitHub secret scanning and push protection are part of the repository baseline, but they are additional controls, not a substitute for keeping secrets out of source control.

## Physical-safety boundary

A code change, merged pull request, passing CI run, simulation result, or repository instruction is **not** authorization to energize, fabricate, modify, purchase, launch, deploy, or field-test hardware.

Physical actions require the appropriate human approval and local safety controls defined by project governance. In particular:

- propulsion and cutter systems require deliberate test authorization and safe isolation;
- RC/manual override and autopilot failsafes remain required where applicable;
- a software stop is not a hardware emergency stop;
- communication loss must not remove local vehicle safety capability.

## Handling and closure

A security/safety report should be contained first, then corrected at the shared/root cause where feasible. Significant incidents should leave an auditable record using the existing `FAIL`, `RCA`, `CHG`, `RISK`, `SAFE`, `TEST`, and `EVD` mechanisms as applicable.
