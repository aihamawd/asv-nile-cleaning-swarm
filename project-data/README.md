# Project Data Registers

This directory contains machine-readable indexes used by the AI/MCP administrative layer and generated reporting.

| File | Purpose |
|---|---|
| `gantt.csv` | schedule baseline/source for generated Gantt views |
| `requirements-traceability.csv` | requirement-to-design/test/evidence thread |
| `evidence-index.csv` | EVD index and evidence locations |
| `cost-register.csv` | budget, purchase, commitment, actual and rework cost events |
| `failure-register.csv` | failure-family, recurrence, RCA/change/retest linkage |
| `experiment-index.csv` | experiment configuration, result and evidence index |

The detailed engineering record remains in the corresponding GitHub Issue/document/PR. A CSV row is an index entry, not a duplicate narrative report.

Do not fabricate missing register values. Unknown values remain blank until evidence exists.
