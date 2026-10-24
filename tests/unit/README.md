# Unit Test Suite (`tests/unit`)

## Purpose
Comprehensive isolated unit tests for contracts, schemas, AST Cypher validation, deterministic policy transitions,
NLI decision adapters, and capability token verification. Implements Track D0 exit criteria.

## Test Modules
- **`test_contracts.py`**: Validates JSON/YAML schemas for Evidence Snapshots, Structured Claims, and Action Proposals.
- **`test_policy.py`**: Verifies deterministic policy state transitions (`ACCEPT`, `ABSTAIN`, `ESCALATE`, `BLOCK`) on mock inputs.
- **`test_roe.py`**: Validates ed25519 signature checking, expiration verification, and revocation epochs.
- **`test_cypher_ast.py`**: Tests read-only AST parser on Cypher queries, rejecting mutations and unauthorized procedures.
- **`test_nli_adapter.py`**: Tests ModernBERT decision adapter formatting, input clamping, and fail-closed timeout handling.
