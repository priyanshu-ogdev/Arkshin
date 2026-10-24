# Integration Test Suite (`tests/integration`)

## Purpose
End-to-end offline integration tests validating the first vertical slice (Track D0/D1 milestone)
specified in `docs/16-development-readiness-and-targets.md`.

## Vertical Slice Workflow Under Test
```text
Fixture Request
   → Fixture Graph/Vector Retrieval
   → Immutable Evidence Snapshot (`snap_...`)
   → Deterministic Claim Extraction (`claim_...`)
   → Local ModernBERT NLI Decision Adapter
   → Deterministic Policy Engine Decision (`ACCEPT` / `ABSTAIN` / `ESCALATE` / `BLOCK`)
   → Append-Only Cryptographic Audit Log
```

Verifies that the LLM and the verification gate consume the exact same content-hashed evidence snapshot,
and confirms that verification never performs a live re-query against the database.
