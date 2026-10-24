# Data Curation & Pipeline Scripts (`data/curation`)

## Purpose
Automated, human-review-free curation scripts for processing, cleaning, deduplicating,
and validating authentic cybersecurity datasets. Implements specifications from `docs/08-synthetic-data-pipeline.md`.

## Key Pipelines
- **PII & Secret Scrubber (`scrub_secrets.py`)**:
  - Regex patterns and high-entropy scanners for detecting API keys, tokens, private keys, and emails.
- **Deduplication Engine (`dedup.py`)**:
  - Exact SHA256 hashing and MinHash / dense embedding clustering (cosine similarity $> 0.92$) to eliminate duplicated CTI advisories.
- **Contamination Scanner (`contamination_check.py`)**:
  - Scans training candidates against locked evaluation benchmarks using 13-gram and 8-gram overlap filters.
- **Trajectory Sandbox Validator (`validate_trajectories.py`)**:
  - Automatically spins up Docker containers to execute CodeAct bash sequences and verify exit status codes and output artifacts.
