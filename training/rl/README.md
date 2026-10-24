# Execution-Feedback Reinforcement Learning (`training/rl`)

## Purpose
Stage 2 training pipeline for agentic bash tool execution using verifiable sandboxed environment outcomes.
Implements specifications from `docs/04-model-training.md` and `docs/06-agentic-execution-layer.md`.

## Methodology
- **RLEF / StepPO**: Reinforcement Learning from Execution Feedback with step-level credit assignment,
  mitigating compounding-error propagation in multi-step agent trajectories.
- **Environment Grounding**: Executes candidate bash actions inside containerized CTF-Dojo and InterCode environments.
- **Reward Signal**:
  - `+1.0`: Command succeeded (exit code 0), achieved intermediate security sub-goal, and strictly adhered to scope.
  - `0.0`: Command failed or produced syntax/permission error.
  - `-1.0`: Out-of-scope command invocation or policy violation (terminal penalty).
- **Fission-GRPO**: Error-recovery training encouraging the model to diagnose and repair failed tool invocations.
