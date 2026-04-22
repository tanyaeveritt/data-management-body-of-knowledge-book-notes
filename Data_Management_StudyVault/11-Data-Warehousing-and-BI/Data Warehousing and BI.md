---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 11"
keywords:
  - data warehouse
  - business intelligence
  - dimensional modeling
  - Inmon
  - Kimball
  - OLAP
  - star schema
  - data mart
  - ETL
  - CDC
tags:
  - dmbok2
  - data-warehousing
---

# Data Warehousing and BI
*Reading time: ~7 min*

## Overview Table (At a Glance)

| Aspect | Detail |
|---|---|
| **Definition** | Planning, implementation, and control processes to provide decision support data and support knowledge workers engaged in reporting, query, and analysis |
| **Goals** | (1) Build and maintain the technical environment and processes to deliver integrated data for operational functions, compliance, and BI; (2) Support effective business analysis and decision-making |
| **Key Activities** | Understand requirements, define and maintain DW/BI architecture, develop DW and data marts, populate the DW, implement BI portfolio, maintain data products |
| **Key Roles** | Sponsors, Product Owners, Architects, Analysts, DW/BI Specialists, Project Management, Change Management |
| **Key Metrics** | Usage metrics, customer/user satisfaction, subject area coverage %, response/performance metrics |

---

## Business Intelligence (BI)

- **Dual meaning**: (1) A type of data analysis aimed at understanding organizational activities and opportunities; (2) A set of technologies supporting that analysis
- Evolution of decision support tools; includes querying, data mining, statistical analysis, reporting, scenario modeling, data visualization, dashboarding
- Primary driver for data warehousing; promises insight into products, services, and customers

---

## Data Warehouse (DW) Concepts

- **Data Warehouse**: Integrated decision support database + related software programs to collect, cleanse, transform, and store data from operational and external sources
- **Enterprise Data Warehouse (EDW)**: Centralized DW serving the entire organization; adheres to an enterprise data model
- **Data Warehousing**: The operational ETL processes that maintain DW data -- enforcing business rules and maintaining data relationships

---

## Two Primary Approaches to Data Warehousing

### Inmon -- Corporate Information Factory (CIF)

Inmon defines a DW as "a subject-oriented, integrated, time-variant, and non-volatile collection of data":

- **Subject-oriented**: Organized by major business entities, not by function/application
- **Integrated**: Unified and cohesive; consistent key structures, encoding, definitions, naming
- **Time-variant**: Stores data at set points in time; query results for a time period are reproducible
- **Non-volatile**: Records are not updated; new data is appended to existing data
- **Aggregate and detail**: Includes atomic-level transactions and summarized data
- **Historical**: Contains vast amounts of historical data

**CIF components**: Applications -> Staging Area -> Integration & Transformation -> ODS -> Data Warehouse -> Data Marts -> Operational Data Marts

### Kimball -- Dimensional Data Warehouse

Kimball defines a DW as "a copy of transaction data specifically structured for query and analysis":

- Uses **dimensional data model** (Star Schema) with **facts** (quantitative data) and **dimensions** (descriptive attributes)
- Multiple fact tables share **conformed dimensions** via a "bus" (integration mechanism)
- **DW Bus Matrix**: Shows intersection of business processes (facts) and data subject areas (dimensions); identifies conformed dimension candidates

**Components**: Operational Source Systems -> Data Staging Area -> Data Presentation Area (marts) -> Data Access Tools

### Data Vault

- Cleanses and standardizes during staging
- History stored in a normalized atomic structure with dimensional surrogate, primary, and alternate keys
- Retains history inside the vault; supports reloading facts when grain changes
- Can virtualize the presentation layer for agile delivery

---

## DW Architecture Components

- **Source Systems**: Operational systems (CRM, Accounting, HR) + external data, DaaS, web content, Big Data results
- **Data Integration**: ETL, data virtualization, data services layers (see [[Data Integration and Interoperability]])
- **Staging Area**: Intermediate data store for transformation, integration, and load preparation
- **Reference and Master Data Conformed Dimensions**: May be stored in separate repositories; DW feeds new Master Data and receives conformed dimensions
- **Central Warehouse (Atomic Layer)**: Stores all historical atomic data; uses surrogate keys, indices, CDC techniques
- **Operational Data Store (ODS)**: Supports lower latency/operational use; contains 30-90 days of volatile data; can audit or source a DW
- **Data Marts**: Subject-area subsets for analysis; often use dimensional modeling (denormalization); can aggregate for faster analysis
- **Cubes / OLAP**: Support multi-dimensional analysis; three types: ROLAP, MOLAP, HOLAP

---

## Types of Load Processing

### Historical Data
- Usually loaded once; different approaches for point-in-time snapshots vs. current state
- Inmon: single DW layer stores all atomic data; Kimball: departmental data marts store history; Data Vault: normalized atomic structure

### Change Data Capture (CDC) Techniques

| Method | Complexity | Speed | Overlap | Deletes Tracked |
|---|---|---|---|---|
| Time-stamped Delta | Low | Fast | Yes | No |
| Log Table Delta | Medium | Nominal | Yes | Yes |
| Database Transaction Log | High | Nominal | No | Yes |
| Message Delta | Extreme | Slow | No | Yes |
| Full Load | Simple | Slow | Yes | Yes |

### Near-Real-Time / Real-Time Processing

- **Trickle Feeds** (source accumulation): Frequent batch loads (e.g., hourly, every 5 minutes)
- **Messaging** (bus accumulation): Real-time small packets published to a bus; source and target systems independent
- **Streaming** (target accumulation): Target collects data as received into a buffer/queue; processes in order

---

## BI Tools Types

- **Operational Reporting**: Business users generating reports from transactional systems or DW; ad-hoc query tools; production reports
- **Business Performance Management (BPM)**: Formal assessment of metrics aligned with organizational goals; scorecards, dashboards; budgeting, planning, financial consolidation
- **Descriptive / Self-Service Analytics**: BI to front lines; operational analytics guiding near-real-time decisions
- **OLAP (Online Analytical Processing)**: Multi-dimensional analysis using cubes
  - Operations: **Slice** (subset on one dimension), **Dice** (slice on 2+ dimensions), **Drill down/up**, **Roll-up** (aggregate), **Pivot** (change orientation)
  - Types: **ROLAP** (relational), **MOLAP** (multi-dimensional), **HOLAP** (hybrid)

---

## DW/BI Governance

- Critical for regulated industries needing compliance-centric reporting
- Must be business-driven and aligned with risk management
- Key elements: data quality feedback loop, end-to-end Metadata, verifiable data lineage
- **Release Management**: Incremental development; quarterly/monthly releases
- **Service Level Agreements**: Response time, data retention, and availability requirements
- **Reporting Strategy**: Security access, user community types, tool matching, visualization, timeliness/performance trade-offs

---

## Implementation Guidelines

- **Guiding Principles**: Focus on business goals; start with the end in mind; think globally/act locally; summarize and optimize last; promote transparency and self-service; build Metadata with the warehouse; collaborate; one size does not fit all
- **Readiness Assessment**: Define data sensitivity/security, perform tool selection, secure resources, create ingestion process
- **Release Roadmap**: Incremental builds using DW bus matrix; each increment modifies or adds capabilities aligned with business units
- **Configuration Management**: Automates development, testing, transport to production; brands model by release at database level
- **Critical Success Factors**: Business sponsorship, clear goals/scope, committed business resources, business readiness for incremental delivery, vision alignment between IT strategy and business

---

## Exam/Test Patterns (Frequently Tested)

- Inmon (CIF) vs. Kimball (Dimensional): definitions, key differences, components
- Inmon's four DW characteristics: subject-oriented, integrated, time-variant, non-volatile
- Star Schema: facts (quantitative) + dimensions (descriptive); conformed dimensions via bus
- DW Bus Matrix: business processes x subject areas; identifies conformed dimension candidates
- ODS vs. DW: latency, volatility, history depth
- CDC techniques and their trade-offs (complexity, speed, overlap, delete tracking)
- Three near-real-time approaches: trickle feeds, messaging, streaming
- OLAP operations: slice, dice, drill down/up, roll-up, pivot
- ROLAP vs. MOLAP vs. HOLAP
- DW guiding principle: "Summarize and optimize last, not first" (build on atomic data)

---

## Related Notes

- [[Data Integration and Interoperability]] -- ETL/ELT processes, data virtualization, data movement
- [[Data Architecture]] -- Enterprise data models, DW placement in overall architecture
- [[Data Modeling and Design]] -- Star schema, dimensional modeling, entity-relationship models
- [[Reference and Master Data]] -- Conformed dimensions depend on consistent master/reference data
- [[Metadata Management]] -- Build Metadata with the warehouse; data dictionary; lineage
- [[Data Quality]] -- DW often reveals poor quality in source systems; data quality feedback loop
- [[Data Governance]] -- DW governance, release management, SLAs, reporting strategy
- [[Data Security]] -- Masking/obfuscating sensitive data in warehouse
