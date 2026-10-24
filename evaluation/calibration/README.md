# Calibration & Conformal Verification Evaluation (`evaluation/calibration`)

## Purpose
Quantifies uncertainty, confidence reliability, and selective prediction quality for the verification gates.
Implements specifications from `docs/05-verification-calibration-layer.md` and `docs/14-evaluation-layer.md`.

## Metrics & Analyses
- **Expected Calibration Error (ECE) & Brier Score**: Computed per question type (Noul, Choice, Score) and per gate.
- **Reliability Diagrams**: Visualizing model verbalized confidence vs. true empirical accuracy.
- **Conformal Coverage Verification**: Testing whether prediction-set sizes satisfy theoretical $\alpha$-coverage guarantees.
- **Faithfulness-Gap Test**: Verifying whether low verbalized confidence actively triggers downstream human escalation (`ESCALATE`) or is ignored.
- **Trajectory-Level Uncertainty**: Tracking uncertainty compounding across multi-turn agent sequences.
