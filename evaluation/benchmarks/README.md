# Knowledge & Reasoning Benchmarks (`evaluation/benchmarks`)

## Purpose
Execution harnesses for static cybersecurity knowledge, reasoning, and CTI benchmarks.
Implements specifications from `docs/14-evaluation-layer.md`.

## Primary Benchmarks
- **RedSage-Bench**: 30K Multiple-Choice Questions + 240 open-ended CTI items.
  - Baseline to beat: 81.30% (Ins) / 81.10% (DPO).
- **CTI-Bench**: Comprehensive CTI evaluation across CTI-MCQ, CTI-RCM, CTI-VSP, and CTI-ATE tasks.
- **CyberMetric, SecEval, MMLU-CSec**: Standard industry reasoning and domain knowledge suites.
- **Attribution Accuracy Scorer**: Evaluates whether cited source passages logically entail the generated claim.
