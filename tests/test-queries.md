# Test Queries — DORA Technical Implementation Advisor

## Testing Methodology

Each query is evaluated on a 1–5 scale across four criteria:

- **Accuracy**: correct DORA article and RTS citations
- **Completeness**: covers all relevant technical implementations
- **Specificity**: names concrete tools and gives actionable steps
- **Hallucination check**: does not invent requirements absent from DORA

**Target**: average score ≥ 3.5 across all 30 queries indicates a viable system.

---

## Round 1 — Basic Factual Retrieval

These test whether the RAG retrieves the correct chunks from the knowledge base.

| # | Query | Expected Key Points |
|---|---|---|
| 1 | What are the 5 pillars of DORA? | ICT Risk Management, Incident Reporting, Resilience Testing, Third-Party Risk, Information Sharing |
| 2 | How often must the ICT risk management framework be reviewed? | At least annually (Art. 6) |
| 3 | What are the 7 criteria for classifying a major incident? | Clients affected, reputational impact, duration, geographical spread, data losses, criticality of services, economic impact (RTS 2024/1772) |
| 4 | What is the deadline for the initial incident notification? | 4 hours from classification as major, no later than 24 hours after detection (Art. 19, RTS 2025/301) |
| 5 | What is TLPT and who must perform it? | Threat-Led Penetration Testing, mandated for G-SIIs, O-SIIs, and other designated entities (Art. 26, RTS 2025/1190) |
| 6 | What is the Register of Information? | A register of all ICT third-party contractual arrangements, submitted annually to competent authority (Art. 28, ITS 2024/2956) |
| 7 | How often must TLPT be performed? | At least every 3 years (Art. 26) |
| 8 | What is the minimum active testing duration for TLPT? | 12 weeks (RTS 2025/1190) |
| 9 | Must the Blue Team know about a TLPT in advance? | No — the Blue Team must NOT be informed (Art. 26, covert testing) |
| 10 | Is purple teaming mandatory in TLPT? | Yes, mandatory under RTS 2025/1190 |

---

## Round 2 — Technical Implementation Queries

These test whether the system provides concrete, actionable technical guidance.

| # | Query | Expected Key Points |
|---|---|---|
| 11 | What network security controls does DORA require for a bank? | VLANs, NGFW, IDS/IPS, micro-segmentation, NAC (802.1X), VPN+MFA/ZTNA, DNS filtering (Art. 9, RTS 2024/1774 Art. 12-13) |
| 12 | What encryption standards must a bank implement under DORA? | TLS 1.2+ in transit, AES-256 at rest, HSM for key management, key rotation schedules (Art. 9, RTS 2024/1774 Art. 11) |
| 13 | What backup strategy satisfies DORA Art. 11-12 requirements? | 3-2-1-1 with immutable backups, encryption, segregated restoration environment, frequency aligned with RPO per tier, regular restore testing (RTS 2024/1774 Art. 18) |
| 14 | What open-source SIEM options satisfy DORA detection requirements? | Wazuh, Elastic SIEM/Security — must cover all log sources, real-time alerting, correlation rules (Art. 10, RTS 2024/1774 Art. 12) |
| 15 | What mandatory contractual provisions must be in ICT third-party contracts? | Service description, SLAs, subcontracting conditions, data location, audit rights, incident notification, termination rights, exit strategy (Art. 30) |
| 16 | What are the patch management SLAs recommended for banking? | Critical (CVSS 9-10): 24-48h; High: 7d; Medium: 30d; Low: 90d — for Tier 1 systems (RTS 2024/1774 Art. 8-9) |
| 17 | How should a bank implement access control to comply with DORA? | MFA for all remote/privileged access, PAM, RBAC, least privilege, annual access review (quarterly for critical), automated provisioning/de-provisioning (RTS 2024/1774 Art. 10) |
| 18 | What scenario-based tests should a bank run? | Ransomware, data breach, DDoS, third-party failure, insider threat, phishing — at least 2x per year (Art. 25) |
| 19 | What is required for exit strategies with ICT third-party providers? | Transition plan (min 6 months), data return in standard format, data deletion with certification, continued service during transition, knowledge transfer (Art. 30, RTS 2024/1773 Art. 5) |
| 20 | What threat intelligence sharing communities should a bank consider? | FS-ISAC, national CERT/CSIRT, ECRB (for systemic institutions), national banking ISACs, vendor TI sharing (Art. 45) |

---

## Round 3 — Complex Cross-Pillar Queries

These test the system's ability to synthesize across multiple documents and pillars.

| # | Query | Expected Key Points |
|---|---|---|
| 21 | A ransomware attack hits our online banking. Walk me through all DORA obligations triggered. | Detection (Art. 10), incident response (Art. 17), classification against 7 criteria (Art. 18, RTS 2024/1772), 4h initial notification (Art. 19, RTS 2025/301), client notification (Art. 19(3)), backup restoration from immutable backups (Art. 11-12), post-incident review (Art. 13), third-party notification if provider involved (Art. 30) |
| 22 | How does DORA map to ISO 27001 for network security controls? | Art. 9 maps to A.8.20-8.22 (Network Security), A.8.23 (Web Filtering); key gap: ISO 27001 does not mandate specific technology choices like IDS/IPS |
| 23 | What is the difference between regular pen testing (Art. 25) and TLPT (Art. 26)? | Scope, frequency, environment (production vs test), Blue Team awareness, regulatory oversight, duration, mutual recognition, mandatory purple teaming |
| 24 | Our cloud provider (AWS) is designated as a CTPP. What changes for us? | Enhanced due diligence, monitor Lead Overseer recommendations, ensure contract includes CTPP cooperation clauses, assess concentration risk, maintain exit strategy (Art. 31-44) |
| 25 | What evidence should we prepare for a DORA regulatory audit? | Framework documents, risk register, asset inventory, BIA, vulnerability scans, pen test reports, incident register, backup test records, RoI, contracts with Art. 30 provisions, testing programme, board reporting, training records |
| 26 | We want to implement a SOC. What DORA requirements define its capabilities? | Art. 10 (detection layers), Art. 9 (logging — SIEM with minimum log sources), Art. 17 (incident management), Art. 13 (learning/improvement), RTS 2024/1774 Art. 12 (logging), Art. 20-22 (monitoring and alerting) |
| 27 | How do DORA incident reporting and GDPR breach notification interact? | Parallel obligations: DORA 4h to NCA (Art. 19), GDPR 72h to DPA (Art. 33), GDPR Art. 34 to data subjects; a single incident can trigger both; coordinate but do not delay either |
| 28 | What concentration risk assessment must we do before contracting a new cloud provider for core banking? | Assess substitutability, count CIFs with same provider, evaluate geographic concentration, check sub-outsourcing chains, define thresholds (amber/red), present to ICT Risk Committee (Art. 29) |
| 29 | What qualifications must a TLPT red team have? | Lead: 5+ years pen test/red team experience; members: 2+ years each; 5+ references; relevant certs (OSCP, OSEP, CRTO); professional indemnity insurance; no conflicts of interest (RTS 2025/1190 Art. 7) |
| 30 | Design a DORA compliance roadmap for a mid-sized bank starting from zero. | Phase 1: Governance (Art. 5-6), asset inventory (Art. 7-8), risk assessment; Phase 2: Security controls (Art. 9), detection (Art. 10); Phase 3: BCP/DRP (Art. 11-12), incident management (Art. 17-19); Phase 4: Third-party review (Art. 28-30), RoI; Phase 5: Testing programme (Art. 24-25); Phase 6: TLPT if designated (Art. 26-27) |
