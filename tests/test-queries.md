# Test Queries — DORA Technical Implementation Advisor

**Status: revised evaluation specification; no completed validation claimed.** The 30 query IDs and three difficulty rounds are retained. Several prompts and reference expectations have been revised to avoid rewarding unsupported legal or technical claims. Scores from earlier prompt/corpus versions must not be treated as directly comparable.

## Evaluation method

Review the expected answer against the cited official provisions before scoring. The reference points below are working evaluation guidance, not a complete legal opinion. Record the exact paragraphs, source edition, applicability assumptions, and reviewer approval in the run record. Missing source text must be disclosed, not replaced with a confident guess.

Score each completed answer separately on four dimensions:

| Dimension | What to assess |
| --- | --- |
| Accuracy | Correct interpretation and citations that actually support the claims. |
| Completeness | Covers the material requirements for the stated scenario and identifies scope limits. |
| Specificity | Useful, justified controls and evidence; tool names are optional and do not earn points by themselves. |
| Unsupported-claim resistance | Avoids invented provisions, universal technology mandates, unsupported deadlines, and compliance assurances; acknowledges missing context. |

| Score | Common anchor, applied independently to each dimension |
| --- | --- |
| 1 | Fundamentally wrong, unsupported, or unusable for the scenario. |
| 2 | Material errors or omissions requiring substantial correction. |
| 3 | Useful partial answer with identifiable corrections or gaps. |
| 4 | Substantially correct and supported; minor gaps. |
| 5 | Correct, sufficiently scoped, well-supported, and explicit about material uncertainty. |

Record the mean of the four dimension scores for each scored answer and retain the individual scores. Failed or incomplete runs are not scored; report them separately and show coverage. Do not hide missing cases behind an average. Report material errors and false citations separately even when the average is high. Check retrieved passages separately from generated answers to distinguish retrieval and generation failures.

The original average target of **3.5/5** is retained only as an exploratory project target. It is not a validated acceptance threshold for legal accuracy, banking deployment, or compliance assurance. No current threshold authorises production use.

## Round 1 — Basic factual retrieval

### Q01 — What are the five commonly described DORA pillars?

**Expected review points:** ICT risk management; incident reporting; resilience testing; ICT third-party risk; information sharing. Explain that the five-pillar grouping is a useful summary, not the regulation’s complete chapter structure.

**Source anchors to check:** DORA Chapters II–VI.

### Q02 — How often must the ICT risk management framework be reviewed?

**Expected review points:** For the assumed full-framework credit institution, at least yearly and on relevant event-driven triggers. Identify the microenterprise distinction rather than generalising to every entity.

**Source anchors to check:** DORA Art. 6(5).

### Q03 — What criteria determine whether an ICT-related incident is major?

**Expected review points:** Assess clients/financial counterparts/transactions, reputation, duration/downtime, geographical spread, data losses, criticality, and economic impact. Apply the critical-services condition and Article 8 combination logic using the exact Article 9 thresholds; do not treat any confidentiality breach as automatically major. Consider recurring incidents where applicable.

**Source anchors to check:** DORA Art. 18; RTS 2024/1772 Arts. 1–9.

### Q04 — When is the initial major-incident notification due?

**Expected review points:** Distinguish awareness from classification. Apply Article 5(1)(a), the later-classification rule in 5(2), and relevant exceptions; do not state an unconditional four-hour-from-detection rule. Credit institutions must not assume the weekend/bank-holiday extension applies to them.

**Source anchors to check:** DORA Art. 19; RTS 2025/301 Art. 5.

### Q05 — What is TLPT, and which entities must perform it?

**Expected review points:** Threat-led penetration testing for entities identified by the competent authority under the applicable criteria. Explain authority assessment and exclusions; do not infer scope from bank size alone or present indicative categories as automatic final designation.

**Source anchors to check:** DORA Arts. 26–27; RTS 2025/1190 Art. 2.

### Q06 — What is the Register of Information and what must be reported?

**Expected review points:** Maintain and update the register of all ICT third-party contractual arrangements at the relevant levels. Distinguish annual reporting on arrangements from providing the full register on request and any specific supervisory collection instructions.

**Source anchors to check:** DORA Art. 28(3); ITS 2024/2956.

### Q07 — How often must designated entities perform TLPT?

**Expected review points:** At least every three years, subject to the competent authority’s ability to adjust frequency. Establish entity designation and the applicable authority schedule.

**Source anchors to check:** DORA Art. 26(1).

### Q08 — What is the minimum duration of active red-team testing in a TLPT?

**Expected review points:** At least 12 weeks for the active phase; distinguish this from the total engagement and explain scope/proportionality.

**Source anchors to check:** RTS 2025/1190 Art. 11(5).

### Q09 — Should the Blue Team know about a TLPT in advance?

**Expected review points:** Explain covert active testing, control-team governance, and disclosure during closure. Recognise authority-controlled exceptional limited purple teaming rather than an absolute rule that the Blue Team can never be informed.

**Source anchors to check:** RTS 2025/1190 Arts. 11–12.

### Q10 — What purple-teaming activities are required in TLPT?

**Expected review points:** Distinguish replay and purple teaming in closure from exceptional limited purple teaming during the active phase.

**Source anchors to check:** RTS 2025/1190 Arts. 11(10), 12(5).

## Round 2 — Technical implementation

### Q11 — What network security controls should a bank assess under DORA?

**Expected review points:** Source-supported network management, risk-based segmentation, network/data-flow documentation, administration-network separation, and access controls. VLANs, NGFW, IDS/IPS, NAC, VPN/MFA, and ZTNA are candidate designs, not a universal product checklist.

**Source anchors to check:** DORA Art. 9; RTS 2024/1774 Arts. 13–14.

### Q12 — Does DORA universally require TLS 1.2, AES-256, and an HSM?

**Expected review points:** Do not assert those precise technologies as universal mandates. Explain risk- and classification-based cryptographic policy, key lifecycle, and justified implementation choices.

**Source anchors to check:** DORA Art. 9; RTS 2024/1774 Arts. 6–7.

### Q13 — How should backup and recovery controls be designed?

**Expected review points:** Address backup scope and frequency, recovery objectives, segregation, restoration testing, and evidence. A 3-2-1-1 pattern or immutable backup is an implementation option; it does not by itself satisfy DORA.

**Source anchors to check:** DORA Arts. 11–12; RTS 2024/1774 Arts. 24–26.

### Q14 — Can an open-source SIEM demonstrate compliance with detection requirements?

**Expected review points:** Wazuh and Elastic Security are options; evaluate source coverage, detection capability, logging protection, response workflows, and tests. A product cannot certify compliance.

**Source anchors to check:** DORA Art. 10; RTS 2024/1774 Arts. 12, 22–23.

### Q15 — What contractual provisions must be reviewed for ICT services?

**Expected review points:** Separate baseline Article 30(2) provisions from the additional Article 30(3) provisions for services supporting critical or important functions. Assess signed clauses and practical enforceability.

**Source anchors to check:** DORA Art. 30.

### Q16 — How should a bank define patch-management SLAs?

**Expected review points:** Use risk, exposure, exploitation, criticality, and change safety. Numerical targets such as 24–48 hours or 7/30/90 days are project examples, not universal DORA deadlines. Document exceptions and compensating controls.

**Source anchors to check:** RTS 2024/1774 Art. 10.

### Q17 — How should identity and access controls be implemented?

**Expected review points:** Assess identity lifecycle, least privilege, segregation of duties, access reviews, privileged access, and strong authentication in the applicable cases. Separate exact source requirements from a proposed PAM/RBAC implementation and any additional policy cadence.

**Source anchors to check:** DORA Art. 9; RTS 2024/1774 Arts. 20–21.

### Q18 — How should scenario-based resilience testing be scheduled?

**Expected review points:** Use a risk-based programme and suitable methods. Explain the annual appropriate-testing requirement for systems/applications supporting critical or important functions, rather than inventing a universal twice-yearly scenario-test requirement.

**Source anchors to check:** DORA Arts. 24–25.

### Q19 — What should an ICT third-party exit strategy contain?

**Expected review points:** Address credible exit scenarios, continuity, alternatives, data recovery/return, transition, and feasibility testing where applicable. Do not claim a universal six-month transition or three-year exit-test cycle without a source.

**Source anchors to check:** DORA Arts. 28(8), 30(3)(f); RTS 2024/1773.

### Q20 — How should a bank evaluate threat-intelligence sharing communities?

**Expected review points:** Consider trusted communities and suitable arrangements, confidentiality, personal data, competition law, notification on participation/cessation, and handling rules. Participation is voluntary; no mandatory maturity level is established by this case study.

**Source anchors to check:** DORA Art. 45.

## Round 3 — Cross-pillar analysis

### Q21 — A ransomware incident affects online banking: what obligations should be assessed?

**Expected review points:** State scenario assumptions; cover detection, containment, classification, applicable reporting clocks, client communications, recovery, third-party coordination, and lessons learned. Explain missing facts and parallel obligations; do not claim an exhaustive determination from the short scenario.

**Source anchors to check:** DORA Arts. 10–13, 17–19, 30; relevant incident RTS/ITS.

### Q22 — How can DORA network security requirements be compared with ISO/IEC 27001:2022?

**Expected review points:** Provide a bounded interpretive mapping to relevant Annex A controls, including 8.20–8.22 where supported. Explain scope and evidence differences; neither framework implies automatic compliance with the other.

**Source anchors to check:** DORA Art. 9; RTS 2024/1774 Art. 13; ISO/IEC 27001:2022.

### Q23 — How do regular penetration tests differ from TLPT?

**Expected review points:** Compare purpose, entity designation, scope, risk-based frequency, production-system requirements, intelligence-led scenarios, authority oversight, active-phase duration, and closure activities. Article 25 does not impose one uniform penetration-test cadence for every entity and system.

**Source anchors to check:** DORA Arts. 24–27; RTS 2025/1190.

### Q24 — Assume a cloud provider is designated a critical ICT third-party provider: what changes?

**Expected review points:** Treat designation as a scenario assumption, not a verified claim about a named provider. Explain oversight and continuing entity responsibility, monitoring, concentration risk, and contractual/exit review; separate provider/overseer duties from customer obligations.

**Source anchors to check:** DORA Arts. 28–44.

### Q25 — What evidence could support a DORA assurance review?

**Expected review points:** Propose scoped requests for approved governance, inventories, risk assessments, control configurations, test results, incidents, third-party registers/contracts, and remediation. Specify owner, date, scope, and effectiveness assessment; a checklist alone proves nothing.

**Source anchors to check:** Relevant DORA provisions for each evidence category.

### Q26 — What capabilities should be assessed when designing a SOC?

**Expected review points:** Map logging, detection, escalation, incident handling, reporting coordination, and improvement to relevant provisions. Do not claim a named SOC operating model or vendor is mandated.

**Source anchors to check:** DORA Arts. 9–10, 13, 17; RTS 2024/1774 Arts. 12, 22–23.

### Q27 — How should DORA reporting and personal-data-breach notification be coordinated?

**Expected review points:** Assess separate DORA and GDPR triggers, recipients, and clocks. For GDPR, distinguish the risk-based Article 33 authority notification and Article 34 high-risk communication conditions. If GDPR text is absent from retrieved context, disclose that source gap and require verification before giving legal detail.

**Source anchors to check:** DORA Art. 19; RTS 2025/301; GDPR Arts. 33–34 (additional source needed).

### Q28 — How should concentration risk be assessed before outsourcing core banking?

**Expected review points:** Assess substitutability, dependencies, provider/group and geographic concentration, subcontracting, criticality, and exit feasibility. Numerical amber/red thresholds are internal risk choices, not universal DORA limits.

**Source anchors to check:** DORA Art. 29; relevant policy RTS.

### Q29 — What qualifications must external TLPT providers demonstrate?

**Expected review points:** Check Article 7 provider insurance, references, team composition, experience, independence, and restoration requirements. Distinguish external tester and TI-provider conditions; named commercial certifications are examples, not an exclusive legal list.

**Source anchors to check:** DORA Art. 27; RTS 2025/1190 Art. 7.

### Q30 — Design a DORA implementation roadmap for a mid-sized bank.

**Expected review points:** Start with applicability, accountable governance, source inventory, scoped gap assessment, risk-based control design, evidence collection, testing, and remediation. Include third-party arrangements and TLPT only where applicable. Assign owners and dependencies; do not promise compliance by a generic timeline.

**Source anchors to check:** DORA Arts. 2–4 and relevant thematic provisions.

## Required record per query

Keep the model and configuration ID, exact query, raw response, retrieved passages and source IDs, four dimension scores, reviewer rationale, citation checks, material errors, gaps, and final review status. Use [evaluation-results.md](evaluation-results.md) for the run register and procedure. Human review of the reference answer is required before the benchmark can support reliable conclusions.
