# Test Fixtures & Mock Artifacts (`tests/fixtures`)

## Purpose
Pre-recorded, deterministic mock data used across unit and integration test runs to ensure offline reproducibility.

## Fixture Categories
- **`requests/`**: Sample request envelopes with valid and invalid tenant, engagement, and purpose tags.
- **`snapshots/`**: Pinned, immutable evidence snapshots (`snap_sample_01.yaml`) with authentic CVE and CTI text snippets.
- **`claims/`**: Sample structured claims with correct citations, miscitations, and unsupported extrapolations.
- **`proposals/`**: Typed `ActionProposal` contracts for read-only lookups (Tier 0), nmap scans (Tier 1), and exploit simulations (Tier 2).
- **`roe/`**: ed25519-signed Rules of Engagement objects, expired objects, and revoked certificates.
