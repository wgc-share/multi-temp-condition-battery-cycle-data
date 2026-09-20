# Dataset Card

## Summary

This dataset contains processed lithium-ion battery discharge segments designed for SOC estimation experiments under multiple thermal environments and operating-condition families. It includes randomized current profiles and detailed predefined driving-cycle profiles.

## Data collection

- Cell type: 18650 cylindrical lithium-ion cell.
- Chemistry: LiNi0.6Co0.2Mn0.2O2.
- Nominal capacity: approximately 1.50 Ah.
- Recorded signals: current, terminal voltage, capacity, temperature, time-derived features, and reference SOC.
- Sampling interval: 1 s.
- Nominal test temperatures: 10, 25, and 40 degC.
- Intermediate temperature ranges: 15--20 and 30--35 degC.
- Nominal voltage limits: 4.2 V and 2.75 V.

## Condition taxonomy

Randomized profiles are stored under `random/`:

- Staircase
- Congested
- Highway
- Urban

Detailed profiles are stored under `detailed/`:

- Highway-oriented: US06-HWY, HWFET, REP05
- Structured mixed-load: EUDC, DST, ARTERIAL
- Urban and auxiliary-load: UDDS, SC03, LA92
- Congested urban: NYCC, NUREMBERG, MANHATTAN

The detailed-condition labels use the corrected mapping maintained for this release. Public file names intentionally exclude the internal cell and segment identifiers.

## Processing

The released files are processed segment-level CSV records. The public file hierarchy and manifest organize the records by condition family and temperature bin. No raw acquisition exports, model checkpoints, hidden test labels, or internal identity fields are included in the public package.

## Recommended evaluation practices

- Preserve discharge-cycle integrity when creating train/validation/test partitions.
- Report the exact temperature bins, condition families, SOC-start protocol, and aggregation procedure.
- Do not use the public filename order as a temporal sequence or as a training label.
- Evaluate both MAE and other task-relevant metrics with a clearly defined SOC scale.

## Known limitations

- The data cover one cell form factor and chemistry family; results may not transfer to other chemistries or formats.
- The data are collected on a controlled experimental platform, not a fleet of field-operated vehicles.
- The detailed profiles encode driving-cycle current schedules and should not be interpreted as direct vehicle telemetry.
- The release is pre-publication. The maintainers may publish a corrected or expanded version; users should pin an exact version and checksum.

## Ethics, privacy, and safety

The public package contains no personal data, human-subject data, or location traces. The dataset is intended for research. Users remain responsible for validating any model before use in safety-critical battery-management applications.

## Maintenance

Report file-integrity issues, metadata errors, or mapping concerns through the repository issue tracker after publication. Maintainers should publish fixes as a new dataset version and retain prior manifests and checksums.
