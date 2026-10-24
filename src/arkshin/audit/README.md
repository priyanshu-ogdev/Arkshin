# Audit & Evidence Plane (`src/arkshin/audit`)

## Purpose
Maintains the immutable, append-only, tamper-evident cryptographic event ledger for the Arkshin platform.
Implements specifications from `docs/15-evidence-contract-and-control-plane.md` and `docs/18-architecture-artifact-specifications.md`.

## Key Components
- **Audit Ledger Service (`ledger.py`)**:
  - Implements hash-chained event persistence: `previous_event_hash` → `payload_hash` → `event_id`.
  - Captures the complete lineage: Request → Query → Snapshot → Claims → Gate Result → Policy Decision → Token → Execution → Attestation.
- **Write-Ahead Buffer (`wal.py`)**:
  - Bounded signed write-ahead buffer that preserves audit events during transient storage outages.
  - Halts consequential actions if the WAL reaches full capacity (fail-closed behavior).
- **Cryptographic Replay Engine (`replay.py`)**:
  - Replays historical operational traces offline to verify that decisions strictly match recorded inputs and policies.
- **Secret & PII Redactor (`redactor.py`)**:
  - Strips credentials and private identifiers from audit records before long-term retention.
