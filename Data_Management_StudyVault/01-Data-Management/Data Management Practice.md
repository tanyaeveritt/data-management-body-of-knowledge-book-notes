---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 1
keywords: practice, data management, DAMA wheel, data lifecycle, data strategy
---

# Data Management Practice (10 questions)

#practice #data-management

## Related Concepts
- [[Data Management]]
- [[Data Governance]]
- [[Data Architecture]]

> [!hint]- Key Patterns (click to view)
> | Keyword | Answer |
> |---------|--------|
> | DAMA Wheel center | **Data Governance** |
> | Context diagram PDCO | **Plan, Develop, Control, Operate** |
> | Data ROT | **Redundant, Obsolete, Trivial** |
> | Data lifecycle critical points | **Creation and usage** |
> | Environmental Factors Hexagon center | **Goals & Principles** |
> | Cost of poor quality data (US, 2016) | **$3.1 Trillion** (IBM estimate) |
> | CDO primary role | **Lead data management, enable cultural change** |

---

## Question 1 - DAMA Wheel Center [recall]
> What Knowledge Area sits at the center of the DAMA Wheel and why?

> [!answer]- Show Answer
> **Data Governance** sits at the center of the DAMA Wheel because governance is required for consistency within and balance between all the other data management functions. It provides direction and oversight for all data management activities.

---

## Question 2 - Context Diagram Categories [recall]
> What are the four activity classifications used in DAMA Knowledge Area Context Diagrams?

> [!answer]- Show Answer
> The four classifications are **(P) Planning** -- setting strategic/tactical course; **(D) Development** -- organized around SDLC; **(C) Control** -- ensuring ongoing quality, integrity, reliability, security; **(O) Operations** -- supporting use, maintenance, and enhancement.

---

## Question 3 - Data vs. Physical Assets [recall]
> Name three properties that make data unique compared to physical or financial assets.

> [!answer]- Show Answer
> (1) Data is **not consumed** when used -- it can be used simultaneously by multiple people. (2) Data is **easy to copy and transport** but not easy to reproduce if lost. (3) Data is **not tangible** yet durable -- it does not wear out, though its value may change over time. Additional: it can be stolen without being gone, and many uses of data beget more data.

---

## Question 4 - Data Lifecycle Focus [recall]
> What are the most critical points in the data lifecycle according to DMBOK2?

> [!answer]- Show Answer
> **Creation (or obtaining) and usage** are the most critical points. Data management must be executed with an understanding of how data is produced and how it is used. It costs money to produce data, and data is valuable only when it is consumed or applied.

---

## Question 5 - Cost of Poor Quality [recall]
> What was IBM's estimated cost of poor quality data in the US in 2016, and what percentage of revenue do experts estimate organizations spend on DQ issues?

> [!answer]- Show Answer
> IBM estimated the cost at **$3.1 Trillion**. Experts think organizations spend between **10-30% of revenue** handling data quality issues. Costs include scrap/rework, workarounds, organizational conflict, customer dissatisfaction, compliance fines, and reputational damage.

---

## Question 6 - Data ROT [recall]
> What does the acronym ROT stand for in data management, and why is it significant?

> [!answer]- Show Answer
> ROT stands for **Redundant, Obsolete, Trivial** data. It is significant because organizations produce vast amounts of data that is never actually used. Lifecycle management requires focusing on the most critical data and minimizing ROT to effectively manage resources and derive value.

---

## Question 7 - Strategy Components [application]
> A new CDO is tasked with creating a data management strategy. According to DMBOK2, what key components should this strategy include?

> [!answer]- Show Answer
> The strategy should include: (1) A compelling **vision** for data management; (2) A summary **business case** with examples; (3) Guiding **principles, values, and management perspectives**; (4) Mission and **long-term directional goals**; (5) **SMART objectives** for 12-24 months; (6) Descriptions of **roles, organizations, and decision rights**; (7) Descriptions of **program components and initiatives**; (8) A prioritized **program of work** with scope boundaries; (9) A draft **implementation roadmap** with projects. Deliverables include a Data Management Charter, Scope Statement, and Implementation Roadmap.

---

## Question 8 - Aiken Pyramid [application]
> An organization just purchased an ERP system with database capabilities. According to Aiken's Pyramid framework, what phases will they likely progress through to mature their data management?

> [!answer]- Show Answer
> **Phase 1**: The purchased application provides a starting point for data modeling/design, storage, and security, requiring work on integration and interoperability. **Phase 2**: Challenges with data quality emerge, requiring reliable Metadata and consistent Data Architecture. **Phase 3**: Disciplined DQ, Metadata, and architecture practices require **Data Governance** for structural support, enabling MDM, DW/BI, and strategic initiatives. **Phase 4**: The organization leverages well-managed data and advances its **analytics** capabilities (the "golden pyramid").

---

## Question 9 - Framework Comparison [analysis]
> Compare the Strategic Alignment Model and the Amsterdam Information Model. How do they differ in their perspective on the relationship between business and IT?

> [!answer]- Show Answer
> The **Strategic Alignment Model** (Henderson & Venkatraman) focuses on four domains: business strategy, IT strategy, organizational infrastructure, and IT infrastructure, with Data/Information at the center. It emphasizes strategic fit and functional integration. The **Amsterdam Information Model** (9-cell) adds a **middle layer** focused on structure, tactics, planning, and architecture. It also explicitly recognizes the necessity of **information communication** (expressed as information governance and data quality). While SAM abstracts the relationship into strategy and operations, AIM provides a more granular 3x3 matrix (Strategy/Tactics/Operations x Business/Information/IT) that acknowledges the tactical planning layer between strategy and operations.

---

## Question 10 - Enterprise Perspective Challenge [analysis]
> Why does DMBOK2 argue that managing data requires an enterprise perspective, and what specific challenges make this difficult to achieve?

> [!answer]- Show Answer
> Data is a **horizontal** asset that moves across organizational verticals (sales, marketing, operations). Managing it only locally results in: (1) **Disparate representations** -- different departments may represent the same concept differently (e.g., "customer"); (2) Data treated as a **by-product** of operational processes rather than planned strategically; (3) **Integration challenges** -- subtle differences in representational choices create obstacles; (4) Stakeholders still assume data should be **coherent** across the organization. Data governance has become increasingly important specifically to help organizations make decisions about data across verticals, resolving conflicts between local optimization and enterprise-level consistency.

---

> [!summary]- Pattern Summary (click to view)
> | Keyword | Answer |
> |---------|--------|
> | DAMA Wheel center | **Data Governance** |
> | PDCO categories | **Plan, Develop, Control, Operate** |
> | Data unique property | **Not consumed when used** |
> | Lifecycle critical points | **Creation and usage** |
> | Cost of poor DQ (US) | **$3.1 Trillion** |
> | Data ROT | **Redundant, Obsolete, Trivial** |
> | Strategy objectives timeframe | **12-24 months (SMART)** |
> | Aiken Phase 3 enabler | **Data Governance** |
> | Amsterdam Info Model addition | **Middle layer (tactics/architecture)** |
> | Enterprise perspective driver | **Data is horizontal across verticals** |
