---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 15"
keywords: "maturity assessment, DMMA, CMM, capability maturity model, CMMI-DMM, DCAM, framework selection, roadmap, continuous improvement, levels"
tags:
  - dmbok2
  - maturity-assessment
  - practice
---

# Data Management Maturity Assessment -- Practice Questions

## Related Concepts

- [[Maturity Assessment]]
- [[Data Governance]]
- [[Data Quality]]
- [[Data Management]]
- [[DM Organization and Roles]]
- [[Change Management]]

---

> [!hint]- Key Patterns (click to view)
> - **Five maturity levels** (0-5) and their specific characteristics -- especially the differences between Level 3 (Defined) and Level 4 (Managed)
> - **No level can be skipped** -- progression is sequential; executives wanting to skip levels is a known pitfall
> - **CMM origin**: US DoD, Software Engineering Institute, Carnegie-Mellon, mid-1980s
> - **Assessment criteria categories**: Activity, Tools, Standards, People/Resources
> - **Localized vs. enterprise** assessments -- trade-offs between depth and breadth
> - **Consensus view supported by evidence** is the goal of the assessment process
> - **Framework selection criteria** -- especially non-prescriptive, technology neutral, repeatable, vendor neutral
> - **CMMI-DMM** (6 areas), **DCAM** (37 capabilities / 115 sub-capabilities), **IBM** (4 categories), **Stanford** (foundational vs. project)
> - **Metrics**: DMMA ratings, resource utilization, risk exposure, spend management, rate of change
> - The DMMA itself should be **governed** with a lifecycle of planning, assessment, recommendations, and re-evaluation

---

### Question 1 [recall]

What are the five (or six) maturity levels in a typical Capability Maturity Model, and what is the key characteristic of each?

> [!answer]- Show Answer
> | Level | Name | Key Characteristic |
> |---|---|---|
> | **Level 0** | No Capability | No organized DM practices or formal enterprise processes |
> | **Level 1** | Initial / Ad Hoc | Success depends on individual competence; little or no governance; roles in silos |
> | **Level 2** | Repeatable | Minimum process discipline in place; emerging governance; consistent tools; growing DQ awareness |
> | **Level 3** | Defined | Standards set and used; data viewed as organizational enabler; scalable processes; predictable outcomes |
> | **Level 4** | Managed | Processes quantified and controlled; centralized governance; DM performance metrics; measurable DQ improvement |
> | **Level 5** | Optimized | Process improvement goals quantified; highly predictable processes; reduced risk; focus on continuous improvement |
>
> Levels commonly include Level 0 through 5, though some models start at Level 1. **Progression happens in a set order and no level can be skipped.**

---

### Question 2 [recall]

What four categories of assessment criteria are suggested when evaluating data management maturity using the DAMA-DMBOK Context Diagram?

> [!answer]- Show Answer
> 1. **Activity**: To what degree is the activity or process in place? How well defined and executed? Are best-practice outputs produced?
> 2. **Tools**: To what degree is the activity automated and supported by a common tool set? Is tool training provided? Are tools configured optimally? Is long-term technology planning in place?
> 3. **Standards**: To what degree is the activity supported by common standards? How well documented? Are standards enforced through governance and change management?
> 4. **People and Resources**: To what degree is the organization staffed? What specific skills, training, and knowledge are necessary? How well are roles and responsibilities defined?

---

### Question 3 [recall]

Name the four categories of the IBM Data Governance Council Maturity Model.

> [!answer]- Show Answer
> 1. **Outcomes**: Data risk management and compliance, value creation
> 2. **Enablers**: Organizational structure and awareness, policy, stewardship
> 3. **Core Disciplines**: Data Quality Management, information lifecycle management, information security and privacy
> 4. **Supporting Disciplines**: Data Architecture, classification and Metadata, audit information, logging and reporting
>
> The model was based on input from 55 organizations and is presented both as a maturity framework and as assessment questions with answers constructed to indicate maturity levels.

---

### Question 4 [recall]

List at least five criteria that should be considered when selecting a Data Management Maturity (DMM) framework.

> [!answer]- Show Answer
> Key selection criteria include:
> 1. **Accessibility**: Practices stated in non-technical terms
> 2. **Comprehensiveness**: Addresses broad scope including business engagement, not merely IT
> 3. **Extensible and flexible**: Can be enhanced for industry-specific needs; usable in whole or in part
> 4. **Future progress path built-in**: Logical way forward within each function
> 5. **Non-prescriptive**: Describes what needs to be performed, not how
> 6. **Organized by topic**: Data management activities in appropriate context with recognized dependencies
> 7. **Repeatable**: Consistently interpreted, supporting comparable results
> 8. **Supported by a neutral, independent organization**: Vendor neutral, widely available
> 9. **Technology neutral**: Focus on practices, not tools
> 10. **Training support**: Comprehensive training for professionals to master the framework

---

### Question 5 [recall]

What are the five key metrics categories for measuring a DMMA?

> [!answer]- Show Answer
> 1. **DMMA Ratings**: Snapshot of capability level with description, custom weighting, and recommended target state
> 2. **Resource Utilization Rates**: Express cost of DM as headcount (e.g., "every resource spends 10% of their time manually aggregating data")
> 3. **Risk Exposure**: Organization's capabilities relative to DMMA ratings -- ability to respond to risk scenarios
> 4. **Spend Management**: How DM cost is allocated across the organization; impacts on sustainability and value (includes data management sustainability, effectiveness of communication, speed of change adoption, etc.)
> 5. **Rate of Change**: The speed at which the organization is improving its capability from the established baseline through periodic reassessment

---

### Question 6 [application]

An organization is conducting its first DMMA. Executives want to assess the entire enterprise across all Knowledge Areas in a two-week timeframe. What advice would you give, and what risks should you highlight?

> [!answer]- Show Answer
> This approach is risky and likely impractical. Recommended advice:
>
> **Scope concerns:**
> - Enterprise-wide scope may be impractical for a first assessment; it is usually best to **define a manageable scope**, such as a single business area or program
> - Localized assessments can go **much deeper** and can be done **more quickly** because the scope is contained
> - Well-planned localized assessments can often be **aggregated and weighted** to form an enterprise assessment later
>
> **Time and engagement risks:**
> - If there are **delays**, stakeholders will lose enthusiasm for the DM program
> - However, rushing a comprehensive assessment in two weeks risks incomplete coverage and superficial ratings
> - The goal is **consensus view supported by evidence** -- this requires adequate time for interviews, artifact review, and reconciliation
>
> **Recommended approach:**
> - Conduct a first DMMA as a **pilot** on a manageable scope (e.g., a highly regulated function like financial reporting)
> - Apply lessons learned to address broader scope in subsequent phases
> - If executives insist on enterprise scope, reduce the **investigation depth** to a simple DMMA to establish a comparative baseline
> - Consider focusing on the most critical Knowledge Areas first
>
> **Risk of executives wanting to skip levels:**
> - Often executives want to aim higher than assessment recommendations
> - Targeting a higher maturity level has to be reflected in impact analysis -- there is a **cost to acceleration** that must be balanced against benefits

---

### Question 7 [application]

After completing a DMMA, results show the organization is at Level 1 (Ad Hoc) for Data Quality and Level 2 (Repeatable) for Data Governance. The executive team wants to jump directly to Level 4 (Managed) for both within one year. How should you respond?

> [!answer]- Show Answer
> This request conflicts with fundamental CMM principles and carries significant risk:
>
> **Why skipping levels is problematic:**
> - Maturity levels progress in a set order and **no level can be skipped** -- each level builds on capabilities established in the previous level
> - Moving from Level 1 to Level 4 in Data Quality would mean skipping the establishment of consistent tools and role definitions (Level 2) and the institutionalization of scalable processes and standards (Level 3)
> - Without these foundations, Level 4 capabilities (centralized governance, performance metrics, measurable improvements) cannot be sustained
>
> **Cost and risk implications:**
> - The DMBOK2 notes that targeting a higher level of maturity has to be reflected in the **impact analysis for recommendations** -- "there is a cost to this kind of acceleration, and costs must be balanced against benefits"
> - Attempting to skip levels often results in superficial compliance without genuine capability improvement
>
> **Recommended response:**
> - Develop a roadmap with **sequenced activities** that build maturity incrementally
> - Set realistic targets for each assessment period (e.g., reaching Level 2 for DQ and Level 3 for DG within the first year)
> - Use **short-term wins** at each level to demonstrate progress and maintain executive support
> - Re-assess periodically to validate improvement and adjust the roadmap
> - Frame the recommendation in terms of **business outcomes** -- explain what capabilities each level enables and what risks exist in jumping ahead

---

### Question 8 [application]

An organization completed a DMMA eighteen months ago and created a roadmap. No re-assessment has been conducted, and several key initiatives from the roadmap have stalled. What should the organization do?

> [!answer]- Show Answer
> The organization should conduct a **re-assessment** as part of the continuous improvement cycle. According to the DMBOK2:
>
> **Immediate actions:**
> 1. **Re-assess maturity** against the original baseline to identify what progress has been made, what has stalled, and what has regressed
> 2. Track trends relative to the initial baseline using the same framework and criteria
> 3. Develop new recommendations based on re-assessment findings
>
> **Why re-assessment is critical now:**
> - Re-assessment can **re-invigorate or refocus effort** -- measurable progress maintains commitment and enthusiasm
> - Stalled initiatives suggest the organization may have encountered one or more common risks: lack of organizational buy-in, lack of communication, narrow focus, or inaccessible staff
> - Changes to regulatory frameworks, internal/external policy, or technology innovations may have shifted priorities since the original assessment
>
> **Process governance:**
> - Ensure the DMMA lifecycle itself is governed -- the original assessment should have been followed by regular re-evaluations on a published schedule
> - An executive sponsor (ideally the CDO) should ensure improvements map to business objectives
> - Use the stalled initiatives as input to stakeholder communication about why the effort matters
>
> **Addressing root causes of stalled initiatives:**
> - Perform a risk analysis using the DMMA risk/mitigation framework
> - Evaluate whether the original roadmap was too ambitious or insufficiently tied to business priorities
> - Adjust the roadmap with more achievable short-term goals to rebuild momentum

---

### Question 9 [analysis]

Compare and contrast the CMMI-DMM and the EDM Council DCAM frameworks. Under what organizational circumstances would you recommend one over the other?

> [!answer]- Show Answer
> **CMMI-DMM:**
> - Structured around **6 data management areas**: DM Strategy, Data Governance, Data Quality, Platform and Architecture, Data Operations, Supporting Processes
> - Includes **sub-processes** within each area and accounts for relationships between DM areas
> - Addresses stakeholder alignment and the relationship between business processes and DQ Management
> - Developed by the **CMMI Institute** -- broadly applicable across industries
> - Follows the traditional CMM approach with well-defined maturity levels
>
> **EDM Council DCAM:**
> - Describes **37 capabilities and 115 sub-capabilities** associated with developing a sustainable DM program
> - Scoring focuses on **stakeholder engagement**, **formality of process**, and **existence of artifacts** demonstrating achievement
> - Result of a **membership-driven effort** within financial services to get consensus on DM best practices
> - Published by the **Enterprise Data Management Council** -- an industry advocacy organization for financial services
>
> **When to recommend each:**
>
> *CMMI-DMM is better suited when:*
> - The organization is in **any industry** (industry-agnostic)
> - The organization wants a traditional, well-structured maturity model with clear level progression
> - Focus is on the interrelationship between DM processes and business alignment
> - The organization wants a framework that maps well to the DAMA-DMBOK Knowledge Areas
>
> *DCAM is better suited when:*
> - The organization is in **financial services** or a similarly regulated industry
> - Focus is on demonstrating compliance through formal artifacts and evidence
> - The organization values detailed sub-capability decomposition (115 sub-capabilities provide granular assessment)
> - Stakeholder engagement and formality of process are primary evaluation criteria
> - The organization wants a framework developed by consensus among peer institutions in its industry

---

### Question 10 [analysis]

An organization's DMMA reveals that Data Architecture scores Level 4 (Managed) but Data Quality scores Level 1 (Ad Hoc), while Data Governance is at Level 2 (Repeatable). Analyze the implications of this uneven maturity profile and propose a strategic approach to address it.

> [!answer]- Show Answer
> **Implications of uneven maturity:**
>
> This profile reveals a significant and concerning gap between the organization's ability to *design* data solutions (Architecture at Level 4) and its ability to *ensure the quality and governance* of data flowing through those solutions.
>
> - **Data Architecture at Level 4** means standardized tools, centralized planning, performance metrics, and measurable quality in architectural practices -- the organization knows *how* to structure data
> - **Data Quality at Level 1** means quality issues are pervasive but unaddressed, with no formal tools or processes -- the data flowing through well-designed architecture may be unreliable
> - **Data Governance at Level 2** means some awareness and emerging role definitions, but insufficient policy and enforcement to close the gap
>
> This creates a **false sense of capability**: the architecture may look sophisticated, but without quality data and governance enforcement, the organization cannot trust its data for decision-making. The gap between Architecture (4) and Quality (1) represents the **greatest risk** to the organization.
>
> **Strategic approach:**
>
> 1. **Leverage Architecture strength**: Use the mature Architecture capability to support DQ improvement -- data models, data flows, and integration architecture provide the foundation for identifying where quality problems originate
>
> 2. **Prioritize Data Quality to Level 2-3**: Focus on:
>    - Introducing consistent DQ tools (Level 2 objective)
>    - Defining DQ roles and building awareness across the organization
>    - Establishing scalable DQ processes and standards (Level 3 objective)
>    - Using the DMMA visualization (desired vs. current rank) to communicate the risk gap to executives
>
> 3. **Advance Data Governance to Level 3**: Strengthen governance by:
>    - Institutionalizing DG policies that specifically address DQ requirements
>    - Leveraging the Architecture team's maturity as a model for governance practices
>    - Creating feedback loops between Architecture (which can identify DQ issues structurally) and DQ teams
>
> 4. **Use the re-assessment cycle**: Set targets for DQ to reach Level 3 and DG to reach Level 3 in the next assessment period, then pursue Level 4 alignment across all three areas
>
> 5. **Address root causes**: Investigate why Architecture advanced while Quality did not -- often this indicates a technology-focused culture that values system design but undervalues data content management. This cultural issue must be addressed through change management practices (see [[Change Management]]).

---

> [!summary]- Pattern Summary (click to view)
> **High-frequency topics**: Five maturity levels and their characteristics, sequential progression (no skipping), assessment criteria categories (Activity/Tools/Standards/People), localized vs. enterprise trade-offs, framework selection criteria, CMMI-DMM vs. DCAM vs. IBM vs. Stanford differentiators.
>
> **Common traps**: Thinking levels can be skipped; confusing Level 3 (standards set) with Level 4 (metrics and control); assuming enterprise assessment is always best; forgetting that the DMMA process itself requires governance; overlooking the role of re-assessment in continuous improvement.
>
> **Analysis patterns**: Expect questions comparing frameworks, interpreting uneven maturity profiles, advising on scope/approach trade-offs, and addressing executive expectations about acceleration. The DMMA's value is not just in the score -- it's in the roadmap, cultural education, and ongoing measurement cycle.
