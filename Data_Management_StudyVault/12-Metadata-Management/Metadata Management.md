---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 12"
keywords:
  - metadata
  - metamodel
  - business glossary
  - data lineage
  - metadata architecture
  - metadata repository
  - technical metadata
  - business metadata
  - operational metadata
tags:
  - dmbok2
  - metadata
---

# Metadata Management
*Reading time: ~7 min*

## Overview Table (At a Glance)

| Aspect | Detail |
|---|---|
| **Definition** | Planning, implementation, and control activities to enable access to high quality, integrated Metadata |
| **Goals** | (1) Provide organizational understanding of business terms and usage; (2) Collect and integrate Metadata from diverse sources; (3) Provide a standard way to access Metadata; (4) Ensure Metadata quality and security |
| **Key Activities** | Define Metadata strategy, understand requirements, define architecture, create MetaModel, apply standards, manage stores, create/maintain Metadata, integrate, distribute/deliver, query/report/analyze |
| **Key Roles** | Data Stewards, Data Architects, Data Modelers, Business Analysts, System Analysts, Project Managers |
| **Key Metrics** | Metadata repository completeness, Metadata management maturity (CMM-DMM), steward representation, Metadata usage, business glossary activity, documentation quality, repository availability |

---

## Why Metadata Matters

- Metadata includes information about technical and business processes, data rules and constraints, and logical and physical data structures
- **Library analogy**: An organization without Metadata is like a library without a card catalog -- finding a specific book would be difficult or impossible
- Without reliable Metadata, an organization does not know what data it has, what it represents, where it originates, how it moves, who has access, or what quality means
- To be data-driven, an organization must be **Metadata-driven**

---

## Three Types of Metadata

### Business Metadata
- Focuses on content and condition of data; includes data governance details
- Examples: definitions/descriptions of data sets, tables, columns; business rules, transformation rules, calculations; data models; data quality rules and results; update schedules; data provenance and lineage; data standards; system of record designations; valid value constraints; stakeholder contacts (owners, stewards); security/privacy level; known issues; data usage notes

### Technical Metadata
- Information about technical details of data, systems that store it, and processes that move it
- Examples: physical table/column names; column properties; database object properties; access permissions; CRUD rules; physical data models; ETL job details; file format schemas; source-to-target mappings; data lineage documentation; program/application names; update cycle schedules; recovery/backup rules; data access rights/groups/roles

### Operational Metadata
- Details of processing and accessing data
- Examples: batch job execution logs; extract history and results; schedule anomalies; audit/balance/control measurement results; error logs; query access patterns and frequency; patches and version maintenance; backup/retention/disaster recovery provisions; SLA requirements; volumetric/usage patterns; archiving/retention rules; purge criteria; data sharing rules; technical contacts

### Library Science Categories (Alternative)
- **Descriptive** (title, author, subject): Enables identification and retrieval
- **Structural** (pages, chapters): Relationships within and among resources
- **Administrative** (versions, archive dates): Manages resources over lifecycle

---

## ISO/IEC 11179 Metadata Registry Standard

- Framework for defining a Metadata registry to enable Metadata-driven data exchange based on exact definitions
- Parts include: Framework for Generation and Standardization of Data Elements; Basic Attributes; Rules and Guidelines for Formulation of Data Definitions; Naming and Identification Principles; Registration of Data Elements

---

## Sources of Metadata

- **Application Metadata Repositories**: Built into modeling tools, BI tools, and applications
- **Business Glossary**: Documents business concepts, terminology, definitions, and relationships; serves three audiences (business users, Data Stewards, technical users)
- **BI Tools**: Produce Metadata on classes, objects, derived items, filters, reports, layout, distribution
- **Configuration Management Tools (CMDB)**: IT asset Metadata, relationships, contractual details
- **Data Dictionaries**: Structure and contents of data sets; embedded in database tools; can describe business terminology
- **Data Integration Tools**: Document lineage as data moves between systems; provide APIs for extraction
- **Database Management and System Catalogs**: Content, sizing, versions, deployment, uptime, availability
- **Data Mapping Management Tools**: Transform requirements into mapping specifications; version control
- **Data Quality Tools**: Validation rules, quality scores, profile patterns
- **Directories and Catalogs**: Information about systems, sources, and locations of data
- **Event Messaging Tools**: Movement logic, processing statistics
- **Modeling Tools and Repositories**: Conceptual, logical, physical models; entities, attributes, keys, constraints
- **Reference Data Repositories**: Domain values, descriptions, contextual use, relationships across domains
- **Service Registries**: Service version, location, availability, deployment, ports, connection details (SOA)

---

## Business Glossary

- Documents and stores business concepts, terminology, definitions, and relationships
- Three core audiences: **Business users** (understand terminology), **Data Stewards** (manage lifecycle of terms), **Technical users** (design/development decisions, impact analysis)
- Key attributes: term name, definition, acronym, synonyms, responsible business unit, person identifying, date updated, taxonomy association, conflicting definitions, algorithms, lineage, authoritative source
- Should have governance processes: candidate -> approved -> published -> replaced/retired
- Simplicity of search is critical; but robust content is the most important characteristic

---

## Types of Metadata Architecture

### Centralized
- Single Metadata repository containing copies from all sources
- **Pros**: High availability (independent of sources), quick retrieval, resolved structures, extracted Metadata can be enhanced
- **Cons**: Complex sync processes, costly maintenance, may require custom modules

### Distributed
- Single access point but no persistent repository; retrieves Metadata from sources in real time
- **Pros**: Always current, distributed queries, simpler development, reduced batch processing
- **Cons**: No user-defined Metadata support, dependent on source system availability, no global search

### Hybrid
- Combines centralized and distributed; central repository stores user-added, critical standardized, and manual-source Metadata; delegates to sources for detailed Metadata
- **Pros**: Near-real-time retrieval plus enhanced Metadata; lower manual IT effort; global search possible
- **Cons**: Source system availability still a limitation; overhead for linking results

### Bi-Directional
- Allows Metadata to change in any part of the architecture with feedback coordinated back to sources
- **Challenges**: Must contain latest version and manage changes to the source; trapping changes systematically; additional interfaces

---

## Data Lineage and Impact Analysis

- Traces how data is transformed as it moves between systems
- **As Implemented Lineage**: Current lineage based on programming code
- **As Designed Lineage**: Lineage described in mapping specification documents
- **Stitching**: Process of connecting lineage pieces from various tools into a holistic visualization
- Two focus strategies:
  - **Business focus**: Start from target locations, trace back to sources for specific data elements
  - **Technical focus**: Start at source systems, identify all consumers, repeat for each layer

---

## Metadata for Big Data Ingest

- Metadata tags should be applied upon ingestion to identify data content for later access in the data lake
- Ingestion engines can profile data to identify domains, relationships, and quality issues
- Tags can identify sensitive or private data (PII) on ingestion
- Data scientists may add confidence scores, textual identifiers, and behavior cluster codes

---

## Exam/Test Patterns (Frequently Tested)

- Three types of Metadata: business, technical, operational -- with examples of each
- Library analogy: organization without Metadata = library without card catalog
- Business glossary: three audiences, governance lifecycle (candidate -> approved -> published -> retired)
- Four Metadata architecture types: centralized, distributed, hybrid, bi-directional -- trade-offs
- Data lineage: "As Implemented" vs. "As Designed"; stitching process
- Business focus (target-to-source) vs. technical focus (source-to-consumers) lineage strategies
- MetaModel: a data model for the Metadata repository itself
- ISO/IEC 11179: Metadata Registry Standard for data exchange based on exact definitions
- Key Metadata sources: business glossary, data dictionaries, modeling tools, data integration tools, CMDB, service registries
- Metadata for Big Data: tag on ingest, profile during ingest, identify PII

---

## Related Notes

- [[Data Governance]] -- Metadata is critical to governance; governance processes depend on reliable Metadata
- [[Data Quality]] -- Metadata defines expectations; DQ rules are Metadata; DQ results stored as Metadata
- [[Data Warehousing and BI]] -- Build Metadata with the warehouse; data dictionary; lineage for DW
- [[Data Architecture]] -- Metadata architecture as part of overall enterprise architecture
- [[Data Modeling and Design]] -- Models are key Metadata sources; logical model captures definitions
- [[Data Integration and Interoperability]] -- Integration tools document lineage; source-to-target mapping is Metadata
- [[Reference and Master Data]] -- Reference Data repositories are Metadata sources; RDM needs Metadata about versions and providers
- [[Data Security]] -- Some Metadata must be protected because it reveals existence of sensitive data
