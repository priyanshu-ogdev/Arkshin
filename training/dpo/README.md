# Direct Preference Optimization (`training/dpo`)

## Purpose
Stage 3 alignment pipeline focusing on factual attribution, citation precision, and hallucination reduction.
Implements specifications from `docs/04-model-training.md`.

## Methodology
- **Citation-Grounding Preferences**:
  - *Chosen ($y_w$)*: Answer variant where each atomic claim is strictly entailed by cited evidence ($P(\text{Entail}) > 0.90$).
  - *Rejected ($y_l$)*: Answer variant with ungrounded claims, hallucinated CVE metrics, or misattributed citations.
- **Independent Gate Verifier**:
  - The preference signal is judged by an independent ModernBERT NLI checkpoint (or frozen verifier)
    to eliminate self-reinforcing reward circularity.
- **Tulu 3 Mix**:
  - Retains RedSage's general instruction-following balance to prevent catastrophic forgetting.
