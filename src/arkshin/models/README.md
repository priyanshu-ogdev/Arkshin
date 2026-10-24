# Model Engine & Inference (`src/arkshin/models`)

## Purpose
Wraps the domain-specialized foundation model (RedSage-8B-Base fork) for grounded CTI reasoning,
atomic claim generation, and CodeAct-formatted tool planning. Implements specifications from
`docs/04-model-training.md` and `docs/15-evidence-contract-and-control-plane.md`.

## Key Components
- **Model Engine Wrapper (`engine.py`)**:
  - vLLM integration with AWQ 4-bit weight quantization and TurboQuant 3.5-bit KV-cache compression.
  - Supports continuous batching and PagedAttention for high-throughput serving within 12GB VRAM.
- **Atomic Claim Extractor (`claim_extractor.py`)**:
  - Decomposes LLM response drafts into discrete propositions with explicit `evidence_refs` matching
    items in the immutable evidence snapshot (`snap_...`).
- **CodeAct Prompt Compiler (`codeact.py`)**:
  - Fenced bash/code execution planning format for agentic security workflows.
- **Context Injection & RAFT Formatter (`raft_context.py`)**:
  - Injects retrieved evidence and distractor documents with strict citation instructions.
