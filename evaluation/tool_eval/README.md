# Agentic Tool-Use & Execution Evaluation (`evaluation/tool_eval`)

## Purpose
Evaluates agentic bash tool execution, pentesting problem-solving, and containment abilities in real
interactive environments. Reported separately from static MCQ scores. Implements `docs/14-evaluation-layer.md`.

## Evaluation Environments
- **CTF-Dojo**: Containerized holdout challenges testing recon, web exploitation, binary analysis, and privilege escalation.
- **InterCode-CTF**: PicoCTF benchmark tasks with Docker execution feedback.
- **NYU CTF Bench & Cybench**: Out-of-family CTF holdout benchmarks testing generalization to novel environments.
- **Metrics Tracked**: Task success rate, step efficiency, command error rate, and CodeAct vs JSON formatting delta.
