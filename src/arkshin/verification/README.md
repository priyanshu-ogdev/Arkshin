# Verification & Calibration Layer (`src/arkshin/verification`)

## Purpose
Implements the calibrated Natural Language Inference (NLI) typed-decision gate downstream of LLM generation.
Evaluates claim entailment, evidence sufficiency, and action risks without prose generation.
Implements Track D2 specifications from `docs/05-verification-calibration-layer.md`.

## Key Components
- **ModernBERT-Large NLI Adapter (`nli_gate.py`)**:
  - Domain-adapted ModernBERT-large 421M encoder (Laya/Gyra) with native 8K context support and FlashAttention.
  - Scores directional entailment: $P(\text{Entail} \mid \text{Evidence}, \text{Claim})$.
- **Typed Question Evaluator (`decision_adapter.py`)**:
  - Handles Noul (yes/no), Choice, and Score typed question interfaces.
  - Decoupled gate families: Faithfulness Gate, Sufficiency Gate, Action-Risk Gate, and Containment Severity Gate.
- **Conformal Prediction Calibrator (`conformal.py`)**:
  - Implements ConfTS (Conformal Temperature Scaling) providing non-asymptotic coverage guarantees ($\alpha$-conformal risk bounds).
  - Triggers explicit human escalation (`ESCALATE`) or abstention (`ABSTAIN`) when prediction set entropy exceeds calibrated bounds.
- **Fail-Closed Gate Guard (`guard.py`)**:
  - Ensures missing evidence, hash mismatches, or gate timeouts fail closed without granting implicit approvals.
