# Processed Training & Evaluation Splits (`data/processed`)

## Purpose
Contains curated, cleaned, tokenized, and deduplicated data splits ready for model fine-tuning,
reinforcement learning, and calibration. All bulk parquet/arrow data files are excluded via `.gitignore`.

## Split Partitions
- **`sft_train.jsonl`**: Knowledge and tool-use SFT mix (Primus-Instruct, NL2Bash, Corrected InterCode, CTF-Dojo).
- **`sft_val.jsonl`**: Source-disjoint validation partition for hyperparameter tuning.
- **`raft_train.jsonl`**: Authentic context-curriculum examples (2–8 retrieved passages with authentic citations).
- **`dpo_pairs.jsonl`**: Citation-grounded preference pairs and execution success/failure trajectories.
- **`nli_pairs.jsonl`**: Domain-adapted premise-hypothesis pairs (NVD ↔ CISA KEV, ATT&CK ↔ D3FEND).
