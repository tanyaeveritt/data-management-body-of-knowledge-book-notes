---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 8
keywords: data integration, interoperability, ETL, ELT, latency, hub-and-spoke, canonical model, SOA, ESB, CDC, data lineage, complex event processing
---

# Data Integration and Interoperability (Importance: ★★★)
*Reading time: ~8 min*

#dmbok2 #data-integration

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Managing the movement and consolidation of data within and between applications and organizations |
| Goals | 1) Provide data securely in the format and timeframe needed 2) Lower cost/complexity via shared models and interfaces 3) Identify meaningful events and trigger alerts 4) Support BI, analytics, MDM, and operational efficiency |
| Primary Business Driver | **Efficient management of data movement** across hundreds/thousands of data stores |
| Key Process | **ETL** (Extract, Transform, Load) -- whether physical or virtual, batch or real-time |
| Key Architecture Principle | **Hub-and-spoke** over point-to-point to reduce complexity |
| Inputs | Business goals, data needs/standards, regulatory/security requirements, data architectures, source data |
| Deliverables | DII architecture, data exchange specifications, data access agreements, data services, CEP thresholds/alerts |

## Business Drivers
- Managing the **cost and complexity** of data movement. Point-to-point solutions between applications can result in thousands to millions of interfaces (approaching s-squared).
- Purchased applications each come with their own data stores that must be integrated.
- **Hub-and-spoke** model consolidates shared data, providing consistent views with limited performance impact on source systems.
- Enterprise-level DII systems enable **re-use of code** for compliance rules and simplify verification.

---

## ETL: Extract, Transform, Load
The fundamental process for moving data. Can be batch or real-time, physical or virtual.

- **Extract**: Select and extract required data from source; ideally uses few resources on operational systems
- **Transform**: Make data compatible with target structure. Examples: format changes (EBCDIC to ASCII), structure changes (denormalized to normalized), semantic conversion (code mappings), de-duping, re-ordering
- **Load**: Physically store or present transformed data in the target system

### ELT (Extract, Load, Transform)
When the target system has more transformation capability, data is loaded first, then transformed. Common in **Big Data/data lake** environments where raw data is loaded and then processed.

### Mapping
Both the process and the result of developing source-to-target lookup matrices. Defines sources, extraction rules, targets, update rules, and transformation rules.

---

## Latency Spectrum
| Type | Description | Latency |
|------|-------------|---------|
| **Batch** | Data moves in clumps on schedule; **delta** (changes) or **snapshot** (full point-in-time) | High |
| **Micro-batch** | Batch on higher frequency (e.g., every 5 minutes) | Medium |
| **Change Data Capture** | Monitors for inserts/changes/deletes; passes only deltas | Medium-Low |
| **Near-real-time / Event-driven** | Processed when event happens; usually via ESB | Low |
| **Asynchronous** | Sending system doesn't wait for acknowledgment; measured in seconds/minutes | Low |
| **Real-time / Synchronous** | Executing process waits for confirmation; two-phase commits ensure perfect sync | Very Low |
| **Streaming / Low Latency** | Continuous real-time data flow as events occur; uses in-memory/SSD | Ultra-Low |

Key trade-offs: Synchronous = perfect consistency but fewer transactions and dependency risk. Asynchronous = more resilient but small delay.

---

## Change Data Capture (CDC)
Reduces bandwidth by filtering to only changed data within a timeframe. Three data-based techniques:
1. Source system populates **timestamps/flags** as change indicators
2. Source system adds to a **list of changed objects/identifiers**
3. Source system copies changed data into a **separate object** as part of the transaction

Also: **log-based CDC** reads database transaction logs for changes.

---

## Interaction Models
| Model | Description | When to Use |
|-------|-------------|-------------|
| **Point-to-point** | Direct data exchange between systems | Small number of systems; quickly becomes unmanageable |
| **Hub-and-spoke** | Central data hub; all systems exchange through it | 3+ systems (critical for 100+ systems); reduces interfaces dramatically |
| **Publish-subscribe** | Systems push data out (publish); others pull in (subscribe) | Multiple consumers need consistent data sets |

Point-to-point: number of interfaces approaches **s-squared** (systems squared). Hub-and-spoke becomes cost-justified with even a small number of systems.

---

## DII Architecture Concepts

### Application Coupling
- **Tightly coupled**: Synchronous interface; if one is unavailable, both effectively unavailable
- **Loosely coupled**: Data passed without waiting for response; one system may be unavailable without affecting the other. Implemented via services, APIs, or message queues. **Preferred design**.

### Enterprise Application Integration (EAI)
Software modules interact only through well-defined **APIs**. Data stores updated only by their own modules. Built on object-oriented concepts emphasizing reuse.

### Enterprise Service Bus (ESB)
Acts as intermediary between systems passing messages. Applications are encapsulated from other processes. Implements incoming/outgoing message queues with adapters on each system. Central processor polls for messages and delivers to subscribers. **Near real-time** (seconds to minutes). Example of loose coupling.

### Service Oriented Architecture (SOA)
Well-defined service calls between applications. Each module provides services without foreknowledge of calling application (black box). Implemented as APIs available to calling systems. Requires a **governance model** for service registration and reuse.

### Complex Event Processing (CEP)
Combines data from multiple sources to identify **meaningful events** (opportunities/threats) and trigger **real-time response**. Rules guide processing and routing. Often tied to Big Data. Requires ultra-low latency (in-memory databases, streaming).

### Data Federation and Virtualization
- **Federation**: Access to combination of individual data stores regardless of structure
- **Virtualization**: Multiple heterogeneous data stores accessed/viewed as a single database

### Data-as-a-Service (DaaS)
Data licensed from a vendor and provided on demand. Also used within organizations to provide enterprise data services to various functions.

### Cloud-based Integration (IPaaS)
Integration delivered as cloud service. Addresses data, process, SOA, and application integration use cases.

---

## Enterprise Message Format / Canonical Model
A common model standardizing the format for data sharing. Each system transforms only to/from the canonical model rather than to every other system. **Significantly reduces** complexity and cost. Justifiable for 3+ systems; critical for 100+ systems.

---

## Data Exchange Standards
Formal rules for data element structure. ISO standards, industry-specific standards. **NIEM** (National Information Exchange Model) uses XML for schema definitions to ensure unambiguous understanding across communities.

---

## Activities
### Plan and Analyze
1. Define data integration and lifecycle requirements
2. **Perform Data Discovery**: Identify potential sources; high-level quality assessment
3. **Document Data Lineage**: How data is acquired, where it moves, how it's used and changed
4. **Profile Data**: Analyze format, population, values, patterns, relationships. Critical -- actual data always differs from assumptions.
5. **Collect Business Rules**: Definitions, facts, constraints, derivations. For MDM: match/merge/survivorship/trust rules.

### Design
- Select interaction model (hub-and-spoke, point-to-point, publish-subscribe)
- Design data services or exchange patterns (start with industry standards)
- Model data hubs, interfaces, messages
- **Map sources to targets**: Format, transformations, calculations, value lookups
- **Design data orchestration**: Pattern of data flows from start to finish

### Develop
- Develop data services, data flows, migration approach, publication approach, CEP flows
- **Maintain DII Metadata**: Document structures, business definitions, transformation rules

### Implement and Monitor
- Real-time processing requires real-time monitoring
- Data interaction capabilities must be serviced at the same level as the most demanding target application

---

## Governance
- Business stakeholders responsible for defining data modeling and transformation rules
- **Data Sharing Agreements** (MOUs): Stipulate responsibilities, acceptable use, restrictions, service levels
- **Data Lineage**: Required for changes to data flows; emerging compliance standards (e.g., Solvency II) require tracing data origins

### Metrics
| Category | Examples |
|----------|----------|
| Data Availability | Availability of data requested |
| Data Volumes and Speed | Volumes transported/transformed, speed, latency, time to availability |
| Solution Costs and Complexity | Cost of managing solutions, ease of acquiring new data, number of systems using DII |

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| ETL stands for | Extract, Transform, Load |
| ELT vs. ETL | ELT loads raw data first, then transforms on target system (common in Big Data/data lakes) |
| Point-to-point interface count | Approaches s-squared (number of systems squared) |
| Hub-and-spoke advantage | Reduces interfaces; systems exchange only with central hub; consistent data views |
| Canonical model purpose | Standard format for data sharing; each system transforms only to/from the canonical model |
| Tight vs. loose coupling | Tight = synchronous, dependent; Loose = asynchronous, independent (preferred) |
| ESB full name | Enterprise Service Bus -- intermediary for near-real-time messaging between systems |
| SOA key concept | Independent services; no foreknowledge of calling application (black box) |
| Data profiling importance | Actual data always differs from assumptions; skipping profiling defers issues to testing or operations |
| CDC purpose | Sends only deltas (changes) rather than entire data sets; reduces bandwidth |
| Complex Event Processing | Combines multiple data sources to identify meaningful events and trigger real-time responses |
| Data Sharing Agreement | MOU stipulating responsibilities, acceptable use, and service levels before data exchange |
| Batch delta vs. snapshot | Delta = only changed data since last send; Snapshot = full data at a point in time |
| Lambda Architecture connection | Speed path uses near-real-time; Batch path uses batch processing (see Ch 14) |

## Related Notes
- [[Data Storage and Operations]]
- [[Data Security]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Metadata Management]]
- [[Data Governance]]
- [[Document and Content Management]]
