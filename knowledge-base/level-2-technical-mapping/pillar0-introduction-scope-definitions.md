# DORA — Introduction, Scope, Definitions, and Proportionality (Articles 1–4)

## Regulatory Scope

- **DORA Articles**: 1–4 (Chapter I — General Provisions)
- **Key RTS/ITS**: None — these articles provide the interpretive foundation for all subsequent chapters
- **Relevance**: These articles define what DORA covers, who it applies to, what key terms mean, and how requirements should be scaled. They are essential context for interpreting the technical requirements in Pillars 1–5.

---

## Art. 1 — Subject Matter

### Content

DORA establishes uniform requirements concerning the security of network and information systems supporting the business processes of financial entities. Specifically, it sets requirements in five areas:

1. **ICT risk management** (Chapter II, Art. 5–16)
2. **ICT-related incident management, classification, and reporting** (Chapter III, Art. 17–23)
3. **Digital operational resilience testing** (Chapter IV, Art. 24–27)
4. **ICT third-party risk management** (Chapter V, Art. 28–44)
5. **Information sharing** (Chapter VI, Art. 45)

The regulation also establishes the oversight framework for critical ICT third-party service providers (CTPPs) and cooperation mechanisms between competent authorities.

DORA applies from **17 January 2025**.

### Relevance for Implementation

Art. 1 confirms that DORA is a comprehensive, cross-sectoral regulation — not a guideline or directive that requires national transposition. It applies directly and uniformly across all EU Member States. This means financial entities cannot rely on varying national interpretations; the same requirements apply whether the entity is in Germany, France, Italy, or any other Member State.

---

## Art. 2 — Scope

### Entities in Scope

DORA applies to the following 21 categories of financial entities:

| # | Entity Type | Examples |
|---|---|---|
| 1 | Credit institutions | Commercial banks, savings banks, cooperative banks |
| 2 | Payment institutions | Licensed payment service providers (PSD2) |
| 3 | Account information service providers | Open banking providers (PSD2) |
| 4 | Electronic money institutions | E-money issuers |
| 5 | Investment firms | Broker-dealers, portfolio managers |
| 6 | Crypto-asset service providers | Crypto exchanges, custody providers (MiCAR) |
| 7 | Issuers of asset-referenced tokens | Stablecoin issuers (MiCAR) |
| 8 | Central securities depositories | CSDs (CSDR) |
| 9 | Central counterparties | CCPs (EMIR) |
| 10 | Trading venues | Regulated markets, MTFs, OTFs (MiFID II) |
| 11 | Trade repositories | Derivatives trade repositories (EMIR) |
| 12 | Managers of alternative investment funds | AIFM (AIFMD) |
| 13 | Management companies | UCITS management companies |
| 14 | Data reporting service providers | APAs, ARMs, CTPs (MiFID II) |
| 15 | Insurance and reinsurance undertakings | Insurers, reinsurers (Solvency II) |
| 16 | Insurance intermediaries, reinsurance intermediaries, and ancillary insurance intermediaries | Insurance brokers, agents (IDD) |
| 17 | Institutions for occupational retirement provision | Pension funds (IORP II) |
| 18 | Credit rating agencies | CRAs (CRA Regulation) |
| 19 | Administrators of critical benchmarks | Benchmark administrators (BMR) |
| 20 | Crowdfunding service providers | Crowdfunding platforms (ECSPR) |
| 21 | Securitisation repositories | Securitisation data repositories |

Additionally, DORA applies to **ICT third-party service providers** through the oversight framework (Art. 31–44) when they are designated as critical (CTPPs).

### Exclusions

The following are explicitly excluded from DORA's scope:
- Managers of alternative investment funds as referred to in Art. 3(2) of Directive 2011/61/EU (small AIFM)
- Insurance and reinsurance undertakings as referred to in Art. 4 of Directive 2009/138/EC (small insurers)
- Institutions for occupational retirement provision which operate pension schemes that together do not have more than 15 members
- Natural or legal persons exempted under specific MiFID II provisions
- Post office giro institutions as referred to in Art. 2(5)(3) of Directive 2013/36/EU

### Relevance for Implementation

When assessing third-party ICT providers (Pillar 4), the entity must determine whether the provider itself might be within DORA scope (e.g., a cloud provider designated as CTPP) or whether the provider serves multiple types of financial entities. The scope determines which competent authority supervises which entity, which in turn affects incident reporting channels and TLPT authority designation.

---

## Art. 3 — Definitions

### Key Definitions for Technical Implementation

DORA Art. 3 contains 63 legal definitions. The following are the most important for interpreting and implementing the technical requirements across all 5 pillars:

---

**Definition 1 — "Digital operational resilience"**
The ability of a financial entity to build, assure, and review its operational integrity and reliability by ensuring, either directly or indirectly through the use of services provided by ICT third-party service providers, the full range of ICT-related capabilities needed to address the security of the network and information systems which a financial entity uses, and which support the continued provision of financial services and their quality, including throughout disruptions.

*Implementation relevance*: This is the overarching goal. Every technical control implemented across Pillars 1–5 should contribute to this objective. Assessment of digital operational resilience is holistic — it encompasses prevention, detection, response, recovery, and learning.

---

**Definition 4 — "ICT risk"**
Any reasonably identifiable circumstance in relation to the use of network and information systems which, if materialised, may compromise the security of the network and information systems, of any technology-dependent tool or process, of operations and processes, or of the provision of services by producing adverse effects in the digital or physical environment.

*Implementation relevance*: ICT risk is defined broadly — it covers not just cyber attacks but also operational failures, configuration errors, capacity issues, and third-party dependencies. The ICT risk management framework (Pillar 1) must address all these dimensions, not just cybersecurity.

---

**Definition 6 — "ICT asset"**
A software or hardware asset in the network and information systems used by the financial entity.

*Implementation relevance*: The ICT asset inventory (Art. 7–8) must cover both software and hardware. This includes cloud resources, virtual machines, containers, and SaaS subscriptions — not just physical servers and endpoints.

---

**Definition 7 — "ICT-related incident"**
A single event or a series of linked events unplanned by the financial entity that compromises the security of the network and information systems, and has an adverse impact on the availability, authenticity, integrity, or confidentiality of data, or on the services provided by the financial entity.

*Implementation relevance*: The definition is based on the four CIA+A properties (Confidentiality, Integrity, Availability, Authenticity). An incident only qualifies as ICT-related if it compromises at least one of these properties. Pure business process failures without ICT involvement are not in scope. However, a service outage caused by ICT failure is in scope even if no cyber attack occurred.

---

**Definition 8 — "Major ICT-related incident"**
An ICT-related incident that has a high adverse impact on the network and information systems that support critical or important functions of the financial entity.

*Implementation relevance*: Only major incidents trigger the reporting obligations under Art. 19. The classification criteria in RTS 2024/1772 (7 criteria with materiality thresholds) determine whether an incident is "major." The entity must have an automated or rapid classification process to meet the 4-hour reporting deadline.

---

**Definition 10 — "Cyber threat"**
A "cyber threat" as defined in Art. 2(8) of Regulation (EU) 2019/881 (the Cybersecurity Act): any potential circumstance, event, or action that could damage, disrupt, or otherwise adversely impact network and information systems, the users of such systems, and other persons.

*Implementation relevance*: Cyber threats are distinct from incidents — a threat is a potential event, an incident is an actual event. The information sharing pillar (Art. 45) and voluntary reporting focus on threats, not just incidents that have occurred.

---

**Definition 14 — "ICT third-party service provider"**
An undertaking providing ICT services.

*Implementation relevance*: This is intentionally broad. Any entity providing ANY ICT service falls under this definition — cloud providers, managed service providers, software vendors, data centre operators, network service providers, hardware maintenance providers, and even consultancy firms providing ICT-related services. The Register of Information (Art. 28, ITS 2024/2956) must include ALL such arrangements.

---

**Definition 15 — "ICT intra-group service provider"**
An undertaking that is part of a financial group and that provides predominantly ICT services to financial entities within the same group or to financial entities belonging to the same institutional protection scheme.

*Implementation relevance*: Intra-group ICT providers are subject to lighter contractual requirements under Art. 30 but are still in scope for the Register of Information and risk assessment. A bank's internal IT shared services centre qualifies as an intra-group provider.

---

**Definition 21 — "ICT services"**
Digital and data services provided through ICT systems to one or more internal or external users on an ongoing basis, including hardware as a service and hardware services which includes the provision of technical support via software or firmware updates by the hardware provider, excluding traditional analogue telephone services.

*Implementation relevance*: The definition is broad enough to cover cloud services (IaaS, PaaS, SaaS), managed security services, co-location, network services, and even hardware maintenance contracts that include firmware updates. Traditional telephony is excluded, but VoIP services are in scope as they run over ICT systems.

---

**Definition 22 — "Critical or important function" (CIF)**
A function, the disruption of which would materially impair the financial performance of a financial entity, or the soundness or continuity of its services and activities, or the discontinued, defective, or failed performance of that function would materially impair the continuing compliance of a financial entity with the conditions and obligations of its authorisation, or with its other obligations under applicable financial services law.

*Implementation relevance*: This is one of the most important definitions in DORA. CIF status triggers enhanced requirements across ALL pillars: enhanced ICT risk management, mandatory scenario testing, stricter third-party contractual provisions (Art. 30(3)), audit rights, exit strategies, and potentially TLPT. Every financial entity must maintain a documented register of its CIFs with justification for the classification. Examples of typical CIFs for a bank: core banking system, payment processing, online/mobile banking, customer onboarding/KYC, regulatory reporting, treasury/trading systems.

---

**Definition 37 — "Threat-led penetration testing" (TLPT)**
A framework that mimics the tactics, techniques, and procedures of real-life threat actors perceived as posing a genuine cyber threat, that delivers a controlled, bespoke, intelligence-led (red team) test of the financial entity's critical live production systems.

*Implementation relevance*: Key elements — TLPT must use real threat actor TTPs (not generic pen testing methodology), must be intelligence-led (requires a Targeted Threat Intelligence Report), must target live production systems (not test environments), and must be bespoke (customised to the entity's specific threat landscape).

---

**Definition 38 — "Red team testing"**

The execution phase of a TLPT — the actual simulated attack performed by the red team against the entity's live production systems.

---

**Definition 39 — "Threat intelligence"**
Information that has been aggregated, transformed, analysed, interpreted, or enriched to provide the necessary context for decision-making and to enable relevant and sufficient understanding in order to mitigate the impact of an ICT-related incident or of a cyber threat, including the technical details of a cyber attack, those responsible for the attack, and their modus operandi and motivations.

*Implementation relevance*: Threat intelligence is not raw data (IOCs alone) — it requires context, analysis, and enrichment. This definition supports the requirements in Art. 13 (learning and evolving) and Art. 45 (information sharing). A financial entity's threat intelligence capability should produce actionable intelligence, not just collect IOC feeds.

---

### Additional Definitions Relevant for Specific Pillars

| Definition # | Term | Most Relevant Pillar |
|---|---|---|
| 2 | Network and information system | All pillars |
| 3 | Legacy ICT system | Pillar 1 (asset management, risk assessment) |
| 5 | Information asset | Pillar 1 (asset classification, Art. 8) |
| 9 | Significant cyber threat | Pillar 2 (voluntary reporting, Art. 19) |
| 11 | ICT security alert | Pillar 1 (detection, Art. 10) |
| 12 | Vulnerability | Pillar 1 (Art. 8-9), Pillar 3 (Art. 25) |
| 16 | ICT concentration risk | Pillar 4 (Art. 29) |
| 17 | Management body | Pillar 1 (governance, Art. 5) |
| 24 | ICT third-party risk | Pillar 4 (Art. 28) |
| 40 | Critical ICT third-party service provider (CTPP) | Pillar 4 (Art. 31-44) |
| 41 | Lead Overseer | Pillar 4 (Art. 33) |

---

## Art. 4 — Proportionality Principle

### Content

Financial entities must implement the requirements of DORA taking into account their:

- **Size** — total assets, number of employees, balance sheet
- **Nature, scale, and complexity** — of their services, activities, and operations
- **Overall risk profile** — including ICT risk appetite and ICT maturity
- **Type** — systemic bank vs. small payment institution vs. insurance intermediary

The principle of proportionality ensures that a Global Systemically Important Institution (G-SII) with millions of clients across multiple Member States faces stricter expectations than a small, non-interconnected financial entity with 10 employees.

### How Proportionality Applies Across Pillars

| Pillar | Full Framework (large bank) | Simplified/Proportionate (micro/small entity) |
|---|---|---|
| 1 — ICT Risk Management | Full framework (Art. 5-14), dedicated ICT risk function, formal risk assessment methodology, comprehensive controls | Simplified framework (Art. 15-16), basic controls, can assign to existing role, less formal documentation |
| 2 — Incident Reporting | Full classification and reporting (Art. 17-23), all 7 criteria, 4h/72h/1m timeline | Same reporting obligations — no simplification for incident reporting |
| 3 — Resilience Testing | Full testing programme (Art. 24-25), annual pen testing, potentially TLPT (Art. 26) | Proportionate testing, no mandatory pen testing, no TLPT |
| 4 — Third-Party Risk | Full lifecycle management (Art. 28-30), Register of Information, concentration risk assessment | Full RoI requirements, but proportionate due diligence and monitoring |
| 5 — Information Sharing | Voluntary (Art. 45) | Voluntary (Art. 45) |

### Determining Proportionality Tier

The competent authority and the entity itself determine the appropriate level of implementation. Key indicators:

**Full framework applies if the entity has:**
- Total assets above EUR 5 billion
- More than 250 employees
- Cross-border operations in multiple Member States
- Critical market infrastructure role
- G-SII or O-SII designation
- Significant retail client base

**Simplified framework may apply if the entity has:**
- Fewer than 10 employees AND turnover/balance sheet below EUR 2 million (microenterprise under Art. 16(1))
- Limited ICT dependency
- No cross-border operations
- Non-systemic role

**Important**: even under the simplified framework, the entity must still have: a documented ICT risk assessment, basic protection and prevention measures, incident detection and response capability, business continuity arrangements, and participation in the incident reporting framework. Proportionality reduces the depth and formality of implementation — it does NOT exempt entities from the core obligations.

### Relevance for Implementation

When answering implementation questions, always consider proportionality. A question like "what does DORA require for patch management?" has a different answer for a G-SII bank (formal vulnerability management programme with CVSS-based SLAs, dedicated team, automated scanning) versus a small payment institution (regular software updates, basic vulnerability awareness, vendor-supported patching).

The knowledge base in this project is calibrated for a **full-scope credit institution** (bank) applying the full framework — not the simplified framework. This is stated in the metadata of each pillar file.

---

## Document Metadata

- **Version**: 1.0
- **Knowledge base**: DORA Technical Implementation Advisor
- **Coverage**: DORA Articles 1, 2, 3, 4 — General Provisions (Chapter I)
- **RTS/ITS covered**: None (no Level 2 measures for Chapter I)
- **Target entity type**: Credit institution (bank)
- **Last updated**: July 2026
