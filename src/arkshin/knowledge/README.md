# Knowledge & Retrieval Layer (`src/arkshin/knowledge`)

## Purpose
Manages multi-tier ground-truth cybersecurity knowledge storage, concurrent hybrid retrieval,
and immutable evidence snapshot creation. Implements Track D1 specifications from
`docs/03-retrieval-rag-layer.md` and `docs/15-evidence-contract-and-control-plane.md`.

## Key Components
- **OKF Connector (`okf_loader.py`)**:
  - Ingests Git-versioned Markdown + YAML records from the Open Knowledge Format (CVE, ATT&CK, D3FEND, CAPEC).
- **Property Graph DB Engine (`graph_db.py`)**:
  - Embedded Kùzu C++ engine (and optional Neo4j adapter) storing entity relationships and recon subgraphs.
  - AST Cypher query validation enforcing read-only constraints, tenant isolation predicates, and query timeouts.
- **Vector & Contextual Retriever (`vector_store.py`)**:
  - Hybrid dense embedding + BM25 search with Anthropic-style Contextual Retrieval and Late Chunking.
- **Evidence Reconciliation & Snapshot Generator (`snapshot_builder.py`)**:
  - Concurrently queries graph + vector stores, reconciles conflicting assertions, and freezes an
    immutable evidence snapshot (`snap_...`) with cryptographic content hashes (`sha256:...`).
