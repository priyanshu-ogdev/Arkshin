# Platform Configurations (`configs`)

## Purpose
Hierarchical YAML configuration files controlling inference, retrieval weights, policy thresholds,
calibration parameters, and tool registry definitions.

## Key Configs
- **`inference.yaml`**: vLLM serving parameters, AWQ quantization settings, TurboQuant KV-cache bitwidth, batch size, and max context tokens.
- **`retrieval.yaml`**: OKF data paths, Kùzu graph buffer size, BM25 parameters, dense embedding models, and reranker thresholds.
- **`verification.yaml`**: ModernBERT NLI checkpoint paths, Conformal Prediction $\alpha$ coverage targets, and temperature scaling parameters.
- **`policy.yaml`**: Risk-tier approval matrix, blast-radius boundaries, and fail-closed timeout rules.
- **`tools.yaml`**: Tool registry definitions (capabilities, argument schemas, network boundaries, compensation hooks).
