# Dataset Manifests (`data/manifests`)

## Purpose
Maintains machine-readable, cryptographic provenance records for all ingested training, calibration,
and evaluation samples. Implements specifications from `docs/07-dataset-layer.md` and `docs/08-synthetic-data-pipeline.md`.

## Manifest Schema
Each dataset item is cataloged in YAML/JSON manifests specifying:
- `item_id`: Unique identifier (`item_...`).
- `source_dataset`: Source identifier (e.g. `primus_instruct`, `cve_nvd`, `intercode_bash_corrected`).
- `source_license`: Open-source license identifier (e.g. `ODC-BY`, `MIT`, `CC0`).
- `provenance_class`: `human_authored` or `execution_verified` (zero synthetic data).
- `source_sha256`: Cryptographic content checksum.
- `pii_credential_scan`: Verification status of automated secret/PII scrubbing (`pass`).
- `contamination_status`: Multi-benchmark n-gram overlap check (`clean` or `quarantined`).
- `execution_verified`: Boolean attestation of successful containerized execution.
