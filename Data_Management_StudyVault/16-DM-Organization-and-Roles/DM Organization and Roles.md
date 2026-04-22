---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 16"
keywords: "data management organization, operating model, centralized, decentralized, federated, hybrid, network, CDO, data governance, roles, stakeholder analysis, RACI, center of excellence"
tags:
  - dmbok2
  - dm-organization
---

# Data Management Organization and Role Expectations
*Reading time: ~9 min*

## Overview Table (At a Glance)

| Aspect | Details |
|---|---|
| **Focus** | Principles for structuring DM and Data Governance organizations; operating models; roles and responsibilities |
| **Key Challenge** | Clarifying ownership, collaboration, accountability, and decision-making in an evolving data landscape |
| **Operating Models** | Decentralized, Network, Centralized, Hybrid, Federated |
| **Critical Success Factors** | Executive sponsorship, clear vision, proactive change management, leadership alignment, communication, stakeholder engagement, orientation/training, adoption measurement, guiding principles, evolution not revolution |
| **Key Bodies** | CDO Organization, Data Governance Bodies, Data Quality teams, Enterprise Architecture |
| **Principle** | No perfect organizational structure exists -- much depends on industry drivers and corporate culture |

---

## Understanding Current State

Before defining or improving a DM organization, assess:

- **Role of data**: What key processes are data-driven? How well-recognized is data's role in organizational strategy?
- **Cultural norms about data**: Potential obstacles to implementing or improving management and governance
- **DM and governance practices**: How and by whom is data-related work executed?
- **How work is organized**: Relation between project-focused and operational execution; committee structures
- **Reporting relationships**: Centralized vs. decentralized, hierarchical vs. flat
- **Skill levels**: Data knowledge of SMEs and stakeholders from line staff to executives

### Current State Assessment Framework

Three dimensions to assess:
1. **Culture**: How decisions are made, who makes them, how committees are used, who currently manages data
2. **Operating Model**: Centralized, Decentralized, or Hybrid/Federated
3. **People**: DM owner, Data Governance owner, SMEs, Leadership

### Satisfaction Assessment Questions
- Does the organization have information needed for sound, timely business decisions?
- Does it have confidence in revenue reports?
- Can it track organizational KPIs?
- Is it in compliance with all data management laws?

---

## Five Operating Models

### 1. Decentralized Operating Model
- DM responsibilities distributed across lines of business and IT
- Collaboration is committee-based; no single owner
- **Benefits**: Flat structure; alignment to LOB/IT; clear understanding of data requirements; easy to implement
- **Drawbacks**: Many participants in governance; harder to implement collaborative decisions; less formal; harder to sustain; difficult to enforce consistency; hard to define data ownership

### 2. Network Operating Model
- Decentralized informality made more formal through a **RACI matrix** (Responsible, Accountable, Consulted, Informed)
- Operates as a series of known connections between people and roles
- **Benefits**: Same as decentralized plus accountability without impacting org charts
- **Drawbacks**: Same as decentralized plus need to maintain and enforce RACI expectations

### 3. Centralized Operating Model
- Everything owned by the Data Management Organization
- All data roles report directly to a DM leader
- **Benefits**: Formal executive position; one person at top; clear accountability; data managed by type or subject area
- **Drawbacks**: Requires significant organizational change; risk of separating DM from core business processes; knowledge loss over time; question of where DMO fits in enterprise

### 4. Hybrid Operating Model
- Combines benefits of decentralized and centralized
- Centralized DM **Center of Excellence** works with decentralized business unit groups
- Executive steering committee plus tactical working groups
- **Benefits**: Appropriate direction from top; executive accountability; BU teams align to business priorities; CoE support
- **Drawbacks**: Requires additional headcount for CoE; BU priority conflicts; central vs. decentralized conflicts

### 5. Federated Operating Model
- Variation on hybrid with additional layers of centralization/decentralization
- Enterprise DMO with multiple hybrid models delineated by division or region
- **Benefits**: Centralized strategy with decentralized execution; may be only model for large global enterprises; enables regional priority accommodation
- **Drawbacks**: Complexity; many layers; balance needed between LOB autonomy and enterprise needs

---

## Identifying the Best Model

- Assess current organizational structure: centralized, decentralized, or combination
- Characterize how independent divisions/regions are
- Determine how decisions are made (democratically vs. by fiat) and implemented
- Most organizations start **decentralized** then evolve toward more formal models
- Some organizations forced to mature quickly due to market shock or regulation

### DMO Design Tips
- Determine starting point by assessing current state
- Tie operating model to organization structure
- Account for: Organization Complexity + Maturity, Domain Complexity + Maturity, Scalability
- Get executive sponsorship -- a must for sustainability
- Ensure leadership forums are **decision-making bodies**
- Consider pilot programs and waves of implementation
- Focus on high-value, high-impact data domains
- Use what already exists
- **Never take a One-Size-Fits-All approach**

---

## Ten Critical Success Factors

1. **Executive Sponsorship** -- ensures guidance for stakeholders to transition; sponsor must believe in the initiative
2. **Clear Vision** -- all stakeholders understand what DM is, why it's important, and how their work is affected
3. **Proactive Change Management** -- plan for, manage, and sustain change; address people challenges
4. **Leadership Alignment** -- unified support and agreement on how success is defined; regularly re-assess leaders at all levels
5. **Communication** -- start early, continue openly and often; customize to stakeholder groups; repeat and test messages
6. **Stakeholder Engagement** -- understand how individuals/groups will react; map by influence and interest level
7. **Orientation and Training** -- leaders need orientation; stewards/owners/custodians need in-depth training on policies, processes, tools
8. **Adoption Measurement** -- measure adoption, delta from previous state, enabling aspects, innovation aspects
9. **Adherence to Guiding Principles** -- shared values, strategic vision, basis for integrated decision-making
10. **Evolution Not Revolution** -- minimize big changes; incrementally improve; easier to justify and gain support

---

## Building the DMO

### Identify Current DM Participants
- Start with teams already engaged in DM activities
- Survey who creates, manages data; who measures data quality; who has "data" in their title
- Identify gaps in roles and skill sets needed
- Review compensation; align with DM expectations; involve HR
- Assign roles to the right people at the right level for credibility

### Identify Committee Participants
- Data Governance Steering Committee and working groups
- Get the right people; use their time well; keep focused on business objectives
- Can leverage existing committees but risk DM not getting adequate attention
- Conduct stakeholder analysis to identify executive sponsors

### Stakeholder Analysis
- Stakeholder: any person or group who can influence or be affected by the DM program
- Internal: IT, operations, compliance, legal, HR, finance, LOBs
- External: customers, government, regulators, vendors, agents
- Key questions: Who is affected? How will roles shift? How might they respond? What issues/concerns?
- Map stakeholders by **influence level** and **interest/impact level**
- Pay attention to who controls resources, who could block initiatives, who could influence others

---

## Key Organizational Interactions

### Chief Data Officer (CDO)
- Bridges gap between technology and business
- Common mandates: establish data strategy, align data-centric requirements, establish governance standards/policies, advise on analytics/Big Data/DQ, evangelize DM principles, oversight of data usage in BI
- Common for DMO to report through CDO
- In decentralized model, CDO determines strategy while IT/operations/LOBs execute

### Data Governance
- Organizing framework for strategy, objectives, and policy
- Synergistic relationship with DM: governance provides marching orders; DM executes
- **Governance = "Doing the right things"**; **Data Management = "Doing things right"** (Ladley, 2012)
- In centralized model, DG Office can report to DMO or vice versa
- In decentralized model, tight partnership between DG Office and DMO is essential

### Data Quality
- Many DMOs start with DQ focus -- desire to measure and improve quality
- DQ practice can mature into a Center of Excellence
- Often evolves organically into a broader DM organization
- Align DQ operating model to overall DMO for consistent stakeholders, relationships, tools

### Enterprise Architecture
- Disciplines: Technology Architecture, Application Architecture, Information/Data Architecture, Business Architecture
- Data Architects can sit in either DMO or EA group with dotted line to the other
- Interface through: Data Governance, Architecture Review Boards (ARBs), or Ad-hoc meetings

---

## Managing a Global Organization

Global companies must pay special attention to:
- Adhering to standards
- Synchronizing processes
- Aligning accountability
- Training and communication
- Monitoring and measuring effectively
- Developing economies of scale
- Reducing duplication of effort
- Networked or federated models become more attractive for global operations

---

## Data Management Roles

### Executive Roles
- **CIO** and **CTO** (IT side, well-established)
- **CDO** (business side, gaining credibility)

### Business Roles
- **Data Stewards**: SMEs with accountability for Metadata and DQ of business entities; define business terms, valid values, DQ requirements and business rules
- **Business Process Analysts / Process Architects**: Ensure business process models support downstream data uses

### IT Roles
- **Data Architect**: Data architecture and integration (enterprise or functional level)
- **Data Modeler**: Data requirements, definitions, business rules, logical/physical models
- **Data Model Administrator**: Model version and change control
- **Database Administrator (DBA)**: Design, implementation, support of structured data assets
- **Data Security Administrator**: Controlled access to protected data
- **Data Integration Architect**: Design technology for integrating and improving data quality
- **Data Integration Specialist**: Implement systems to replicate, extract, transform, load data
- **Analytics / Report Developer**: Reporting and analytical application solutions
- **Application Architect**: Integrating application systems
- **Technical Architect**: IT infrastructure and technology portfolio
- **Technical Engineer**: IT infrastructure implementation and administration
- **Help Desk Administrator**: Issue handling and resolution
- **IT Auditor**: Audit of IT responsibilities including DQ and data security

### Hybrid Roles (Business + Technical)
- **Data Quality Analyst**: Fitness of data for use; root cause analysis; process improvement
- **Metadata Specialist**: Integration, control, and delivery of Metadata
- **Business Intelligence Architect**: Design of BI user environment
- **BI Analyst / Administrator**: Supporting effective use of BI data
- **BI Program Manager**: Coordinates BI requirements and initiatives across corporation

---

## Exam/Test Patterns (Frequently Tested)

- **Five operating models**: Decentralized, Network, Centralized, Hybrid, Federated -- pros and cons of each
- **RACI matrix** distinguishes Network model from Decentralized
- **Hybrid model**: Center of Excellence + decentralized BU groups + executive steering committee
- **Federated model**: Only model that may work for large global enterprises
- **Ten critical success factors** -- especially Executive Sponsorship, Evolution Not Revolution, Leadership Alignment
- **"Doing the right things" vs. "Doing things right"** (Governance vs. Management -- Ladley)
- **CDO role** and where DMO typically reports
- **Stakeholder analysis** -- map by influence and interest/impact
- **Data Steward** role and responsibilities (business terms, valid values, DQ requirements)
- **Hybrid roles** -- DQ Analyst, Metadata Specialist, BI Architect
- Most organizations start **decentralized** and evolve toward more formal models
- **Never take a One-Size-Fits-All approach**

---

## Related Notes

- [[Big Data and Data Science]]
- [[Maturity Assessment]]
- [[Change Management]]
- [[Data Governance]]
- [[Data Quality]]
- [[Data Architecture]]
- [[Data Management]]
- [[Metadata Management]]
