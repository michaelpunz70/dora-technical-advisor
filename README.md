# DORA Technical Implementation Advisor

**Version 1.0** · **Status: Knowledge base complete — model evaluation in progress**

A local-first, privacy-preserving AI advisor that maps EU Regulation 2022/2554 (Digital Operational Resilience Act) requirements to concrete technical implementations for credit institutions.

> *This project was developed offline as a structured GRC case study for DORA technical implementation and subsequently published on GitHub for documentation and continued improvement.*

## Problem

DORA entered into force on 17 January 2025, requiring all EU financial entities to implement comprehensive ICT risk management, incident reporting, resilience testing, and third-party risk management. The regulation spans 64 articles plus 9 RTS/ITS documents — over 500 pages of regulatory text. Security teams struggle to translate principles-based regulatory requirements into specific technical controls, tools, and audit evidence.

## Solution

A RAG-based (Retrieval-Augmented Generation) advisory system running entirely on local infrastructure — no data leaves the machine. The system ingests the full DORA regulatory corpus plus a custom-built technical mapping knowledge base, and answers natural language queries with specific article references, implementation steps, tool recommendations, and audit evidence checklists.

```
┌─────────────────────────────────────────────────────────┐
│                    User Query                           │
│        "What technical controls does Art. 9             │
│         require for network security?"                  │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│              AnythingLLM (RAG Engine)                    │
│  ┌─────────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │  Embedding   │  │ Vector Store │  │   Retrieval   │  │
│  │   Model      │→ │  (LanceDB)   │→ │  (Top-K = 6)  │  │
│  └─────────────┘  └──────────────┘  └───────┬───────┘  │
│                                             │          │
│                    Retrieved context ───────┘          │
│                                             ▼          │
│  ┌──────────────────────────────────────────────────┐  │
│  │         LM Studio (Local LLM Server)              │  │
│  │         Model: Local LLM (Apple Silicon Metal)     │  │
│  │         Backend: Metal | Endpoint: localhost:1234  │  │
│  └──────────────────────────────────────────────────┘  │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│                  AI Response                            │
│  - DORA Art. 9(2) + RTS 2024/1774 Art. 12-13          │
│  - Technical: VLANs, IDS/IPS, NGFW, micro-segmentation│
│  - Tools: Suricata, Snort, pfSense, Wazuh             │
│  - Evidence: network diagrams, firewall rule reviews   │
│  - ISO 27001: A.8.20-8.22 | NIST CSF: PR.DS, PR.IP   │
│  - Priority: CRITICAL                                  │
└─────────────────────────────────────────────────────────┘
```

## DORA Coverage

| Pillar | Articles | RTS/ITS | Status |
|---|---|---|---|
| 0 — Introduction, Scope, Definitions | Art. 1–4 | — | ✅ Complete |
| 1 — ICT Risk Management | Art. 5–16 | RTS 2024/1774 | ✅ Complete |
| 2 — Incident Reporting | Art. 17–23 | RTS 2024/1772, RTS 2025/301, ITS 2025/302 | ✅ Complete |
| 3 — Resilience Testing | Art. 24–27 | RTS 2025/1190 | ✅ Complete |
| 4 — Third-Party Risk | Art. 28–44 | RTS 2024/1773, RTS 2025/532, ITS 2024/2956 | ✅ Complete |
| 5 — Information Sharing | Art. 45 | — | ✅ Complete |

## Knowledge Base

The system uses a three-level knowledge base totaling 18 documents:

**Level 1 — Regulatory texts** (9 PDFs from [EUR-Lex](https://eur-lex.europa.eu/)): DORA full text (Reg. 2022/2554) plus all 8 RTS/ITS. See [`docs/document-sources.md`](docs/document-sources.md) for the complete list with official download links.

**Level 2 — Technical mapping** (6 Markdown files, 25,000+ words): custom-built knowledge base covering every DORA article (Art. 1–45) — from definitions and scope through all 5 pillars. Each entry includes the regulatory requirement, technical controls, recommended tools (open-source and commercial), expected audit evidence, cross-references to ISO 27001:2022 and NIST CSF 2.0, and implementation priority. Browse them in [`knowledge-base/level-2-technical-mapping/`](knowledge-base/level-2-technical-mapping/).

**Level 3 — Context frameworks** (3 PDFs): TIBER-EU 2025 (ECB), NIST CSF 2.0 (NIST), and Elvinger Hoss DORA compilation. Links in [`docs/document-sources.md`](docs/document-sources.md).

## Example Queries

- "What network security controls does RTS 2024/1774 Art. 12-13 require for a bank?"
- "Walk me through all DORA obligations triggered by a ransomware attack on online banking."
- "What are the 7 classification criteria for major incidents and their materiality thresholds?"
- "What mandatory contractual provisions must be in ICT third-party contracts under Art. 30?"
- "What is the difference between regular penetration testing (Art. 25) and TLPT (Art. 26)?"

See [`tests/test-queries.md`](tests/test-queries.md) for the full validation suite of 30 queries across 3 difficulty levels with expected answers.

## Model Evaluation

The system was validated using 30 structured test queries across 6 models from 4 different organizations, scoring accuracy, completeness, specificity, and hallucination resistance on a 1–5 scale:

| Model | Organization | Parameters | Architecture | Avg Score | Notes |
|---|---|---|---|---|---|
| Ministral 3 3B Reasoning | Mistral AI | 3B | Dense | TBD | TBD |
| Phi-4 Mini Reasoning | Microsoft | 3.8B | Dense | TBD | TBD |
| Gemma 4 E4B | Google | 8B total / 4B active | MoE | TBD | TBD |
| Qwen3 8B | Alibaba | 8B | Dense | TBD | TBD |
| Gemma 4 12B QAT | Google | 12B | Dense (QAT) | TBD | TBD |
| Ministral 3 14B Reasoning | Mistral AI | 14B | Dense | TBD | TBD |

Full results and analysis in [`tests/evaluation-results.md`](tests/evaluation-results.md).

## Tech Stack

| Component | Technology |
|---|---|
| LLM | 6 models evaluated: Ministral 3 3B/14B, Phi-4 Mini, Gemma 4 E4B/12B, Qwen3 8B via LM Studio (local, Apple Silicon Metal backend) |
| RAG Engine | AnythingLLM Desktop |
| Vector Database | LanceDB (embedded) |
| Embedding | AnythingLLM built-in embedder |
| Hardware | MacBook Air M3, 16 GB unified memory |
| Cloud dependencies | None — 100% local inference |

## Privacy & Security

This system is designed for financial sector use where data sovereignty is non-negotiable:

- All processing happens locally — zero API calls to external services
- No telemetry or data collection
- Documents never leave the local machine
- Suitable for deployment within bank internal networks
- Model runs on-device via Apple Silicon Metal — no GPU cloud services

## Quick Start

1. Install [LM Studio](https://lmstudio.ai/) and download one of the evaluated models
2. Start the LM Studio local server on `localhost:1234`
3. Install [AnythingLLM Desktop](https://anythingllm.com/download) and connect to LM Studio
4. Download the Level 1 PDFs from EUR-Lex (links in [`docs/document-sources.md`](docs/document-sources.md))
5. Upload all documents (Level 1 + Level 2 + Level 3) to a new AnythingLLM workspace
6. Set the system prompt from [`config/system-prompt.md`](config/system-prompt.md)
7. Start querying

Detailed setup instructions for macOS Apple Silicon: [`docs/setup-guide.md`](docs/setup-guide.md)

## Repository Structure

```
├── knowledge-base/
│   ├── level-2-technical-mapping/    # 6 mapping files — Art. 1–45 (25,000+ words)
│   ├── level-1-regulatory/           # EUR-Lex PDFs — not committed, links in docs
│   └── level-3-context/              # Context frameworks — not committed, links in docs
├── config/
│   └── system-prompt.md              # AnythingLLM system prompt
├── docs/
│   ├── setup-guide.md                # Step-by-step setup for macOS M3
│   └── document-sources.md           # All source document links
└── tests/
    ├── test-queries.md               # 30 validation queries with expected answers
    └── evaluation-results.md         # Model comparison results
```

## Version History

| Version | Date | Description |
|---|---|---|
| 1.0 | July 2026 | Initial release — knowledge base (Art. 1–45), system architecture, evaluation framework |
| 1.1 | (planned) | Model evaluation results for 6 LLMs |
| 1.2 | (planned) | Prompt tuning improvements based on evaluation findings |

## Author

**Michael Punz** — Cybersecurity (GRC & IAM)

## License

MIT License. The regulatory documents (Level 1 and Level 3) are published by EU institutions and are subject to their respective terms of reuse.
