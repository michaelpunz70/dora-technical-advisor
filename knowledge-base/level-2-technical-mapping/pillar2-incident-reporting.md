# DORA Pillar 2 — ICT-Related Incident Management, Classification, and Reporting

## Interpretation and assurance status

**Editorial revision: 30 October 2026. Human legal/control review remains open.** This document is an author-created working mapping, not an authoritative statement or evidence of implemented controls. Regulatory summaries must be checked against the current official text and entity-specific applicability. This revision corrects selected identified issues; it is not a paragraph-by-paragraph legal assurance opinion.

**Reading rules:** technical designs, products, numeric thresholds, internal SLAs, review cadences, staffing choices, and maturity targets in implementation sections are project examples unless an exact source provision expressly supports them. They are not universal regulatory minima. Priority labels are project judgements. Evidence lists are requests for material to collect, not assertions that it exists or is sufficient. ISO/NIST cross-references are interpretive and require edition-specific review.

For each adopted control, record: provision and applicability rationale; control objective and design; accountable owner; evidence artifact, period, and location; design and operating-effectiveness checks; result, gap, remediation owner, and due date. Use [the mapping review procedure](../../docs/mapping-review.md) before relying on this material.

## Regulatory Scope

- **DORA Articles**: 17–23 (Chapter III)
- **Key RTS/ITS**:
  - Commission Delegated Regulation (EU) 2024/1772 — criteria for classification of ICT-related incidents and cyber threats, materiality thresholds
  - Commission Delegated Regulation (EU) 2025/301 — content of incident reports, time limits for reporting
  - Commission Implementing Regulation (EU) 2025/302 — standard forms, templates, and procedures for reporting
- **Applicability**: All financial entities (simplified reporting for microenterprises under Art. 15–16)
- **Dates**: DORA applies from 17 January 2025; verify each supporting instrument’s own entry-into-force and application provisions.

---

## Art. 17 — ICT-Related Incident Management Process

### Working Regulatory Summary — Verify Against Official Text

Financial entities must define, establish, and implement an ICT-related incident management process to detect, manage, and notify ICT-related incidents. They must record all ICT-related incidents and significant cyber threats. They must establish appropriate procedures and processes to ensure consistent and integrated monitoring, handling, and follow-up of ICT-related incidents, ensuring that root causes are identified, documented, and addressed to prevent recurrence.

The incident management process must:
- Put in place early warning indicators
- Establish procedures to identify, track, log, categorise, and classify incidents according to priority and severity and the criticality of the services impacted
- Assign roles and responsibilities for different incident types and scenarios
- Set out plans for communication to staff, external stakeholders, and media, as well as for client notification and escalation to senior management
- Ensure reporting of at least major ICT-related incidents to relevant senior management and the management body, explaining the impact, response, and additional controls to be established

### Proposed Technical Implementations — Project Examples

**Incident management process framework:**
- Document a formal Incident Response Plan (IRP) covering the full lifecycle: Preparation → Detection → Analysis → Containment → Eradication → Recovery → Post-Incident Review
- Align with established frameworks: NIST SP 800-61 (Computer Security Incident Handling Guide) or ISO 27035 (Incident Management)
- Define incident categories: security incidents, availability incidents, integrity incidents, confidentiality incidents, third-party incidents, payment-related incidents (for credit institutions under PSD2)
- Establish a formal triage process with defined severity levels mapped to response SLAs

**Early warning indicators:**
- Deploy SIEM correlation rules tuned for precursor activity: scanning, reconnaissance, credential stuffing, anomalous data transfers, configuration drift on critical systems
- Integrate threat intelligence feeds for proactive IOC matching
- Monitor dark web and underground forums for mentions of the entity (credential dumps, planned attacks, data for sale)
- Track anomaly baselines for critical KPIs: transaction volumes, authentication failure rates, network traffic patterns — alert when deviations exceed 2+ standard deviations

**Incident logging and tracking:**
- Deploy a dedicated incident management platform — all incidents must have a unique ID, timestamp, severity, category, status, owner, and timeline of actions
- Automate ticket creation from SIEM alerts for qualifying events
- Maintain a single source of truth: every incident, whether detected internally or reported by a third party, enters the same tracking system
- Implement real-time dashboards showing: open incidents by severity, MTTD, MTTR, incidents by category, trend over time
- Define and justify incident-record retention against applicable law, supervisory instructions, privacy requirements, and internal policy; five years is a project example, not a universal DORA minimum established here.

**Roles and responsibilities:**
- Define an Incident Response Team (IRT) with clear roles: Incident Commander, Technical Lead, Communications Lead, Legal/Compliance Lead, Third-Party Liaison
- Establish an on-call rotation for 24/7 incident response capability (critical for banks)
- Define escalation matrix: L1 (SOC analyst) → L2 (Senior analyst) → L3 (Incident Commander) → CISO → Management Body
- Identify and maintain contact lists for: national competent authority (NCA), national CSIRT, law enforcement, legal counsel, external forensics provider, crisis communication agency

**Incident playbooks:**
- Develop specific playbooks for the most likely and most impactful incident types:
  - **Ransomware**: isolation procedures, backup verification, negotiation policy (do not pay without board/legal approval), law enforcement notification, forensic preservation
  - **Data breach / data exfiltration**: scope assessment, GDPR 72-hour notification assessment, client notification triggers, containment of data flow
  - **DDoS attack**: traffic analysis, CDN/WAF activation, ISP coordination, failover to backup services
  - **Third-party/supply chain compromise**: vendor notification, contract review, service isolation, alternative provider activation
  - **Insider threat**: evidence preservation (do not alert the subject), HR and legal coordination, access revocation sequence
  - **Payment fraud / unauthorised transactions**: transaction reversal procedures, card scheme notification, PSD2 reporting
  - **Phishing / business email compromise**: account containment, credential reset scope, mail rule review, impacted communication identification
- Each playbook must include: trigger criteria, step-by-step actions, decision points, escalation triggers, evidence collection checklist, communication templates, DORA reporting assessment

### Tools

- **Incident Management Platforms**: TheHive (open-source), DFIR-IRIS (open-source), ServiceNow Security Incident Response, PagerDuty, Jira Service Management
- **SOAR (Security Orchestration, Automation, Response)**: Shuffle (open-source), Cortex XSOAR, Splunk SOAR, IBM QRadar SOAR
- **Forensic Tools**: Velociraptor (open-source), GRR Rapid Response (open-source), EnCase, FTK
- **Evidence Collection**: Velociraptor (open-source), CyLR (open-source), KAPE
- **Playbook Management**: Playbooks stored in Confluence/Wiki with version control, or integrated into SOAR platform

### Candidate Evidence to Collect and Assess

- Documented Incident Response Plan with annual review date
- Incident playbooks for each major scenario
- IRT membership list with roles, contact details, and on-call schedule
- Incident register/log with complete records for all incidents
- MTTD and MTTR metrics trending reports
- Escalation matrix with evidence of functioning (sample escalation records)
- Annual IRP exercise/drill records

### Priority: CRITICAL

---

## Art. 18 — Classification of ICT-Related Incidents and Cyber Threats

### Working Regulatory Summary — Verify Against Official Text

Financial entities must classify ICT-related incidents and determine their impact based on criteria defined in the RTS 2024/1772. An incident is classified as "major" when it meets specific materiality thresholds. Financial entities must also classify cyber threats as "significant" based on criteria including the criticality of the services at risk, the number of clients potentially affected, and the geographical spread.

### RTS 2024/1772 — Classification Criteria

Use Articles 1–9 together. Article 8 combines the critical-services condition with the applicable Article 9 materiality tests; a confidentiality event alone is not an automatic universal major-incident trigger. In particular, Article 9(5)(b) concerns successful malicious unauthorised access that may result in data losses, not every confidentiality breach.

| Criterion family | Review required |
| --- | --- |
| Clients, financial counterparts, transactions | Assess affected-service denominators, relevant clients/counterparts, counts and transaction values under Articles 1 and 9(1). |
| Reputation | Apply the conditions in Articles 2 and 9(2); do not use a generic media score. |
| Duration and downtime | Distinguish incident duration over 24 hours from downtime over two hours for ICT services supporting CIFs; apply Articles 3 and 9(3). |
| Geographical spread | Assess impact in two or more Member States under Articles 4 and 9(4). |
| Data losses | Assess availability, authenticity, integrity and confidentiality and the distinct conditions in Articles 5 and 9(5). |
| Critical services | Apply Article 6, not only an informal asset tier. |
| Economic impact | Apply Articles 7 and 9(6), including the EUR 100,000 threshold and prescribed cost treatment. |

Check the complete Article 8 logic, aggregation of recurring incidents where applicable, and current source wording before automating any classification decision. The table is an index, not a sufficient executable specification.

### Proposed Technical Implementations — Project Examples

**Automated classification engine:**
- Build or configure an automated incident classification workflow in the incident management platform that evaluates each incident against all seven RTS criteria in real-time
- Pre-populate entity-specific thresholds: total client count, critical service list, Member State presence, economic impact thresholds
- Implement a reviewed decision table reproducing RTS 2024/1772 Arts. 8–9, including the critical-services condition, the two materiality paths, relevant exclusions, and recurring-incident assessment. Retain the classification inputs and reviewer decision.
- Generate an automatic preliminary classification within 30 minutes of incident detection to support the 4-hour initial notification deadline
- Allow for reclassification: an initially minor incident can be upgraded to major if its impact grows — monitor open incidents continuously against thresholds

**Critical service identification:**
- Maintain an up-to-date register of all critical or important functions (CIFs) as defined under DORA Art. 3(22) — linked to the ICT asset register from Pillar 1
- Map each CIF to its supporting ICT systems, so that when an ICT system is impacted, the classification engine can immediately determine if a CIF is affected
- Review and update the CIF register at least annually or upon significant business changes

**Client impact assessment:**
- Integrate incident management with client-facing service monitoring: when a service goes down, automatically calculate the number of affected clients based on service usage data
- Count ALL clients who cannot access the service, not just those who attempted to connect during the incident — this is an explicit requirement of RTS 2024/1772
- For banking: integrate with core banking system client counts, online banking active user metrics, and payment processing volumes

**Duration tracking:**
- Implement automated service availability monitoring with precise timestamping
- Duration measurement starts when the service becomes unavailable — not when the incident is detected or when remediation begins
- Track both full outage and degraded service separately
- If the incident causes delayed processing even after service restoration, the duration extends to when the delay is cleared

**Economic impact estimation:**
- Define a methodology to estimate financial impact in real-time, including:
  - Direct costs: emergency IT expenses, external consultant fees, forensic investigation
  - Revenue impact: transaction fees not collected, interest not generated during outage, failed trades
  - Fraud losses: unauthorised transactions directly related to the incident
  - Regulatory costs: potential fines, mandatory notifications, reporting overhead
- Exclude from DORA calculation: reputational damage estimates, stock price impact, future customer attrition
- Implement a rapid impact estimation template that the Incident Commander can populate within the first 2 hours

**Significant cyber threat classification:**
- Monitor incoming threat intelligence for threats that could materially affect the entity even if not yet realised
- Classification criteria for significant cyber threats: the threat targets critical services, could affect multiple clients or geographical areas, and the threat actor has demonstrated capability
- Voluntary reporting to the NCA is strongly encouraged even though not mandatory — the regulator recommends it

### Tools

- **Classification Automation**: SOAR playbook with decision tree logic, custom scripts integrated into TheHive/DFIR-IRIS, ServiceNow automated classification workflows
- **Service Monitoring**: Uptime Kuma (open-source), Pingdom, Datadog, StatusCake — feed availability data into classification engine
- **Client Impact Dashboards**: Custom dashboards pulling from core banking/CRM systems, integrated with incident platform
- **Threat Intelligence for Significant Cyber Threats**: MISP (open-source), OpenCTI (open-source), FS-ISAC alerts, national CERT advisories

### Candidate Evidence to Collect and Assess

- Documented classification methodology aligned with RTS 2024/1772 criteria
- Entity-specific materiality thresholds (documented and approved)
- Classification decision records for each incident (which criteria evaluated, which thresholds met, classification result)
- Register of critical or important functions with ICT system mapping
- Evidence of reclassification reviews for evolving incidents
- Significant cyber threat register with classification rationale

### Priority: CRITICAL

---

## Art. 19 — Reporting of Major ICT-Related Incidents and Voluntary Notification of Significant Cyber Threats

### Working Regulatory Summary — Verify Against Official Text

Financial entities must report major ICT-related incidents to the relevant competent authority (NCA). The reporting follows a three-stage process with strict deadlines:

1. **Initial notification**: as early as possible within the applicable limits in RTS 2025/301 Art. 5(1)(a), using awareness and classification timestamps. Article 5(2) addresses classification later than 24 hours after awareness; do not treat the awareness limit as unconditional regardless of later classification.
2. **Intermediate report**: within 72 hours of the initial notification — detailed impact assessment, root cause (if known), and measures taken
3. **Final report**: no later than one month after the intermediate report or, where applicable, the latest updated intermediate report — confirmed root cause analysis, complete impact figures, remediation actions taken and planned, lessons learned

Financial entities must also notify affected clients without undue delay when the incident impacts their financial interests — describing the measures taken to mitigate the adverse effects. This client notification obligation is one of DORA's most operationally demanding requirements.

Financial entities may voluntarily report significant cyber threats to the NCA when they consider the threat relevant to the financial system, service users, or clients.

Determine the competent authority, submission channel, and onward-sharing arrangements for the entity; do not infer a duplicate direct ECB submission from SSM status alone.

### Proposed Technical Implementations — Project Examples

**Reporting workflow automation — implement the actual clocks:**
- Record awareness, detection, classification, initial submission, intermediate submissions, and recovery as separate timestamps.
- Calculate the initial deadline using RTS 2025/301 Art. 5(1)(a) and the later-classification case in Art. 5(2).
- Calculate the intermediate deadline from submission of the initial notification, not from classification. Track required updates and recovery-triggered updates.
- Calculate the final deadline from the relevant intermediate report, including the latest updated intermediate report where applicable.
- Implement delay escalation and check the scope of any weekend/bank-holiday rule. A credit institution must not assume it can use an extension available to other entity categories.
- Keep human approval, submission receipts, and a record of the rule version used by the deadline calculator.
- Use the required ITS 2025/302 templates and the reporting channel currently specified for the entity.

**Initial notification content (subject to the applicable Article 5 clock):**
- Entity identification (LEI, name, NCA reference number)
- Incident unique identifier
- Date and time of detection
- Date and time of classification as major
- Brief description of the incident
- Classification criteria met (which of the 7 thresholds triggered)
- Whether the incident is ongoing or resolved
- Whether other financial entities, third-party providers, or financial market infrastructures are affected
- Whether a crisis management plan has been activated
- Preliminary impact assessment

**Intermediate report content (within 72 hours):**
- Updated and more detailed description of the incident
- Incident timeline: detection → classification → containment → resolution (or ongoing status)
- Confirmed classification criteria with quantified impact:
  - Number of clients affected (exact or best estimate)
  - Duration of service disruption (hours and minutes)
  - Geographical scope (Member States affected)
  - Data compromised (type, volume, classification level)
  - Estimated economic impact (direct costs, revenue losses)
- Services and business functions affected
- Root cause analysis (preliminary if not yet confirmed)
- ICT systems and infrastructure involved
- Third-party providers involved (if applicable)
- Containment and mitigation measures taken
- Communication actions taken (client notifications, media, regulators)
- Whether the incident has been reported to other authorities (GDPR supervisory authority, law enforcement)

**Final report content (within 1 month):**
- Confirmed root cause analysis (technical root cause and contributing factors)
- Complete and verified impact figures (clients, duration, financial impact, data loss)
- Comprehensive timeline of the incident from detection to full resolution
- Effectiveness assessment of the response (what worked, what failed)
- Remediation actions completed and planned (with timelines and owners)
- Lessons learned and improvements to the ICT risk management framework
- Changes to policies, procedures, or controls resulting from the incident
- Assessment of whether the incident type could recur and the mitigations in place
- Updated classification if the impact assessment has changed

**Client notification process:**
- Define triggers for client notification: any major incident that impacts client financial interests (service unavailability affecting transactions, data breach involving client PII or financial data, fraud events)
- Pre-draft client notification templates for common incident types (in national language and English for cross-border clients)
- Notification must include: nature of the incident, measures the entity has taken to mitigate adverse effects, recommended actions the client should take (e.g., change credentials, monitor accounts)
- Channels: direct communication preferred (email, secure message in banking app, SMS) — avoid sole reliance on website banner
- Document all client notifications sent (timestamp, content, recipient count, channel used)
- Align with GDPR Art. 34 when personal data breach triggers notification to data subjects

**Multi-authority coordination:**
- If personal data is affected: conduct a separate GDPR Article 33/34 trigger, risk, clock, and recipient assessment; obtain the relevant source and qualified review rather than assuming every breach has identical notification duties.
- If the incident involves suspected criminal activity → notify law enforcement
- For cross-border incidents: check authority-sharing arrangements under DORA and current instructions; RTS 2024/1772 should not be used as an unsupported citation for the forwarding route.
- For SSM significant credit institutions: verify the currently applicable reporting route and authority coordination instructions.
- For payment services: check current sector-specific reporting rules and DORA interactions; do not assume historical PSD2 reporting remains an additional duplicate submission.

**ECB reporting for significant institutions:**
- Verify the designated recipient, submission route, and onward-sharing process for the institution; archive the authority instructions used.
- Coordinate with the ECB's SSM cyber incident reporting mechanism
- Ensure reporting templates are compatible with ECB requirements

### Tools

- **Reporting Templates**: Pre-configured ITS 2025/302 templates in the incident management platform, or standalone secure forms hosted on internal systems
- **NCA Submission Portals**: Each national NCA maintains a submission portal (e.g., BaFin MVP portal for Germany, ACPR for France, Banca d'Italia) — integrate via API where available, or manual submission via secure portal
- **Timer and Workflow Management**: SOAR platform with automated deadline tracking, or incident management platform with SLA timers (TheHive, ServiceNow)
- **Client Notification**: Mass notification systems (Everbridge, SendGrid for email at scale), secure messaging via banking app push notifications
- **Regulatory Tracking**: GRC platform to track all regulatory submissions, deadlines, and follow-ups

### Candidate Evidence to Collect and Assess

- All incident reports submitted to the NCA (initial, intermediate, final) with timestamps proving compliance with deadlines
- Internal workflow records showing the classification-to-submission timeline
- Client notification records (content, recipients, timestamp, channel)
- Evidence of multi-authority coordination where applicable (GDPR notification, law enforcement referral)
- Incident register showing which incidents were classified as major and the reporting status
- Records of voluntary significant cyber threat notifications

### Priority: CRITICAL

---

## Art. 20 — Harmonisation of Reporting Content and Templates

### Working Regulatory Summary — Verify Against Official Text

This article provides the legal basis for the ESAs to develop RTS on the content of incident reports (RTS 2025/301) and ITS on the standard forms, templates, and procedures (ITS 2025/302). The reporting framework must be proportionate and consistent with the approach for incident reporting under NIS2 Directive (EU) 2022/2555.

### Proposed Technical Implementations — Project Examples

**ITS 2025/302 template compliance:**
- Implement the current ITS forms and the format required by the receiving authority; do not assume a universal XBRL/XML submission format
- Validate all fields before submission — the template includes mandatory and conditional fields with validation rules
- Key mandatory fields in the template:
  - Entity identification section: LEI code, entity name, entity type, NCA of reference
  - Incident identification: unique incident ID (generated by the entity), report type (initial/intermediate/final), report version
  - Incident timeline: detection date-time, classification date-time, resolution date-time (if applicable)
  - Classification section: assessment of each of the 7 criteria with quantified values
  - Description section: free-text description with structured sub-fields for affected services, root cause category, threat type
  - Impact section: quantified impact across all materiality criteria
  - Response section: containment and mitigation actions, recovery actions, planned remediation
  - Cross-references: related incidents, related significant cyber threats, GDPR notifications, other authority reports

**Reporting process automation:**
- Build a data pipeline from the incident management platform to the reporting template:
  - Incident platform auto-populates entity data, incident ID, timeline fields, and classification results
  - Analyst completes qualitative descriptions and assessments
  - Pre-submission validation checks against ITS field requirements
  - Submission via NCA portal (API integration or manual upload)
  - Receipt confirmation tracking and archival of submitted reports
- Implement version control for reports: if the intermediate or final report updates previously submitted data, track the delta

**Consistency with NIS2 reporting:**
- Assess DORA’s sector-specific relationship with NIS2 and any national CSIRT routing requirements; do not presume an additional duplicate NIS2 report from an entity label alone
- Under DORA Art. 19(1) second subparagraph, Member States may require financial entities to also submit incident reports to CSIRTs designated under NIS2 — check national transposition requirements
- Avoid duplicate reporting where possible by using the DORA report as the primary submission and coordinating with NCA on NIS2 channel

### Tools

- **XBRL/XML Template Tools**: Eurofiling XBRL tools, Arelle (open-source XBRL processor), or NCA-provided submission applications
- **Reporting Automation**: Custom middleware connecting incident platform API → template population → NCA portal submission
- **Validation**: NCA-provided validation rules or custom validation scripts

### Candidate Evidence to Collect and Assess

- Completed report templates for all reported incidents (archived copies with submission timestamps)
- Validation reports showing all mandatory fields were completed before submission
- NCA submission receipts/acknowledgements
- Version history of updated reports (intermediate and final report deltas)

### Priority: HIGH

---

## Art. 21 — Centralisation of Reporting of Major ICT-Related Incidents

### Working Regulatory Summary — Verify Against Official Text

The ESAs must prepare a joint report assessing the feasibility of further centralising incident reporting through a single EU Hub. This article establishes the mandate for the ESAs to explore whether a single EU-level reporting hub could reduce the reporting burden while maintaining supervisory effectiveness. The current operational reporting route must be verified against the applicable competent-authority instructions; this document does not establish the present status of a future EU hub.

### Proposed Technical Implementations — Project Examples

**Reporting route — verify current authority instructions:**
- Identify the correct NCA for the entity type and Member State of authorisation
- For SSM credit institutions: confirm the current reporting route and onward-sharing process for the institution.
- Maintain an up-to-date contact register for each relevant NCA reporting channel
- Monitor ESA communications for any updates on the EU Hub project timeline

**Preparing for potential centralisation:**
- Design the internal reporting workflow to be NCA-agnostic where possible — decouple the report generation from the submission channel
- Implement API-based submission capability that can be redirected to a future EU Hub without redesigning the entire workflow
- Standardise internal incident data to the ITS 2025/302 schema regardless of the current NCA submission format

### Candidate Evidence to Collect and Assess

- Documentation of NCA reporting channel and contacts
- Internal workflow documentation showing adaptability to future centralised reporting

### Priority: LOW (monitoring only — no current entity obligation beyond NCA reporting)

---

## Art. 22 — Supervisory Feedback

### Working Regulatory Summary — Verify Against Official Text

Upon receipt of the initial notification and subsequent reports, the competent authority must acknowledge receipt and may provide relevant and proportionate feedback to the financial entity, including anonymised threat intelligence, information on similar threats across the sector, and guidance on remedies. This feedback does not relieve the financial entity of its responsibility for handling the incident and its consequences.

### Proposed Technical Implementations — Project Examples

**Feedback integration process:**
- Establish a process to receive, review, and act upon supervisory feedback:
  - Designate a regulatory liaison officer (typically in Compliance or CISO office) as the single point of contact for NCA feedback
  - Log all supervisory feedback received in the GRC platform with tracking for follow-up actions
  - Distribute anonymised threat intelligence received from NCA to relevant security teams (SOC, threat intelligence, IT operations)
  - Incorporate NCA recommendations into incident response actions and remediation plans
  - If the NCA shares information about similar threats affecting the sector, update internal threat assessments and detection rules accordingly

**Supervisory communication protocols:**
- Maintain secure communication channels with the NCA (encrypted email, dedicated portal, secure file exchange)
- Respond to NCA information requests within requested timeframes
- Keep records of all supervisory interactions related to incident reporting

### Tools

- **Regulatory Liaison Management**: GRC platform with regulatory interaction tracking, dedicated mailbox for NCA communications
- **Threat Intelligence Distribution**: MISP (open-source) for distributing NCA-shared IOCs to internal detection systems

### Candidate Evidence to Collect and Assess

- Log of all supervisory feedback received with response actions
- Records of anonymised threat intelligence distributed internally
- Evidence of NCA recommendations incorporated into remediation plans

### Priority: MEDIUM

---

## Art. 23 — Operational or Security Payment-Related Incidents Concerning Credit Institutions, Payment Institutions, Account Information Service Providers, and Electronic Money Institutions

### Working Regulatory Summary — Verify Against Official Text

This article provides specific provisions for payment-related incidents for entities subject to PSD2. Credit institutions, payment institutions, and e-money institutions must apply the DORA incident management framework (Art. 17–20) to operational or security payment-related incidents, replacing the PSD2 incident reporting requirements. This ensures a single reporting framework for all ICT-related incidents, including payment-specific ones.

Payment-related incidents are defined as incidents that have an adverse impact on the availability, authenticity, integrity, or confidentiality of payment-related data, or on the payment-related services provided by the financial entity.

### Proposed Technical Implementations — Project Examples

**Unified reporting framework for payment incidents:**
- Merge the previously separate PSD2 incident reporting process into the DORA reporting framework — there should be ONE incident management process covering both
- Map the old PSD2 incident classification criteria to the DORA RTS 2024/1772 criteria — in practice, DORA criteria supersede PSD2 criteria
- Ensure payment-specific incidents are captured with appropriate categorisation:
  - Payment transaction failures (card processing, SEPA transfers, SWIFT messages)
  - Online banking / mobile banking outages
  - ATM network disruptions
  - Authentication system failures (3D Secure, SCA)
  - Payment fraud events (card cloning, unauthorised transactions, account takeover)
  - Instant payment system failures

**Payment-specific detection and monitoring:**
- Monitor transaction processing rates in real-time — alert on deviations (drop in successful transactions, increase in timeouts, increase in error rates)
- Implement fraud detection systems with real-time transaction monitoring (rule-based + ML-based anomaly detection)
- Monitor card scheme networks (Visa/Mastercard) for disruption alerts
- Monitor SWIFT network connectivity and message processing
- Track SCA (Strong Customer Authentication) success/failure rates

**Payment-specific client notification:**
- For payment outages: notify affected clients through banking app push notifications and website status page
- For fraud events: immediate direct notification to affected account holders through secure channel
- For SCA disruptions: provide alternative authentication paths or manual transaction processing
- Track regulatory obligations: PSD2 Art. 96 notification is now subsumed by DORA, but confirm with NCA whether any transitional national requirements remain

**Integration with payment schemes:**
- Maintain notification channels with card schemes (Visa, Mastercard, domestic schemes) for fraud and security incidents
- Coordinate with national payment system operators (e.g., TARGET2 for Eurozone) for systemic payment incidents
- Participate in sector-wide incident coordination if the incident affects the broader payment ecosystem

### Tools

- **Transaction Monitoring**: Real-time dashboards (Grafana, Kibana) connected to payment processing logs, ACI Worldwide, FIS
- **Fraud Detection**: FICO Falcon, SAS Fraud Management, Featurespace, or custom ML models on transaction data
- **Payment Network Monitoring**: SWIFT Alliance monitoring, card scheme operational dashboards
- **Client Communication**: Banking app push notification infrastructure, automated SMS gateway, status page (StatusPage, Uptime Kuma)

### Candidate Evidence to Collect and Assess

- Unified incident management process document covering both ICT and payment-related incidents
- Mapping document: former PSD2 classification → DORA RTS 2024/1772 classification
- Transaction monitoring dashboards and alerting configuration
- Fraud detection system configuration and tuning records
- Payment-related incident records with DORA classification
- Client notification records for payment incidents
- Coordination records with card schemes, SWIFT, national payment systems

### Priority: CRITICAL (for credit institutions, payment institutions, and e-money institutions)

---

## Incident Reporting Quick Reference — Clocks and Decisions

| Stage | Review rule |
| --- | --- |
| Awareness and detection | Record separately where they differ; preserve the facts supporting each timestamp. |
| Classification | Apply the reviewed RTS 2024/1772 Arts. 8–9 decision table and relevant recurring-incident rules. Do not classify solely by an informal asset tier or a confidentiality label. |
| Initial notification | Use RTS 2025/301 Art. 5(1)(a): as early as possible, within four hours of major classification and no later than 24 hours after awareness; apply the later-classification rule in Art. 5(2). |
| Intermediate report | Deadline runs from submission of the initial notification; account for updates, including recovery-related updates. |
| Final report | Deadline runs from the relevant intermediate report or latest updated intermediate report where applicable. |
| Exceptions and delay | Check the full Article 5 rules and entity-specific scope. Credit institutions must not assume a weekend/bank-holiday extension. |
| Client communication | Assess the Article 19 conditions, including impact on clients’ financial interests; distinguish this from authority reporting. |

### Classification automation boundary

Before implementing a decision engine, verify every threshold, denominator, aggregation rule, service-criticality condition, and exception against RTS 2024/1772. Test boundary and recurring-incident cases. This documentation is not an executable legal specification. Retain analyst review and reclassification capability.

### Parallel obligations — assess triggers separately

| Regime or recipient | Review required |
| --- | --- |
| DORA competent authority | Major-incident classification, reporting clocks, templates, and current submission route. An outage or ransomware label alone does not determine the reporting outcome. |
| Data protection authority / individuals | Separate GDPR Articles 33–34 analysis, including awareness, risk/high-risk conditions, exceptions, and applicable communications; a breach need not involve exfiltration to be relevant. |
| ECB / other supervisory authorities | Current entity-specific recipient and onward-sharing arrangements; do not assume duplicate direct reporting. |
| CSIRT / NIS2 channels | Sector-specific DORA interaction and applicable national routing provisions. |
| Law enforcement / payment schemes | Applicable legal or contractual duties and current arrangements; do not infer a universal notification rule from the incident name. |

Additional legal texts not in the baseline corpus must be obtained and reviewed before relying on cross-regime conclusions.

## Incident Response Maturity Metrics

Financial entities should track these KPIs to demonstrate continuous improvement of their incident management capabilities:

The values below are illustrative internal metrics, not regulatory service-level guarantees. Classification may legitimately change as new evidence emerges; do not discourage necessary reclassification to improve a metric.

| Metric | Description | Illustrative internal target |
|---|---|---|
| MTTD (Mean Time to Detect) | Time from incident occurrence to detection | < 1 hour for critical services |
| MTTC (Mean Time to Classify) | Time from detection to classification (major/non-major) | < 30 minutes |
| MTTN (Mean Time to Notify) | Time from classification to initial NCA notification | Track actual Article 5 deadline compliance per case; a mean alone is insufficient |
| MTTR (Mean Time to Respond/Contain) | Time from detection to containment | < 4 hours for critical services |
| MTTREC (Mean Time to Recover) | Time from detection to full service restoration | Within defined RTO per function |
| Report accuracy | Percentage of final reports requiring no corrections after submission | > 95% |
| Post-incident review completion | Percentage of major incidents with completed PIR within 1 month of closure | 100% |
| Remediation action closure | Percentage of PIR remediation actions closed within agreed timelines | > 90% |
| Drill frequency | Number of incident response drills per year | ≥ 2 per year (different scenarios) |
| Classification accuracy | Percentage of incidents correctly classified at first assessment (not later reclassified) | > 90% |

---

## Cross-Reference: DORA Pillar 2 ↔ ISO 27001:2022 ↔ NIST CSF 2.0

| DORA Article | ISO 27001:2022 Controls | NIST CSF 2.0 |
|---|---|---|
| Art. 17 Incident Management Process | A.5.24 (Incident Mgmt Planning), A.5.25 (Assessment and Decision), A.5.26 (Response), A.6.8 (Reporting) | RS.MA (Incident Management) |
| Art. 18 Classification | A.5.25 (Assessment and Decision on InfoSec Events) | DE.AE (Adverse Event Analysis) |
| Art. 19 Reporting | A.5.5 (Contact with Authorities), A.5.6 (Contact with Special Interest Groups), A.6.8 (Reporting) | RS.CO (Incident Reporting and Communication) |
| Art. 20 Harmonisation of Reporting | A.6.8 (InfoSec Event Reporting) | RS.CO |
| Art. 22 Supervisory Feedback | A.5.5 (Contact with Authorities) | RS.CO |
| Art. 23 Payment Incidents | A.5.24–5.26 (Incident Mgmt), A.5.5 (Contact with Authorities) | RS.MA, RS.CO |

**Key gap**: ISO 27001 does not prescribe the specific classification criteria, materiality thresholds, or reporting timelines that DORA requires. Financial entities with ISO 27001 certification must supplement their ISMS with DORA-specific incident classification procedures and reporting workflows.

---

## Document Metadata

- **Version**: 1.0 — revised documentation; evaluation pending
- **Knowledge base**: DORA Technical Implementation Advisor
- **Pillar**: 2 of 5 — ICT-Related Incident Management, Classification, and Reporting
- **DORA Articles covered**: 17, 18, 19, 20, 21, 22, 23
- **RTS/ITS covered**: RTS 2024/1772 (classification), RTS 2025/301 (reporting content), ITS 2025/302 (templates)
- **Target entity type**: Credit institution (bank)
- **Proportionality tier**: Full framework (not simplified)
- **Original content date**: July 2026
- **Editorial revision date**: 30 October 2026
