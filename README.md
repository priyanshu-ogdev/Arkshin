# Arkshin: Calibrated, Verified Agentic Cybersecurity LLM Platform

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%20%7C%203.11-brightgreen.svg)]()
[![Hardware](https://img.shields.io/badge/Inference-12GB_Docker-orange.svg)]()
[![Research](https://img.shields.io/badge/Target-Academic_Paper_%26_Open_Weights-purple.svg)]()

**Arkshin** is an open-weights, agentic cybersecurity AI platform combining:
1. **Domain-Specialized Foundation LLM**: Fork of RedSage-8B trained with RAFT and CodeAct on 100% authentic, execution-verified cybersecurity data.
2. **Concurrent Hybrid Retrieval (RAG)**: Git-versioned Open Knowledge Format (OKF) + embedded Kùzu property graph + vector retrieval producing immutable evidence snapshots (`snap_...`).
3. **Calibrated NLI Verification Gate**: Domain-adapted ModernBERT-large (421M) scoring claim entailment with Conformal Prediction (ConfTS) coverage guarantees.
4. **Sandboxed Agentic Execution**: Planner-Interpreter-Critic architecture compiling raw actions into typed `ActionProposal` contracts executed inside warm-pooled Firecracker microVMs.
5. **Deterministic Policy Control**: Non-bypassable scope gateway derived strictly from verified infrastructure inventory and signed ed25519 Rules of Engagement (ROE).

---

## Repository Structure

```text
Arkshin/
├── configs/             # Runtime, model, retrieval, and policy configuration files
├── data/                # Authentic dataset manifests, curation pipelines, and taxonomies
│   ├── curation/        # Ingestion, PII/secret scrubbing, deduplication, and execution validation
│   ├── manifests/       # Cryptographic provenance manifests (item_..., sha256)
│   ├── processed/       # Execution-verified training and validation splits
│   ├── raw/             # Authentic raw public corpora staging
│   └── taxonomies/      # Normalized MITRE ATT&CK, D3FEND, NVD, CWE/CAPEC mappings
├── docker/              # Multi-stage Docker inference container (12GB profile)
├── docs/                # Comprehensive 19-document PRD, architecture, and specifications
├── evaluation/          # Benchmark harnesses, calibration evaluation, and contamination audits
│   ├── adversarial/     # Scope-gateway bypass and prompt-injection adversarial suite
│   ├── benchmarks/      # RedSage-Bench, CTI-Bench, CyberMetric, SecEval runners
│   ├── calibration/     # ECE, Brier score, reliability diagrams, conformal coverage
│   ├── contamination/   # 13-gram/8-gram overlap contamination auditing tools
│   └── tool_eval/       # CTF-Dojo, InterCode-CTF, Cybench execution evaluation
├── research/            # Academic research artifacts, literature survey, and paper drafts
│   ├── paper/           # LaTeX paper draft, figures, tables, and camera-ready assets
│   └── survey/          # Literature review notes and citations (IEEE, Scopus, ScienceDirect, Springer)
├── scripts/             # Environment setup, build, benchmark, and validation scripts
├── src/                 # Core Python source package
│   └── arkshin/
│       ├── api/         # REST (FastAPI) and gRPC gateway with emergency stop
│       ├── audit/       # Append-only hash-chained tamper-evident audit ledger
│       ├── control_plane/ # Deterministic policy engine, ROE verification, capability tokens
│       ├── execution/   # Typed ActionProposal compiler, Firecracker manager, attestation
│       ├── knowledge/   # OKF connectors, Kùzu graph DB, vector retriever, snapshot generator
│       ├── models/      # LLM inference wrappers (vLLM), CodeAct compiler, claim extractor
│       └── verification/# Domain-adapted ModernBERT NLI gate (Laya/Gyra), ConfTS calibrator
├── tests/               # Unit, integration, and property test suites
│   ├── fixtures/        # Mock requests, signed ROE objects, and evidence snapshots
│   ├── integration/     # Offline end-to-end vertical slice (D0 track)
│   └── unit/            # Unit tests for schemas, policy logic, and adapters
├── .env.example         # Environment template for publisher credentials & runtime config
└── .gitignore           # Comprehensive exclusion rules (credentials, weights, caches)
```

---

## Core Principles

- **Zero Synthetic Data**: The model is trained exclusively on 100% authentic, human-authored, and execution-verified open-source datasets (Primus-Instruct, Primus-Seed, NVD, MITRE, NL2Bash, Corrected InterCode-Bash 600, CTF-Dojo).
- **Calibration is Not Control**: Calibrated gate probabilities inform human escalation, but never override signed ROE constraints, asset ownership, or risk-tier approval requirements.
- **Immutable Evidence Snapshots**: The generative LLM and the NLI verification gate consume the exact same content-hashed evidence snapshot (`snap_...`). Live re-retrieval during verification is strictly prohibited.
- **Open Science & Weights**: Released with open model weights, public training recipes, frozen benchmark evaluation harnesses, and an academic research publication.

---

## Quickstart (Containerized Inference)

Arkshin packages the complete inference and verification stack into an optimized Docker container targeting consumer and workstation GPUs ($12\text{GB}$ usable memory):

```bash
# 1. Clone repository
git clone https://github.com/arkshin/arkshin.git
cd arkshin

# 2. Configure environment
cp .env.example .env

# 3. Launch optimized inference container
docker run --gpus all -p 8000:8000 arkshin-inference:latest
```

---

## Citation

```bibtex
@article{arkshin2026,
  title={Arkshin: Calibrated, Verified Agentic Cybersecurity LLM Platform with Immutable Evidence Grounding},
  author={Arkshin Research Team},
  year={2026}
}
```
