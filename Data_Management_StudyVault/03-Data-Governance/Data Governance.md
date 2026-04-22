---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 3
keywords: data governance, stewardship, DGC, operating model, business glossary, change management, data policies
---

# Data Governance (Importance: ★★★)
*Reading time: ~5 min*

#dmbok2 #data-governance

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Exercise of authority and control (planning, monitoring, enforcement) over data asset management |
| Goals | (1) Manage data as an asset, (2) Define policies/procedures/metrics, (3) Monitor and guide compliance |
| Relationship to DM | DG = **oversight** (ensuring data is managed); DM = **execution** (managing data to achieve goals) |
| Common Driver | **Regulatory compliance** (especially financial services, healthcare) |
| Operating Models | Centralized, Replicated, Federated |
| Key Roles | CDO, Data Stewards (Chief, Executive, Enterprise, Business, Technical, Coordinating), Data Owners |

## Data Governance vs. Data Management
DG represents an inherent **separation of duty** between oversight and execution:
- **Data Governance** = ensuring data is managed (oversight, like an auditor)
- **Data Management** = managing data to achieve goals (execution, like accounting)
- DG is also separate from **IT Governance** (which focuses on hardware, software, technical architecture via COBIT)

## Scope of Data Governance Programs
Most programs include:
- **Strategy**: Defining and driving execution of Data Strategy and DG Strategy
- **Policy**: Setting and enforcing policies for Metadata, access, usage, security, quality
- **Standards and quality**: Setting Data Quality and Data Architecture standards
- **Oversight**: Audit and correction in key areas (stewardship)
- **Compliance**: Meeting data-related regulatory requirements
- **Issue management**: Identifying, escalating, resolving data-related issues
- **Data management projects**: Sponsoring improvements
- **Data asset valuation**: Defining business value of data assets

## Business Drivers
Most common driver: **Regulatory compliance**. Other drivers:
- **Reducing Risk**: General risk management, data security, privacy (PII)
- **Improving Processes**: Regulatory compliance efficiency, DQ improvement, Metadata management, SDLC improvements, vendor management

DG is **not an end in itself** -- must align with organizational strategy. Often organizations "back into" DG via MDM or major data problems.

## Goals and Principles
A DG program must be:
- **Sustainable**: Not a project with a defined end; requires ongoing commitment
- **Embedded**: Incorporated into development methods, analytics, MDM, risk management
- **Measured**: Must demonstrate positive financial impact from a known starting point

Core principles:
- **Leadership and strategy**: Visionary, committed leadership required
- **Business-driven**: Governs IT decisions about data as much as business interaction
- **Shared responsibility**: Between business Data Stewards and technical professionals
- **Multi-layered**: Enterprise and local levels
- **Framework-based**: Operating framework defines accountabilities and interactions
- **Principle-based**: Guiding principles are the foundation of DG policy

## DG Operating Model Types
| Model | Description |
|-------|-------------|
| **Centralized** | One DG organization oversees all activities in all subject areas |
| **Replicated** | Same DG model and standards adopted by each business unit |
| **Federated** | One DG organization coordinates with multiple BUs for consistent definitions |

## DG Organization Structure
Key bodies (per Table 4):
- **DG Steering Committee**: Highest authority; cross-functional senior executives; releases funding
- **Data Governance Council (DGC)**: Manages DG initiatives, issues, escalations
- **Data Governance Office (DGO)**: Enterprise-level definitions and standards across all KAs
- **Data Stewardship Teams**: Communities of interest on specific subject areas or projects
- **Local DG Committee**: Divisional/departmental councils under Enterprise DGC

Governance functions mirror political governance:
- **Legislative**: Defining policies, standards, Enterprise Data Architecture
- **Judicial**: Issue management and escalation
- **Executive**: Protecting, serving, administrative responsibilities

## Data Stewardship
**Data Stewardship** = accountability and responsibility for effective control and use of data assets.

Types of Data Stewards:
- **Chief Data Steward**: Chairs DG bodies in lieu of CDO
- **Executive Data Steward**: Senior managers on DGC
- **Enterprise Data Steward**: Oversight of a data domain across business functions
- **Business Data Steward**: Subject matter experts accountable for a data subset
- **Data Owner**: Business Data Steward with approval authority for decisions
- **Technical Data Steward**: IT professionals (DBA, BI Specialist, DQ Analyst, etc.)
- **Coordinating Data Steward**: Leads and represents steward teams across discussions

Key stewardship activities: Creating/managing Metadata, documenting rules/standards, managing DQ issues, executing operational DG activities.

## Data Policies and Standards
- **Data policies**: Global directives codifying principles; describe the **"what"** of DG
- **Standards and procedures**: Describe the **"how"** of DG
- Policies should be few, brief, and direct
- Standards can be standardized across all 11 Knowledge Areas
- **Business Glossary**: Core DG tool; houses agreed-upon definitions; reduces ambiguity

## Data Asset Valuation
Methods to measure data value:
- **Replacement cost**: Recovery cost of data lost in disaster/breach
- **Market value**: Value at time of merger/acquisition
- **Identified opportunities**: Income from BI opportunities, transactions, or selling data
- **Risk cost**: Penalties, remediation, litigation from regulatory risk

**Generally Accepted Information Principles** (adapted from GAAP): Accountability, Asset, Audit, Due Diligence, Going Concern, Level of Valuation, Liability, Quality, Risk, Value.

## Change Management (ADKAR)
Five areas to measure change management effects:
- **A**wareness of the need to change
- **D**esire to participate and support the change
- **K**nowledge about how to change
- **A**bility to implement new skills and behaviors
- **R**einforcement to keep the change in place

## DG Metrics
Three categories:
- **Value**: Contributions to business objectives, risk reduction, improved efficiency
- **Effectiveness**: Achievement of goals, tool usage by stewards, communication/training effectiveness
- **Sustainability**: Policy/process performance, conformance to standards, staff behavior change

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| DG vs DM | DG = **oversight**; DM = **execution** |
| Three DG operating models | **Centralized, Replicated, Federated** |
| Most common DG driver | **Regulatory compliance** |
| DG program must be... | **Sustainable, Embedded, Measured** |
| Highest DG authority body | **DG Steering Committee** |
| Data Owner definition | Business Data Steward with **approval authority** for decisions |
| Business Glossary purpose | Houses **agreed-upon definitions**; reduces ambiguity |
| DG three governance functions | **Legislative, Judicial, Executive** |
| ADKAR model | **Awareness, Desire, Knowledge, Ability, Reinforcement** |
| DG separate from IT Governance | IT Gov = hardware/software/COBIT; DG = **data assets exclusively** |

## Related Notes
- [[Data Management]]
- [[Data Handling Ethics]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Data Quality]]
- [[Metadata Management]]
