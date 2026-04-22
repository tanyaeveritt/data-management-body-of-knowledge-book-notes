---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 1
keywords: data management, DAMA wheel, data lifecycle, data strategy, data principles, DMBOK framework
---

# Data Management (Importance: ★★★)
*Reading time: ~5 min*

#dmbok2 #data-management

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Development, execution, and supervision of plans, policies, programs to deliver, control, protect, and enhance data value |
| Primary Driver | Enable organizations to get value from data assets |
| DAMA Wheel | 11 Knowledge Areas with Data Governance at the center |
| Data Lifecycle | Create/Obtain -> Store/Maintain -> Use/Enhance -> Dispose |
| Key Frameworks | Strategic Alignment Model, Amsterdam Information Model, DAMA Wheel, Aiken Pyramid |
| CDO Role | Leads data management initiatives, enables cultural change |

## Data as an Organizational Asset
Data is an **economic resource** that can be owned or controlled and holds or produces value. Unlike physical assets, data is **not consumed when used**, can be used by multiple people simultaneously, and is easy to copy but hard to reproduce if lost.
- Organizations increasingly identify as **data-driven**
- Data monetization is becoming increasingly common
- Data is unique to each organization -- customer lists, product inventories, claim history are irreplaceable
- Data valuation categories: cost of obtaining, cost of replacing, impact if missing, risk mitigation cost, competitor value

## Data Management Principles
Core principles that guide data management practice:
- **Data is an asset with unique properties** -- not consumed when used, durable, easy to copy
- **Value should be expressed in economic terms** -- no standards yet, but organizations must develop consistent quantification
- **Managing data means managing quality** -- ensuring fitness for purpose
- **It takes Metadata to manage data** -- definitions, origin, classification, lineage
- **It takes planning to manage data** -- architectural and process perspective required
- **Cross-functional** -- requires both technical and business skills
- **Enterprise perspective** -- must be applied across verticals
- **Lifecycle management** -- data has a lifecycle; different types have different characteristics
- **Risk management** -- data can be lost, stolen, or misused
- **Leadership commitment** -- requires vision, coordination, collaboration

## Data Management Challenges
Key challenges include:
- Data differs from other assets (intangible, durable, non-consumable)
- **Data valuation** is contextual and temporal
- **Data quality** -- IBM estimated $3.1 Trillion cost of poor quality data in the US (2016)
- Planning requires balancing long-term and short-term goals
- **Metadata management** is often neglected
- Cross-functional coordination across organizational silos
- Establishing an enterprise perspective vs. departmental silos
- Managing the **data lifecycle** and lineage
- Different data types (transactional, Reference Data, Master Data, Metadata) have different requirements
- Balancing technology temptation with business-driven decisions

## The Data Lifecycle
Data lifecycle activities: **Create/Obtain -> Store/Maintain -> Use/Enhance -> Archive/Purge**
- Creation and usage are the **most critical points**
- Data quality must be managed **throughout** the lifecycle
- Metadata quality must also be managed throughout
- Data security must be managed throughout
- Focus on the most critical data; minimize **data ROT** (Redundant, Obsolete, Trivial)
- Data lineage = the pathway from origin to point of usage

## DAMA-DMBOK Framework
Three visuals depict the framework:
- **DAMA Wheel** (Figure 5): Data Governance at center, 10 Knowledge Areas around it
- **Environmental Factors Hexagon** (Figure 6): People, Process, Technology with Goals & Principles at center
- **Knowledge Area Context Diagrams** (Figure 7): SIPOC-based (Suppliers, Inputs, Process, Outputs, Consumers)

Activities classified as: **(P)** Planning, **(D)** Development, **(C)** Control, **(O)** Operations

## The 11 Knowledge Areas
1. **Data Governance** -- direction and oversight (Ch 3)
2. **Data Architecture** -- blueprint for managing data assets (Ch 4)
3. **Data Modeling and Design** -- discovering and representing data requirements (Ch 5)
4. **Data Storage and Operations** -- stored data lifecycle support (Ch 6)
5. **Data Security** -- privacy, confidentiality, access control (Ch 7)
6. **Data Integration and Interoperability** -- movement and consolidation (Ch 8)
7. **Document and Content Management** -- unstructured media lifecycle (Ch 9)
8. **Reference and Master Data** -- core shared data reconciliation (Ch 10)
9. **Data Warehousing and BI** -- decision support data management (Ch 11)
10. **Metadata Management** -- access to integrated Metadata (Ch 12)
11. **Data Quality** -- measuring and improving fitness for use (Ch 13)

## Data Management Strategy
Components include:
- Compelling **vision** for data management
- Summary **business case** with examples
- Guiding **principles**, values, management perspectives
- Mission and **long-term directional goals**
- **SMART objectives** (12-24 months)
- Roles, organizations, responsibilities, decision rights
- Prioritized **program of work** with scope boundaries
- **Implementation roadmap** with projects and action items

Deliverables: Data Management Charter, Scope Statement, Implementation Roadmap.

## Frameworks Beyond the DAMA Wheel
- **Strategic Alignment Model** (Henderson & Venkatraman): Business strategy <-> IT strategy, Operations <-> Information systems
- **Amsterdam Information Model** (9-cell): Strategy / Tactics / Operations x Business / Information / IT
- **Aiken Pyramid**: Phase 1 (app + DB) -> Phase 2 (DQ, Metadata, Architecture) -> Phase 3 (Governance, MDM, DW/BI) -> Phase 4 (Analytics)
- **Geuens Framework**: BI/Analytics depend on MDM/DW, which depend on systems, which depend on DQ/Design/Interoperability, all on governance foundation

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| "Data is not consumed when used" | **Unique property** that distinguishes data from physical/financial assets |
| "DAMA Wheel center" | **Data Governance** is at the center |
| Context diagram categories (P, D, C, O) | **Plan, Develop, Control, Operate** |
| "$3.1 Trillion" | IBM's estimate of **cost of poor quality data** in US (2016) |
| "Data ROT" | **Redundant, Obsolete, Trivial** data |
| CDO role | Leads data management, enables **cultural change**, business-driven |
| Environmental Factors Hexagon center | **Goals & Principles** |
| Data lifecycle critical points | **Creation and usage** |
| SMART objectives timeframe | **12-24 months** |
| Aiken Pyramid Phase 3 | **Governance** enables MDM, DW/BI, strategic initiatives |

## Related Notes
- [[Data Handling Ethics]]
- [[Data Governance]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Data Quality]]
- [[Metadata Management]]
- [[Data Storage and Operations]]
- [[Data Security]]
