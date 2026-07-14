# DORA Pillar 3 — Digital Operational Resilience Testing

## Regulatory Scope

- **DORA Articles**: 24–27 (Chapter IV)
- **Key RTS**: Commission Delegated Regulation (EU) 2025/1190 — criteria for identifying entities required to perform TLPT, requirements for scope, methodology, testing phases, results, closure, remediation, and mutual recognition
- **Supporting Framework**: TIBER-EU (updated February 2025 to align with DORA RTS on TLPT)
- **Applicability**:
  - Art. 24–25 (basic testing): ALL financial entities
  - Art. 26–27 (TLPT): Only entities identified by competent authorities based on systemic importance, ICT risk profile, and ICT maturity
- **In force since**: 17 January 2025 (DORA); 8 July 2025 (RTS 2025/1190)
- **TLPT deadline**: First mandatory TLPT exercise must be completed before 17 January 2028

---

## Art. 24 — General Requirements for the Performance of Digital Operational Resilience Testing

### Requirement Summary

All financial entities must establish, maintain, and review a sound and comprehensive digital operational resilience testing programme as an integral part of the ICT risk management framework. The testing programme must include a range of assessments, tests, methodologies, practices, and tools. The programme must follow a risk-based approach taking into account the evolving landscape of ICT risk. Financial entities must ensure that tests are undertaken by independent parties — either internal or external. Where tests are conducted by an internal tester, the entity must dedicate sufficient resources and avoid conflicts of interest throughout the design and execution phases.

Microenterprises qualifying for the simplified framework under Art. 16 are exempt from the full testing programme requirements but must still perform proportionate testing.

### Technical Implementations

**Testing programme governance:**
- Document a formal Digital Operational Resilience Testing Programme approved by the management body
- The programme must define: scope (which systems and functions are tested), frequency (annual minimum for most tests), methodologies, responsible parties, reporting and follow-up processes
- Appoint a testing programme owner (typically the CISO or Head of ICT Risk)
- The testing programme must be reviewed and updated at least annually, and upon significant changes to infrastructure, applications, or threat landscape
- Maintain a testing calendar with planned tests for the year, tracking execution status

**Risk-based test planning:**
- Prioritise testing based on asset criticality and risk assessment results:
  - Tier 1 (critical/important functions): comprehensive annual testing including penetration testing
  - Tier 2 (significant): annual vulnerability assessment plus periodic penetration testing (at least every 2 years)
  - Tier 3 (standard): annual vulnerability assessment
- Factor in threat intelligence: if a new critical threat emerges targeting the banking sector, trigger ad-hoc testing of relevant controls
- Consider testing coverage across all layers: network, application, cloud, endpoint, physical, social engineering, third-party interfaces

**Independence requirements:**
- Internal testers must be independent from the teams responsible for developing, implementing, or operating the systems being tested
- Internal testers must have adequate skills, training, and resources — not simply reassigned developers
- External testers must have no conflicts of interest (e.g., the same firm should not be both building and testing the same system)
- For TLPT specifically: threat intelligence provider must always be external (see Art. 26)

**Testing programme documentation:**
- Maintain records of all tests performed: type, scope, date, tester, findings, risk ratings, remediation actions, closure dates
- Report testing results to the ICT Risk Committee and management body at least quarterly (summary) and annually (comprehensive review)
- Track remediation of testing findings with defined SLAs by severity:
  - Critical findings: 30 days
  - High findings: 60 days
  - Medium findings: 90 days
  - Low findings: next maintenance cycle or 180 days

### Tools

- **Testing Programme Management**: GRC platform (ServiceNow, Archer), Jira for finding tracking, custom testing calendar in SharePoint/Confluence
- **Reporting**: Power BI / Grafana dashboards showing testing coverage, finding trends, remediation status

### Audit Evidence

- Approved Digital Operational Resilience Testing Programme document
- Annual testing calendar with planned vs. executed tests
- Test reports for all conducted tests
- Finding tracking register with severity, SLA, remediation status, and closure evidence
- Management body reporting on testing results (board pack extracts)
- Independence evidence: tester qualifications, conflict of interest declarations

### Priority: CRITICAL

---

## Art. 25 — Testing of ICT Tools and Systems

### Requirement Summary

The digital operational resilience testing programme shall provide for the execution of appropriate tests, including at minimum:

- Vulnerability assessments and scans
- Open-source analyses
- Network security assessments
- Gap analyses
- Physical security reviews
- Questionnaires and scanning software solutions
- Source code reviews where feasible
- Scenario-based tests
- Compatibility testing
- Performance testing
- End-to-end testing
- Penetration testing

Financial entities other than microenterprises must perform all these tests at appropriate intervals. ICT systems and applications supporting critical or important functions must be tested at least annually.

### Technical Implementations

**Vulnerability assessments and scans:**
- Deploy automated vulnerability scanning across the full IT estate
- External scan frequency: weekly for internet-facing assets (web servers, email gateways, VPN endpoints, APIs)
- Internal scan frequency: monthly for all internal networks, servers, and endpoints
- Scan scope must include: operating systems, applications, databases, network devices, cloud workloads, container images
- Use authenticated scanning to identify configuration issues and missing patches (not just network-level CVEs)
- Produce monthly vulnerability management reports showing: total vulnerabilities by severity, new vs. recurring, remediation SLA compliance, aging analysis
- Integrate scan results with the asset inventory to automatically link vulnerabilities to asset criticality tier

**Open-source analysis (Software Composition Analysis — SCA):**
- Scan all applications for open-source and third-party library dependencies
- Identify known CVEs in open-source components using SCA tools
- Maintain a Software Bill of Materials (SBOM) for each critical application
- Monitor for newly disclosed vulnerabilities in used libraries (continuous monitoring, not just point-in-time)
- Enforce policies: block deployment of applications with critical or high CVEs in dependencies unless a documented exception exists
- Track license compliance for open-source components (avoid copyleft conflicts in proprietary systems)

**Network security assessments:**
- Annual comprehensive network security assessment covering: firewall rule review, network segmentation validation, wireless security assessment, DNS security, external footprint analysis
- Validate network segmentation controls: attempt lateral movement between security zones (production → development, user → server, DMZ → internal)
- Review and rationalize firewall rules: remove unused rules, validate business justification for each allow rule, identify overly permissive rules (any-any)
- Assess remote access security: VPN configuration, ZTNA implementation, MFA enforcement
- Perform external attack surface discovery: identify all internet-facing assets, shadow IT, cloud resources not in the official inventory

**Gap analyses:**
- Conduct annual gap analysis of the ICT risk management framework against DORA requirements, RTS 2024/1774, and other applicable standards (ISO 27001, NIST CSF)
- Document gaps with risk rating, remediation plan, and timeline
- Use the gap analysis to update the testing programme priorities

**Physical security reviews:**
- Annual review of data centre physical security: access controls, CCTV, environmental controls (cooling, fire suppression, water detection), power redundancy (UPS, generators)
- Review physical security of network equipment rooms, cabling infrastructure, and remote/branch offices
- Assess physical security of endpoint devices: laptop theft controls, secure printing, clean desk policy compliance
- For cloud-hosted systems: review cloud provider's SOC 2 Type II or ISO 27001 certificate covering physical security

**Source code reviews:**
- Perform static application security testing (SAST) on all critical applications before production deployment
- Conduct manual security code review for high-risk application components (authentication, authorisation, payment processing, cryptographic implementations)
- Review code for OWASP Top 10 vulnerabilities as a minimum baseline
- Integrate SAST into CI/CD pipeline with quality gates: builds with critical findings are blocked from deployment

**Scenario-based tests:**
- Design and execute scenario-based tests simulating realistic threat scenarios relevant to the banking sector:
  - **Ransomware scenario**: test detection, containment, communication, backup restoration, and recovery timeline
  - **Data breach scenario**: test data loss detection, scope assessment, DORA/GDPR notification process, client communication
  - **Third-party provider failure**: test business continuity when a critical ICT provider becomes unavailable
  - **Insider threat scenario**: test detection of malicious insider activity and response procedures
  - **Mass phishing campaign**: test email gateway filtering, user reporting, incident response activation
  - **DDoS attack**: test DDoS mitigation activation, traffic rerouting, service degradation management
- Run scenario tests at least twice annually, with different scenarios each time
- Include non-technical participants (management, legal, communications) in tabletop exercises

**Compatibility and performance testing:**
- Perform compatibility testing before any major system upgrade, migration, or integration change
- Conduct performance testing (load testing, stress testing) for critical systems:
  - Baseline: test at normal expected load
  - Peak: test at 2–3x normal load (e.g., month-end processing, salary payment days)
  - Stress: test to failure point to identify maximum capacity and degradation behaviour
- Run performance regression tests after significant changes to critical applications
- Validate cloud auto-scaling configurations under simulated load

**End-to-end testing:**
- Test complete business process chains from user interface through to backend systems and third-party integrations
- Focus on critical business processes: payment initiation → processing → settlement → confirmation
- Test failover scenarios end-to-end: primary system failure → DR activation → service restoration → validation
- Include third-party interface testing: test what happens when SWIFT, card scheme, or other external interfaces are unavailable

**Penetration testing:**
- Conduct annual penetration testing on all critical and important function systems
- Penetration test scope must include:
  - **External**: internet-facing applications, APIs, email infrastructure, VPN, cloud entry points
  - **Internal**: assumes a compromised workstation or insider access, tests lateral movement, privilege escalation, domain compromise
  - **Web application**: targeted testing of online banking, mobile banking APIs, payment portals
  - **Wireless**: rogue access point detection, WPA configuration, wireless segmentation
  - **Social engineering**: phishing campaigns, vishing, pretexting (with appropriate scope agreements)
- Penetration tests must go beyond automated scanning — testers must attempt to chain vulnerabilities and simulate real attack paths
- Retest all critical and high findings within 30 days of remediation
- Penetration test reports must include: executive summary, methodology, findings with CVSS scoring, evidence (screenshots, proof of concept), risk rating, and remediation recommendations

### Tools

- **Vulnerability Scanning**: OpenVAS/Greenbone (open-source), Nessus, Qualys, Rapid7 InsightVM, Tenable.io
- **SCA**: OWASP Dependency-Check (open-source), Snyk, Black Duck, FOSSA
- **SBOM Generation**: Syft (open-source), CycloneDX tools (open-source), Snyk SBOM
- **SAST**: SonarQube (open-source), Semgrep (open-source), Checkmarx, Fortify
- **DAST**: OWASP ZAP (open-source), Burp Suite, Acunetix, Rapid7 InsightAppSec
- **Network Assessment**: Nmap (open-source), Wireshark (open-source), Nipper (firewall audit), Qualys PCI compliance scans
- **Attack Surface Discovery**: Amass (open-source), Shodan, Censys, SecurityTrails
- **Penetration Testing**: Kali Linux (open-source), Metasploit (open-source), Cobalt Strike, Burp Suite Pro
- **Load/Performance Testing**: Apache JMeter (open-source), k6 (open-source), Gatling, Locust (open-source)
- **Phishing Simulation**: GoPhish (open-source), KnowBe4, Proofpoint Security Awareness

### Audit Evidence

- Vulnerability scan reports (monthly) with trending analysis
- SCA/SBOM reports for critical applications
- Network security assessment reports (annual)
- Gap analysis reports with remediation tracking
- Physical security review reports or cloud provider certification review records
- Source code review / SAST reports per release cycle
- Scenario-based test exercise reports with lessons learned
- Performance test reports with baseline, peak, and stress results
- End-to-end test reports for critical business processes
- Penetration test reports with findings, severity, remediation actions, and retest confirmations
- Phishing simulation results with metrics (click rate, report rate, training completion)

### Priority: CRITICAL

---

## Art. 26 — Advanced Testing of ICT Tools, Systems, and Processes Based on TLPT (Threat-Led Penetration Testing)

### Requirement Summary

Financial entities identified by competent authorities must carry out TLPT at least every 3 years. TLPT must cover several or all critical or important functions and must be performed on live production systems. The scope must be validated by the competent authority (TLPT authority). TLPT must be carried out in accordance with the TIBER-EU framework.

Financial entities may use internal testers but must contract external testers every third test. The threat intelligence provider must always be external. Credit institutions under direct ECB supervision must always use external testers.

Upon completion, the entity must submit a summary of findings, remediation plans, and documentation to the competent authority. The TLPT authority issues a formal attestation confirming the test was conducted in compliance with DORA. This attestation enables mutual recognition across Member States.

### RTS 2025/1190 — Key Requirements

**Identification of entities required to perform TLPT (RTS Art. 2):**

Entities automatically in scope include:
- Credit institutions classified as G-SIIs (Global Systemically Important Institutions) or O-SIIs (Other Systemically Important Institutions), or part of a G-SII/O-SII group
- Payment institutions that processed > EUR 150 billion in total transactions in each of the last 2 years
- Electronic money institutions with total outstanding e-money > EUR 2 billion in each of the last 2 years
- Central securities depositories with total value of securities settled > EUR 1 trillion per year
- Central counterparties
- Trading venues operating at least one market classified as a Significant Market
- Additional entities designated at the discretion of the national competent authority based on: impact on the financial sector, financial stability concerns, specific ICT risk profile, and ICT maturity

Competent authorities may also exclude entities that meet the above criteria if they determine the entity lacks sufficient ICT maturity to safely conduct a TLPT, or if TLPT would pose a disproportionate risk to continuity of services.

**TLPT participants (RTS Art. 3–7):**

| Participant | Role | Internal/External |
|---|---|---|
| TLPT Authority | Designated national authority that oversees the test, assigns test managers, approves scope, issues attestation | Regulatory body |
| TLPT Cyber Team (TCT) | Team within the TLPT authority composed of test managers; coordinates and monitors the test | Regulatory body |
| Control Team (CT) | Small internal team within the financial entity (formerly "White Team" under TIBER-EU); manages test logistics, maintains confidentiality from Blue Team | Internal to entity |
| Control Team Lead (CTL) | Named individual accountable for test management within the entity; single point of contact for the TLPT authority | Internal to entity |
| Threat Intelligence (TI) Provider | Analyses the adversarial landscape, develops threat scenarios and the Targeted Threat Intelligence Report | Always external |
| Red Team (RT) | Executes the attack scenarios on live production systems based on TI report | External or internal (external every 3rd test; always external for ECB-supervised institutions) |
| Blue Team (BT) | The entity's defensive security team — NOT aware the test is taking place | Internal to entity |

**Provider qualification requirements (RTS Art. 7):**

- TI provider staff: manager with ≥ 5 years threat intelligence experience, supporting analysts with ≥ 2 years
- TI provider: ≥ 3 references from previous TI/red team assignments
- External red team lead: ≥ 5 years penetration testing and red team experience
- Supporting red team members: ≥ 2 years each
- External testers: ≥ 5 references from previous penetration testing / red team assignments
- Professional indemnity insurance covering misconduct and negligence
- No conflicts of interest: red team and TI providers must not have been involved in the entity's defensive security operations
- TI and RT providers can be from the same company but must have separate staff with no overlap

### Technical Implementations

**TLPT process — six phases:**

**Phase 1 — Initiation (0–3 months from notification):**
- Receive formal notification from the TLPT authority identifying the entity for TLPT
- Appoint the Control Team Lead (CTL) and establish the Control Team (maximum 3–5 people with strict need-to-know)
- Submit high-level project plan to the TLPT authority
- Confirm communication protocols and secure channels with TLPT authority test managers
- Establish confidentiality framework: the Blue Team must NOT be informed at any stage before the test conclusion
- Procure TI provider and red team provider (or designate internal red team if eligible)
- Verify provider qualifications against RTS Art. 7 requirements

**Phase 2 — Scoping (0–6 months from notification):**
- Identify all critical or important functions (CIFs) within the entity
- Map CIFs to underlying ICT systems, applications, infrastructure, and data stores
- Define the scope specification document including:
  - CIFs to be tested (must cover several or all — TLPT authority approves the scope)
  - Underlying ICT systems and live production environments in scope
  - Attack surface: network entry points, application interfaces, human targets
  - Any exclusions (must be justified and approved by TLPT authority — e.g., specific third-party systems where provider has not consented)
  - Risk management measures: rules of engagement, escalation procedures, stop conditions, data handling restrictions
- Submit scope specification to TLPT authority for validation
- TLPT authority may require scope expansion if critical CIFs are missing

**Phase 3 — Threat Intelligence (2–3 months):**
- TI provider conducts research on the entity's threat landscape:
  - Business profile and public footprint analysis (OSINT)
  - Sector-specific threat actors, their motivations, capabilities, and TTPs
  - Entity-specific attack surface analysis
  - Geopolitical and sector-wide threat trends
- TI provider delivers the Targeted Threat Intelligence (TTI) Report containing:
  - Prioritised list of relevant threat actors
  - Most realistic attack scenarios based on actual threat actor TTPs
  - Recommended red team test objectives and attack paths
- Control Team reviews TTI Report with TLPT authority test managers
- TLPT authority validates the scenarios are sufficiently challenging and realistic

**Phase 4 — Red Team Testing (minimum 12 weeks active testing):**
- Red team executes attack scenarios on LIVE PRODUCTION SYSTEMS
- Testing must replicate real-world TTPs — not just automated vulnerability exploitation
- Attack vectors may include: network attacks, web application exploitation, social engineering (phishing, vishing, physical access attempts), supply chain simulation, credential harvesting, lateral movement, privilege escalation, data exfiltration (simulated)
- Blue Team is NOT aware the test is happening — they respond as they would to a real attack
- Control Team monitors the test to ensure it stays within rules of engagement and does not threaten business continuity
- If the red team achieves objectives early, extend testing to additional objectives rather than stopping
- If an actual incident is detected by the Blue Team during the test, the Control Team must assess whether to continue, pause, or abort — in coordination with the TLPT authority
- Minimum duration: 12 weeks of active testing (not including preparation and closure)

**Phase 5 — Closure (immediately after testing):**
- Red team delivers the Red Team Test Report: all actions taken, vulnerabilities exploited, objectives achieved, evidence collected
- **Replay workshop**: Red team walks through the attack timeline with the Blue Team and Control Team — this is where the Blue Team learns the test occurred
- **Purple teaming (mandatory under RTS 2025/1190)**: Red team and Blue Team collaborate to:
  - Understand exactly what the Blue Team detected vs. missed
  - Test additional detection capabilities in a collaborative environment
  - Identify defensive gaps and jointly develop improvements
  - Validate that specific TTPs could be detected with control adjustments
- Blue Team contributes a Blue Team Report documenting: what they detected, how they responded, and what they missed
- Entity produces a Remediation Plan with specific actions, owners, and timelines for each identified gap
- Control Team produces a Test Summary Report (sanitised version suitable for wider distribution)

**Phase 6 — Attestation and follow-up:**
- Submit to the TLPT authority:
  - Test Summary Report
  - Remediation Plan
  - Red Team Test Report (confidential, limited distribution)
  - Blue Team Report
  - Any additional evidence requested
- TLPT authority reviews all deliverables and issues a formal attestation (Annex VIII of RTS 2025/1190) confirming the test was conducted in accordance with DORA Art. 26 and the RTS
- The attestation enables mutual recognition: if the entity operates in multiple Member States, the attestation can be presented to other competent authorities without requiring a duplicate test
- Execute the remediation plan — TLPT authority may follow up on remediation progress
- Feed findings into the ICT risk management framework (Pillar 1), update detection rules, and improve incident response playbooks (Pillar 2)

**Internal tester requirements (when using internal red team):**
- Internal testers must be independent from the area responsible for the systems being tested
- Internal testers must not be involved in any defensive security activity for the entity
- Internal testers must meet the same qualification standards as external testers
- The TI provider must always be external, even when using internal red team
- Every third TLPT must use external testers (mandatory rotation)
- ECB-supervised significant credit institutions cannot use internal testers — always external

**Risk management during TLPT:**
- Define clear rules of engagement before testing begins:
  - Permitted attack techniques and any exclusions
  - Data handling: no actual exfiltration of real customer data — simulated exfiltration with proof of access
  - System availability: stop conditions if testing threatens system stability
  - Working hours and escalation contacts
  - Legal protections for testers (authorisation letter)
- Maintain a real-time communication channel between Control Team and red team for emergency stop situations
- Have a pre-agreed process for distinguishing test activity from actual attacks (deconfliction protocol with SOC)

### Tools

- **Threat Intelligence**: MISP (open-source), OpenCTI (open-source), Recorded Future, Mandiant, Flashpoint, FS-ISAC intelligence
- **OSINT**: Maltego, SpiderFoot (open-source), Recon-ng (open-source), theHarvester (open-source), Amass (open-source)
- **Red Team**: Kali Linux (open-source), Cobalt Strike, Metasploit (open-source), Sliver (open-source), Havoc (open-source), Brute Ratel
- **C2 Frameworks**: Cobalt Strike, Sliver (open-source), Havoc (open-source), Mythic (open-source)
- **Social Engineering**: GoPhish (open-source), Evilginx2 (open-source for phishing simulation), SET (Social Engineering Toolkit, open-source)
- **Purple Teaming**: MITRE Caldera (open-source), Atomic Red Team (open-source), Vectr (open-source for engagement tracking), AttackIQ
- **Test Management**: Vectr (open-source), PlexTrac, custom reporting templates aligned with TIBER-EU deliverables

### Audit Evidence

- TLPT notification letter from TLPT authority
- Control Team appointment documentation with CTL designation
- Provider contracts with qualification evidence (CVs, certifications, references, insurance)
- Scope specification document with TLPT authority validation
- Targeted Threat Intelligence (TTI) Report
- Red Team Test Report (confidential, restricted access)
- Blue Team Report
- Purple teaming session records and outcomes
- Remediation Plan with tracked actions and closure evidence
- Test Summary Report
- TLPT authority attestation (Annex VIII)
- Rules of engagement document
- Risk management measures and deconfliction protocol documentation

### Priority: CRITICAL (for entities identified by competent authority)

---

## Art. 27 — Requirements for Testers for the Carrying Out of TLPT

### Requirement Summary

Financial entities must only use testers that meet specific requirements for TLPT:

- Are of the highest suitability and reputability
- Possess technical and organisational capabilities (specifically in threat intelligence, penetration testing, and red team testing)
- Are certified by an accreditation body or adhere to formal codes of conduct or ethical frameworks
- Provide an independent assurance or audit report on sound management of risks associated with TLPT, including proper protection of the entity's confidential information and redress for business risks
- Are duly and fully covered by professional indemnity insurance

For internal testers: they must be approved or not objected to by the competent authority, must be independent from the tested functions, and the entity must have sufficient resources to avoid conflicts of interest.

### Technical Implementations

**Tester qualification verification checklist:**

For **external testers** (Red Team):
- [ ] Red Team Lead: ≥ 5 years penetration testing / red team experience
- [ ] Supporting members: ≥ 2 years each
- [ ] ≥ 5 references from previous pen test / red team engagements
- [ ] Relevant certifications: OSCP, OSEP, CRTO, CRTE, OSED, CREST CRT/CCT, GXPN, or equivalent
- [ ] Professional indemnity insurance covering misconduct and negligence
- [ ] No conflict of interest: not involved in the entity's defensive security
- [ ] Independent assurance report or audit on risk management practices
- [ ] Adherence to ethical framework / code of conduct (e.g., CREST Code of Conduct, EC-Council Code of Ethics)
- [ ] NDA and confidentiality agreement covering all entity data
- [ ] Data handling procedures: no retention of entity data post-engagement, secure deletion verification

For **Threat Intelligence providers**:
- [ ] TI manager: ≥ 5 years threat intelligence experience
- [ ] Supporting analysts: ≥ 2 years each
- [ ] ≥ 3 references from previous TI / red team testing assignments
- [ ] Professional indemnity insurance
- [ ] No conflict of interest with the entity's security operations
- [ ] Always external (cannot be internal staff)

For **internal testers** (when permitted):
- [ ] Competent authority approval or non-objection obtained
- [ ] Independence from ICT development, operations, and security operations
- [ ] Meet same qualification standards as external testers
- [ ] Sufficient dedicated resources (not shared with operational duties during testing)
- [ ] Cannot be used for more than 2 consecutive TLPTs — every 3rd test must use external red team
- [ ] NOT permitted for ECB-supervised significant credit institutions

**Provider procurement process:**
- Issue an RFP with explicit qualification requirements aligned with RTS Art. 7
- Evaluate proposals against qualification matrix — reject non-compliant providers
- Verify references through direct contact with previous clients
- Review provider's own security posture: how do they protect engagement data?
- Include contractual obligations: data handling, destruction post-engagement, incident notification, liability
- Maintain a pre-approved provider panel to avoid procurement delays when TLPT notification arrives

**Post-test obligations for testers:**
- Red team must restore all systems to their pre-test state: remove implants, backdoors, test accounts, and artefacts
- Red team must provide a complete list of all tools used during the test
- Red team must securely delete all entity data collected during the test, with certification of deletion
- Red team must not retain any offensive capabilities specific to the entity (custom exploits, credentials, access paths)

### Tools

- **Provider Vetting**: Custom qualification matrix spreadsheet, reference check templates, compliance checklists
- **Contract Management**: Standard TLPT contract templates (some TIBER-EU national implementations provide these)
- **Certification Verification**: Offensive Security portal (OSCP verification), CREST member directory, EC-Council certificate verification

### Audit Evidence

- Provider qualification assessment records (CVs, certifications, references verified)
- Professional indemnity insurance certificates
- Conflict of interest declarations
- NDAs and confidentiality agreements
- Independent assurance reports on provider risk management
- Ethical framework adherence declarations
- Post-test system restoration confirmation
- Data deletion certificates from providers
- Competent authority approval for internal testers (if applicable)

### Priority: CRITICAL (for TLPT-designated entities)

---

## Testing Requirements Matrix — Summary by Entity Type

| Test Type | All Financial Entities | Entities with CIFs | TLPT-Designated Entities | Microenterprises |
|---|---|---|---|---|
| Vulnerability assessments | Annual | Annual | Annual | Proportionate |
| Open-source / SCA analysis | Annual | Annual | Annual | Not required |
| Network security assessment | Annual | Annual | Annual | Proportionate |
| Gap analysis | Annual | Annual | Annual | Simplified |
| Physical security review | Annual | Annual | Annual | Proportionate |
| Source code review (SAST) | Per release cycle | Per release cycle | Per release cycle | Not required |
| Scenario-based tests | Annual | ≥ 2x per year | ≥ 2x per year | Not required |
| Performance testing | Annual for critical | Annual for critical | Annual for critical | Not required |
| End-to-end testing | Annual | Annual | Annual | Proportionate |
| Penetration testing | Annual for critical | Annual | Annual | Not required |
| TLPT (red team) | Not required | Not required | Every 3 years | Not required |
| Purple teaming | Not required | Recommended | Mandatory with TLPT | Not required |

---

## TLPT Process Timeline (Typical 6–12 Month Engagement)

```
MONTH 1–3: INITIATION
│ ├─ Receive notification from TLPT authority
│ ├─ Appoint Control Team Lead and Control Team
│ ├─ Submit project plan to TLPT authority
│ ├─ Procure TI provider and Red Team provider
│ └─ Verify provider qualifications (RTS Art. 7)
│
MONTH 2–6: SCOPING
│ ├─ Identify all CIFs and map to ICT systems
│ ├─ Define scope specification document
│ ├─ Submit scope to TLPT authority for validation
│ └─ Finalise rules of engagement
│
MONTH 4–7: THREAT INTELLIGENCE
│ ├─ TI provider conducts research (OSINT, sector analysis)
│ ├─ TI provider delivers Targeted Threat Intelligence Report
│ ├─ Control Team and TLPT authority validate scenarios
│ └─ Red Team prepares test plan based on TTI Report
│
MONTH 5–10: RED TEAM TESTING (minimum 12 weeks active)
│ ├─ Red Team executes attack scenarios on live production
│ ├─ Blue Team unaware — responds as to real attacks
│ ├─ Control Team monitors, manages risks, liaises with TLPT authority
│ └─ Red Team documents all actions, findings, evidence
│
MONTH 10–11: CLOSURE
│ ├─ Red Team delivers Red Team Test Report
│ ├─ Replay workshop: Red Team walks through attack timeline
│ ├─ Purple teaming: collaborative Red + Blue Team exercises
│ ├─ Blue Team delivers Blue Team Report
│ ├─ Entity produces Remediation Plan
│ └─ Control Team produces Test Summary Report
│
MONTH 11–12: ATTESTATION
│ ├─ Submit all deliverables to TLPT authority
│ ├─ TLPT authority reviews and issues attestation
│ ├─ Execute remediation plan
│ └─ Feed findings into ICT risk management framework
```

---

## Penetration Testing vs. TLPT — Key Differences

| Aspect | Penetration Testing (Art. 25) | TLPT (Art. 26) |
|---|---|---|
| Who must do it | All financial entities (for critical systems) | Only entities identified by competent authority |
| Frequency | Annually | At least every 3 years |
| Scope | Specific systems, applications, or network segments | Several or all critical/important functions |
| Environment | Can be done in test/staging or production | Must be on live production systems |
| Blue Team awareness | Usually aware a test is happening | NOT aware — covert testing |
| Threat intelligence | Generic methodology | Custom TI report based on real threat actors targeting the entity |
| Duration | Typically 1–4 weeks | Minimum 12 weeks active testing (6–12 months total engagement) |
| Regulatory oversight | No direct regulatory involvement | TLPT authority oversees all phases, issues attestation |
| Purple teaming | Optional best practice | Mandatory |
| Provider requirements | Qualified pen testers | Strict RTS qualification requirements with minimums for experience and references |
| Mutual recognition | No | Yes — attestation recognised across Member States |
| Output | Vulnerability report | Red Team Report + Blue Team Report + Purple Team outcomes + Remediation Plan + Attestation |

---

## Cross-Reference: DORA Pillar 3 ↔ ISO 27001:2022 ↔ NIST CSF 2.0

| DORA Article | ISO 27001:2022 Controls | NIST CSF 2.0 |
|---|---|---|
| Art. 24 General Testing Requirements | A.8.8 (Management of Technical Vulnerabilities), A.5.35–5.36 (Independent Review, Compliance with Policies) | ID.RA (Risk Assessment), PR.PS |
| Art. 25 Testing of ICT Tools and Systems | A.8.8 (Vuln Management), A.8.34 (Protection of Info Systems during Audit Testing), A.8.25–8.31 (Secure Dev Lifecycle) | DE.CM, ID.RA, PR.DS |
| Art. 26 TLPT | No direct ISO 27001 equivalent — TIBER-EU is the recognised framework | DE.CM, RS.MA, ID.RA |
| Art. 27 Tester Requirements | A.5.35 (Independent Review of Information Security), A.5.19–5.22 (Supplier Management) | GV.SC (Supply Chain Risk Management) |

**Key gap**: ISO 27001 requires vulnerability management and independent security reviews but does not mandate threat-led penetration testing on live production systems with regulatory oversight. TLPT under DORA goes significantly beyond what ISO 27001 requires.

---

## Document Metadata

- **Version**: 1.0
- **Knowledge base**: DORA Technical Implementation Advisor
- **Pillar**: 3 of 5 — Digital Operational Resilience Testing
- **DORA Articles covered**: 24, 25, 26, 27
- **RTS covered**: Commission Delegated Regulation (EU) 2025/1190
- **Supporting framework**: TIBER-EU (updated February 2025)
- **Target entity type**: Credit institution (bank)
- **Proportionality tier**: Full framework (assumes potential TLPT designation)
- **Last updated**: July 2026
