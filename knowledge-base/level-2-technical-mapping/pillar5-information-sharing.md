# DORA Pillar 5 — Information Sharing

## Regulatory Scope

- **DORA Articles**: 45 (Chapter VI)
- **Key RTS/ITS**: None — this pillar has no dedicated Level 2 technical standards
- **Applicability**: All financial entities (voluntary participation)
- **Legal basis**: Art. 45 provides the legal framework that removes previous legal uncertainty around sharing threat intelligence under data protection and competition law

---

## Art. 45 — Information-Sharing Arrangements

### Requirement Summary

Financial entities may exchange amongst themselves cyber threat information and intelligence, including indicators of compromise (IOCs), tactics, techniques and procedures (TTPs), cybersecurity alerts, and configuration tools, to the extent that such information and intelligence sharing:

- Aims to enhance the digital operational resilience of financial entities, in particular through raising awareness in relation to cyber threats, limiting or impeding the cyber threats' ability to spread, supporting defence capabilities, threat detection techniques, mitigation strategies, or response and recovery stages
- Takes place within trusted communities of financial entities
- Is implemented through information-sharing arrangements that protect the potentially sensitive nature of the information shared and that are subject to rules of conduct in full respect of business confidentiality, protection of personal data in accordance with GDPR, and competition law policy

Financial entities must notify competent authorities of their participation in information-sharing arrangements.

Where financial entities receive cyber threat information or intelligence shared by other financial entities, or through information-sharing arrangements, they must implement effective detection capabilities based on that information — incorporating the shared indicators and threat signatures into their monitoring systems.

### Technical Implementations

**Establishing or joining information-sharing arrangements:**
- Identify and evaluate relevant information-sharing communities for the banking sector:

| Community | Type | Scope | Participation |
|---|---|---|---|
| FS-ISAC (Financial Services ISAC) | Sector-specific ISAC | Global, financial services sector | Membership fee required |
| European Cyber Resilience Board (ECRB) | ECB-facilitated | Euro area financial infrastructure | By invitation (systemic institutions) |
| National CERT/CSIRT | Government | National scope | Usually free |
| EBF Cyber Intelligence Sharing Initiative | Industry association | European banking | EBF membership |
| National banking association ISACs | Sector-specific | National scope | Via national banking association |
| Bilateral sharing with peer institutions | Direct peer-to-peer | Custom scope | Bilateral agreement |
| Vendor threat intelligence sharing | Commercial | Cross-sector | Part of vendor contract (e.g., CrowdStrike, Microsoft) |

- Evaluate each community against DORA requirements: does it have rules protecting sensitive information? Does it respect data protection and competition law? Is it a trusted community of financial entities?
- Formalise participation through a written agreement defining: scope of sharing, handling rules (TLP protocol), data protection measures, competition law safeguards, opt-out provisions
- Designate an internal point of contact (typically within the threat intelligence team or SOC) responsible for managing information sharing

**Notification to competent authority:**
- Notify the competent authority of the entity's participation in information-sharing arrangements
- Notification should include: name and type of arrangement, scope of information shared, governance rules, data protection measures
- Update the notification if the entity joins or exits additional arrangements

**Traffic Light Protocol (TLP) implementation:**
- Adopt the TLP 2.0 standard for classifying shared information:

| TLP Level | Meaning | Handling |
|---|---|---|
| TLP:RED | For named recipients only | Do not share outside the specific exchange; for eyes only of the individuals present |
| TLP:AMBER+STRICT | Limited disclosure, restricted to the organisation | May be shared within the organisation on a need-to-know basis only |
| TLP:AMBER | Limited disclosure, restricted to the community | May be shared with members of the same community/sector |
| TLP:GREEN | Limited disclosure, restricted to the community at large | May be shared within the financial sector peer community |
| TLP:CLEAR | No restrictions | May be shared freely, subject to standard copyright rules |

- Configure SIEM, TIP, and email systems to enforce TLP handling rules
- Train all staff involved in information sharing on TLP classification and handling

**Operationalising received intelligence:**
- Establish a workflow for processing incoming shared intelligence:
  1. **Receive**: Ingest IOCs, TTPs, and alerts from sharing platforms and communities
  2. **Validate**: Assess relevance and reliability — is the intelligence applicable to the entity's technology stack and threat profile? Is the source trustworthy?
  3. **Enrich**: Correlate received IOCs with internal data — have any of these indicators been observed in the entity's environment?
  4. **Action**: Deploy validated IOCs into detection systems (SIEM rules, IDS/IPS signatures, EDR watchlists, firewall block rules, DNS filters)
  5. **Feedback**: Report back to the sharing community whether the intelligence was relevant and whether it led to detection of threats — this closes the intelligence loop and improves future sharing quality

- Define maximum processing times for received intelligence:
  - Critical IOCs (active exploitation targeting financial sector): deploy to detection systems within 4 hours
  - High-priority TTPs: assess and update detection rules within 24 hours
  - Standard intelligence: process within 1 week

**What to share (and what not to share):**

**Share:**
- Indicators of compromise: IP addresses, domains, file hashes, URLs, email addresses associated with malicious activity
- TTPs observed in attacks against the entity (anonymised — do not reveal internal vulnerabilities or affected systems)
- Malware samples and analysis reports
- Phishing email samples and social engineering techniques observed
- Threat actor profiles and campaign analysis
- Defensive measures that proved effective (without revealing specific internal architecture)
- Vulnerability information when publicly known (CVE-based)

**Do not share:**
- Information that could identify specific clients or individuals (GDPR)
- Internal vulnerability details that could be exploited by attackers
- Information about specific ongoing incidents before they are contained and resolved
- Commercially sensitive information that could violate competition law (pricing, business strategy, M&A)
- Information received from other sharing arrangements under TLP:RED or other restrictive handling instructions, unless re-sharing is explicitly permitted
- Information that could be used to undermine the entity's competitive position

**Data protection safeguards (GDPR compliance):**
- Anonymise or pseudonymise any personal data before sharing (e.g., redact IP addresses that could identify individuals, use hashed email addresses)
- Conduct a Data Protection Impact Assessment (DPIA) for the information-sharing arrangement if personal data processing is involved
- Ensure a legal basis under GDPR Art. 6 for processing: legitimate interest in cybersecurity (Art. 6(1)(f)) is the most common basis, supported by DORA Art. 45 as a specific legal framework
- Include data protection provisions in the sharing arrangement agreement
- Appoint the DPO as a review point for any sharing that could include personal data

**Competition law safeguards:**
- Do not share commercially sensitive information through information-sharing arrangements
- Ensure sharing is limited to cybersecurity information — not business intelligence
- Maintain records of what was shared and by whom to demonstrate compliance
- Consider legal review of the sharing arrangement's rules of conduct to confirm competition law compliance

### Tools

- **Threat Intelligence Platforms (TIP)**: MISP (open-source, widely used in financial sector), OpenCTI (open-source), ThreatConnect, Recorded Future, Anomali
- **ISAC Platforms**: FS-ISAC Intelligence Exchange, CIRCL (Luxembourg CSIRT, operates MISP instance for the financial sector)
- **IOC Integration**: MISP → SIEM integration (Wazuh, Splunk, Elastic all support MISP feeds), STIX/TAXII feeds for automated IOC sharing
- **Automated IOC Deployment**: SOAR playbooks that auto-ingest validated IOCs into IDS/IPS rules, SIEM watchlists, EDR block lists, and firewall rules
- **TLP Enforcement**: MISP natively supports TLP tagging, email classification plugins for Outlook/Gmail

### Audit Evidence

- Competent authority notification of participation in information-sharing arrangements
- Information-sharing arrangement agreements with governance rules, data protection provisions, and competition law safeguards
- TLP handling procedures and training records
- Records of intelligence received and actions taken (IOC deployment logs)
- Intelligence processing workflow documentation with SLA targets
- Evidence of intelligence operationalisation: SIEM rules created from shared IOCs, detection events triggered by shared intelligence
- DPIA for information-sharing arrangement (if personal data is processed)
- Records of intelligence shared by the entity (with TLP classification and content summary)

### Priority: MEDIUM (voluntary but strongly recommended)

---

## Information Sharing Maturity Model

| Level | Description | Characteristics |
|---|---|---|
| Level 1 — Ad hoc | No formal sharing arrangements | Entity receives public threat intelligence (CERT advisories, vendor bulletins) but does not participate in structured sharing |
| Level 2 — Reactive | Basic sharing participation | Entity has joined one ISAC or sharing community, receives IOCs, manually reviews and deploys some indicators, no structured feedback |
| Level 3 — Structured | Formal sharing with automation | Entity participates in 2+ sharing communities, has deployed a TIP (MISP), automates IOC ingestion into SIEM/IDS, has TLP procedures, provides occasional feedback |
| Level 4 — Proactive | Active contributor | Entity actively shares anonymised intelligence from own incidents, contributes to community reports, has dedicated threat intelligence analyst(s), measures detection improvement from shared intelligence |
| Level 5 — Collaborative | Strategic intelligence partner | Entity co-develops threat analysis with peers, participates in joint threat hunting exercises, shares detection rules and defensive playbooks, contributes to sector-wide early warning initiatives, tracks intelligence-driven detection metrics |

Financial entities should aim for at least Level 3 to demonstrate meaningful compliance with the spirit of DORA Art. 45.

---

## Cross-Reference: DORA Pillar 5 ↔ ISO 27001:2022 ↔ NIST CSF 2.0

| DORA Article | ISO 27001:2022 Controls | NIST CSF 2.0 |
|---|---|---|
| Art. 45 Information Sharing | A.5.5 (Contact with Authorities), A.5.6 (Contact with Special Interest Groups), A.5.7 (Threat Intelligence) | ID.RA (Risk Assessment — threat intelligence input), DE.AE (Adverse Event Analysis) |

**Key gap**: ISO 27001 A.5.7 requires the entity to collect and analyse threat intelligence, and A.5.6 requires contact with special interest groups — but neither mandates participation in structured information-sharing arrangements or the notification to competent authorities that DORA requires. ISO 27001 also does not address the specific legal safeguards (data protection, competition law) needed for financial sector threat intelligence sharing.

---

## Document Metadata

- **Version**: 1.0
- **Knowledge base**: DORA Technical Implementation Advisor
- **Pillar**: 5 of 5 — Information Sharing
- **DORA Articles covered**: 45
- **RTS/ITS covered**: None (no dedicated Level 2 standards for this pillar)
- **Target entity type**: Credit institution (bank)
- **Proportionality tier**: Full framework
- **Last updated**: July 2026
