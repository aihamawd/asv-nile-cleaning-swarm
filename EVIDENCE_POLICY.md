# Evidence Policy

Engineering claims in this project must be supportable by traceable evidence.

## Evidence classes

Evidence may include:

- raw sensor or telemetry data;
- ROS bags / MCAP files;
- photographs and video;
- calibrated measurements;
- test sheets and checklists;
- simulation input files and result exports;
- CAD/CAE native files and drawings;
- firmware/software logs;
- supplier quotations and component datasheets;
- supervisor or stakeholder records.

## Minimum evidence record

Each `EVD-###` reference should identify:

- source test/experiment/design record;
- date;
- configuration/revision;
- file path(s);
- author/operator where relevant;
- what claim the evidence supports;
- limitations or anomalies.

## Raw vs processed data

Preserve raw evidence whenever practical. Processed plots, filtered data, screenshots, or summary tables must not replace the raw source when the raw source is available.

If data processing materially affects the conclusion, preserve the script/notebook/configuration used to produce the processed result.

## Reproducibility

For simulation and software evidence, preserve enough information to rerun the result:

- model/source revision;
- tool/version where material;
- configuration/parameters;
- input data;
- command or launch procedure;
- expected output/check.

## Failures and negative results

Failed tests, jams, leaks, navigation divergence, brownouts, communication loss, structural deformation, and similar negative outcomes are valid engineering evidence. They must not be deleted simply because a later iteration succeeds.

## Naming recommendation

Where practical:

`EVD-###_<source-id>_<short-description>_<YYYY-MM-DD>.<ext>`

Example:

`EVD-014_TEST-009_thruster-static-thrust_2026-10-18.csv`

## Integrity

Do not manipulate images, video, plots, or datasets in ways that change the engineering meaning without documenting the transformation. Cosmetic cropping/compression is acceptable when the original is preserved.
