# NLI Gate Domain Adaptation (`training/gate_adaptation`)

## Purpose
Domain adaptation and fine-tuning scripts for the ModernBERT-large 421M verification gate (Laya/Gyra).
Implements specifications from `docs/05-verification-calibration-layer.md`.

## Methodology
- **Backbone**: ModernBERT-large (421M parameters) initialized with 8K native context support.
- **Objective**: REINFORCE against strictly proper scoring rules (Brier score loss, clipped log loss)
  with GRPO-style group-mean baselines ("Rewarding Doubt", RLCR).
- **Training Pairs**:
  - Authentic NVD vulnerability descriptions ↔ CISA KEV remediation actions.
  - MITRE ATT&CK technique descriptions ↔ D3FEND defensive countermeasures.
  - Security advisory summaries ↔ official patch notes.
- **Compute Budget**:
  - ~4–5 hours on 2x T4 GPUs or $<1.5\text{ hours}$ on a single RTX 6000 Ada.
  - Lifts zero-shot classification from near-random (0.362) to $>0.82$ on cybersecurity claim verification.
