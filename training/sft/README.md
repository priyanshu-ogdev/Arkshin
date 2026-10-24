# Supervised Fine-Tuning (`training/sft`)

## Purpose
Stage 1 training pipeline for the RedSage-8B-Base model across the merged real-data corpus.
Implements specifications from `docs/04-model-training.md`.

## Hardware Configuration
- **Workstation**: 1x NVIDIA RTX 6000 Ada (48GB GDDR6 with ECC) + 128GB System RAM.
- **DGX System**: Single DGX Spark unit (128GB unified memory).

## Training Speed Stack
- **FlashAttention-2**: IO-aware exact attention with 2–4x attention speedup.
- **Liger Kernel**: Fused Triton kernels (cross-entropy, RMSNorm, SwiGLU, RoPE) reducing VRAM by 40–60%.
- **Parallelism**: FSDP2 / DeepSpeed ZeRO-3 with sample packing to eliminate padding tokens across mixed-length security dialogues.
