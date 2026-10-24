# Docker Packaging & Containerization (`docker`)

## Purpose
Multi-stage build files and orchestration configurations for packaging the entire Arkshin inference
and verification stack into a reproducible, optimized Docker container.
Implements specifications from `docs/09-deployment-packaging.md`.

## Contents
- **`Dockerfile.inference`**:
  - Multi-stage build based on Debian-slim with NVIDIA CUDA 12.4+ and cuDNN 9.
  - Bundles vLLM with AWQ 4-bit, TurboQuant KV compression, embedded Kùzu graph DB, vector index,
    and ModernBERT/Laya verification runtime.
  - Runs under unprivileged `secagent` user with dropped Linux capabilities.
- **`entrypoint.sh`**:
  - Validates GPU passthrough, initializes embedded buffer pools, runs local health probes, and starts FastAPI.
- **`docker-compose.yml`**:
  - Orchestrates the inference container with optional Firecracker execution broker sidecars.
