# Cloud Drive Evidence Vault

GitHub remains the engineering source of truth; the Cloud Drive is the storage layer for large/raw evidence that should not be duplicated into Git history by default.

## Recommended structure

```text
ASV-FYP/
├── 01_Admin/
├── 02_Requirements/
├── 03_Design/
├── 04_CAD/
├── 05_Procurement/
│   └── PUR-###/
├── 06_Experiments/
│   └── EXP-###/
├── 07_Failures/
│   └── FAIL-###/
├── 08_Photos_Video/
├── 09_Raw_Data/
├── 10_Supervisor/
└── 11_Submissions/
```

## Evidence-link rule

Every material Drive artifact should be reachable from a GitHub engineering record through an `EVD-###` entry in `project-data/evidence-index.csv`.

Prefer stable folder/file links and include the permanent project ID in the folder or filename. Avoid names such as `final2.xlsx`, `newdesign_final.step`, or `IMG_1234.mov` when the file is an engineering record.

Recommended naming pattern:

`EVD-###_<source-id>_<short-description>_<YYYY-MM-DD>.<ext>`

## What belongs in Drive by default

- native CAD/CAE projects and large assemblies;
- photos/video;
- invoices, receipts and supplier quotations;
- large datasheets or vendor packages when needed as evidence;
- ROS bags / MCAP;
- large raw datasets;
- signed/formal documents;
- submission files and archived presentation media.

## What belongs in GitHub

- source code and configuration;
- requirements, architecture and ADRs;
- scripts/notebooks needed to reproduce analysis;
- small processed data/plots where useful;
- test/experiment metadata and conclusions;
- CSV indexes/registers;
- links to Drive evidence.

Git LFS may be used for version-coupled engineering binaries that genuinely benefit from repository versioning, but it is not the default substitute for the evidence vault.

## Integrity

Never overwrite or delete original raw evidence to make a later result look cleaner. Derived or compressed copies may be added if the original remains preserved and the transformation is documented when it affects engineering meaning.
