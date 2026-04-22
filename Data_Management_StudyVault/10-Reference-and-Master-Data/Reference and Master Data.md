---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 10"
keywords:
  - reference data
  - master data
  - MDM
  - entity resolution
  - golden record
  - data sharing hub
  - identity management
  - trusted source
  - system of record
  - cross-reference
tags:
  - dmbok2
  - master-data
---

# Reference and Master Data
*Reading time: ~6 min*

## Overview Table (At a Glance)

| Aspect | Detail |
|---|---|
| **Definition** | Managing shared data to meet organizational goals, reduce risks of data redundancy, ensure higher quality, and reduce costs of data integration |
| **Goals** | (1) Enable sharing of information assets across business domains; (2) Provide authoritative source of reconciled, quality-assessed master and reference data; (3) Lower cost and complexity through standards, common models, and integration patterns |
| **Key Roles** | Data Stewards, Data Architects, Data Modelers, Data Quality Analysts, Data Integrators, Subject Matter Experts |
| **Governance Focus** | Stewardship of shared resources, controlled change processes, conditions-of-use agreements |
| **Key Metrics** | Data quality & compliance, data change activity, ingestion & consumption, SLA adherence, steward coverage, total cost of ownership, sharing volume & usage |

---

## Reference Data

- **Definition**: Any data used to characterize or classify other data, or to relate data to information external to an organization
- Simplest form: code + description pairs (e.g., country codes, status codes)
- Less volatile and smaller than Master Data sets; entity resolution is NOT part of RDM

### Reference Data Structures

- **Simple Lists**: Code-description pairs (e.g., ISO country codes: US = United States of America, GB = United Kingdom)
- **Cross-Reference Lists**: Map between different code sets representing the same concept at the same or different granularity (e.g., USPS State Code vs. FIPS Numeric Code vs. ISO State Code)
- **Taxonomies**: Hierarchical structures capturing information at different levels of specificity using recursive parent-child relationships (e.g., UNSPSC product classification, NAICS industry codes)
- **Ontologies**: Complex taxonomic structures used to manage website content; also a form of Metadata

### Reference Data Categories

- **Proprietary / Internal**: Created by the organization to support internal processes; often grows organically
- **Industry Reference Data**: Created and maintained by industry associations or government bodies (e.g., ICD codes for healthcare, NAICS for industry classification)
- **Geographic / Geo-statistical**: Census data, weather history, population density for market planning
- **Computational**: Time-stamped calculation data (e.g., foreign exchange rates); changes frequently; often purchased from third parties

### Reference Data Metadata

- Critical to maintain: formal name, internal name, data provider, provider source URI, latest version number/date, internal version number, reconciliation date, last update date

---

## Master Data

- **Definition**: Data about business entities (employees, customers, products, financial structures, assets, locations) that provide context for business transactions and analysis
- Master Data should represent the authoritative, most accurate data available about key business entities
- Common Master Data domains: **Parties** (customers, vendors, employees), **Products/Services**, **Financial Structures** (GL accounts, cost centers), **Locations** (addresses, GPS)

### Key Concepts

- **System of Record (SOR)**: Authoritative system where data is created/maintained through defined rules (e.g., ERP for sell-to customers)
- **System of Reference**: Authoritative system where data consumers obtain reliable data, even if it did not originate there (e.g., MDM application, DW)
- **Trusted Source**: Recognized as the "best version of the truth" based on automated rules and manual stewardship; also called Single View or 360-degree View
- **Golden Record**: The single record representing the most accurate data about an entity instance; term can be misleading as it implies 100% completeness

### Master Data Management (MDM)

- **Definition (Gartner)**: A technology-enabled discipline in which business and IT work together to ensure uniformity, accuracy, stewardship, semantic consistency, and accountability of shared Master Data assets
- MDM is a **discipline** (people + processes + technology), not just a product
- Primary challenge: **Entity Resolution** (identity management) -- discerning and managing associations between data from different systems

### MDM Key Processing Steps

1. **Data Model Management**: Establish clear, consistent logical definitions that overcome "system speak"
2. **Data Acquisition**: Evaluate and incorporate new data sources via repeatable processes including profiling and quality assessment
3. **Data Validation, Standardization, and Enrichment**: Reduce variation in format; reconcile values; add attributes (e.g., DUNS numbers) to improve resolution
4. **Entity Resolution**: Determine whether two references refer to the same real-world object
   - **Matching**: Candidate identification via deterministic algorithms (rule-based, predictable) or probabilistic algorithms (statistical, self-improving)
   - **False Positives**: Two different entities linked with one identifier
   - **False Negatives**: Same entity assigned multiple identifiers
5. **Data Sharing and Stewardship**: Resolve incorrectly matched records; improve algorithms over time

### Matching Workflows / Reconciliation Types

- **Duplicate Identification**: Identify merge opportunities without automatic action; stewards review case-by-case
- **Match-Link**: Cross-reference records to a master record without updating content; easier to implement and reverse
- **Match-Merge**: Match records and merge into a single reconciled record; complex but provides unified view

### Master Data ID Management

- **Global ID**: MDM-assigned unique identifier for reconciled records; generated by one authorized solution only
- **Cross-Reference (X-Ref)**: Relationship between source IDs and the Global ID; must maintain history for match rate metrics

### Master Data Domains

- **Party Master Data**: Individuals, organizations, roles (customers, employees, vendors); CRM systems; unique challenges with roles/relationships and mobile/social channels
- **Financial Master Data**: Business units, cost centers, GL accounts, budgets; typically hub is ERP
- **Legal Master Data**: Contracts, regulations; enables analysis across contracts for negotiation
- **Product Master Data**: PLM (lifecycle), PDM (engineering), ERP (SKUs), MES (manufacturing), CRM (marketing/sales)
- **Location Master Data**: Business party addresses, facility locations; distinction from location reference data (geopolitical, relatively static)

---

## Data Sharing Architecture

Three basic approaches for implementing a Master Data hub:

| Approach | Description | Pros | Cons |
|---|---|---|---|
| **Registry** | Index pointing to Master Data in various SORs | Easy to implement, few changes to SORs | Complex queries needed; business rules in multiple places |
| **Transaction Hub** | All Master Data exists in the hub; hub is the SOR | Better governance, consistent source | Costly to remove update functionality from existing SORs |
| **Consolidated** | Hybrid: SORs manage locally; hub consolidates for reference | Enterprise view, limited impact on SORs | Data replication, latency between hub and SORs |

---

## Reference Data Change Management

- Changes can be row-level, structural, to internal or external data sets, or creation of new sets
- Changes can be planned/scheduled or ad hoc
- Process: Receive Change Request -> Identify Stakeholders -> Identify Impact -> Decide -> Update and Communicate

---

## Exam/Test Patterns (Frequently Tested)

- Distinction between Reference Data and Master Data (volatility, size, entity resolution)
- MDM is a discipline, not just a tool/application
- Three data sharing hub architectures (Registry, Transaction Hub, Consolidated)
- Entity resolution: matching (deterministic vs. probabilistic), false positives vs. false negatives
- Golden Record vs. Trusted Source distinction
- System of Record vs. System of Reference
- Match-Link vs. Match-Merge workflows and their trade-offs
- Reference Data structures: lists, cross-references, taxonomies, ontologies
- Chisholm's six-layer data taxonomy (Metadata, Reference Data, enterprise structure data, transaction structure data, transaction activity data, transaction audit data)

---

## Related Notes

- [[Data Governance]] -- MDM/RDM require governance for stewardship and controlled change
- [[Data Quality]] -- MDM and RDM directly improve data quality; Master Data is critical by definition
- [[Data Architecture]] -- Data sharing hub architecture decisions; system of record identification
- [[Data Modeling and Design]] -- Logical/canonical models guide MDM integration
- [[Data Integration and Interoperability]] -- MDM is a form of data integration; ETL, hub-and-spoke patterns
- [[Metadata Management]] -- Reference Data requires Metadata (source, version, lineage)
- [[Data Warehousing and BI]] -- DW consumes Master Data; conformed dimensions rely on consistent master/reference data
- [[Data Security]] -- Data sharing agreements, access controls
