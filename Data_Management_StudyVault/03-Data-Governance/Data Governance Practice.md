---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 3
keywords: practice, data governance, stewardship, operating model, DGC, policies
---

# Data Governance Practice (10 questions)

#practice #data-governance

## Related Concepts
- [[Data Governance]]
- [[Data Management]]
- [[Data Handling Ethics]]

> [!hint]- Key Patterns (click to view)
> | Keyword | Answer |
> |---------|--------|
> | DG vs DM | DG = **oversight**; DM = **execution** |
> | Three operating models | **Centralized, Replicated, Federated** |
> | DG program must be | **Sustainable, Embedded, Measured** |
> | Most common DG driver | **Regulatory compliance** |
> | Highest DG body | **DG Steering Committee** |
> | Data Owner = | Business steward with **approval authority** |
> | DG three functions | **Legislative, Judicial, Executive** |

---

## Question 1 - DG vs DM [recall]
> What is the fundamental difference between Data Governance and Data Management?

> [!answer]- Show Answer
> Data Governance is **oversight** -- ensuring data is managed properly according to policies and best practices. Data Management is **execution** -- managing data to achieve organizational goals. This represents an inherent **separation of duty**, analogous to how an auditor controls financial processes but does not actually execute financial management.

---

## Question 2 - Operating Models [recall]
> Describe the three Data Governance operating model types.

> [!answer]- Show Answer
> (1) **Centralized**: One DG organization oversees all activities in all subject areas. (2) **Replicated**: The same DG operating model and standards are adopted independently by each business unit. (3) **Federated**: One DG organization coordinates with multiple business units to maintain consistent definitions and standards. The choice depends on organizational structure, culture, and the level of coordination needed.

---

## Question 3 - DG Program Characteristics [recall]
> What three characteristics must a Data Governance program exhibit to achieve its goals?

> [!answer]- Show Answer
> (1) **Sustainable** -- DG is not a project with a defined end; it is an ongoing process requiring organizational commitment and business leadership. (2) **Embedded** -- DG activities must be incorporated into development methods, analytics, MDM, and risk management, not treated as an add-on. (3) **Measured** -- DG must demonstrate positive financial impact, which requires understanding the starting point and planning for measurable improvement.

---

## Question 4 - DG Bodies [recall]
> Name the five typical Data Governance committees/bodies and describe the role of the highest authority body.

> [!answer]- Show Answer
> The five bodies are: (1) **DG Steering Committee** (highest authority), (2) **Data Governance Council (DGC)**, (3) **Data Governance Office (DGO)**, (4) **Data Stewardship Teams**, (5) **Local DG Committee**. The DG Steering Committee is the primary and highest authority, consisting of cross-functional senior executives. It is responsible for oversight, support, and **funding** of DG activities, and releases funding as recommended by the DGC and CDO.

---

## Question 5 - Types of Data Stewards [recall]
> What is the difference between a Data Owner and a Business Data Steward?

> [!answer]- Show Answer
> A **Business Data Steward** is a business professional, usually a recognized subject matter expert, who is accountable for a subset of data and works with stakeholders to define and control data. A **Data Owner** is a Business Data Steward who additionally has **approval authority** for decisions about data within their domain. In other words, all Data Owners are Business Data Stewards, but not all Business Data Stewards have the approval authority that defines a Data Owner.

---

## Question 6 - Governance Functions [recall]
> DMBOK2 compares DG to political governance. What three types of governance functions does it identify?

> [!answer]- Show Answer
> (1) **Legislative** functions -- defining policies, standards, and the Enterprise Data Architecture. (2) **Judicial** functions -- issue management and escalation. (3) **Executive** functions -- protecting and serving, administrative responsibilities. Most organizations adopt a representative form of DG so all stakeholders can be heard, similar to representative political governance.

---

## Question 7 - Implementing DG [application]
> A financial services company wants to implement Data Governance primarily due to regulatory pressure. According to DMBOK2, what foundational activities should be prioritized in the early stages?

> [!answer]- Show Answer
> Prioritized early-stage activities include: (1) **Defining DG procedures** required to meet high-priority regulatory goals; (2) **Establishing a Business Glossary** and documenting terminology and standards; (3) **Coordinating with Enterprise Architecture and Data Architecture** for better understanding of data and systems; (4) **Assigning financial value to data assets** to enable better decision-making. Additionally, the DG should monitor and ensure regulatory compliance by evaluating what constitutes compliance, when it is required, how it is demonstrated, and the risk/penalty for non-compliance. Regulatory compliance is often the **initial reason** for implementing DG.

---

## Question 8 - Change Management [application]
> A DG program is experiencing resistance from business units. Using the ADKAR model referenced in DMBOK2, how would you structure a change management approach?

> [!answer]- Show Answer
> The ADKAR model measures change management in five areas: (1) **Awareness** -- educate employees about why data governance is needed and its business benefits; (2) **Desire** -- build willingness to participate by aligning DG with business value and career incentives; (3) **Knowledge** -- provide training on how to change behaviors, DG procedures, and stewardship practices; (4) **Ability** -- ensure people can implement new skills through tools, support, and practice; (5) **Reinforcement** -- sustain change through realigned KPIs, incentives for cross-functional cooperation, monitoring, and feedback loops. Communications promoting the value of data assets and eliciting stakeholder feedback are vital throughout.

---

## Question 9 - DG vs IT Governance [analysis]
> Why does DMBOK2 distinguish Data Governance from IT Governance? What risks arise when they are conflated?

> [!answer]- Show Answer
> IT Governance focuses on IT **investments, application portfolio, and project portfolio** -- hardware, software, and technical architecture, often guided by the COBIT framework. Data Governance focuses exclusively on **management of data assets** and data as an asset. When conflated, organizations risk: (1) Data decisions being driven by **technology temptation** rather than business strategy; (2) Data being treated as a by-product of IT systems rather than a strategic asset; (3) Critical data management concerns like quality, ethics, and stewardship being subordinated to technical architecture decisions; (4) Some critical topics (like Sarbanes-Oxley) that span corporate, IT, and data governance may fall through the cracks.

---

## Question 10 - Data Asset Valuation [analysis]
> DMBOK2 describes Generally Accepted Information Principles adapted from GAAP. Explain how the Liability Principle and the Going Concern Principle apply to data governance.

> [!answer]- Show Answer
> The **Liability Principle** states there is a financial liability connected to data based on regulatory and ethical misuse or mismanagement. For DG, this means governance programs must account for and mitigate the financial risks of data breaches, non-compliance fines, and reputational damage. The **Going Concern Principle** states that data is critical to successful, ongoing business operations and should not be viewed as temporary means or a mere by-product. For DG, this reinforces that data governance must be **sustainable** -- it is an ongoing program, not a one-time project, because the data it governs is essential to continuous business operations. Together, these principles justify sustained DG investment and executive sponsorship.

---

> [!summary]- Pattern Summary (click to view)
> | Keyword | Answer |
> |---------|--------|
> | DG = oversight, DM = | **execution** |
> | Three operating models | **Centralized, Replicated, Federated** |
> | DG must be | **Sustainable, Embedded, Measured** |
> | DG highest body | **DG Steering Committee** |
> | Data Owner distinction | **Approval authority** for data decisions |
> | Three governance functions | **Legislative, Judicial, Executive** |
> | Most common DG driver | **Regulatory compliance** |
> | ADKAR | **Awareness, Desire, Knowledge, Ability, Reinforcement** |
> | DG vs IT Governance | DG = data assets; IT Gov = hardware/software/COBIT |
> | Going Concern Principle | Data is **critical to ongoing operations**, not temporary |
