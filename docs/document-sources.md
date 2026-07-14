# Document Sources — Official Download Links

All Level 1 documents are from EUR-Lex (Official Journal of the European Union). All Level 3 documents are from official institutional sources (ECB, NIST). These documents are not committed to the repository due to size and copyright — download them directly from the links below.

---

## Level 1 — Regulatory Documents

### Core Regulation

| # | Document | Link |
|---|---|---|
| 1 | **Regulation (EU) 2022/2554 — DORA full text** | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32022R2554) |

### First Batch RTS/ITS (published June 2024, in force 17 January 2025)

| # | Document | Link |
|---|---|---|
| 2 | **RTS 2024/1774** — ICT Risk Management framework | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202401774) |
| 3 | **RTS 2024/1772** — Incident Classification criteria and materiality thresholds | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202401772) |
| 4 | **RTS 2024/1773** — Third-Party ICT Service Provider Policy | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202401773) |
| 5 | **ITS 2024/2956** — Register of Information templates | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32024R2956) |

### Second Batch RTS/ITS (published February–June 2025)

| # | Document | Link |
|---|---|---|
| 6 | **RTS 2025/301** — Incident Reporting content and timelines | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202500301) |
| 7 | **ITS 2025/302** — Incident Reporting templates and forms | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202500302) |
| 8 | **RTS 2025/532** — Subcontracting ICT services | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202500532) |
| 9 | **RTS 2025/1190** — Threat-Led Penetration Testing (TLPT) | [PDF](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=OJ:L_202501190) |

---

## Level 2 — Technical Mapping (included in this repository)

These 6 files (25,000+ words total) are committed to the repository in `knowledge-base/level-2-technical-mapping/`:

| # | File | Content | DORA Articles |
|---|---|---|---|
| 1 | `pillar0-introduction-scope-definitions.md` | Scope, 63 definitions, proportionality | Art. 1–4 |
| 2 | `pillar1-ict-risk-management.md` | ICT Risk Management | Art. 5–16 |
| 3 | `pillar2-incident-reporting.md` | Incident Reporting | Art. 17–23 |
| 4 | `pillar3-resilience-testing.md` | Resilience Testing | Art. 24–27 |
| 5 | `pillar4-third-party-risk.md` | Third-Party Risk | Art. 28–44 |
| 6 | `pillar5-information-sharing.md` | Information Sharing | Art. 45 |

---

## Level 3 — Supporting Context Documents

| # | Document | Source | Link |
|---|---|---|---|
| 1 | **TIBER-EU Framework 2025** (updated for DORA TLPT alignment) | ECB | [PDF](https://www.ecb.europa.eu/pub/pdf/other/ecb.tiber_eu_framework_2025~b32eff9a10.en.pdf) |
| 2 | **NIST Cybersecurity Framework 2.0** | NIST | [PDF](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf) |
| 3 | **DORA Compilation** (all 27 DORA documents in one indexed PDF) | Elvinger Hoss Prussen | [PDF](https://elvingerhoss.lu/sites/default/files/upload/media/document/2025-04/Brochure%20DORA.pdf) |

---

## EBA Reference Page

The EBA maintains a central page with all DORA-related publications, Q&As, and updates:

[EBA — Digital Operational Resilience Act](https://www.eba.europa.eu/activities/direct-supervision-and-oversight/digital-operational-resilience-act)

---

## Source Authenticity

All Level 1 regulatory documents were downloaded directly from [EUR-Lex](https://eur-lex.europa.eu/) (Official Journal of the European Union) via HTTPS. EUR-Lex is the only authoritative digital source for EU legislation, operated by the Publications Office of the European Union. The TLS/SSL certificate guarantees server identity and transport integrity.

EUR-Lex does not publish file hashes (SHA-256 or similar checksums) for its PDF documents, as they are generated dynamically from the legislative database. To verify document authenticity, each PDF was validated against the following internal identifiers:

- **CELEX number** (unique document identifier in the EU legal database, e.g., `32022R2554`)
- **Official Journal reference** (volume, date, and page range, e.g., `OJ L 333, 27.12.2022`)
- **ELI** (European Legislation Identifier URI)
- **Cross-references**: each RTS/ITS cites the DORA articles it implements, and DORA cites the empowering provisions for each RTS — internal consistency across the 9-document corpus was verified

Level 3 documents were downloaded from their respective official institutional sources: ECB (`ecb.europa.eu`) for TIBER-EU and NIST (`nist.gov`) for CSF 2.0. The Elvinger Hoss compilation is a third-party resource used as supplementary context only — the official EUR-Lex versions remain the primary source of truth.

---

*All links verified as of July 2026. If a link is broken, search for the document number on [EUR-Lex](https://eur-lex.europa.eu/) or the respective institutional website.*
