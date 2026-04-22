---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 15"
keywords: "maturity assessment, DMMA, CMM, capability maturity model, CMMI-DMM, DCAM, Stanford, Gartner EIM, readiness assessment, roadmap, continuous improvement, governance"
tags:
  - dmbok2
  - maturity-assessment
---

# Data Management Maturity Assessment
*Reading time: ~10 min*

## Overview Table (At a Glance)

| Aspect | Details |
|---|---|
| **Definition** | A method for ranking practices for handling data within an organization to characterize the current state of data management and its impact on the organization |
| **Goals** | 1) Comprehensively discover and evaluate critical DM activities; 2) Educate stakeholders about DM concepts, principles, practices, roles, and responsibilities; 3) Establish or enhance a sustainable enterprise-wide DM program |
| **Inputs** | Business strategy and goals, culture and risk tolerance, maturity frameworks and DAMA-DMBOK, policies/processes/standards/operating models, benchmarks |
| **Activities** | (P) Plan assessment activities, Establish scope and approach, Plan communications; (C) Gather information, Perform assessment, Interpret results; (D) Develop recommendations; (P) Create targeted improvement program; (C) Re-assess maturity |
| **Deliverables** | Ratings and ranks, maturity baseline, readiness assessment, risk assessment, staffing capability, investment/outcomes options, recommendations, roadmap, executive briefings |
| **Suppliers** | Executives, data stewards, DM executives, subject matter experts, employees |
| **Participants** | CDO/CIO, business management, DM executives and governance bodies, Data Governance Office, maturity assessors, employees |
| **Consumers** | Executives, audit/compliance, regulators, data stewards, Data Governance bodies, organizational effectiveness group |
| **Tools** | DM maturity frameworks, communications plan, collaboration tools, knowledge management and Metadata repositories, data profiling tools |
| **Metrics** | DMMA local and total ratings, resource utilization, risk exposure, spend management, inputs to DMMA, rate of change |

---

## Business Drivers

- **Regulation**: Regulatory oversight requires minimum maturity levels
- **Data Governance**: The governance function requires assessment for planning and compliance
- **Organizational readiness**: Recognizing need to improve practices (e.g., MDM deployment readiness)
- **Organizational change**: Mergers or other changes presenting DM challenges
- **New technology**: Understanding likelihood of successful adoption
- **Data management issues**: Baselining current state to address DQ issues or other challenges

---

## Capability Maturity Model -- Origin

- Grew out of US Department of Defense efforts to evaluate software contractors
- Mid-1980s: Capability Maturity Model for Software published by Software Engineering Institute, Carnegie-Mellon University
- Adapted to many fields including data management
- Progression happens in a set order -- **no level can be skipped**

---

## The Five (Six) Maturity Levels

| Level | Name | Characteristics |
|---|---|---|
| **Level 0** | No Capability | No organized DM practices or formal enterprise processes. Very few organizations exist here. |
| **Level 1** | Initial / Ad Hoc | Little or no governance; limited tool set; roles defined within silos; controls applied inconsistently; data quality issues not addressed. Success depends on individual competence. |
| **Level 2** | Repeatable | Emerging governance; introduction of consistent tool set; some roles and processes defined; growing awareness of DQ issues. Minimum process discipline. |
| **Level 3** | Defined | Data viewed as organizational enabler; scalable processes and tools; reduction in manual processes; process outcomes more predictable. Standards are set and used. |
| **Level 4** | Managed | Centralized planning and governance; management of data-related risks; DM performance metrics; measurable improvements in data quality. Processes quantified and controlled. |
| **Level 5** | Optimized | Highly predictable processes; reduced risk; well-understood metrics for data quality and process quality. Process improvement goals are quantified. Focus on continuous improvement. |

---

## Assessment Criteria Categories

Based on the DAMA-DMBOK Context Diagram, criteria can be formulated across:

- **Activity**: Degree the activity/process is in place; how well defined and executed; whether best-practice outputs are produced
- **Tools**: Degree of automation; common tool set availability; tool training; long-term technology planning
- **Standards**: Degree of common standards; documentation quality; enforcement through governance and change management
- **People and Resources**: Staffing adequacy; specific skills, training, and knowledge; role/responsibility definition clarity

Assessment within each level uses a scale: 1 - Not Started, 2 - In Process, 3 - Functional, 4 - Effective

---

## Existing DMMA Frameworks

### CMMI Data Management Maturity Model (DMM)
- Six areas: DM Strategy, Data Governance, Data Quality, Platform and Architecture, Data Operations, Supporting Processes
- Includes sub-processes and accounts for relationships between DM areas
- Addresses stakeholder alignment and business process/DQ relationship

### EDM Council DCAM
- 37 capabilities and 115 sub-capabilities
- Focus: stakeholder engagement, formality of process, existence of artifacts
- Industry advocacy for financial services

### IBM Data Governance Council Maturity Model
- Based on input from 55 organizations
- Four categories: **Outcomes** (risk management, value creation), **Enablers** (organization, policy, stewardship), **Core Disciplines** (DQ, lifecycle, security/privacy), **Supporting Disciplines** (architecture, classification, Metadata, audit)
- Presented as both maturity framework and assessment questions

### Stanford Data Governance Maturity Model
- Developed for the university, not an industry standard
- Differentiates **foundational** (awareness, formalization, Metadata) from **project** (stewardship, DQ, Master Data) components
- Articulates drivers for people, policies, and capabilities

### Gartner's Enterprise Information Management Maturity Model
- Criteria for: vision, strategy, metrics, governance, roles and responsibilities, lifecycle, infrastructure

---

## DMMA Activities

### 1. Plan Assessment Activities

#### Define Objectives
- Clarify drivers; describe focus; influence scope
- Objectives must be clearly understood by executives and lines of business
- Provide criteria for evaluating which model to adopt and which areas to prioritize

#### Choose a Framework
- Review frameworks in context of current state assumptions and assessment objectives
- The team should have expertise in the chosen model and methodology

#### Define Organizational Scope
- Enterprise-wide scope may be impractical for a first assessment
- **Localized assessments**: Go deeper, faster; select highly regulated functions
- **Enterprise assessments**: Broad, sometimes disconnected; can aggregate from localized DMMAs
- Trade-offs exist between local depth and enterprise breadth

#### Define Interaction Approach
- Methods: workshops, interviews, surveys, artifact reviews
- Minimize time commitment; complete quickly so actions are fresh
- Avoid delays -- stakeholders lose enthusiasm

#### Plan Communications
- Inform stakeholders about expectations, purpose, process, involvement, schedule
- Include schedule for reporting findings and recommendations at all levels
- Consider resistance/cooperation factors, legal concerns, HR concerns

### 2. Perform Maturity Assessment

#### Gather Information
- Formal ratings, interviews, focus groups, documentation, data investigation, email, procedure manuals, policies, Metadata repositories, architecture documents, templates

#### Perform the Assessment
- Multi-phased rating: participants rate criteria, then refine through artifact review
- Goal: **consensus view of current state supported by evidence**
- Steps: review against rating method, document evidence, review with participants, document interpretation, develop visualizations

### 3. Interpret Results
- Identify improvement opportunities aligned with strategy
- Define next steps toward target state
- Present ratings with respect to organizational/cultural drivers and business goals
- Illustrate linkage between current capabilities and business processes/strategies

#### Report Assessment Results
- Includes: business drivers, overall results, ratings by topic with gaps, recommended approach, strengths, risks, investment options, governance/metrics, resource analysis, reusable artifacts

#### Executive Briefings
- Summarize strengths, gaps, and recommendations
- Tailor messages to clarify impacts and benefits per executive group
- Caution: executives often want to skip levels -- costs must balance benefits

### 4. Create Targeted Improvement Program
- Recommendations must be actionable -- describe capabilities required
- Roadmap should contain: sequenced improvement activities, timeline, expected rating improvements, oversight activities
- Assessment results should support a multi-year improvement program

### 5. Re-assess Maturity
- Conduct at regular intervals as part of continuous improvement
- Establish baseline, define re-assessment parameters, repeat on published schedule
- Track trends relative to initial baseline
- Re-assessment can re-invigorate effort; measurable progress maintains commitment

---

## Framework Selection Criteria

- **Accessibility**: Non-technical terms conveying functional essence
- **Comprehensiveness**: Broad scope including business engagement
- **Extensible and flexible**: Enhancement for industry-specific needs; usable in whole or part
- **Future progress path built-in**: Logical way forward within each function
- **Industry-agnostic vs. industry-specific**: Match organizational needs
- **Level of abstraction or detail**: Sufficient for relating to organizational work
- **Non-prescriptive**: Describes what, not how
- **Organized by topic**: Appropriate context; recognizes dependencies
- **Repeatable**: Consistent interpretation; comparable results
- **Supported by neutral organization**: Vendor neutral; widely available
- **Technology neutral**: Focus on practices, not tools
- **Training support**: Comprehensive training for framework mastery

---

## DAMA-DMBOK as Assessment Tool

- Can prepare for or establish criteria for a DMMA
- Knowledge Areas, activities, and deliverables can be configured to a specific framework
- Fast checklist approach to determine areas needing deeper analysis
- Large community of professionals across multiple industries

---

## Risks and Mitigations

| Risk | Mitigation |
|---|---|
| Lack of organizational buy-in | Socialize concepts; establish benefit statements; engage executive sponsor |
| Lack of DMMA expertise | Use third-party specialists; require knowledge transfer |
| Lack of time or expertise | Relate DMMA to specific business problems |
| Lack of communication planning | Address in communications plan; orient participants to key concepts |
| Conversations devolve into systems talk | DMMA educates all participants regardless of background |
| Incomplete/out-of-date assets | Flag "as of" dates; adjust ratings accordingly |
| Narrow focus | Reduce depth; do a quick assessment to establish comparative baseline |
| Inaccessible staff or systems | Reduce horizontal scope to available Knowledge Areas and staff |
| Surprises (e.g., regulation changes) | Add flexibility into the assessment work stream |

---

## Metrics

- **DMMA Ratings**: Snapshot of capability level; can include custom weighting and target state
- **Resource Utilization Rates**: Express cost of DM as headcount (e.g., "10% of time manually aggregating data")
- **Risk Exposure**: Organization's capabilities relative to DMMA ratings
- **Spend Management**: How DM cost is allocated; sustainability and value impacts
- **Inputs to DMMA**: Count, coverage, availability, systems, data volumes, teams involved
- **Rate of Change**: Speed of capability improvement from baseline through periodic reassessment

---

## Governance of the DMMA

- Oversight belongs to the Data Governance team (or steering committee if no formal governance)
- Should have an executive sponsor, ideally the CDO
- Each function involved has a voice in execution, method, results, and roadmaps
- The DMMA lifecycle (planning, assessment, recommendations, action plan, re-evaluation) should itself be governed

---

## Organizational and Cultural Change

- Establishing or enhancing a DM program includes changes to processes, methods, and tools
- Cultural transformation begins with acknowledging that things can be better
- DMMA locates the organization on a maturity scale and provides a roadmap for improvement
- Results should be part of a larger organizational discussion, supported by effective data governance

---

## Exam/Test Patterns (Frequently Tested)

- **Five maturity levels** and their characteristics (0-5)
- **CMM origin** -- US DoD, Software Engineering Institute, Carnegie-Mellon
- **No level can be skipped** -- progression is sequential
- **CMMI-DMM** six areas vs. **DCAM** 37 capabilities vs. **IBM** four categories vs. **Stanford** foundational/project split
- **Assessment criteria categories**: Activity, Tools, Standards, People/Resources
- **Localized vs. enterprise** assessment trade-offs
- **Consensus view supported by evidence** -- goal of the assessment
- **Framework selection criteria** -- especially non-prescriptive, technology neutral, repeatable
- **Re-assessment** as part of continuous improvement cycle
- **Executive briefing** pitfall -- wanting to skip levels (costs vs. benefits)
- **Metrics**: DMMA ratings, resource utilization, risk exposure, spend management, rate of change
- **DMMA governance** -- oversight by Data Governance team, executive sponsor role

---

## Related Notes

- [[Big Data and Data Science]]
- [[DM Organization and Roles]]
- [[Change Management]]
- [[Data Governance]]
- [[Data Quality]]
- [[Data Architecture]]
- [[Data Management]]
- [[Metadata Management]]
