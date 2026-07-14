# Setup Guide

## System Architecture

The DORA Technical Implementation Advisor runs on a fully local stack with three components:

**LM Studio** serves as the local inference engine. It loads GGUF-quantized models and exposes an OpenAI-compatible API endpoint at `localhost:1234`. The Apple Silicon Metal backend handles GPU acceleration through the M3's unified memory architecture.

**AnythingLLM** provides the RAG layer. It handles document ingestion, chunking, vector embedding (via its built-in embedder), and vector search (LanceDB). Each query retrieves the top-K most relevant chunks from the knowledge base and passes them as context to the LLM via the LM Studio API.

**The Knowledge Base** consists of three levels of documents loaded into a single AnythingLLM workspace:

| Level | Content | Files | Source |
|---|---|---|---|
| Level 1 | DORA regulation + 8 RTS/ITS | 9 PDFs | EUR-Lex (see [`document-sources.md`](document-sources.md)) |
| Level 2 | Technical implementation mapping (Art. 1–45) | 6 Markdown files (25,000+ words) | Original content in `knowledge-base/level-2-technical-mapping/` |
| Level 3 | TIBER-EU, NIST CSF 2.0, cross-reference frameworks | 3–4 PDFs | ECB, NIST (see [`document-sources.md`](document-sources.md)) |

```
User Query
    │
    ▼
AnythingLLM ──► Vector Search (LanceDB, Top-K=6) ──► Relevant Chunks
    │                                                       │
    ▼                                                       ▼
LM Studio (localhost:1234) ◄─── Context: Chunks + System Prompt
    │
    ▼
Structured Response (article references, technical controls, tools, audit evidence)
```

---

## Hardware Requirements

| Component | Minimum | Used in This Project |
|---|---|---|
| Machine | Any Apple Silicon Mac or PC with 16+ GB RAM | MacBook Air M3, 16 GB unified memory, macOS Sequoia 15.6.1 |
| Disk space | 20 GB free | For models (4–10 GB each) + AnythingLLM data |
| GPU | Apple Silicon Metal or NVIDIA with 8+ GB VRAM | M3 integrated GPU via Metal |

**Memory considerations**: macOS reserves approximately 4–5 GB, leaving ~11 GB for applications. Models up to 8B parameters in Q4_K_M quantization (~5 GB) run comfortably. The 12B and 14B models used in this evaluation push closer to the memory limit and may trigger occasional swap, resulting in slower inference but still functional results.

---

## Model Selection

Six models were selected to cover four organizational ecosystems, three parameter size tiers, and both dense and Mixture-of-Experts architectures:

| Model | Organization | Parameters | Architecture | Rationale |
|---|---|---|---|---|
| Ministral 3 3B Reasoning | Mistral AI | 3B | Dense | Smallest model — baseline for minimum viable quality on regulatory content |
| Phi-4 Mini Reasoning | Microsoft | 3.8B | Dense | Reasoning-optimized small model — tests whether specialized training compensates for limited parameters |
| Gemma 4 E4B | Google | 8B total / 4B active | MoE | Tests whether MoE efficiency (only 4B active parameters) delivers comparable quality to dense 8B models |
| Qwen3 8B | Alibaba | 8B | Dense | Strong general-purpose model — benchmark for the 8B dense category |
| Gemma 4 12B QAT | Google | 12B | Dense (QAT) | Quantization-Aware Trained — tests whether QAT improves accuracy over standard quantization at this size |
| Ministral 3 14B Reasoning | Mistral AI | 14B | Dense | Largest model in the evaluation — upper bound for quality on 16 GB hardware |

All models were sourced from LM Studio's model library in GGUF format. Quantization levels were selected to balance quality and memory footprint within the 16 GB constraint.

---

## Installation

### LM Studio

Download from [lmstudio.ai](https://lmstudio.ai/) (macOS Apple Silicon version). After installation, download the desired model via the Search tab, then start the local server on the Local Server tab. The server runs at `http://localhost:1234` and must remain active during all AnythingLLM queries.

Verify the Metal backend is active in the server settings — this enables GPU acceleration on Apple Silicon.

### AnythingLLM

Download from [anythingllm.com](https://anythingllm.com/download) (macOS Desktop version).

Configuration:
- LLM Preference → LM Studio, Base URL: `http://localhost:1234/v1`
- Embedding Preference → AnythingLLM built-in embedder
- Vector Database → LanceDB (default)

### Workspace Configuration

Create a workspace named "DORA Technical Implementation Advisor" and upload all documents from the three knowledge base levels (9 PDFs + 6 Markdown files + 3–4 context PDFs).

Workspace settings:
- Chat Mode: **Query** (restricts answers to document content — reduces hallucination)
- Top-K: **6** (number of chunks retrieved per query)
- Similarity Threshold: **0.25**

The system prompt is documented in [`config/system-prompt.md`](../config/system-prompt.md).

---

## Evaluation Methodology

Each model was evaluated using 30 test queries (documented in [`tests/test-queries.md`](../tests/test-queries.md)) organized in three rounds of increasing complexity:

- **Round 1** (Q1–Q10): Basic factual retrieval — tests whether the RAG retrieves correct regulatory references
- **Round 2** (Q11–Q20): Technical implementation queries — tests whether responses include concrete controls, tools, and actionable guidance
- **Round 3** (Q21–Q30): Complex cross-pillar queries — tests synthesis across multiple DORA chapters and RTS documents

Scoring uses a 1–5 scale across four criteria: accuracy of regulatory citations, completeness of technical implementations, specificity of tool recommendations, and absence of hallucinated requirements.

The same workspace, embedding, and Top-K configuration were maintained across all model evaluations to ensure comparability. Only the LLM model was changed between runs.

Full results are documented in [`tests/evaluation-results.md`](../tests/evaluation-results.md).

---

## Source Document Authenticity

All Level 1 regulatory documents were downloaded directly from EUR-Lex via HTTPS. Each document was validated against its CELEX number, Official Journal reference, and cross-references to other DORA instruments. See the Source Authenticity section in [`document-sources.md`](document-sources.md) for the full verification methodology.
