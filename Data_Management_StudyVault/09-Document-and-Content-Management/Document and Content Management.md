---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 9
keywords: document management, content management, records management, e-discovery, taxonomy, controlled vocabulary, ECM, GARP, ontology, unstructured data
---

# Document and Content Management (Importance: ★★)
*Reading time: ~9 min*

#dmbok2 #content-management

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Planning, implementation, and control activities for lifecycle management of data and information found in any form or medium |
| Goals | 1) Comply with legal obligations and customer expectations for records management 2) Ensure effective storage, retrieval, and use of documents and content 3) Ensure integration between structured and unstructured content |
| Primary Business Drivers | **Regulatory compliance**, responding to litigation and **e-discovery** requests, **business continuity**, and operational efficiency |
| Key Fact | Estimated 80% of all stored data is maintained **outside relational databases** (unstructured) |
| Key Framework | **ARMA GARP** (Generally Accepted Recordkeeping Principles) |
| Inputs | Business strategy, IT strategy, legal retention requirements, text/electronic/paper files, social media streams |
| Deliverables | Content and records management strategy, policies and procedures, content repository, managed records, audit trail/log |

## Business Drivers
- **Regulatory compliance**: Laws require maintaining records of certain activities
- **E-discovery**: Finding electronic records that may serve as evidence in legal action. Big Data has become a driver for more efficient e-discovery.
- **Business continuity**: Good records management is necessary for continuity
- **Operational efficiency**: Streamlining processes, managing workflow, eliminating repetitive manual tasks, enabling collaboration
- **Cost savings**: Freeing file cabinet space, reducing document handling costs

---

## Content vs. Document
- **Content**: The data and information inside a file, document, or website -- the "water in the bucket"
- **Document**: The container for content -- the "bucket"
- Content is managed based on **concepts**, type, status, and lifecycle. Some content becomes a matter of **record**.

### Content Management
Processes, techniques, and technologies for organizing, categorizing, and structuring information resources for storage, publishing, and reuse. Enterprise-wide scope = **Enterprise Content Management (ECM)**.

### Content Metadata
Essential for managing unstructured data. Based on: format, searchability, self-documentation, existing patterns, content subjects, and requirements for thoroughness.

### Content Modeling
Converting logical content concepts into content types, attributes, and data types with relationships. Two levels: **information product level** (e.g., a website) and **component level** (elements within the product).

### Content Delivery Methods
- **Push**: Users choose content type delivered on a schedule (e.g., RSS feeds)
- **Pull**: Users retrieve content themselves (e.g., visiting an online store)
- **Interactive**: Real-time data exchange between enterprise applications (e.g., EPOS apps)

---

## Controlled Vocabularies
A defined list of explicitly allowed terms used to index, categorize, tag, sort, and retrieve content. Range in complexity:

| Type | Description |
|------|-------------|
| **Term/Pick Lists** | Simple lists with no term relationships; reduce ambiguity by limiting domain of values |
| **Synonym Rings** | Set of roughly equivalent terms; allows search on one to access content for all |
| **Authority Lists** | One preferred term with variants; cross-references guide to preferred term (e.g., Library of Congress Subject Headings) |
| **Taxonomies** | Naming structures with controlled vocabulary for organizing topics and enabling navigation/search |
| **Thesauri** | Combine synonym lists and taxonomies; hierarchical, associative, and equivalent relationships |
| **Ontologies** | Represent concepts and relationships within a domain; primary knowledge representation for the Semantic Web |

### Taxonomy Structures
- **Flat**: No relationships; all categories equal (e.g., list of countries)
- **Hierarchical**: Tree structure; bi-directional (e.g., geography: continent to street address)
- **Polyhierarchy**: Child nodes may have multiple parents; complex traversal paths
- **Facet**: Star structure; each node is an attribute of the center object (e.g., Metadata attributes)
- **Network**: Both hierarchical and facet; any two nodes linked by association (e.g., recommender engines, thesauri)

### Taxonomy vs. Ontology
| Aspect | Taxonomy / Data Model | Ontology |
|--------|----------------------|----------|
| Scope | Provides data content classifications | Entity, attribute, and content concepts can be completely mixed |
| Assumption | **Closed-world**: What is defined is what is known | **Open-world**: Possible relationships inferred from existing ones |

### Folksonomy
Classification obtained through **social tagging**. Not authoritative; not compiled by experts. But directly reflects user vocabulary and can enhance information retrieval when linked to structured controlled vocabularies.

---

## Documents and Records

### Document Management
Encompasses processes for controlling and organizing documents throughout their lifecycle: storage, inventory, control (electronic and paper). **More than 90% of documents created today are electronic.**

Lifecycle includes: Inventory, Policy, Classification, Storage, Retrieval/Circulation, Preservation/Disposal.

### Records Management
Records = evidence of actions taken and decisions made. Special requirements governed by ISO 15489.

Characteristics of well-prepared records:
- **Content**: Accurate, complete, truthful
- **Context**: Descriptive Metadata collected at time of creation
- **Timeliness**: Created promptly after the event
- **Permanency**: Cannot be changed for legal length of existence
- **Structure**: Clear appearance, correct forms, legible, consistent terminology

**Vital Record**: Required to resume operations in the event of a disaster.

### Digital Asset Management (DAM)
Storage, tracking, and use of rich media (video, logos, photographs, etc.).

---

## Data Map
An inventory of all ESI data sources, applications, and IT environments including owners, custodians, geographic locations, and data types.

---

## E-Discovery
Finding electronic records that may serve as evidence in a legal action. Governed by the **EDRM** (Electronic Discovery Reference Model).

### EDRM Phases
1. **Identification**: Early Case Assessment + Early Data Assessment
2. **Preservation**: Place potentially relevant data on legal hold
3. **Collection**: Acquire and transfer identified data to legal counsel
4. **Processing**: De-duplicate, search, analyze
5. **Review**: Identify documents for response; identify privileged documents
6. **Analysis**: Understand circumstances, facts, potential evidence
7. **Production**: Turn over to opposing counsel in agreed formats (native, near-native, image, fielded data)
8. **Presentation**: Display ESI at depositions, hearings, trials

**Legal Hold Notification (LHN)**: Identifying information for legal proceedings, locking it to prevent editing/deletion, notifying all parties.

---

## Information Architecture
Creating structure for a body of content. Components: controlled vocabularies, taxonomies/ontologies, navigation maps, Metadata maps, search specifications, use cases, user flows.

---

## Semantic Models and Search
- **Semantic model**: Network of concepts and relationships; maps database tables/views to business-meaningful concepts
- **Semantic search**: Focuses on meaning and context rather than exact keyword matches; uses AI for concept matching
- Types of semantic keywords: Core, Thematic, Stem

---

## Unstructured Data
Estimated **80% of stored data** is outside relational databases. Includes: word processing, email, social media, chats, flat files, spreadsheets, XML, graphics, images, video, audio, paper files.

Fundamental data management principles apply: governance, architecture, security, Metadata, quality.

---

## ARMA GARP Principles
Eight Generally Accepted Recordkeeping Principles:
1. **Accountability**: Assign senior executive; adopt policies; ensure auditability
2. **Integrity**: Guarantee authenticity and reliability of records
3. **Protection**: Ensure reasonable protection for personal/sensitive information
4. **Compliance**: Comply with applicable laws and binding authorities
5. **Availability**: Maintain information for timely, efficient, accurate retrieval
6. **Retention**: Retain for appropriate time considering all requirements
7. **Disposition**: Provide secure and appropriate disposition per policies and laws
8. **Transparency**: Document policies, processes, and activities in an available/understandable manner

### ARMA Maturity Model (5 levels)
Level 1: Sub-Standard > Level 2: In Development > Level 3: Essential > Level 4: Proactive > Level 5: Transformational

---

## Activities
### Plan for Lifecycle Management
- Identify organizational unit responsible for managing documents/records
- Develop overall document management plan including business continuity
- Follow retention policies aligned with company standards and government regulations
- Develop a **content strategy** starting with current state inventory and gap assessment

### Content Handling Policies
Policies cover: audit scope, vital records protection, retention schedules, information hold orders, onsite/offsite storage, email management, proper destruction methods. Additional policies for: social media, BYOD/BYOA/WYOD, handling sensitive data.

### Versioning and Control (ANSI 859)
Three levels: **Formal** (full change control), **Revision** (less formal; notify and increment), **Custody** (safe storage and retrieval only)

### Retention and Disposal
Clear policies on timeframes for retention. Risk exists in retaining records past legally required timeframes (they remain discoverable for litigation).

---

## Tools
- **Document Management System**: Track/store electronic documents; versioning, security, indexing, retrieval
- **Content Management System**: Collect, organize, index, retrieve content; manage through lifecycle
- **Records Management System**: Automate retention/disposition, e-discovery support, long-term archiving
- **Collaboration Tools**: Team document sharing, blogs, wikis, RSS, tagging
- **Standard Markup Formats**: XML (structured + unstructured integration), JSON (lightweight, web-centric), RDF (Semantic Web triples), Schema.org (semantic markup for search engines)

---

## Governance and Metrics
| Area | KPI Examples |
|------|-------------|
| Records Management | % documents identified as corporate records, % records under retention control |
| E-discovery | Cost reduction, average turnaround time, speed of legal hold implementation |
| ECM Program | Number of ECM projects, adoption rates, user satisfaction |
| ECM Operational | Downtime, storage utilization, search retrieval performance (precision and recall) |
| Financial | Cost of ECM system, reduced physical storage costs, decreased operational costs |
| Risk Mitigation | Reduction of discovery costs, number of audit trails for e-discovery |

**Precision** = proportion of retrieved documents that are actually relevant.
**Recall** = proportion of all relevant documents that are actually retrieved.

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| 80% of stored data is | **Unstructured** (outside relational databases) |
| GARP stands for | Generally Accepted Recordkeeping Principles (8 principles from ARMA) |
| E-discovery definition | Finding electronic records that may serve as evidence in a legal action |
| Vital Record | Required to resume operations in event of a disaster |
| Taxonomy vs. Ontology | Taxonomy = closed-world (what's defined = what's known); Ontology = open-world (relationships can be inferred) |
| Folksonomy | Classification obtained through social tagging; not authoritative |
| ANSI 859 three control levels | Formal > Revision > Custody |
| Content delivery: Push vs. Pull | Push = scheduled delivery (RSS); Pull = user retrieves (online shopping) |
| Legal Hold Notification (LHN) | Lock data to prevent editing/deletion; notify parties of legal hold |
| ECM stands for | Enterprise Content Management |
| EDRM phases (simplified) | Identification > Preservation > Collection > Processing > Review > Analysis > Production > Presentation |
| Precision vs. Recall | Precision = relevant among retrieved; Recall = retrieved among all relevant |
| Records management ISO | ISO 15489 |

## Related Notes
- [[Data Storage and Operations]]
- [[Data Security]]
- [[Data Integration and Interoperability]]
- [[Metadata Management]]
- [[Data Governance]]
- [[Data Quality]]
