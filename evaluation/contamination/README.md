# Contamination Auditing Suite (`evaluation/contamination`)

## Purpose
Implements multi-scale n-gram overlap scanning to ensure zero contamination between training corpora
and benchmark evaluation sets. Implements specifications from `docs/14-evaluation-layer.md`.

## Methodology
- **n-Gram Overlap Scanner**:
  - Computes 13-gram and 8-gram exact overlaps between all training splits and benchmark questions/contexts.
- **Reporting Requirement**:
  - Every benchmark score claimed in the research paper must be published alongside its exact
    measured contamination percentage.
  - Zero tolerance for benchmark leakage into the SFT or RL datasets.
