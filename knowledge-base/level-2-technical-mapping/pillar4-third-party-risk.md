# DORA Pillar 4 — ICT Third-Party Risk Management

## Interpretation and assurance status

**Editorial revision: 30 October 2026. Human legal/control review remains open.** This document is an author-created working mapping, not an authoritative statement or evidence of implemented controls. Regulatory summaries must be checked against the current official text and entity-specific applicability. This revision corrects selected identified issues; it is not a paragraph-by-paragraph legal assurance opinion.

**Reading rules:** technical designs, products, numeric thresholds, internal SLAs, review cadences, staffing choices, and maturity targets in implementation sections are project examples unless an exact source provision expressly supports them. They are not universal regulatory minima. Priority labels are project judgements. Evidence lists are requests for material to collect, not assertions that it exists or is sufficient. ISO/NIST cross-references are interpretive and require edition-specific review.

For each adopted control, record: provision and applicability rationale; control objective and design; accountable owner; evidence artifact, period, and location; design and operating-effectiveness checks; result, gap, remediation owner, and due date. Use [the mapping review procedure](../../docs/mapping-review.md) before relying on this material.

## Regulatory Scope

- **DORA Articles**: 28–44 (Chapter V)
  - Section I (Art. 28–30): Key principles for sound management of ICT third-party risk
  - Section II (Art. 31–44): Oversight framework for critical ICT third-party service providers (CTPPs)
- **Key RTS/ITS**:
  - Commission Delegated Regulation (EU) 2024/1773 — detailed content of the policy on contractual arrangements for ICT services supporting critical or important functions
  - Commission Delegated Regulation (EU) 2025/532 — elements to determine and assess when subcontracting ICT services supporting critical or important functions
  - Commission Implementing Regulation (EU) 2024/2956 — standard templates for the Register of Information (RoI)
  - Commission Delegated Regulation (EU) 2024/1502 — criteria for designating critical ICT third-party service providers
  - Commission Delegated Regulation (EU) 2025/295 — harmonisation of oversight conduct
  - Commission Delegated Regulation (EU) 2025/420 — joint examination teams
  - Commission Delegated Regulation (EU) 2024/1505 — oversight fees for CTPPs
- **Applicability**: All financial entities, including those under the simplified framework
- **Reporting schedules**: verify current authority collection instructions; a historical collection date is not a universal deadline for every entity or reporting year.

---

## Art. 28 — General Principles

### Working Regulatory Summary — Verify Against Official Text

Financial entities must manage ICT third-party risk as an integral component of ICT risk within their ICT risk management framework. They remain fully responsible at all times for compliance with, and discharge of, all obligations under DORA and applicable financial services law — regardless of the use of ICT third-party service providers. Financial entities must adopt and regularly review a strategy on ICT third-party risk, including a policy on the use of ICT services supporting critical or important functions provided by ICT third-party service providers.

The management body must regularly review the risks identified with respect to contractual arrangements on the use of ICT services. Financial entities must maintain and update at entity, sub-consolidated, and consolidated level a Register of Information in relation to all contractual arrangements on the use of ICT services provided by third-party service providers.

Article 28(3) distinguishes reporting at least yearly on arrangements from making the full register available on request. Specific supervisory collections may require full-register submission; verify the current instructions for the entity.

Financial entities must adequately inform the competent authority in a timely manner about any planned contractual arrangement on the use of ICT services supporting critical or important functions, as well as when a function has become critical or important.

### Proposed Technical Implementations — Project Examples

**ICT third-party risk strategy:**
- Develop and document an overarching ICT Third-Party Risk Management Strategy approved by the management body, covering:
  - Risk appetite for third-party ICT dependencies
  - Principles for selection, contracting, monitoring, and exiting third-party arrangements
  - Concentration risk policy (avoiding excessive dependency on a single provider or a small number of providers)
  - Multi-vendor strategy for critical functions where feasible
  - Cloud-specific risk assessment criteria and controls
  - Geographical considerations (data location, jurisdictional risks, geopolitical factors)
- Review the strategy at least annually and upon significant changes to the provider landscape

**ICT third-party risk policy (RTS 2024/1773 Art. 1–2):**
- Establish a detailed policy covering the full lifecycle of ICT third-party arrangements:
  - **Planning**: identification of functions to be supported by third parties, risk assessment requirements, approval process
  - **Due diligence**: pre-contractual assessment criteria (financial stability, security posture, compliance, reputation, BCP capability)
  - **Contracting**: mandatory contractual provisions (see Art. 30)
  - **Implementation**: onboarding, integration, security baseline verification
  - **Monitoring**: ongoing risk assessment, performance monitoring, compliance verification, audit rights exercise
  - **Exit**: exit strategy, transition planning, data return and deletion
- The policy must distinguish between arrangements supporting critical or important functions (CIFs) and non-critical arrangements — CIF-supporting arrangements have enhanced requirements throughout the lifecycle
- Define roles and responsibilities: who assesses, approves, monitors, and manages third-party arrangements (typically a combination of procurement, IT, security, risk, and compliance)

**Governance structure for third-party risk:**
- Assign a senior manager or function responsible for ICT third-party risk oversight (may be the CISO, CRO, or a dedicated Third-Party Risk Management function)
- Establish a Third-Party Risk Committee or integrate into the ICT Risk Committee with a dedicated agenda item
- Implement an approval workflow: all new ICT third-party arrangements supporting CIFs require management body or delegated committee approval before contract signing
- Report to the management body at least quarterly on: third-party risk profile, concentration risk, significant changes, incidents involving providers, audit findings

**Register of Information (ITS 2024/2956):**
- Establish and maintain a comprehensive Register of Information (RoI) covering ALL contractual arrangements for ICT services from third-party providers — not just CIF-supporting ones
- The RoI must be maintained at entity level, and where applicable at sub-consolidated and consolidated (group) level
- The ITS 2024/2956 defines mandatory templates with specific data fields structured across multiple tables:

**RoI template structure (ITS 2024/2956 key tables):**

| Template Table | Content |
|---|---|
| b_01 — Entity information | Legal entity identifiers (LEI), entity type, competent authority, group structure |
| b_02 — Contractual arrangements | Contract ID, provider ID, contract type, start date, end date/renewal, total annual cost, governing law |
| b_03 — ICT services | Description of ICT service, service type (cloud, on-premises, hybrid), whether it supports a CIF, data classification level |
| b_04 — Functions identification | Business functions supported, whether classified as critical or important, rationale for CIF classification |
| b_05 — ICT third-party service providers | Provider identification (LEI or alternative ID), provider name, country of incorporation, country of service delivery, parent company |
| b_06 — Subcontracting/sub-outsourcing chains | Subcontractors used by the provider, services subcontracted, subcontractor identification, country |

- Populate required fields accurately and apply the receiving authority’s validation rules; record errors and remediation rather than assuming a universal rejection outcome.
- Implement a process to keep the RoI continuously updated: trigger reviews when contracts are signed, amended, or terminated
- Distinguish annual reporting on new arrangements under Art. 28(3) from provision of the full register on request and any specific supervisory collection instructions. Confirm entity-specific submission dates and formats.
- Groups may maintain a single consolidated RoI covering all entities in the group

**Competent authority notification for CIF arrangements:**
- Notify the competent authority in a timely manner before entering into new contractual arrangements supporting CIFs
- Define an internal process for what constitutes "timely" notification — best practice is at least 30 days before contract execution
- Notification must include: description of the function, the provider, key contract terms, risk assessment summary
- Also notify when an existing function becomes critical or important (which elevates the corresponding third-party arrangement to CIF-supporting status)

### Tools

- **Third-Party Risk Management (TPRM) Platforms**: OneTrust Third-Party Risk, Prevalent, BitSight, SecurityScorecard, ProcessUnity, Aravo
- **Register of Information**: Purpose-built tools aligned with ITS 2024/2956 templates (e.g., Resiplan), or structured spreadsheet implementation in Excel/Google Sheets following the ITS template structure
- **GRC Platforms with TPRM modules**: ServiceNow Third-Party Risk, RSA Archer Third-Party Governance, Eramba (open-source)
- **Provider Security Rating**: BitSight, SecurityScorecard, RiskRecon, UpGuard — for continuous external monitoring of provider security posture
- **Contract Management**: ContractPodAi, Icertis, SharePoint-based contract repositories with metadata tagging

### Candidate Evidence to Collect and Assess

- ICT Third-Party Risk Management Strategy (approved, dated, version-controlled)
- Approved ICT third-party risk policy, with a documented gap assessment against applicable RTS 2024/1773 provisions
- Register of Information (complete, current, structured per ITS 2024/2956 templates)
- Proof of annual RoI submission to competent authority (submission receipt, timestamp)
- Competent authority notifications for CIF-supporting arrangements
- Management body / committee approval records for CIF-supporting arrangements
- Third-party risk reports to management body (quarterly)
- Roles and responsibilities documentation for TPRM

### Priority: CRITICAL

---

## Art. 29 — Preliminary Assessment of ICT Concentration Risk at Entity Level

### Working Regulatory Summary — Verify Against Official Text

Before entering into a contractual arrangement for ICT services, financial entities must identify and assess whether the conclusion of the arrangement would lead to:
- Contracting an ICT third-party service provider that is not easily substitutable
- Having multiple contractual arrangements in place with the same or closely connected ICT third-party service provider

The entity must weigh the benefits and costs of alternative solutions, and consider whether the planned arrangement would give rise to concentration risk. This assessment must account for the number of critical or important functions entrusted to the same provider, the potential effect of disruption at the provider on multiple CIFs simultaneously, and the availability of alternative providers.

### Proposed Technical Implementations — Project Examples

**Concentration risk assessment framework:**
- Develop a formal ICT concentration risk assessment methodology documented in the TPRM policy
- Assess concentration risk along multiple dimensions:

| Dimension | Assessment Criteria |
|---|---|
| Provider concentration | How many CIFs are supported by the same provider? What percentage of total ICT spend goes to a single provider? |
| Substitutability | Are alternative providers available for this service? What is the realistic switching timeline? Are there technical lock-in factors (proprietary APIs, formats, platforms)? |
| Geographical concentration | Are multiple critical services delivered from the same country or data centre region? |
| Technological concentration | Are multiple CIFs dependent on the same underlying technology platform (e.g., all cloud services on a single hyperscaler)? |
| Sub-outsourcing concentration | Does the provider's supply chain introduce hidden concentration (e.g., provider A and provider B both rely on the same cloud infrastructure)? |

- Define concentration risk thresholds and escalation triggers:
  - Amber: single provider supports ≥ 3 CIFs, or ≥ 30% of ICT spend with one provider
  - Red: single provider supports ≥ 5 CIFs, or ≥ 50% of ICT spend with one provider, or provider assessed as not substitutable within 12 months
- Present concentration risk assessment to the ICT Risk Committee before approving new CIF-supporting arrangements
- Produce an annual ICT concentration risk report as part of the management body reporting

**Substitutability assessment:**
- For each CIF-supporting arrangement, document:
  - At least 2 alternative providers that could deliver the service
  - Estimated migration timeline and cost
  - Technical barriers to switching (data portability, API compatibility, integration complexity)
  - Contractual barriers (minimum terms, termination notice periods, data return clauses)
- If a provider is assessed as not easily substitutable, the entity must implement enhanced monitoring and contingency measures

**Multi-vendor strategy:**
- For the most critical functions, evaluate feasibility of a multi-vendor or multi-cloud approach
- Where multi-vendor is not feasible, implement enhanced exit strategies and contingency plans
- Document the rationale for accepting single-vendor dependency for specific CIFs

### Tools

- **Concentration Analysis**: Custom dashboards (Power BI, Tableau) mapping providers to CIFs, spend analysis, geographic distribution
- **TPRM Platforms with concentration risk features**: OneTrust, Prevalent, ServiceNow
- **Cloud provider dependency mapping**: CloudHealth, Flexera, open-source cost analysis tools

### Candidate Evidence to Collect and Assess

- ICT concentration risk assessment methodology
- Pre-contract concentration risk assessment records for all CIF-supporting arrangements
- Annual ICT concentration risk report with trend analysis
- Provider substitutability assessments for CIF-supporting providers
- Multi-vendor strategy documentation with rationale for single-vendor decisions
- Concentration risk thresholds and breach records

### Priority: HIGH

---

## Art. 30 — Key Contractual Provisions

### Working Regulatory Summary — Verify Against Official Text

All contractual arrangements on the use of ICT services must include specific provisions. Arrangements supporting critical or important functions have additional mandatory requirements. DORA specifies minimum contractual clauses that must be present, and the rights of the entity that cannot be contractually waived.

This is one of DORA's most operationally impactful articles — it requires renegotiation of many existing third-party contracts.

### Mandatory Contractual Provisions — All ICT Arrangements (Art. 30(2))

| Provision | Description |
|---|---|
| Clear and complete description | Full description of all functions and ICT services, with quantitative and qualitative performance targets |
| Subcontracting provisions | Conditions for subcontracting, including notification and approval requirements |
| Location of data processing | Indication of where services are provided and data is processed and stored, including obligation to notify any planned changes |
| Data availability, integrity, confidentiality | Provisions ensuring data protection, including return, transfer, and deletion obligations |
| Service levels | Service level descriptions with quantitative and qualitative targets |
| Assistance in case of incident | Provider obligation to assist in case of ICT-related incidents at no additional cost or at pre-determined cost |
| Provider cooperation with authorities | Obligation to cooperate with competent authorities and resolution authorities |
| Termination rights | Clear termination rights including for material breach, regulatory change, or provider change of control |

### Additional Mandatory Provisions — CIF-Supporting Arrangements (Art. 30(3))

| Provision | Description |
|---|---|
| Full SLA with penalties | Comprehensive service level agreements with penalties/remedies for non-achievement |
| Notice periods for changes | Adequate notice periods for material changes to the service |
| BCP/DRP obligations | Provider must have and test business continuity and disaster recovery arrangements for the service |
| Security measures | Provider must implement and maintain appropriate security measures at least equivalent to the entity's own requirements |
| Audit and access rights | Unrestricted right to audit the provider — either directly, through pooled audits, or through third-party auditors — and right to on-site access |
| Cooperation with TLPT | Provider must participate in and cooperate with TLPT when the entity is subject to TLPT requirements |
| Exit strategy | Mandatory exit plan with adequate transition periods, data portability, and continued service during transition |
| Provider incident notification | Provider must notify the entity without undue delay of any ICT-related incident impacting the service, and cooperate in incident management |
| Regulatory cooperation | Provider must cooperate fully with competent authorities, including on-site inspections by regulators |

### Proposed Technical Implementations — Project Examples

**Contract review and remediation programme:**
- Conduct a comprehensive gap analysis of ALL existing ICT third-party contracts against Art. 30 requirements
- Prioritise remediation: CIF-supporting arrangements first, then non-CIF
- Develop a standard contract addendum or supplementary agreement template containing all DORA mandatory provisions — for use in renegotiating existing contracts
- Develop a legally reviewed master contract template mapped to applicable Article 30 provisions; a template alone does not establish compliance
- Track contract remediation progress in the RoI or contract management system

**Mandatory contract clauses — implementation detail:**

**Service levels and performance monitoring (RTS 2024/1773 Art. 3):**
- Define quantitative SLA targets: availability (e.g., 99.95% for Tier 1 services), response time, recovery time, incident resolution time
- Define qualitative targets: security posture, compliance maintenance, staffing adequacy
- Implement automated SLA monitoring dashboards
- Define escalation procedures for SLA breaches and contractual remedies (service credits, remediation plans, termination triggers)
- Review SLA performance at least monthly for CIF-supporting arrangements, quarterly for non-CIF

**Audit and access rights:**
- Contract must grant unrestricted audit rights — no advance notice limitations or scope restrictions for regulatory audits
- Define the entity's annual audit plan for third-party providers: direct audits, pooled audits (multiple financial entities auditing the same provider together), or third-party certification reviews (SOC 2 Type II, ISO 27001)
- For cloud/hyperscaler providers where direct audit is impractical: rely on independent certification (SOC 2 Type II, ISO 27001, C5) supplemented by contractual right to audit, and participation in pooled audit arrangements
- Exercise audit rights at least annually for CIF-supporting providers
- Document all audit findings and track remediation

**Incident notification by provider:**
- Contract must require provider to notify the entity of ICT-related incidents without undue delay
- Define maximum notification time: aligned with DORA incident reporting timelines (account for the applicable awareness/classification/submission clocks; a one-hour provider target is an illustrative contractual control, not a regulatory requirement)
- Provider must cooperate in incident investigation, provide forensic data, and support root cause analysis
- Provider must implement incident management processes compatible with the entity's processes (see Pillar 2)

**Exit strategy and data portability (RTS 2024/1773 Art. 5):**
- Every CIF-supporting contract must have a documented exit strategy covering:
  - Transition plan with a justified, contractually agreed period sufficient for safe migration; six months is an illustrative planning choice, not a universal DORA minimum
  - Data return: provider must return all entity data in a standard, usable format
  - Data deletion: provider must securely delete all entity data after confirmed return, with certification
  - Continued service: provider must continue providing services during the transition period at the same SLA
  - Knowledge transfer: provider must support knowledge transfer to the replacement provider or back to the entity
  - Transitional arrangements and associated costs must be pre-agreed
- Set and justify the exit-strategy review and testing frequency for CIF-supporting arrangements; a three-year cycle is an internal example, not a universal minimum established here.
- Maintain documented contingency plans in case of abrupt provider termination (no transition period)

**Subcontracting provisions (RTS 2025/532):**
- Contract must require provider to obtain entity approval before subcontracting CIF-supporting services or material parts thereof
- Provider must notify the entity of any planned changes to subcontracting arrangements
- Entity retains the right to object to subcontracting if it would materially affect service quality, security, or compliance
- Entity must assess subcontractor risks, including subcontractor location, security posture, and further sub-outsourcing
- Maintain visibility of the full subcontracting chain: who does what, where, with what data
- Include right to terminate if unacceptable subcontracting changes are implemented against the entity's objection

**Data location and processing:**
- Contract must specify the countries and regions where data is processed and stored
- Provider must notify the entity before any change in data processing location
- Entity must assess data sovereignty implications: GDPR, local data protection laws, government access risk
- For sensitive data: require processing within the EU/EEA, unless a specific risk assessment justifies otherwise
- Cloud provider contracts must specify data residency options and geographic failover locations

### Tools

- **Contract Management**: Icertis, ContractPodAi, SharePoint with contract metadata tracking, Juro
- **Contract Gap Analysis**: Custom DORA compliance checklist in spreadsheet, mapped to Art. 30 provisions
- **SLA Monitoring**: Datadog, Grafana + Prometheus (open-source), cloud provider SLA dashboards, StatusPage
- **Audit Management**: AuditBoard, TeamMate+, custom audit tracker in GRC platform
- **Data Classification and Location Tracking**: Data flow mapping tools (OneTrust DataDiscovery, Varonis, BigID)

### Candidate Evidence to Collect and Assess

- DORA contract compliance gap analysis results and remediation tracker
- Updated contracts with DORA mandatory provisions (signed versions)
- Standard DORA contract template (approved by legal/compliance)
- SLA monitoring reports and breach records
- Audit plan for third-party providers (annual)
- Audit reports and finding remediation tracking
- Exit strategy documents for all CIF-supporting arrangements
- Exit strategy feasibility test records
- Subcontracting approval records
- Data location register for all CIF-supporting arrangements
- Provider incident notification log

### Priority: CRITICAL

---

## Art. 31–44 — Oversight Framework for Critical ICT Third-Party Service Providers (CTPPs)

### Working Regulatory Summary — Verify Against Official Text

DORA establishes a pan-European oversight framework for ICT third-party service providers designated as "critical" (CTPPs). This framework is directly managed by the ESAs (EBA, EIOPA, ESMA) through a Lead Overseer model. The oversight framework applies to the providers themselves — not directly to financial entities. However, financial entities that use CTPPs must understand the framework as it affects their provider relationships, contractual arrangements, and concentration risk assessments.

**Key elements of the oversight framework:**

**Designation of CTPPs (Art. 31, RTS 2024/1502):**
- The ESAs jointly designate CTPPs through the Joint Committee, based on criteria including:
  - Systemic impact of the provider on the financial sector
  - Number and nature of financial entities relying on the provider
  - Degree of substitutability of the provider
  - The extent to which the provider supports critical or important functions across the financial sector
- The ESAs publish a list of designated CTPPs — first designations expected in 2025–2026
- Major cloud providers (AWS, Azure, Google Cloud) and key financial infrastructure providers (SWIFT, Bloomberg, ICE) are expected candidates
- CTPPs established outside the EU must establish a subsidiary within the EU to fall under the oversight framework (Art. 31(12))

**Lead Overseer (Art. 33):**
- For each CTPP, one ESA is designated as Lead Overseer based on the type of financial entities most reliant on the provider:
  - EBA: if primarily used by credit institutions and payment/e-money institutions
  - ESMA: if primarily used by investment firms and trading venues
  - EIOPA: if primarily used by insurance and reinsurance undertakings and pension funds
- The Lead Overseer has powers to: request information, conduct general investigations, conduct on-site inspections, issue recommendations, and impose penalties for non-compliance

**Oversight activities (Art. 35–37):**
- The Lead Overseer assesses whether the CTPP has in place comprehensive, sound, and effective rules, procedures, mechanisms, and arrangements to manage ICT risk
- Assessment covers the CTPP's: ICT security measures, physical security, risk management processes, governance, BCP/DRP, incident management, data management, encryption, network security, change management, audit processes
- The Lead Overseer can issue recommendations requiring the CTPP to remediate identified risks or deficiencies
- If the CTPP fails to comply with recommendations, the Lead Overseer can impose a periodic penalty payment

### Proposed Technical Implementations — Project Examples for Financial Entities Using CTPPs

**Monitoring CTPP designation status:**
- Track ESA publications and Joint Committee decisions on CTPP designation
- Maintain awareness of which of the entity's providers have been designated as CTPPs
- Assess the impact of CTPP designation on existing contractual arrangements

**Enhanced due diligence for CTPP arrangements:**
- When using a designated CTPP, conduct enhanced due diligence covering:
  - Review the CTPP's compliance with Lead Overseer recommendations (publicly available or obtained through audit rights)
  - Assess concentration risk implications of using a CTPP that many other financial entities also rely upon
  - Evaluate the CTPP's exit strategy provisions and the entity's ability to migrate away if needed
  - Consider the CTPP's willingness to provide audit access and cooperate with the entity's compliance needs
- Factor CTPP oversight outcomes into the entity's own risk assessment of the provider

**Contractual alignment with oversight framework:**
- Ensure contracts with CTPPs include clauses enabling the entity to comply with DORA while the provider is subject to Lead Overseer oversight
- Include specific clause: the CTPP must notify the entity of any Lead Overseer recommendations that could affect the service provided to the entity
- Ensure audit right clauses are compatible with the Lead Overseer's own audit and inspection activities — coordinate to avoid redundancy but maintain independent verification rights

**Concentration risk considerations for CTPPs:**
- If a CTPP is designated as critical because many financial entities rely on it, this inherently signals concentration risk at systemic level
- Document how the entity manages its specific concentration risk with this CTPP
- Consider multi-cloud or hybrid architectures to reduce dependency on a single CTPP
- Maintain and test exit strategies for CTPP-dependent services

### Tools

- **CTPP Monitoring**: ESA publication alerts, regulatory intelligence services (Thomson Reuters Regulatory Intelligence, Wolters Kluwer), direct subscription to ESA newsletters
- **Enhanced Due Diligence**: TPRM platforms with regulatory monitoring integration

### Candidate Evidence to Collect and Assess

- Record of CTPP designation monitoring activities
- Enhanced due diligence reports for CTPP arrangements
- Concentration risk assessment including CTPP-specific analysis
- Contract clauses addressing Lead Overseer cooperation requirements
- Exit strategy for CTPP-dependent services

### Priority: HIGH

---

## Third-Party Risk Management Lifecycle — Summary

```
1. PLANNING & IDENTIFICATION
│ ├─ Identify business need for ICT third-party service
│ ├─ Determine if the function is critical or important (CIF)
│ ├─ Conduct preliminary concentration risk assessment (Art. 29)
│ └─ Notify competent authority if CIF-supporting (Art. 28)
│
2. DUE DILIGENCE & SELECTION
│ ├─ Assess provider: financial stability, security posture, certifications
│ ├─ Evaluate provider's BCP/DRP, incident management, data handling
│ ├─ Assess provider's subcontracting arrangements and chain
│ ├─ Assess data location and jurisdictional risks
│ ├─ Check provider CTPP designation status
│ └─ Present risk assessment to approval authority
│
3. CONTRACTING
│ ├─ Include all Art. 30(2) mandatory provisions
│ ├─ Include all Art. 30(3) additional provisions if CIF-supporting
│ ├─ Define SLAs with quantitative and qualitative targets
│ ├─ Secure unrestricted audit and access rights
│ ├─ Define exit strategy and transition provisions
│ ├─ Define subcontracting approval requirements
│ └─ Obtain management body / committee approval for CIF arrangements
│
4. ONBOARDING & IMPLEMENTATION
│ ├─ Verify provider security baseline before going live
│ ├─ Integrate provider monitoring into SLA dashboards
│ ├─ Register in the Register of Information (ITS 2024/2956)
│ ├─ Establish communication channels for incident notification
│ └─ Conduct initial security assessment / onboarding audit
│
5. ONGOING MONITORING
│ ├─ Monitor SLA compliance continuously (dashboards)
│ ├─ Review provider security posture continuously (security ratings)
│ ├─ Exercise audit rights at least annually for CIF providers
│ ├─ Review and approve any subcontracting changes
│ ├─ Monitor provider for incidents, regulatory actions, financial health
│ ├─ Assess changes in concentration risk
│ ├─ Review and update the RoI upon any changes
│ └─ Report to management body quarterly
│
6. EXIT & TRANSITION
│ ├─ Activate exit strategy when needed (contract end, breach, strategic change)
│ ├─ Execute the approved transition plan with the justified and agreed migration period
│ ├─ Ensure data return in standard format
│ ├─ Verify data deletion by provider with certification
│ ├─ Knowledge transfer to replacement provider or in-house
│ ├─ Update the Register of Information
│ └─ Post-exit review and lessons learned
```

---

## Register of Information — Key Data Points Checklist

| Data Category | Key Fields | Source |
|---|---|---|
| Entity identification | LEI, entity name, entity type, parent entity, competent authority | Internal master data |
| Contract details | Contract ID, start date, end date, renewal terms, annual cost, governing law | Contract management system |
| ICT services | Service description, service type (cloud IaaS/PaaS/SaaS, on-premises, managed service), criticality classification | IT service catalogue |
| Functions supported | Business function name, CIF classification (yes/no), CIF justification | BIA / function register |
| Provider identification | Provider LEI or BIC or EIC, legal name, country of incorporation, country of service delivery, parent company | Provider master data |
| Data location | Countries where data is processed, stored, and backed up | Contract terms, provider documentation |
| Subcontracting | Subcontractor name, ID, services subcontracted, subcontractor country | Provider disclosure, audit findings |
| Assessment | Date of last risk assessment, date of last audit, key findings status | TPRM platform |

---

## Cross-Reference: DORA Pillar 4 ↔ ISO 27001:2022 ↔ NIST CSF 2.0

| DORA Article | ISO 27001:2022 Controls | NIST CSF 2.0 |
|---|---|---|
| Art. 28 General Principles | A.5.19 (Information Security in Supplier Relationships), A.5.20 (Addressing InfoSec within Supplier Agreements), A.5.21 (Managing InfoSec in the ICT Supply Chain) | GV.SC (Supply Chain Risk Management) |
| Art. 29 Concentration Risk | A.5.22 (Monitoring, Review, and Change Management of Supplier Services) | GV.SC, ID.RA |
| Art. 30 Contractual Provisions | A.5.20 (Addressing InfoSec within Supplier Agreements) | GV.SC |
| Art. 31–44 Oversight Framework | No direct ISO 27001 equivalent (regulatory oversight framework) | GV.SC |

**Key gap**: ISO 27001 Annex A covers supplier relationship security at a high level (A.5.19–5.22) but does not mandate: a detailed Register of Information, specific mandatory contractual provisions comparable to Art. 30, concentration risk assessment with substitutability analysis, exit strategy requirements, or regulatory notification of CIF-supporting arrangements. Financial entities with ISO 27001 must significantly expand their supplier management to meet DORA requirements.

---

## EBA Guidelines Relevant to Pillar 4

In addition to the RTS/ITS, financial entities should consider the following EBA Guidelines which complement DORA Pillar 4:

- **EBA Guidelines on Outsourcing Arrangements (EBA/GL/2019/02)**: While largely superseded by DORA for in-scope entities, these guidelines provide additional practical guidance on outsourcing governance, risk assessment, and contractual provisions that remains useful as implementation reference
- **Joint ESA Guidelines on Cooperation between DORA Oversight and Competent Authorities (JC/GL/2024/36)**: Defines how competent authorities and ESAs cooperate in oversight activities — relevant for understanding supervisory expectations
- **ESA Guidelines on Estimation of Aggregated Costs and Losses from ICT-Related Incidents (JC/GL/2024/34)**: While primarily related to Pillar 2, relevant for assessing economic impact of third-party provider incidents

---

## Document Metadata

- **Version**: 1.0 — revised documentation; evaluation pending
- **Knowledge base**: DORA Technical Implementation Advisor
- **Pillar**: 4 of 5 — ICT Third-Party Risk Management
- **DORA Articles covered**: 28, 29, 30, 31–44 (overview)
- **RTS/ITS covered**: RTS 2024/1773, RTS 2025/532, ITS 2024/2956, RTS 2024/1502, RTS 2025/295, RTS 2025/420, Reg. 2024/1505
- **Target entity type**: Credit institution (bank)
- **Proportionality tier**: Full framework
- **Original content date**: July 2026
- **Editorial revision date**: 30 October 2026
