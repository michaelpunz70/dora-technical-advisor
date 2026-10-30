# DORA Pillar 1 — ICT Risk Management

## Interpretation and assurance status

**Editorial revision: 30 October 2026. Human legal/control review remains open.** This document is an author-created working mapping, not an authoritative statement or evidence of implemented controls. Regulatory summaries must be checked against the current official text and entity-specific applicability. This revision corrects selected identified issues; it is not a paragraph-by-paragraph legal assurance opinion.

**Reading rules:** technical designs, products, numeric thresholds, internal SLAs, review cadences, staffing choices, and maturity targets in implementation sections are project examples unless an exact source provision expressly supports them. They are not universal regulatory minima. Priority labels are project judgements. Evidence lists are requests for material to collect, not assertions that it exists or is sufficient. ISO/NIST cross-references are interpretive and require edition-specific review.

For each adopted control, record: provision and applicability rationale; control objective and design; accountable owner; evidence artifact, period, and location; design and operating-effectiveness checks; result, gap, remediation owner, and due date. Use [the mapping review procedure](../../docs/mapping-review.md) before relying on this material.

## Regulatory Scope

- **DORA Articles**: 5–16 (Chapter II)
- **Key RTS**: Commission Delegated Regulation (EU) 2024/1774 — ICT risk management tools, methods, processes, policies, and simplified framework
- **Applicability**: All financial entities, with proportionality based on size, complexity, and risk profile
- **DORA application date**: 17 January 2025

---

## Art. 5 — Governance and Organisation

### Working Regulatory Summary — Verify Against Official Text

The management body (board of directors) bears ultimate responsibility for ICT risk management. It must define, approve, oversee, and be accountable for the implementation and review of the ICT risk management framework. The management body must set clear roles and responsibilities for ICT-related functions, establish risk appetite levels for ICT risk, and approve the digital operational resilience strategy.

Members of the management body must actively keep up-to-date knowledge and skills on ICT risks — including through regular training.

### Proposed Technical Implementations — Project Examples

**Governance structure:**
- Assign ICT risk management responsibilities to an appropriately independent control function, consistent with DORA Art. 6(4) where applicable; a dedicated team is a possible organisational design, not a universal staffing prescription
- Appoint a Chief Information Security Officer (CISO) or equivalent role with direct reporting line to the management body
- Create an ICT Risk Committee or integrate ICT risk into the existing Operational Risk Committee
- Implement a RACI matrix for ICT risk roles across three lines of defense

**Board-level reporting:**
- Deploy GRC platform dashboards (e.g., ServiceNow GRC, Archer, OpenPages) with real-time ICT risk KPIs and KRIs
- Schedule quarterly ICT risk reports to the management body including: threat landscape summary, incident trends, risk appetite utilisation, control effectiveness metrics
- Maintain a risk appetite statement with quantified thresholds for ICT risk (e.g., maximum acceptable downtime per critical function, maximum tolerable data loss)

**Training and awareness:**
- Regular ICT risk training for management body members, with annual scheduling as a proposed internal cadence — covering cyber threats, ICT architecture, and regulatory obligations
- Tabletop exercises for the management body simulating major ICT incidents (ransomware, data breach, third-party failure)

### Tools

- **GRC Platforms**: ServiceNow GRC, RSA Archer, IBM OpenPages, open-source: Eramba
- **Board Reporting**: Power BI / Tableau dashboards connected to SIEM and GRC data
- **Training**: KnowBe4 (executive track), SANS Security Awareness, custom tabletop scenarios

### Candidate Evidence to Collect and Assess

- Approved ICT risk management framework document with board signatures and date
- Board meeting minutes showing ICT risk discussions and decisions
- Training attendance records and completion certificates for management body members
- RACI matrix for ICT risk functions
- ICT risk appetite statement approved by the management body

### Priority: CRITICAL

---

## Art. 6 — ICT Risk Management Framework

### Working Regulatory Summary — Verify Against Official Text

Financial entities must establish, maintain, and continuously update a sound, comprehensive, and well-documented ICT risk management framework as part of their overall risk management system. The framework must include strategies, policies, procedures, ICT protocols, and tools necessary to protect all information and ICT assets. The framework must be documented and, for the assumed full-framework credit institution, reviewed at least yearly and on applicable event-driven triggers, and improved based on lessons learned from incidents and testing. Internal audit must review it according to the entity's audit plan.

### Proposed Technical Implementations — Project Examples

**Framework architecture:**
- Structure the framework following the NIST CSF 2.0 functions (Govern, Identify, Protect, Detect, Respond, Recover) mapped to DORA-specific requirements
- Maintain a master policy document hierarchy: Framework → Policies → Standards → Procedures → Work Instructions
- Implement version control for all framework documents (Git-based or document management system)

**Annual review process:**
- Schedule annual framework review triggered by: calendar date, post-incident lessons learned, significant infrastructure changes, or regulatory updates
- Use a maturity model (e.g., CMMI or custom 5-level scale) to track year-over-year improvement across all framework domains
- Document all changes with rationale in a change log

**Internal audit integration:**
- Define an ICT audit universe covering all framework domains
- Plan risk-based ICT audits on a 3-year rotation minimum, with critical areas audited annually
- Use audit management tools to track findings, remediation plans, and closure

### Tools

- **Document Management**: Confluence, SharePoint, Git-based wikis
- **Framework Mapping**: NIST CSF 2.0 reference tool, custom spreadsheet mapping DORA articles → controls → policies
- **Audit Management**: TeamMate+, AuditBoard, Eramba (open-source)
- **Maturity Assessment**: Custom scorecards, COBIT 2019 maturity model

### Candidate Evidence to Collect and Assess

- Complete ICT risk management framework document set with version history
- Annual review records with change log and approval signatures
- Internal audit reports on ICT risk management
- Maturity assessment results with trend analysis
- Mapping document: DORA articles → framework controls → implementing policies

### Priority: CRITICAL

---

## Art. 7 — ICT Systems, Protocols, and Tools

### Working Regulatory Summary — Verify Against Official Text

Financial entities must use and maintain updated ICT systems, protocols, and tools that are appropriate to the scale of operations and adequate to support critical or important functions. These must be reliable, have sufficient capacity, and be technologically resilient. The entity must implement ICT solutions and processes that ensure data integrity, confidentiality, and availability.

### Proposed Technical Implementations — Project Examples

**ICT asset management (RTS 2024/1774 Art. 4–5):**
- Maintain a comprehensive ICT asset inventory including all hardware, software, network devices, cloud resources, and data assets
- Classify each asset by criticality tier (Tier 1: critical/important functions, Tier 2: significant, Tier 3: standard) based on the business functions it supports
- Map dependencies between assets, business processes, and third-party providers
- Track asset lifecycle: procurement → deployment → maintenance → decommissioning
- Monitor end-of-life and end-of-support dates for all software and hardware — flag assets approaching EOL 12 months in advance

**Capacity and performance management (RTS 2024/1774 Art. 9):**
- Implement infrastructure monitoring with alerting on CPU, memory, disk, and network utilisation thresholds (warning at 70%, critical at 85%)
- Conduct annual capacity planning reviews for all Tier 1 systems
- Perform load testing and stress testing before major releases and annually for critical systems
- Implement auto-scaling for cloud-based workloads supporting critical functions

**Technology resilience:**
- Deploy redundant architectures (active-active or active-passive) for all Tier 1 systems
- Implement high availability configurations: database clustering, load balancing, failover mechanisms
- Design for zero single points of failure on critical paths
- Maintain technology currency: define maximum acceptable version lag (e.g., current minus 2 major versions)

### Tools

- **Asset Inventory**: ServiceNow CMDB, Snipe-IT (open-source), Lansweeper, GLPI (open-source)
- **Monitoring**: Zabbix (open-source), Prometheus + Grafana (open-source), Datadog, Nagios
- **Capacity Planning**: Grafana dashboards with historical trending, cloud provider native tools (AWS CloudWatch, Azure Monitor)
- **Load Testing**: Apache JMeter (open-source), k6 (open-source), Gatling

### Candidate Evidence to Collect and Assess

- Complete ICT asset register with classification, owner, criticality tier, and lifecycle status
- Asset dependency maps (visual diagrams showing critical paths)
- Capacity monitoring dashboards and historical reports
- Load test results for critical systems
- EOL/EOS tracking reports with remediation plans for aging assets

### Priority: CRITICAL

---

## Art. 8 — Identification

### Working Regulatory Summary — Verify Against Official Text

Financial entities must identify, classify, and adequately document all ICT-supported business functions, roles, responsibilities, and supporting ICT assets. They must identify all sources of ICT risk, assess cyber threats and ICT vulnerabilities relevant to their ICT-supported business functions, and review risk scenarios and threat assessments at least annually. They must maintain an inventory of information assets and ICT assets — including those at remote sites. For critical or important functions, they must map the ICT systems that support them, including interconnections with ICT third-party providers.

### Proposed Technical Implementations — Project Examples

**Business function mapping:**
- Document every business function with its supporting ICT systems, data flows, and third-party dependencies
- Create Business Impact Analyses (BIA) for each critical or important function — define RTO, RPO, MTPD
- Use visual mapping tools to diagram: Business Function → Application → Database → Infrastructure → Network → Third-Party

**ICT risk assessment (RTS 2024/1774 Art. 3):**
- Conduct formal ICT risk assessments at least annually and upon significant changes
- Use a risk assessment methodology aligned with ISO 27005 or NIST SP 800-30
- Maintain a risk register with: risk ID, description, source, affected assets, inherent risk score (likelihood × impact), control effectiveness, residual risk score, risk owner, treatment plan
- Perform threat modeling for critical applications using STRIDE or MITRE ATT&CK
- Assess risks from concentration in ICT third-party providers

**Vulnerability identification:**
- Run automated vulnerability scans weekly on external-facing assets, monthly on internal assets
- Perform annual penetration tests on critical systems (separate from Art. 25–27 TLPT)
- Subscribe to threat intelligence feeds (MITRE ATT&CK, CISA KEV, sector-specific ISACs)
- Monitor CVE databases and vendor security advisories continuously

**Information asset classification (RTS 2024/1774 Art. 4):**
- Classify information assets by confidentiality (Public, Internal, Confidential, Strictly Confidential), integrity (Low, Medium, High), and availability (Low, Medium, High, Critical)
- Apply data classification labels across storage, transmission, and processing
- Maintain a data flow diagram showing where classified data resides and moves

### Tools

- **Risk Assessment**: Eramba (open-source), SimpleRisk (open-source), RSA Archer, ServiceNow IRM
- **BIA**: Custom templates in Excel/SharePoint, Fusion Framework
- **Vulnerability Scanning**: OpenVAS/Greenbone (open-source), Nessus, Qualys, Rapid7 InsightVM
- **Threat Intelligence**: MISP (open-source), OpenCTI (open-source), Recorded Future, Mandiant
- **Threat Modeling**: Microsoft Threat Modeling Tool (free), OWASP Threat Dragon (open-source)
- **Architecture Diagrams**: draw.io (open-source), Lucidchart, Visio

### Candidate Evidence to Collect and Assess

- Information asset and ICT asset inventories with classification labels
- Business Impact Analysis documents for all critical/important functions
- ICT risk register with risk assessments dated within the last 12 months
- Vulnerability scan reports and remediation tracking
- Threat assessment reports
- Architecture diagrams showing system interconnections and third-party dependencies
- Data flow diagrams with classification labels

### Priority: CRITICAL

---

## Art. 9 — Protection and Prevention

### Working Regulatory Summary — Verify Against Official Text

Financial entities must continuously monitor and control the security and functioning of ICT systems and tools. They must minimise the impact of ICT risk through the deployment of appropriate ICT security tools, policies, and procedures. The entity must design, procure, and implement ICT security policies covering: network security management, safeguards against intrusion and data misuse, data confidentiality and integrity (including cryptographic techniques), accurate and timely logging, and segregation of ICT management functions.

### Proposed Technical Implementations — Project Examples

**Network security management (RTS 2024/1774 Art. 13; information in transit in Art. 14):**
- Implement network segmentation using VLANs and firewalls — separate at minimum: production, development/test, management, DMZ, user segments
- Deploy next-generation firewalls (NGFW) at network boundaries with application-layer inspection
- Implement micro-segmentation for critical application zones (zero-trust architecture)
- Deploy Intrusion Detection/Prevention Systems (IDS/IPS) on all critical network segments
- Implement network access control (NAC) — 802.1X authentication for wired and wireless
- Secure remote access via VPN with MFA or Zero Trust Network Access (ZTNA)
- Disable unnecessary ports and protocols — maintain a documented list of allowed services per zone
- Implement DNS filtering and web proxy for outbound traffic
- Deploy DDoS mitigation for internet-facing services
- Conduct network security assessments at least annually

**Identity and access control (RTS 2024/1774 Arts. 20–21):**
- Implement principle of least privilege across all systems
- Deploy Multi-Factor Authentication (MFA) for: all remote access, all privileged accounts, all access to critical/important function systems, all access from outside the corporate network
- Implement Privileged Access Management (PAM): session recording, just-in-time access, password vaulting
- Review access rights at least annually for all systems, quarterly for critical systems
- Enforce role-based access control (RBAC) with documented role definitions
- Implement automated provisioning and de-provisioning linked to HR systems (joiners/movers/leavers)
- Define and enforce password policies or, preferably, passwordless authentication
- Implement account lockout and monitoring for brute-force attempts
- Maintain segregation of duties (SoD) controls — no single person should have conflicting permissions

**Cryptography and encryption (RTS 2024/1774 Arts. 6–7):**
- Encrypt data in transit: TLS 1.2 minimum (TLS 1.3 preferred) for all internal and external communications
- Encrypt data at rest: AES-256 for databases, file systems, and backups containing confidential or above data
- Implement end-to-end encryption for particularly sensitive data flows (e.g., payment transactions, PII)
- Deploy Hardware Security Modules (HSM) for cryptographic key management of critical keys
- Implement a documented cryptographic key management lifecycle: generation, distribution, storage, rotation, revocation, destruction
- Define key rotation schedules: symmetric keys annually minimum, certificates before expiry with 30-day lead time
- Maintain an inventory of all cryptographic algorithms and key lengths in use — plan migration away from algorithms approaching end-of-life (e.g., RSA-2048 toward post-quantum)
- Monitor for cryptographic misconfigurations (expired certificates, weak ciphers)

**Logging and monitoring (RTS 2024/1774 Art. 12):**
- Centralise all security logs in a SIEM platform
- Minimum log sources: firewalls, IDS/IPS, endpoint detection, authentication systems (AD/LDAP), privileged access management, application logs for critical systems, cloud audit trails, email gateway, DNS
- Define log retention from security objectives, risk assessment, privacy requirements, and applicable law. Twelve months online and five-to-seven-year archival are illustrative proposals requiring justification, not generic statutory minima.
- Implement log integrity controls: tamper-evident logging, write-once storage, or cryptographic log signing
- Configure real-time alerting for: failed authentication patterns, privilege escalation, lateral movement indicators, data exfiltration indicators, malware detection, anomalous network traffic
- Implement a 24/7 monitoring capability (internal SOC or outsourced MDR) for critical systems
- Synchronise time across all systems using NTP with authenticated sources

**Endpoint security:**
- Deploy Endpoint Detection and Response (EDR) on all endpoints — servers, workstations, laptops
- Implement application whitelisting on critical servers
- Enforce host-based firewalls with deny-by-default policies on servers
- Deploy full-disk encryption on all mobile endpoints (laptops, tablets)
- Implement USB and removable media controls
- Maintain anti-malware with automatic signature updates (daily minimum)
- Enforce automatic screen lock after 5 minutes of inactivity

**Email security:**
- Deploy email gateway with anti-phishing, anti-malware, and sandboxing capabilities
- Implement SPF, DKIM, and DMARC for all corporate domains
- Configure URL rewriting and time-of-click analysis
- Implement Data Loss Prevention (DLP) rules for outbound email containing sensitive data

**Secure development lifecycle (RTS 2024/1774 Art. 16):**
- Implement a documented SDLC policy covering: security requirements definition, secure coding standards, code review (peer review and automated SAST), dynamic testing (DAST), dependency scanning (SCA), pre-production security sign-off
- Maintain separate environments: development, testing/QA, staging, production — with no direct code deployment from development to production
- Implement change management process with: change request, impact assessment, approval, testing, rollback plan, post-implementation review
- Scan all code for vulnerabilities before production deployment (SAST/DAST/SCA)
- Maintain a Software Bill of Materials (SBOM) for critical applications

### Tools

- **Firewalls/NGFW**: pfSense (open-source), OPNsense (open-source), Palo Alto, Fortinet, Check Point
- **IDS/IPS**: Snort (open-source), Suricata (open-source), Zeek (open-source)
- **SIEM**: Wazuh (open-source), Elastic SIEM (open-source), Splunk, Microsoft Sentinel, IBM QRadar
- **EDR**: Wazuh (open-source), CrowdStrike Falcon, Microsoft Defender for Endpoint, SentinelOne
- **PAM**: Teleport (open-source), HashiCorp Vault (open-source), CyberArk, BeyondTrust
- **MFA**: Keycloak (open-source), Authelia (open-source), Duo, Okta, Microsoft Entra ID
- **Encryption/Key Management**: HashiCorp Vault (open-source), AWS KMS, Azure Key Vault, Thales Luna HSM
- **Vulnerability Scanning**: OpenVAS/Greenbone (open-source), Nessus, Qualys
- **SAST/DAST/SCA**: SonarQube (open-source), OWASP ZAP (open-source), Semgrep (open-source), Snyk, Checkmarx
- **Email Security**: Proxmox Mail Gateway (open-source), Proofpoint, Mimecast, Microsoft Defender for Office 365
- **DLP**: OpenDLP (open-source), Microsoft Purview DLP, Symantec DLP
- **Network Monitoring**: Zeek (open-source), Wireshark (open-source), ntopng (open-source), Darktrace

### Candidate Evidence to Collect and Assess

- Network architecture diagrams with security zones and firewall rules
- Firewall rule review reports (at least annual, ideally semi-annual)
- IDS/IPS deployment records and alert statistics
- Access control policy and RBAC role definitions
- Access review completion records with timestamps
- MFA deployment coverage report
- PAM session logs and access justification records
- Cryptographic inventory (algorithms, key lengths, certificate expiry dates)
- Key management procedures and rotation records
- SIEM deployment scope, log source inventory, and retention configuration
- Alert triage and escalation records
- EDR deployment coverage report
- Vulnerability scan reports with remediation SLAs and closure rates
- SDLC policy and evidence of security testing (SAST/DAST/SCA reports per release)
- Change management records

### Priority: CRITICAL

---

## Art. 10 — Detection

### Working Regulatory Summary — Verify Against Official Text

Financial entities must have mechanisms in place to promptly detect anomalous activities, ICT network performance issues, and ICT-related incidents. Detection mechanisms must enable multiple layers of control, define alert thresholds and criteria for triggering ICT-related incident detection and response processes, and include automatic alert mechanisms for staff responsible for ICT-related incident response. Financial entities must test the detection mechanisms at regular intervals.

### Proposed Technical Implementations — Project Examples

**Multi-layered detection architecture:**
- **Layer 1 — Network**: Network-based IDS (Snort/Suricata) monitoring east-west and north-south traffic, NetFlow analysis for anomaly detection, DNS query monitoring for DGA/tunneling
- **Layer 2 — Endpoint**: EDR with behavioural analysis detecting fileless malware, living-off-the-land techniques, and lateral movement
- **Layer 3 — Application**: Web Application Firewall (WAF) rules, database activity monitoring (DAM), API gateway anomaly detection
- **Layer 4 — User behaviour**: User and Entity Behaviour Analytics (UEBA) detecting anomalous login patterns, data access patterns, privilege usage
- **Layer 5 — Cloud**: Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP) for cloud environments

**Alert thresholds and correlation:**
- Define alert severity levels: Critical (immediate response, 15 min), High (1 hour), Medium (4 hours), Low (next business day)
- Implement SIEM correlation rules covering at minimum: brute-force attacks, impossible travel, privilege escalation chains, data exfiltration patterns, known IOC matches, mass file encryption (ransomware), configuration tampering
- Tune detection rules to maintain false positive rate below 10% — review and tune monthly
- Implement threat intelligence feed integration for automated IOC matching

**Automated alerting:**
- Configure SIEM to push critical and high alerts to the SOC/incident response team via multiple channels (ticketing system, SMS/pager, email, Slack/Teams)
- Implement escalation procedures: if no acknowledgement within defined SLA, auto-escalate to next tier
- Deploy automated enrichment: when an alert fires, auto-collect context (asset info, user details, recent activity, threat intel match) before human review

**Detection testing:**
- Conduct quarterly purple team exercises: red team executes known TTPs, blue team validates detection coverage
- Run detection rule unit tests: inject synthetic events matching each detection rule and verify alerts fire correctly
- Perform annual detection gap analysis against MITRE ATT&CK matrix — document coverage percentage by tactic and technique
- Test detection of insider threat scenarios at least annually

### Tools

- **SIEM**: Wazuh (open-source), Elastic Security (open-source), Splunk, Microsoft Sentinel
- **UEBA**: Elastic ML (open-source), Microsoft Sentinel UEBA, Exabeam
- **WAF**: ModSecurity (open-source), AWS WAF, Cloudflare WAF, F5 Advanced WAF
- **CSPM**: Prowler (open-source for AWS), ScoutSuite (open-source), Prisma Cloud, Wiz
- **Database Activity Monitoring**: pgAudit (open-source for PostgreSQL), Imperva DAM, IBM Guardium
- **Purple Teaming**: Atomic Red Team (open-source), MITRE Caldera (open-source), Vectr (open-source for tracking)

### Candidate Evidence to Collect and Assess

- SIEM deployment scope and correlation rule inventory
- Detection rule testing records (date, rule tested, result, tuning actions)
- MITRE ATT&CK coverage heatmap with gaps identified and remediation plan
- Purple team exercise reports
- Alert volume and false positive rate trending reports
- Mean Time to Detect (MTTD) metrics
- Escalation procedure documentation and evidence of functioning (sample escalation logs)

### Priority: CRITICAL

---

## Art. 11 — Response and Recovery

### Working Regulatory Summary — Verify Against Official Text

Financial entities must put in place a comprehensive ICT business continuity policy — including arrangements, plans, procedures, and mechanisms aimed at ensuring continuity of critical or important functions, quick and effective response to ICT-related incidents, and activation of containment measures, tailored processes, and dedicated plans for each type of ICT-related incident. They must estimate downtime and data loss impacts, set recovery targets (RTO and RPO), and test their plans.

### Proposed Technical Implementations — Project Examples

**ICT business continuity policy (RTS 2024/1774 Art. 24):**
- Develop and maintain a documented ICT Business Continuity Plan (BCP) covering all critical and important functions
- Define per-function recovery objectives:
  - RTO (Recovery Time Objective): maximum acceptable downtime (e.g., Tier 1: 2 hours, Tier 2: 8 hours, Tier 3: 24 hours)
  - RPO (Recovery Point Objective): maximum acceptable data loss (e.g., Tier 1: 0–15 minutes, Tier 2: 1 hour, Tier 3: 24 hours)
  - MTPD (Maximum Tolerable Period of Disruption): absolute outer limit before business viability is threatened
- Document crisis communication plans: internal escalation chain, regulator notification procedures, customer communication templates, media handling protocols
- Identify and document manual workarounds for critical functions during ICT outages

**ICT response and recovery plans (RTS 2024/1774 Art. 26):**
- Implement disaster recovery architecture:
  - Primary data centre with secondary DR site — geographically separated based on risk analysis; a 100 km distance is an example, not a universal statutory minimum
  - For Tier 1 systems: synchronous or near-synchronous replication to DR site (RPO ≈ 0)
  - For Tier 2 systems: asynchronous replication (RPO per classification)
  - Cloud-based DR (DRaaS) as alternative for entities without secondary physical DC
- Implement automated failover for Tier 1 systems where technically feasible
- Document the Disaster Recovery Plan (DRP) with step-by-step runbooks for each critical system
- Maintain updated network diagrams and system documentation for both primary and DR sites

**Backup strategy (DORA Art. 12; continuity context in RTS 2024/1774 Arts. 24–26):**
- Implement the 3-2-1-1 backup rule: 3 copies of data, on 2 different media types, 1 offsite, 1 immutable/air-gapped
- Immutable backups: use WORM storage (Write Once Read Many) or immutability locks to prevent tampering — critical for ransomware resilience
- Encrypt all backups with AES-256; store encryption keys separately from backup media
- Define backup frequency aligned with RPO: continuous/near-real-time for Tier 1, daily for Tier 2, weekly for Tier 3
- Implement backup monitoring: automated verification that backups complete successfully, with alerting on failures

**Business continuity testing (RTS 2024/1774 Art. 25):**
- Test ICT business continuity plans at least annually
- Test disaster recovery through actual failover to DR site at least annually for Tier 1 systems
- Test backup restoration monthly — select a sample of systems and perform full restore to verify data integrity and measure actual recovery time vs. documented RTO
- Conduct scenario-based exercises: ransomware attack, data centre loss, critical third-party provider failure, widespread network outage
- Document test results, deviations from targets, and corrective action plans

### Tools

- **Backup**: Veeam, Commvault, Bacula (open-source), Restic (open-source), BorgBackup (open-source)
- **Immutable Storage**: AWS S3 Object Lock, Azure Immutable Blob Storage, MinIO (open-source with object locking), dedicated WORM appliances
- **Replication**: VMware SRM, Zerto, database-native replication (PostgreSQL streaming replication, Oracle Data Guard, SQL Server Always On)
- **DR Orchestration**: Zerto, AWS Elastic Disaster Recovery, Azure Site Recovery
- **BCP Management**: Fusion Framework, Castellan, custom templates in SharePoint/Confluence

### Candidate Evidence to Collect and Assess

- ICT Business Continuity Plan documents with RTO/RPO per critical function
- Disaster Recovery Plans with step-by-step runbooks
- Backup policy documenting frequency, retention, encryption, and immutability requirements
- Backup monitoring reports showing success/failure rates
- BCP/DRP test reports with dates, scope, results, deviations, and corrective actions
- Backup restoration test records (system tested, data verified, actual recovery time)
- Crisis communication plan with contact lists and escalation procedures
- Lessons learned documents from tests and actual incidents

### Priority: CRITICAL

---

## Art. 12 — Backup Policies and Procedures, Restoration and Recovery Procedures and Methods

### Working Regulatory Summary — Verify Against Official Text

Financial entities must define backup policies specifying the scope of data subject to backup and the minimum frequency of backup, based on the criticality of the information or the criticality level of the business function. Restoration and recovery procedures must be part of the ICT risk management framework. When restoring from backups, financial entities must use ICT systems that are physically and logically segregated from the source. Backup and restoration must not jeopardise the security of network and information systems.

### Proposed Technical Implementations — Project Examples

**Backup scope and frequency:**
- Document explicit backup scope: databases, application configurations, system state/images, user data, logs, encryption keys, certificates
- Define backup schedule matrix per system tier:
  - Tier 1 (critical): continuous replication + daily full backup + transaction log backup every 15 min
  - Tier 2 (significant): daily incremental + weekly full backup
  - Tier 3 (standard): weekly full backup
- Include cloud workload backups: SaaS data (Microsoft 365, Salesforce), cloud-native database snapshots, infrastructure-as-code state files

**Segregated restoration environment:**
- Maintain an isolated recovery environment (clean room) for forensic-safe restoration — not connected to production network during restoration
- Use this environment to verify backup integrity and scan for malware before restoring to production
- Implement network isolation controls (air-gapped or firewall-enforced) for the clean room

**Backup security:**
- Encrypt all backups in transit and at rest (AES-256)
- Implement access controls on backup systems — restrict to authorised backup operators with MFA
- Audit backup system access logs
- Store backup encryption keys in a separate key management system — not on the backup server itself
- Implement anti-ransomware controls on backup infrastructure: immutable snapshots, separate admin credentials (not joined to domain), network segmentation of backup VLAN

**Retention and disposal:**
- Define retention periods aligned with regulatory requirements and business needs (typically 7 years for banking)
- Implement automated lifecycle management: creation → retention → archival → secure destruction
- Verify secure deletion of expired backups using cryptographic erasure or physical destruction

### Tools

- See Art. 11 backup tools
- **Clean Room**: dedicated virtual or physical environment with network isolation
- **Backup Security**: Veeam SureBackup (automated restore verification), dedicated backup admin accounts with separate PAM

### Candidate Evidence to Collect and Assess

- Backup policy with scope, frequency, retention, and encryption requirements per system tier
- Backup schedule configuration screenshots or exports
- Backup success/failure reports (daily monitoring)
- Restoration test records from segregated environment
- Clean room environment documentation and network isolation evidence
- Backup encryption configuration evidence
- Backup access control lists and audit logs

### Priority: HIGH

---

## Art. 13 — Learning and Evolving

### Working Regulatory Summary — Verify Against Official Text

Financial entities must gather information on vulnerabilities, cyber threats, and ICT-related incidents and analyse their likely impact on digital operational resilience. They must conduct post-incident reviews after ICT-related incidents that disrupt critical or important functions, analysing root causes and identifying required improvements. Lessons learned must be shared across the organisation and fed back into the ICT risk management framework. Financial entities must monitor the effectiveness of the implementation of the digital operational resilience strategy.

### Proposed Technical Implementations — Project Examples

**Post-incident review process:**
- Conduct root cause analysis (RCA) for every major incident and every incident affecting critical/important functions — a one-month internal completion target is a project example, not a universal deadline established by Article 13
- Use structured RCA methodologies: 5-Whys, Ishikawa/Fishbone, or Fault Tree Analysis
- Document for each post-incident review: incident timeline, root cause(s), contributing factors, what worked well, what failed, specific improvement actions with owners and deadlines
- Present post-incident review findings to the ICT Risk Committee and, for major incidents, to the management body
- Track remediation actions to closure in the GRC platform or ticketing system

**Threat intelligence and vulnerability monitoring:**
- Subscribe to sector-specific information sharing (ISACs for financial sector, e.g., FS-ISAC)
- Monitor national CERT/CSIRT advisories relevant to the banking sector
- Integrate threat intelligence feeds into SIEM for automated correlation
- Produce monthly threat landscape reports summarising relevant threats, vulnerabilities, and recommended actions
- Track all relevant CVEs against the ICT asset inventory — prioritise patching based on CVSS score and asset criticality

**Continuous improvement:**
- Maintain a lessons learned register accessible to all ICT and security teams
- Feed post-incident improvements into the annual framework review (Art. 6)
- Track ICT resilience KPIs over time: incident count, MTTD, MTTR, backup success rate, vulnerability remediation SLA compliance, detection coverage (ATT&CK heatmap evolution)
- Benchmark against industry peers where possible (e.g., FS-ISAC benchmarking reports)

### Tools

- **Incident Management**: TheHive (open-source), PagerDuty, ServiceNow ITSM, Jira Service Management
- **RCA**: Miro/Mural for collaborative diagramming, structured templates in Confluence
- **Threat Intelligence**: MISP (open-source), OpenCTI (open-source), FS-ISAC membership, Recorded Future
- **KPI Dashboards**: Grafana (open-source), Power BI, Splunk dashboards

### Candidate Evidence to Collect and Assess

- Post-incident review reports for all major incidents
- Lessons learned register with status tracking
- Remediation action tracking (open/closed, on-time/overdue)
- Monthly/quarterly threat landscape reports
- ICT resilience KPI trend reports
- Evidence of framework updates driven by lessons learned (change log cross-referencing incidents)

### Priority: HIGH

---

## Art. 14 — Communication

### Working Regulatory Summary — Verify Against Official Text

Financial entities must have communication plans in place enabling responsible disclosure of ICT-related incidents or major vulnerabilities to clients, counterparts, and the public where appropriate. They must have internal communication policies ensuring that staff are aware of ICT-related incidents and their roles during incidents. At least one person must be designated to manage communications during ICT-related incidents.

### Proposed Technical Implementations — Project Examples

**Crisis communication framework:**
- Designate a Crisis Communication Officer (typically CISO or Head of Communications) with a defined deputy
- Prepare pre-approved communication templates for different incident types: data breach, service outage, ransomware, third-party failure
- Define stakeholder notification matrix: who gets notified, by whom, via which channel, within what timeframe — covering: management body, regulators, affected clients, counterparties, media, staff
- Establish a dedicated crisis communication channel (e.g., out-of-band communication via mobile phones or a separate messaging platform not dependent on primary ICT infrastructure)

**Internal communication:**
- Implement a security awareness portal where staff can check incident status and their roles
- Configure automated notifications from the incident management platform to relevant stakeholders based on incident severity
- Conduct annual communication drills as part of BCP testing

**External disclosure:**
- Align client notification processes with DORA Art. 19(3): notify clients without undue delay when incidents impact their financial interests
- Align with GDPR Art. 34 obligations where personal data breaches are involved
- Document a vulnerability disclosure policy if the entity accepts external vulnerability reports (coordinated disclosure)

### Tools

- **Crisis Communication**: Everbridge, PagerDuty (alerting), pre-configured distribution lists, dedicated crisis bridge lines
- **Internal Notifications**: ServiceNow, Slack/Teams incident channels, mass notification systems
- **Templates**: Pre-drafted templates stored in secure, accessible location (not dependent on email infrastructure)

### Candidate Evidence to Collect and Assess

- Crisis communication plan document with roles, contacts, and templates
- Stakeholder notification matrix
- Communication drill records and results
- Evidence of designated Crisis Communication Officer appointment
- Sample incident notifications sent during actual incidents or drills
- Vulnerability disclosure policy (if applicable)

### Priority: MEDIUM

---

## Art. 15 — Further Harmonisation of ICT Risk Management Tools, Methods, Processes, and Policies

### Working Regulatory Summary — Verify Against Official Text

This article provides the legal basis for the RTS 2024/1774 — it mandates the ESAs to develop detailed regulatory technical standards that further specify the elements of the full ICT risk management framework under Articles 5–14. The RTS covers: ICT security policies and procedures, ICT asset management, encryption and cryptographic controls, ICT operations security, network security, ICT project and change management, physical and environmental security, access control and authentication, ICT-related incident detection and response, ICT business continuity management, and the simplified framework.

### Proposed Technical Implementations — Project Examples

The specific technical implementations for this article are distributed throughout the other articles above, as the RTS 2024/1774 requirements have been integrated into each article's implementation section. The key RTS articles mapped to DORA articles are:

| RTS 2024/1774 Article | Topic | Related DORA area (interpretive mapping) |
| --- | --- | --- |
| 2–3 | Security policies and ICT risk management | 6, 8–9 |
| 4–5 | ICT asset management | 7–8 |
| 6–7 | Encryption and cryptographic key management | 9 |
| 8 | ICT operations policies and procedures | 7, 9 |
| 9 | Capacity and performance | 7 |
| 10 | Vulnerability and patch management | 8–9 |
| 11 | Data and system security | 9 |
| 12 | Logging | 9–10 |
| 13–14 | Network security and information in transit | 9 |
| 15–17 | Project management; acquisition/development/maintenance; change management | 9 |
| 18 | Physical and environmental security | 9 |
| 19–21 | Human resources; identity; access control | 9 |
| 22–23 | Incident detection and response | 10, 17 |
| 24–26 | Continuity policy, testing, response/recovery plans | 11–12 |
| 27 | ICT risk management framework review report | 6 |
| 28–41 | Simplified-framework provisions; applicability must be checked separately | 16 |

This replaces the original article index, which assigned several topics to incorrect article numbers. Related DORA areas are explanatory links rather than a legal equivalence table.

### Priority: N/A (meta-article — implemented via all other articles)

---

## Art. 16 — Simplified ICT Risk Management Framework

### Working Regulatory Summary — Verify Against Official Text

Article 16 applies to the specific entity categories listed in Article 16(1). It is not a general option available to every microenterprise or small bank. Establish legal eligibility before selecting simplified controls, and review the detailed simplified-framework provisions in RTS 2024/1774. The controls below are project examples for an eligible entity, not an eligibility determination.

### Proposed Technical Implementations — Project Examples

**Candidate controls for an eligible Article 16 entity:**
- Simplified but documented ICT risk assessment — can be a streamlined questionnaire-based assessment rather than full quantitative analysis
- Basic security controls: endpoint protection (EDR/anti-malware), MFA on critical systems, regular backups with offsite copy, firewall on network perimeter
- Simplified incident detection: managed security service provider (MSSP) or cloud-native security tools rather than full SIEM deployment
- Basic business continuity: documented manual procedures for critical functions, cloud-based backup and recovery
- Annual review of ICT risk posture

**Design considerations — verify each against the applicable provisions:**
- No requirement for dedicated ICT risk management function (can be assigned to existing role)
- Simplified documentation requirements (fewer formal policies, more practical procedures)
- Testing can be less formal but must still occur at regular intervals
- No mandatory TLPT (threat-led penetration testing)

### Tools

- **Endpoint Security**: Microsoft Defender for Business, Bitdefender GravityZone Small Business
- **Backup**: Cloud-native (Microsoft 365 backup, Google Workspace backup), Backblaze
- **MFA**: Microsoft Authenticator, Google Authenticator, Duo Free Tier
- **Managed Security**: MSSP/MDR services (Arctic Wolf, Huntress for SMB)
- **Risk Assessment**: Simple spreadsheet-based risk register

### Candidate Evidence to Collect and Assess

- Simplified ICT risk assessment document
- Evidence of basic security controls in place (EDR deployment, MFA configuration, backup reports)
- Simplified business continuity procedures
- Annual review records

### Priority: MEDIUM (project judgement; Article 16 eligibility must be established)

---

## Cross-Reference: DORA Pillar 1 ↔ ISO 27001:2022 ↔ NIST CSF 2.0

| DORA Article | ISO 27001:2022 Controls | NIST CSF 2.0 |
|---|---|---|
| Art. 5 Governance | A.5.1–5.4 (Policies, Roles) | GV.OC, GV.RM, GV.RR |
| Art. 6 Framework | A.5.1 (Policies for InfoSec) | GV.RM |
| Art. 7 ICT Systems | A.5.9 (Asset Inventory), A.8.6 (Capacity) | ID.AM |
| Art. 8 Identification | A.5.9–5.13 (Asset Mgmt, Risk), A.8.8 (Vuln Mgmt) | ID.AM, ID.RA |
| Art. 9 Protection | A.5.15–5.18 (Access), A.8.1–8.34 (Tech Controls) | PR.AA, PR.DS, PR.PS |
| Art. 10 Detection | A.8.15–8.16 (Logging, Monitoring) | DE.CM, DE.AE |
| Art. 11 Response/Recovery | A.5.29–5.30 (BCP), A.8.13–8.14 (Backup, Redundancy) | RS.MA, RC.RP |
| Art. 12 Backup | A.8.13 (Backup) | PR.DS, RC.RP |
| Art. 13 Learning | A.5.27 (Lessons Learned), A.5.7 (Threat Intel) | ID.IM |
| Art. 14 Communication | A.5.31 (Legal Requirements), A.5.5 (Contact with Authorities) | RS.CO, RC.CO |

---

## Patch Management SLAs — Illustrative Internal Policy Targets

Illustrative internal targets related to vulnerability and patch management under RTS 2024/1774 Art. 10. These numerical SLAs are project proposals, not deadlines prescribed by that article. Approve targets based on exposure, exploitability, business impact, change safety, and compensating controls:

| CVSS Score | Severity | SLA for Tier 1 (Critical) Systems | SLA for Tier 2 Systems | SLA for Tier 3 Systems |
|---|---|---|---|---|
| 9.0–10.0 | Critical | 24–48 hours | 72 hours | 7 days |
| 7.0–8.9 | High | 7 days | 14 days | 30 days |
| 4.0–6.9 | Medium | 30 days | 60 days | 90 days |
| 0.1–3.9 | Low | 90 days | 90 days | Next maintenance window |

Emergency patches (actively exploited zero-days or CISA KEV entries): immediate assessment, emergency change process, 24-hour deployment target for all tiers.

---

## Document Metadata

- **Version**: 1.0 — revised documentation; evaluation pending
- **Knowledge base**: DORA Technical Implementation Advisor
- **Pillar**: 1 of 5 — ICT Risk Management
- **DORA Articles covered**: 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16
- **RTS covered**: Commission Delegated Regulation (EU) 2024/1774
- **Target entity type**: Credit institution (bank)
- **Proportionality tier**: Full framework (not simplified)
- **Original content date**: July 2026
- **Editorial revision date**: 30 October 2026
