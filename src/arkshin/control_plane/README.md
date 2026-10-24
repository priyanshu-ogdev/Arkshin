# Control Plane (`src/arkshin/control_plane`)

## Purpose
The authoritative coordination and authorization boundary of the Arkshin platform.
Implements Track D0 specifications from `docs/15-evidence-contract-and-control-plane.md`
and `docs/10-scope-authorization-model.md`.

## Key Components
- **Deterministic Policy Engine (`policy_engine.py`)**:
  - Evaluates inputs and returns strictly one of: `ACCEPT`, `ABSTAIN`, `ESCALATE`, `BLOCK`.
  - Enforces invariant INV-001: Model probabilities never override signed ROE, verified inventory, or approval tiers.
- **Rules of Engagement (ROE) Validator (`roe_validator.py`)**:
  - Parses and cryptographically validates ed25519-signed ROE objects (`roe_...`).
  - Checks expiration timestamps, authorized target asset IDs, allowed capabilities, and revocation epochs.
- **Asset Inventory Gateway (`inventory.py`)**:
  - Authoritative registry of client infrastructure synced from cloud provider APIs (AWS/GCP/Azure) and DNS zones.
  - Rejects operator chat assertions.
- **Capability Token Issuer (`token_service.py`)**:
  - Mints short-lived, tamper-evident capability tokens bound to specific `action_id`, target asset IDs, and tool hashes.
