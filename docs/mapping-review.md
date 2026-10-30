# Regulatory Mapping Review and Evidence Procedure

## Purpose and status

This procedure makes the relationship between source provisions, author interpretations, proposed controls, and evidence explicit. It is a proposed review process; no completed legal sign-off or control assurance is implied.

The October 2026 revision corrected selected issues in the submitted mapping: proportionality eligibility, reversed DORA Article 15/16 headings, several RTS 2024/1774 article references, incident threshold shortcuts and reporting clocks, generic testing frequencies, full-register reporting assumptions, transition-period claims, and TLP handling. Remaining summaries and framework links require provision-level review before operational reliance.

## Mapping record

| Field | Required content |
| --- | --- |
| Mapping ID | Stable project identifier. |
| Source | Instrument, version/date, article/paragraph, official URL and source snapshot. |
| Applicability | Entity, service, function, system, exemptions/conditions, and rationale. |
| Requirement | Bounded source-supported statement, separate from interpretation. |
| Interpretation | Reasoning, assumptions, ambiguity, and reviewer questions. |
| Proposed control | Objective, design, scope, owner, dependencies, and alternatives. |
| Priority | Risk-based project judgement; cite a legal deadline only where verified. |
| Evidence request | Artifact, owner, date/period, scope, provenance, and access location. |
| Verification | Design review and operating-effectiveness method, sampling, and limitations. |
| Result | Not assessed / design reviewed / implemented / effectiveness tested; record supporting evidence. |
| Gap and treatment | Risk, owner, action, target date, exception or risk acceptance. |
| Review | Reviewer, date, source checks, approval status, and next review trigger. |

## Review sequence

1. Identify the current official source and exact provision. Review any amendments, applicability conditions, and authority-specific instructions.
2. Check that the summary is supported; separate normative text, interpretation, and optional implementation choices.
3. Review each ISO/NIST link against the named edition. A broad conceptual relationship is not a one-to-one control equivalence.
4. Assess the control design for the scoped environment. Numerical examples need an approved risk rationale.
5. Collect evidence before assigning implementation status. Assess relevance, coverage, provenance, recency, and consistency. A policy or screenshot alone may not demonstrate operation over time.
6. Record findings, disagreements, exceptions, and remediation. Re-review on relevant legal, system, provider, or control changes.

## Open review register

| Topic | Current status | Required next evidence |
| --- | --- | --- |
| All remaining article summaries and definitions | Human provision-level review pending | Signed source-to-summary check with applicability rationale. |
| ISO/IEC 27001:2022 mappings | Interpretive; not independently validated | Review against the licensed edition and scoped controls. |
| NIST CSF 2.0 mappings | Interpretive; known PR.IP usage removed from the pillar mapping | Identifier and relationship check against the official framework. |
| TLPT planning, selection, and provider checklists | Selected statements corrected; detailed checks pending | Review exact RTS paragraphs, authority instructions, entity designation. |
| Incident classification automation | Index corrected; not an executable legal specification | Approved decision table, boundary cases, recurring-incident tests, and timestamp tests. |
| Reporting channels and parallel legal obligations | Entity/jurisdiction-specific verification pending | Current authority instructions and qualified review of DORA/GDPR/NIS2/payment-service interactions. |
| Corpus currency and completeness | Selected 18-document baseline; PDFs not supplied | Source manifest, actual versions and hashes, ingestion counts. |
| Deployment privacy and security | No independent assessment supplied | Configuration review, observed network behaviour, access/storage controls, and approval. |
| LLM evaluation | No raw responses or completed scores supplied | Frozen run configuration, reviewed expected answers, response-level scores. |

## Assurance boundary

This repository is a GRC case study and documentation prototype. Editorial correction, a retrieved citation, a completed test query, or a checklist tick does not establish organisational regulatory compliance or operating effectiveness.
