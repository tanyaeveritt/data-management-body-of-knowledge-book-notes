---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 6
keywords: data storage, database administration, DBA, ACID, BASE, CAP theorem, replication, business continuity
---

# Data Storage and Operations (Importance: ★★★)
*Reading time: ~7 min*

#dmbok2 #data-storage

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Design, implementation, and support of stored data to maximize its value throughout its lifecycle |
| Goals | 1) Manage availability of data throughout lifecycle 2) Ensure integrity of data assets 3) Manage performance of data transactions |
| Two Sub-activities | **Database Support** (data lifecycle, backup, purge, monitoring) and **Database Technology Support** (technical requirements, architecture, admin) |
| Key Role | **Database Administrator (DBA)** -- most established and widely adopted data professional role |
| Primary Business Driver | **Business continuity** -- if a system is unavailable, operations may be impaired or stopped |
| Key Framework | ITIL (Information Technology Infrastructure Library) for technology management |
| Inputs | Data Architecture, Data Requirements, Data Models, Service Level Agreements |
| Deliverables | Database environments, migrated/replicated/versioned data, business continuity plans, database performance OLAs |

## DBA Types and Roles
DBAs do not exclusively perform all storage and operations activities. Data stewards, data architects, network administrators, and security analysts also participate.

- **Production DBA**: Ensures performance and reliability; implements backup/recovery, clustering, failover, and archiving mechanisms
- **Application DBA**: Responsible for one or more databases across all environments (dev/test/QA/prod); collaborates closely with data analysts and modelers
- **Procedural DBA**: Leads review/admin of procedural objects -- stored procedures, triggers, UDFs
- **Development DBA**: Focuses on data design activities including sandbox/exploration areas
- **Network Storage Administrator (NSA)**: Concerned with hardware/software supporting data storage arrays

---

## Database Architecture Types
Databases are classified as **centralized** (single system, single place) or **distributed** (multiple databases on multiple systems).

- **Centralized**: All data in one place; ideal for restricted data; risk if system is unavailable
- **Distributed**: Quick access over many nodes; commodity hardware; designed to handle failures via replication
- **Federated Database**: Maps multiple autonomous databases into a single federated view without actual data integration; **loosely coupled** (users construct own schema) vs. **tightly coupled** (integrated federated schema published)
- **Blockchain Database**: Type of federated database for secure financial transactions; uses time-bound blocks with hash algorithms; tampering is apparent when hash values no longer match

---

## Database Processing Types: ACID vs. BASE vs. CAP
These define how databases handle transactions and consistency.

- **ACID** (relational/OLTP): **Atomicity** (all-or-nothing), **Consistency** (all rules met), **Isolation** (independent transactions), **Durability** (cannot be undone once complete). Dominant in relational databases using SQL.
- **BASE** (Big Data/NoSQL): **Basically Available** (some availability even with node failures), **Soft State** (data in constant flux), **Eventual Consistency** (data will be consistent eventually, not immediately). Common in large online and social media companies.
- **CAP Theorem** (Brewer's Theorem): A distributed system cannot comply with all of Consistency, Availability, and Partition Tolerance simultaneously -- "pick two." Drives Lambda Architecture (Speed path = A+P; Batch path = C+A).

| Property | ACID | BASE |
|----------|------|------|
| Casting | Schema must exist, columns typed | Dynamic, store dissimilar data |
| Consistency | Strong | Strong, Eventual, or None |
| Processing | Transactional, row/column | Key-value stores, wide-column |
| Origin | 1970s application storage | 2000s unstructured storage |
| Scaling | Product dependent | Auto-spreads across commodity servers |

---

## Database Organization Types
Three general ways: Hierarchical, Relational, Non-Relational.

- **Hierarchical**: Oldest model; tree-like structure with mandatory parent/child (1-to-many); XML uses this model
- **Relational (RDBMS)**: Based on set theory and relational algebra; schema on write; row-oriented; uses SQL. Variations: **Multidimensional** (cubes, MDX), **Temporal** (valid time + transaction time = bi-temporal)
- **Non-Relational (NoSQL)**: Schema on read; includes **Column-oriented** (good for OLAP/BI), **Spatial** (geometric data), **Key-Value Pair** (document databases, graph databases), **Triplestore** (subject-predicate-object in RDF), **Flat File** (single file, used by Hadoop)

---

## Data Storage Media
- **Disk / SAN**: Stable persistent storage; data movement on SAN backplane avoids network
- **In-Memory (IMDB)**: Faster response; loaded into volatile memory; used for real-time analytics
- **Columnar Compression**: Compresses redundant data; stores column values as pointers
- **Flash / SSD**: Combines access speed of memory with persistence of disk

---

## Common Database Processes
- **Archiving**: Moving data to lower-performance media; must align with partitioning strategy; test restoration regularly
- **Capacity & Growth Projections**: Plan for initial capacity + growth for data, indexes, logs, mirrors
- **Change Data Capture (CDC)**: Detecting data changes via data versioning (timestamps, flags) or log-based replication; sends only deltas
- **Purging**: Completely removing data from storage; reduces cost and risk; data may become a liability if kept too long
- **Replication**: Same data on multiple storage devices; **active** (recreate everywhere) vs. **passive** (primary to secondary); horizontal scaling = more replicas; vertical scaling = geographically distant replicas
- **Sharding**: Small isolated chunks updated independently; refreshes via file copy

---

## Resiliency and Recovery
- **Resiliency**: Measurement of how tolerant a system is to error conditions
- Three recovery types: **Immediate** (design-based auto-resolution), **Critical** (restore ASAP), **Non-critical** (delayed until more critical systems restored)
- **Replication patterns**: **Mirroring** (immediate two-phase commit) vs. **Log Shipping** (secondary receives transaction logs at intervals)

---

## Database Performance Management
Performance = **availability** + **speed**. An unavailable database has performance of zero.

- Four availability factors: **Manageability**, **Recoverability**, **Reliability**, **Serviceability**
- Common performance issues: Memory contention, locking/blocking/deadlocks, inaccurate statistics, poor SQL coding, insufficient indexing, runaway queries, overloaded servers, database volatility
- **Service Level Agreements (SLAs)**: Govern performance, availability, recovery expectations between IT and data owners

---

## Database Environments
- **Production**: Mission-critical; never use for dev/test
- **Development**: Slimmer version of production; first place for patches
- **Test**: QA, integration, UAT, performance testing; ideally same software/hardware as production
- **Sandbox**: Read-only connections to production; managed by users for experimentation/POC
- **Alternate Production**: Supports offline backups, failover, resiliency

---

## Virtualization / Cloud Platforms
Three cloud database methods:
- **Virtual Machine Image**: Run database on purchased VM instances
- **Database-as-a-Service (DaaS)**: Provider installs and maintains database; pay per usage
- **Managed Database Hosting**: Provider hosts and manages on owner's behalf

Systematic approach includes: **Standardization/Consolidation**, **Server Virtualization**, **Automation**, and **Security** integration with physical infrastructure.

---

## Managing Test Data Sets
- Test data can be fabricated, sample, or derived from production (must be **masked** if it contains protected data)
- Types: focused/systematic (functionality testing) or less-focused (high-volume randomized)
- DBAs should monitor and **purge obsolete test data** regularly to preserve capacity
- Amount of test data is limited by time, cost, quality, and **regulation** restricting production data in test environments

---

## Data Migration
- Transferring data between storage types, formats, or systems with minimal change
- Phases: **design, extraction, remediation, load, verification** -- commonly repeated several times
- Key consideration for system implementation, upgrade, or consolidation
- Often under-estimated; requires proper analysis and profiling to avoid data quality issues

---

## Governance and Metrics
| Metric Category | Examples |
|----------------|----------|
| Data Storage | Count of databases by type, capacity used, storage containers, data in queue |
| Performance | Transaction frequency, query performance, API service performance |
| Operational | Data retrieval time, backup size, data quality measurement, availability |
| Service | Issue submission/resolution/escalation count, resolution time |

- **Information Asset Tracking**: Comply with licensing agreements and regulatory requirements; track TCO for each technology
- **Data Audits**: Evaluation of data sets based on defined criteria for compliance with contractual and methodological requirements

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| ACID stands for | Atomicity, Consistency, Isolation, Durability |
| BASE stands for | Basically Available, Soft State, Eventual Consistency |
| CAP Theorem "pick two" | Consistency, Availability, Partition Tolerance -- distributed systems can only guarantee two |
| Primary business driver for Data Storage | **Business continuity** |
| Schema on write vs. schema on read | Relational = schema on write; NoSQL = schema on read |
| Mirroring vs. Log Shipping | Mirroring = immediate two-phase commit; Log Shipping = periodic transaction log copies |
| Active vs. Passive replication | Active = recreate at every replica; Passive = primary to secondary |
| DBA who manages procedural logic | **Procedural DBA** (stored procedures, triggers, UDFs) |
| Federated database purpose | Maps multiple autonomous databases into a single view without actual data integration |
| Temporal database "bi-temporal" | Combines valid time and transaction time |
| When to purge data | When data becomes obsolete, unnecessary, or a liability if kept longer than required |
| Lambda Architecture uses CAP how | Speed path = Availability + Partition Tolerance; Batch path = Consistency + Availability |
| Sharding | Small isolated chunks of database updated independently; refreshes via file copy |
| SLA governs | System performance, data availability, recovery expectations, team response times |

## Related Notes
- [[Data Security]]
- [[Data Integration and Interoperability]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Data Quality]]
- [[Metadata Management]]
