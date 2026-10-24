# API & Experience Plane Gateway (`src/arkshin/api`)

## Purpose
Exposes authenticated REST and gRPC interfaces for operators, integrations, and web UIs.
Implements Track D0 specifications from `docs/18-architecture-artifact-specifications.md`.

## Key Components
- **Request Envelope Middleware (`middleware.py`)**:
  - Validates authenticated identity, session tokens, tenant IDs, and engagement nonces.
  - Rejects malformed requests or requests lacking proper purpose tags.
- **REST Gateway (`server.py`)**:
  - FastAPI application serving endpoints for:
    - Grounded Q&A and CTI analysis (`/api/v1/query`)
    - Approval queue and human-in-the-loop escalation (`/api/v1/approvals`)
    - Asset scope inspection (`/api/v1/scope`)
    - Audit log review and replay (`/api/v1/audit`)
- **Emergency Stop & Kill Switch (`kill_switch.py`)**:
  - Immediate operational revocation endpoint: revokes active capability tokens, invalidates sessions, and freezes sandbox execution.
