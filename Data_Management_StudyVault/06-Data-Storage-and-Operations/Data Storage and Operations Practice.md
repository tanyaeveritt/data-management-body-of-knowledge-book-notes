---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 6
keywords: data storage, database administration, DBA, ACID, BASE, CAP theorem, replication, business continuity, archiving, sharding
---

# Data Storage and Operations Practice

#dmbok2 #data-storage

## Related Concepts
- [[Data Storage and Operations]]
- [[Data Security]]
- [[Data Integration and Interoperability]]
- [[Data Architecture]]
- [[Data Modeling and Design]]

> [!hint]- Key Patterns (click to view)
> - **ACID vs. BASE**: ACID = Atomicity, Consistency, Isolation, Durability (relational/OLTP). BASE = Basically Available, Soft State, Eventual Consistency (NoSQL/Big Data). They are on opposite ends of a spectrum.
> - **CAP Theorem**: "Pick two" from Consistency, Availability, Partition Tolerance. Drives Lambda Architecture design.
> - **Schema on write vs. schema on read**: Relational = schema on write; NoSQL = schema on read.
> - **Replication patterns**: Mirroring (immediate two-phase commit) vs. Log Shipping (periodic transaction log copies). Active vs. Passive replication.
> - **DBA types**: Production, Application, Procedural, Development DBAs plus Network Storage Administrators.
> - **Business continuity** is the primary business driver for Data Storage and Operations.
> - **Federated databases**: Map multiple autonomous databases into a single view without actual data integration. Loosely vs. tightly coupled.
> - **Recovery types**: Immediate, Critical, Non-critical.

---

### Q1. What is the primary business driver for Data Storage and Operations? [recall]

> [!answer]- Show Answer
> **Business continuity** is the primary driver. If a system becomes unavailable, company operations may be impaired or stopped completely. A reliable data storage infrastructure minimizes the risk of disruption.

---

### Q2. What does the acronym ACID stand for, and in what type of database processing is it used? [recall]

> [!answer]- Show Answer
> ACID stands for:
> - **Atomicity**: All operations are performed, or none of them is
> - **Consistency**: The transaction must meet all rules defined by the system
> - **Isolation**: Each transaction is independent
> - **Durability**: Once complete, the transaction cannot be undone
>
> ACID is dominant in **relational database (OLTP)** processing, using SQL as the interface.

---

### Q3. A large social media company needs a database that can handle massive volumes of unstructured data with eventual consistency. Should they use ACID or BASE? Explain. [application]

> [!answer]- Show Answer
> They should use **BASE** (Basically Available, Soft State, Eventual Consistency). BASE systems are common in Big Data environments and large online/social media companies because:
> - Immediate accuracy of all data at all times is not necessary
> - BASE scales automatically across commodity servers
> - It handles dynamic, dissimilar data (schema on read)
> - It prioritizes availability over strong consistency
>
> ACID would be inappropriate here because its strong consistency and rigid schema requirements cannot efficiently scale to handle the volume and variability of social media data.

---

### Q4. What are the three properties of the CAP Theorem, and what does the theorem state? [recall]

> [!answer]- Show Answer
> The **CAP Theorem** (Brewer's Theorem) states that a distributed system can comply with at most **two** of the following three properties ("pick two"):
> - **Consistency**: The system must operate as designed at all times
> - **Availability**: The system must be available when requested and respond to each request
> - **Partition Tolerance**: The system must continue operations during data loss or partial system failure
>
> The **Lambda Architecture** uses CAP by having a Speed path (Availability + Partition Tolerance) and a Batch path (Consistency + Availability).

---

### Q5. What is the difference between a Production DBA and a Procedural DBA? [recall]

> [!answer]- Show Answer
> - **Production DBA**: Takes primary responsibility for **data operations management**, including performance tuning, monitoring, error reporting, implementing backup/recovery mechanisms, clustering/failover, and archiving.
> - **Procedural DBA**: Leads review and administration of **procedural database objects** -- stored procedures, triggers, and user-defined functions (UDFs). Ensures procedural logic is planned, implemented, tested, and shared/reused.
>
> In many cases, the Procedural DBA and Development DBA functions are combined under one position.

---

### Q6. An organization is choosing between mirroring and log shipping for database replication. What factors should drive this decision? [application]

> [!answer]- Show Answer
> The choice depends on **how critical the data is** and **how important immediate failover is**:
> - **Mirroring**: Updates are replicated **immediately** via a two-phase commit process. Best for critical data requiring instant failover. More expensive. Effective for one secondary server.
> - **Log Shipping**: A secondary server receives and applies copies of the primary database's **transaction logs at regular intervals**. Has a delay between updates. Less expensive. Can update additional secondary servers.
>
> For a single highly critical secondary server, use mirroring. For additional less-critical secondary servers or when cost is a factor, use log shipping.

---

### Q7. Explain the difference between schema on write and schema on read, and give an example database type for each. [recall]

> [!answer]- Show Answer
> - **Schema on write** (Relational databases): The schema/structure must be known and defined **before** data can be written. Data is organized into tables with typed columns using SQL. Example: **RDBMS** (Oracle, SQL Server).
> - **Schema on read** (Non-relational/NoSQL databases): Data is stored without a predefined schema and can be read/interpreted in different ways depending on need. Example: **Hadoop flat files, Key-Value stores, Document databases**.
>
> The choice depends on whether the data structure is known and stable (use schema on write) or dynamic and variable (use schema on read).

---

### Q8. A company discovers that their archived data from 5 years ago is stored on media that current systems cannot read. What should they have done to prevent this, and what are their options now? [analysis]

> [!answer]- Show Answer
> **Prevention measures they should have followed:**
> - Schedule **regular tests of archive restoration** to avoid surprises in an emergency
> - When technology or structure changes, **evaluate the archive** to ensure data can still be read
> - For major technology changes: restore archives before the change, upgrade/migrate, then re-archive
>
> **Current options:**
> 1. **Determine if the archive is required** -- what is not required can be considered purged
> 2. **Keep a small version of the old system** running with limited access to extract from archives as needed (but this is not efficient or cost-effective long-term)
> 3. **For high-value archives**: restore using old technology, migrate to new format, then re-archive
>
> Archives that are not recoverable with current technology are **useless**. This is why the DMBOK2 emphasizes that keeping old machinery around to read unreadable archives is not efficient.

---

### Q9. What is Change Data Capture (CDC), and what are the two main methods for detecting changes? [recall]

> [!answer]- Show Answer
> **Change Data Capture (CDC)** is the process of detecting that data has changed and ensuring information about the change is stored appropriately. Often called log-based replication, CDC sends only the **deltas** (changes) rather than the entire database.
>
> Two methods for detecting changes:
> 1. **Data versioning**: Evaluates columns that identify changed rows (e.g., last-update-timestamp, version-number columns, status-indicator columns)
> 2. **Log-based**: Reads database transaction logs that document the changes, enabling replication to secondary systems
>
> CDC is non-invasive -- it replicates changes to a target without affecting the source.

---

### Q10. An organization is planning database environments for a new application. Compare the purposes of Development, Test, Sandbox, and Production environments. Why should production data NOT be used directly in development? [analysis]

> [!answer]- Show Answer
> **Environment purposes:**
> - **Production**: Mission-critical environment where all business processes occur. Never use for dev/test.
> - **Development**: Slimmer version of production. First place for patches/updates. Isolated from production hardware.
> - **Test**: Used for QA, integration testing, UAT, and performance testing. Ideally same software/hardware as production. Should never write to production systems.
> - **Sandbox**: Read-only connections to production data, managed by users for experimentation and proof-of-concept. Must be isolated from production processing.
>
> **Why not use production data in development:**
> - In many industries, **production data is protected through regulation** (see Chapter 7)
> - Moving production data to development could expose sensitive/protected data
> - Organizations must first determine **what restrictions exist** before copying production data
> - If production data must be used, it should be **masked** to protect sensitive information
> - Development and test activities put production data at risk if run in the production environment

---

> [!summary]- Pattern Summary (click to view)
> **Core Framework**: Data Storage and Operations has two sub-activities: Database Support (lifecycle, backup, monitoring) and Database Technology Support (requirements, architecture, admin). The DBA is the most established data professional role.
>
> **Key Distinctions to Remember**:
> - ACID (relational, strong consistency, schema on write) vs. BASE (NoSQL, eventual consistency, schema on read)
> - CAP Theorem: pick two of Consistency, Availability, Partition Tolerance
> - Mirroring (immediate) vs. Log Shipping (periodic) for replication
> - Active (recreate everywhere) vs. Passive (primary to secondary) replication
> - Centralized vs. Distributed; Federated (autonomous) vs. Non-federated
> - Loosely coupled (users construct own schema) vs. Tightly coupled (integrated federated schema)
>
> **Business Driver**: Business continuity. **Performance** = availability + speed; unavailable database = zero performance.
> **Recovery Types**: Immediate, Critical, Non-critical. **Resiliency** = tolerance to error conditions.
> **Common Processes**: Archiving, Capacity/Growth, CDC, Purging, Replication, Sharding.
