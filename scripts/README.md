# Project Utility Scripts (`scripts`)

## Purpose
Automation scripts for environment bootstrapping, dataset downloading, benchmark execution,
Docker image building, and CI/CD validation.

## Key Scripts
- **`setup_env.sh` / `setup_env.bat`**: Creates Python virtual environment, installs PyTorch with CUDA support, and configures dependencies.
- **`download_datasets.py`**: Authenticated script for downloading authentic public datasets (Primus, NVD, MITRE, NL2Bash, InterCode, CTF-Dojo).
- **`build_docker.sh`**: Multi-stage build script compiling the optimized 12GB Docker container with TensorRT/vLLM optimizations.
- **`run_benchmarks.py`**: Orchestrates evaluation runs across RedSage-Bench and CTF benchmarks, computing contamination statistics.
