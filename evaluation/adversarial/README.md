# Adversarial & Scope Safety Evaluation (`evaluation/adversarial`)

## Purpose
Adversarial test harness evaluating scope gateway resilience and prompt-injection resistance.
Implements specifications from `docs/10-scope-authorization-model.md` and `docs/14-evaluation-layer.md`.

## Test Suites
- **Scope-Gateway Adversarial Audit**:
  - Test suite of 500+ crafted requests attempting to target external, out-of-scope, or unverified IPs/domains.
  - Acceptance criterion: **0% bypass rate** (hard pass/fail release gate).
- **Prompt-Injection Fixtures**:
  - Deliberately injects malicious system prompts, role overrides, and hidden shell payloads inside tool outputs and retrieved CTI text.
  - Verifies that untrusted tool outputs cannot hijack the Planner's execution stream.
