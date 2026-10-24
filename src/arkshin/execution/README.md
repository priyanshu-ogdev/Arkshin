# Agentic Execution Layer (`src/arkshin/execution`)

## Purpose
Manages the translation of model-generated proposals into typed, bounded actions, execution
sandboxing via warm-pooled Firecracker microVMs, and cryptographic execution attestations.
Implements Track D3 & D4 specifications from `docs/06-agentic-execution-layer.md`.

## Key Components
- **Action Compiler (`compiler.py`)**:
  - Compiles CodeAct bash commands into strictly typed `ActionProposal` contracts (`action_...`).
  - Rejects arbitrary shell pipes, subshells, metacharacters, and unapproved tool invocations.
- **Signed Tool Registry (`registry.py`)**:
  - Authoritative registry defining tool capabilities, argument schemas, network boundaries, and rollback compensations (nmap, gobuster, etc.).
- **Execution Broker & Firecracker Manager (`broker.py`, `firecracker_pool.py`)**:
  - Manages warm microVM pools: `BOOTING` → `IDLE` → `BOUND` → `DRAINING` → `DESTROYED`.
  - Binds target-specific network namespaces only after policy authorization; destroys microVM unconditionally upon completion.
- **Simulator Runtime (`simulator.py`)**:
  - Offline execution simulator (Track D3) validating state machines, time/step budgets, and prompt-injection mitigations.
- **Attestation Writer (`attestation.py`)**:
  - Generates immutable execution attestations linking tool versions, stdout/stderr hashes, exit codes, and observed effects.
