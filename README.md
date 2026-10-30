# DORA Technical Implementation Advisor

**Version 1.0 · Self-directed GRC case study · Knowledge base documented; model evaluation in progress**

A local-first, retrieval-augmented generation (RAG) prototype for exploring how requirements under the EU Digital Operational Resilience Act (DORA) can be translated into technical controls, implementation guidance, and evidence checklists, with a focus on credit institutions.

The main contribution is a structured **regulatory mapping knowledge base**: linking regulatory provisions to proposed controls, supporting evidence, and related security frameworks. The LLM interface provides a way to query that material; it does not independently establish the correctness of a mapping or demonstrate compliance.

> Developed offline as a structured GRC case study and subsequently published on GitHub for documentation and continued improvement. This is a learning and research prototype, not a certified compliance solution, legal opinion, or production banking deployment.

## Problem and regulatory context

DORA addresses ICT risk management, ICT-related incident reporting, digital operational resilience testing, ICT third-party risk, and information sharing. It entered into force on 16 January 2023 and has applied since 17 January 2025. Applicability, exclusions, proportionality, and specific obligations must be assessed for the entity concerned. See [Regulation (EU) 2022/2554, including Articles 2–4 and 64](https://eur-lex.europa.eu/eli/reg/2022/2554/oj/eng).

For ICT and GRC teams, a practical challenge is connecting regulatory requirements to implementation decisions and evidence that can be reviewed. A technical recommendation alone does not demonstrate that a control is appropriately designed, implemented, or operating effectively.

This project addresses that translation problem through a curated mapping layer and a local RAG interface. Its corpus is a defined project collection, not a claim to contain every DORA-related instrument or subsequent regulatory development.

## Intended use and GRC value

- Explore article-level requirements and their relationship to potential technical controls.
- Structure discussions between ICT, information security, risk, compliance, and assurance stakeholders.
- Identify candidate evidence such as policies, configurations, diagrams, review records, and test results.
- Compare explanatory mappings to ISO/IEC 27001:2022 and NIST CSF 2.0.
- Evaluate how consistently local LLMs answer a fixed set of regulatory and implementation questions.

The intended workflow is:

**Regulatory source → applicability review → interpreted requirement → proposed control → evidence to collect → human review and gap assessment.**

The repository supports the interpretation and preparation stages. It does not, by itself, collect operational evidence, verify control effectiveness, approve risk acceptance, or produce an authoritative readiness score.

## Solution and architecture

The documented design uses AnythingLLM Desktop for document ingestion and retrieval, an embedded LanceDB vector store, and LM Studio for local LLM inference on Apple Silicon. The retrieval setting is **Top-K = 6**.

```text
┌─────────────────────────────────────────────────────────┐
│ User query                                              │
│ "What network security controls support DORA Art. 9?"    │
└───────────────────────────┬─────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────┐
│ AnythingLLM Desktop — RAG engine                         │
│                                                         │
│ Built-in embedding model → LanceDB → Retrieval (K = 6)   │
│                                           │             │
│                                           ▼             │
│ Retrieved regulatory and mapping context                │
│                                           │             │
│                                           ▼             │
│ LM Studio — local LLM server                            │
│ Apple Silicon Metal · endpoint: localhost:1234           │
└───────────────────────────┬─────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────┐
│ Draft response                                          │
│ • Regulatory references and interpretation              │
│ • Candidate controls and implementation options         │
│ • Suggested evidence and framework cross-references     │
│ • Assumptions, gaps, and items requiring verification    │
└───────────────────────────┬─────────────────────────────┘
                            ▼
                 Human source and applicability review
```

Local execution is an architectural objective and configuration choice. It is not evidence that every component is offline, that no telemetry exists, or that the deployment meets an organisation's privacy and security requirements. See [Privacy and security](#privacy-and-security).

## Regulatory mapping and evidence

The Level 2 knowledge base connects regulatory requirements with proposed technical controls, open-source and commercial tool examples, expected evidence, framework cross-references, and implementation priorities.

These categories should be interpreted separately:

| Mapping element | GRC interpretation |
| --- | --- |
| Regulatory reference | A pointer to the source provision; the current official text must be checked. |
| Requirement interpretation | The author's working interpretation, subject to applicability and specialist review. |
| Technical control | A candidate implementation approach, to be tailored to the entity's risks and architecture. |
| Tool example | An implementation option, not a regulatory mandate or product endorsement. |
| Expected evidence | An evidence request or checklist item, not proof that evidence exists or is sufficient. |
| ISO/NIST cross-reference | An interpretive relationship, not equivalence, certification, or automatic compliance. |
| Implementation priority | A project prioritisation judgement, not a regulator-assigned severity or universal deadline. |

### Illustrative network security mapping

For a network security query, the response may connect DORA Article 9 to the more detailed network security management provisions in [Delegated Regulation (EU) 2024/1774, Article 13](https://eur-lex.europa.eu/eli/reg_del/2024/1774/oj/eng). Article 12 addresses logging; it should be distinguished from Article 13's network security requirements.

| Layer | Illustrative content |
| --- | --- |
| Regulatory anchor | DORA Article 9; RTS 2024/1774 Article 13; Article 12 where logging is relevant. |
| Candidate controls | Risk-based network segmentation, network access controls, documented data flows, and separation of administration networks; IDS/IPS, NGFW, or micro-segmentation where justified. |
| Tool examples | Suricata, Snort, pfSense, and Wazuh, depending on the control objective and environment. |
| Candidate evidence | Approved network and data-flow diagrams, segmentation rationale, firewall rule reviews, configuration records, and relevant test or monitoring results. |
| Framework context | ISO/IEC 27001:2022 Annex A controls 8.20–8.22 may provide related context; each cross-reference requires review. |
| Review boundary | Product installation and generated checklists do not establish control effectiveness or regulatory compliance. |

Framework identifiers must be version-specific. The original example used NIST identifiers `PR.DS` and `PR.IP`; these must not be presented together as a verified NIST CSF 2.0 mapping. Cross-references in the knowledge base should be checked against the declared framework edition before reuse.

## Documented DORA coverage

The project records the following mapping coverage. **“Documented” describes the presence of project material, not independently validated legal completeness, control implementation, or compliance.**

| Area | Articles | Supporting instruments listed in the project | Mapping status |
| --- | --- | --- | --- |
| Introduction, scope, definitions, and proportionality | 1–4 | — | Documented |
| ICT risk management | 5–16 | RTS 2024/1774 | Documented |
| Incident reporting | 17–23 | RTS 2024/1772; RTS 2025/301; ITS 2025/302 | Documented |
| Resilience testing | 24–27 | RTS 2025/1190 | Documented |
| ICT third-party risk and oversight provisions | 28–44 | RTS 2024/1773; RTS 2025/532; ITS 2024/2956 | Documented |
| Information sharing | 45 | — | Documented |

DORA contains 64 articles. The custom technical mapping is scoped to **Articles 1–45**, rather than all 64 articles. The instruments above represent the project's selected corpus; they are not an exhaustive inventory of all relevant delegated or implementing acts, guidance, or supervisory expectations. Provisions within Articles 28–44 also address oversight arrangements and do not all impose identical duties on a credit institution.

## Knowledge base

The project inventory describes **18 documents across three levels**. Counts and word totals below are project-reported inventory figures, not an independent content audit.

### Level 1 — Regulatory texts

**9 PDFs:** Regulation (EU) 2022/2554 and the **8 RTS/ITS instruments listed in the coverage table**.

Official download links are recorded in [`docs/document-sources.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/docs/document-sources.md), primarily from [EUR-Lex](https://eur-lex.europa.eu/).

### Level 2 — Technical mapping

**6 Markdown files, reported at 25,000+ words**, covering Articles 1–45 across the introductory material and five thematic areas. Entries include requirements, proposed controls, tool examples, expected evidence, ISO/IEC 27001:2022 and NIST CSF 2.0 cross-references, and implementation priorities.

Browse [`knowledge-base/level-2-technical-mapping/`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/knowledge-base/level-2-technical-mapping).

This is an author-created interpretation layer. Its contents require review against the official sources, entity-specific applicability, and the relevant framework versions.

### Level 3 — Context frameworks

**3 PDFs:** TIBER-EU 2025 (ECB), NIST CSF 2.0 (NIST), and the Elvinger Hoss DORA compilation. Source links are recorded in [`docs/document-sources.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/docs/document-sources.md).

These documents have different roles and authority. A secondary compilation is a reference aid; official legal texts remain the basis for checking regulatory requirements.

## Example queries

- “What network security controls are addressed by RTS 2024/1774 Article 13, and what logging requirements in Article 12 are relevant?”
- “Walk me through the potential DORA obligations triggered by a ransomware attack on online banking, stating applicability assumptions.”
- “What are the seven incident classification criteria and the applicable materiality thresholds under the relevant standards?”
- “What contractual provisions should be reviewed under DORA Article 30, including any distinctions for critical or important functions?”
- “How do the testing provisions in Article 25 differ from threat-led penetration testing under Article 26?”

The project defines **30 test queries across three difficulty levels, with expected answers**, in [`tests/test-queries.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/tests/test-queries.md). Expected answers are evaluation references and should themselves be reviewed; they are not authoritative legal determinations.

## Model evaluation — in progress

The evaluation design covers **six model candidates from four organisations** and the 30-query test set. It proposes scoring **accuracy, completeness, specificity, and hallucination resistance on a 1–5 scale**.

**No completed scores are reported here.** The original results table contains only `TBD` values. This README therefore makes no claim of completed validation, comparative superiority, demonstrated reliability, or measured hallucination resistance.

The following model labels and specifications are retained from the project inventory. Exact model identifiers, publisher specifications, architecture labels, quantisations, and downloaded artifacts must be verified before reporting reproducible results.

| Model label in project inventory | Organisation | Reported parameters | Reported architecture | Average score | Notes |
| --- | --- | --- | --- | --- | --- |
| Ministral 3 3B Reasoning | Mistral AI | 3B | Dense | TBD | Evaluation pending |
| Phi-4 Mini Reasoning | Microsoft | 3.8B | Dense | TBD | Evaluation pending |
| Gemma 4 E4B | Google | 8B total / 4B active | MoE | TBD | Evaluation pending; specifications require verification |
| Qwen3 8B | Alibaba | 8B | Dense | TBD | Evaluation pending |
| Gemma 4 12B QAT | Google | 12B | Dense (QAT) | TBD | Evaluation pending; specifications require verification |
| Ministral 3 14B Reasoning | Mistral AI | 14B | Dense | TBD | Evaluation pending |

Evaluation records and subsequent analysis belong in [`tests/evaluation-results.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/tests/evaluation-results.md).

### Evidence needed for meaningful results

A completed evaluation should record:

- Exact model artifact, version, quantisation, application versions, and hardware configuration.
- Corpus snapshot, embedding model, chunking, retrieval settings, system prompt, and generation parameters.
- Per-query responses, retrieved source passages, expected-answer references, and scoring rationale.
- A defined rubric, reviewer details, citation checks, unsupported claims, omissions, and handling of uncertainty.
- Failed or incomplete runs, repeated-run variability, and relevant latency or memory observations.

The 30-query set is a limited project benchmark. Even completed results would not establish general legal accuracy, production suitability, or compliance assurance. Retrieval failures and generation errors should be analysed separately, and subjective scores should not be presented as statistical proof of reliability.

## Tech stack

| Component | Documented technology or configuration |
| --- | --- |
| LLM serving | LM Studio; six model candidates listed above |
| Inference backend | Apple Silicon Metal |
| RAG engine | AnythingLLM Desktop |
| Vector database | LanceDB, embedded |
| Embeddings | AnythingLLM built-in embedder; exact model/version to be recorded |
| Retrieval | Top-K = 6 |
| Local server | `localhost:1234` |
| Hardware | MacBook Air M3, 16 GB unified memory |
| Intended cloud dependency | No cloud inference API required for the intended local configuration; installation, downloads, updates, telemetry, and integrations require separate verification |

Hardware details describe the project environment, not a guarantee that every listed model or context length will run successfully within available memory.

## Privacy and security

The design aims to keep document processing, embeddings, retrieval, and inference local when all components are configured accordingly. This can reduce exposure to external inference services, but **local-first operation alone does not establish privacy, data sovereignty, security, or GDPR compliance**.

The project does not provide evidence supporting blanket claims of zero external API calls, no telemetry, or suitability for a bank's internal network. Those properties depend on application versions, configuration, integrations, host security, and observed behaviour.

Before processing sensitive information or considering an organisational deployment, review and document:

- Local embedding and inference providers; cloud connectors, agents, external tools, and other outbound integrations.
- Download, update, and telemetry behaviour, with network observations or enforced egress controls where required.
- Server binding and exposure: verify loopback-only access where intended; assess authentication and access restrictions if network access is enabled.
- Storage of uploaded files, extracted text, vector data, prompts, responses, logs, caches, and backups; define access, retention, and deletion controls.
- Host encryption, account permissions, patching, dependency provenance, and model artifact provenance.
- Risks from untrusted retrieved content, including prompt injection, misleading citations, and unsupported output.
- Applicable data protection obligations and internal approvals before introducing personal, confidential, or regulated information.

These are review requirements, not controls claimed to be implemented or tested by this README. Use public regulatory material and synthetic queries until the relevant safeguards have been assessed.

## Quick start

1. Install [LM Studio](https://lmstudio.ai/) and download a suitable local model. Verify the exact model artifact and its hardware requirements; the evaluation candidates above are not validated recommendations.
2. Start the LM Studio local server on `localhost:1234` and verify the intended network binding.
3. Install [AnythingLLM Desktop](https://anythingllm.com/download), connect it to LM Studio, and select a local embedding configuration.
4. Download the Level 1 PDFs using [`docs/document-sources.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/docs/document-sources.md).
5. Create an AnythingLLM workspace and ingest the Level 1, Level 2, and Level 3 documents. Confirm ingestion completed and record the corpus versions.
6. Apply the prompt from [`config/system-prompt.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/config/system-prompt.md) and configure retrieval to Top-K = 6.
7. Run sample queries with public material. Check the retrieved passages and article references against the official sources before relying on a response.
8. Record configuration and test outcomes before conducting the structured evaluation.

Detailed setup instructions for macOS Apple Silicon are in [`docs/setup-guide.md`](https://github.com/michaelpunz70/dora-technical-advisor/blob/main/docs/setup-guide.md). Settings and available options may differ by application version.

## Repository structure

```text
├── knowledge-base/
│   ├── level-2-technical-mapping/    # 6 mapping files; Art. 1–45; reported 25,000+ words
│   ├── level-1-regulatory/           # Regulatory PDFs; not committed; links in docs
│   └── level-3-context/              # Context PDFs; not committed; links in docs
├── config/
│   └── system-prompt.md             # AnythingLLM system prompt
├── docs/
│   ├── setup-guide.md               # Setup for macOS / Apple Silicon M3
│   └── document-sources.md          # Source inventory and download links
└── tests/
    ├── test-queries.md              # 30 queries and expected answers
    └── evaluation-results.md        # Evaluation records; results pending
```

## GRC limitations and review boundaries

- **Regulatory scope:** the selected corpus and Articles 1–45 mapping do not establish exhaustive coverage of all applicable obligations or later amendments. Review current sources and entity-specific requirements.
- **Interpretation:** mappings, suggested tools, and priorities reflect project analysis. They require review by appropriately qualified ICT, risk, compliance, and legal stakeholders.
- **Evidence:** an evidence checklist is not collected evidence. Evidence must be attributable, current, relevant to the scoped control, and assessed for sufficiency.
- **Control assurance:** documented control design does not demonstrate implementation or sustained operating effectiveness. Testing and accountable ownership remain necessary.
- **Framework mapping:** ISO/NIST references are aids to analysis. They do not establish one-to-one equivalence or transfer compliance between frameworks.
- **AI reliability:** RAG can retrieve incomplete or irrelevant context, and an LLM can omit requirements, invent references, or produce confident but incorrect answers. Citations must be checked.
- **Deployment:** no independent security assessment, banking production approval, or privacy certification is evidenced here.
- **Accountability:** regulatory decisions, incident classification and reporting, risk acceptance, and assurance conclusions remain with the responsible organisation and reviewers.

## Version history and next steps

| Version | Date | Description |
| --- | --- | --- |
| 1.0 | July 2026 | Initial release as recorded by the project: Articles 1–45 knowledge base, architecture, and evaluation framework. |
| 1.1 | Planned | Complete and publish the six-model evaluation with reproducible configuration, response-level evidence, and limitations. |
| 1.2 | Planned | Tune prompts based on documented findings and repeat affected evaluation cases. |

Further improvements should prioritise source version tracking, review of article-level mappings and framework identifiers, and explicit separation of proposed controls from verified implementation evidence.

## Author

**Michael Punz — Cybersecurity (GRC & IAM)**

## License and source reuse

Project code and original materials are offered under the **MIT License**, subject to the repository's license file. Third-party regulatory texts, standards, frameworks, compilations, and model artifacts retain their own copyright, licensing, and reuse terms. The project's MIT License does not relicense those materials. Check each publisher's terms before redistribution; Level 3 includes materials from different publishers and must not be treated as uniformly EU-institution content.
