---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: all
keywords: exam traps, weak areas, common mistakes, DAMA, DMBOK2
---

# Exam Traps
*Reading time: ~5 min*

#dashboard #exam-traps #dmbok2

> [!warning] Purpose of this note
> A collection of commonly confused or frequently missed points -- a **mistake and trap reference note**.

## Data Management Foundations

> [!danger]- Trap: Confusing Data Governance with Data Management
> - **Trap**: Treating Data Governance and Data Management as the same thing
> - **Why confusing**: Both deal with data policies and practices
> - **Correct**: Data Governance is the **exercise of authority and control** (decision-making); Data Management is the **execution** of plans and practices. Governance guides management.
> - [[Data Governance]], [[Data Management]]

> [!danger]- Trap: Data Owner vs Data Steward
> - **Trap**: Using Owner and Steward interchangeably
> - **Why confusing**: Both have accountability for data
> - **Correct**: **Owner** = senior business person with accountability for a data domain; **Steward** = operational person responsible for day-to-day data quality and standards
> - [[Data Governance]]

> [!danger]- Trap: DIKW Pyramid implies data "just exists"
> - **Trap**: Accepting the DIKW pyramid uncritically
> - **Why confusing**: Widely taught as foundational concept
> - **Correct**: DMBOK2 criticizes it -- data does not just exist, it must be **created**; it takes knowledge to create data; data and information are intertwined, not strictly sequential
> - [[Data Management]]

## Data Architecture and Modeling

> [!danger]- Trap: Kimball vs Inmon direction
> - **Trap**: Saying Kimball is top-down and Inmon is bottom-up
> - **Why confusing**: Both build data warehouses
> - **Correct**: **Kimball** = bottom-up (dimensional, data mart first); **Inmon** = top-down (normalized enterprise DW first, then data marts)
> - [[Data Modeling and Design]], [[Data Warehousing and BI]]

> [!danger]- Trap: Conceptual vs Logical vs Physical model scope
> - **Trap**: Including implementation details in a conceptual model
> - **Why confusing**: All three describe data structures
> - **Correct**: **Conceptual** = business entities and relationships (no attributes); **Logical** = attributes, keys, normalization (DB-agnostic); **Physical** = tables, columns, indexes, datatypes (DB-specific)
> - [[Data Modeling and Design]]

> [!danger]- Trap: Normalization level confusion
> - **Trap**: Mixing up 2NF and 3NF requirements
> - **Why confusing**: Both eliminate dependencies
> - **Correct**: **2NF** = no partial dependency (all non-key attributes depend on entire composite key); **3NF** = no transitive dependency (non-key attributes depend only on the key)
> - [[Data Modeling and Design]]

## Data Quality

> [!danger]- Trap: Confusing accuracy with validity
> - **Trap**: Using accuracy and validity interchangeably
> - **Why confusing**: Both measure data correctness
> - **Correct**: **Accuracy** = data correctly represents real-world entity; **Validity** = data conforms to defined format, type, range rules. Data can be valid but inaccurate (e.g., valid date format but wrong date)
> - [[Data Quality]]

> [!danger]- Trap: Data profiling vs data monitoring
> - **Trap**: Treating profiling and monitoring as the same activity
> - **Why confusing**: Both assess data characteristics
> - **Correct**: **Profiling** = initial/periodic assessment to discover structure, patterns, anomalies; **Monitoring** = ongoing measurement against established DQ rules and thresholds
> - [[Data Quality]]

## Data Storage and Security

> [!danger]- Trap: SCD Type 2 vs Type 3
> - **Trap**: Mixing up which SCD type preserves full history
> - **Why confusing**: Both track changes over time
> - **Correct**: **Type 2** = new row for each change (full history, uses effective dates); **Type 3** = new column (previous value only, limited history)
> - [[Data Storage and Operations]]

> [!danger]- Trap: Encryption at rest vs in transit
> - **Trap**: Assuming one encryption method covers both scenarios
> - **Why confusing**: Both protect data confidentiality
> - **Correct**: **At rest** = stored data (AES, TDE); **In transit** = data being transmitted (TLS/SSL). Both needed for comprehensive security.
> - [[Data Security]]

## Integration and Master Data

> [!danger]- Trap: ETL vs ELT order of operations
> - **Trap**: Confusing where transformation happens
> - **Why confusing**: Same three letters, different order
> - **Correct**: **ETL** = transform in staging area before loading to target; **ELT** = load raw data to target first, then transform using target system's compute power
> - [[Data Integration and Interoperability]]

> [!danger]- Trap: MDM Registry vs Consolidation style
> - **Trap**: Thinking registry style creates a golden record
> - **Why confusing**: Both provide a unified view of master data
> - **Correct**: **Registry** = index/pointer to source records (no golden copy); **Consolidation** = creates a golden record in a hub but sources remain authoritative for transactions
> - [[Reference and Master Data]]

## Metadata and Content

> [!danger]- Trap: Business vs Technical vs Operational metadata
> - **Trap**: Not distinguishing between the three metadata types
> - **Why confusing**: All describe data about data
> - **Correct**: **Business** = definitions, rules, glossary terms; **Technical** = schemas, lineage, ETL specs; **Operational** = run dates, job status, record counts, usage stats
> - [[Metadata Management]]

> [!danger]- Trap: Taxonomy vs Ontology
> - **Trap**: Using taxonomy and ontology interchangeably
> - **Why confusing**: Both classify concepts
> - **Correct**: **Taxonomy** = hierarchical classification (closed-world assumption); **Ontology** = concepts + relationships + inference rules (open-world assumption, can infer relationships)
> - [[Document and Content Management]]

## Organization and Change

> [!danger]- Trap: Kotter's 8 steps -- skipping urgency
> - **Trap**: Jumping straight to vision and strategy
> - **Why confusing**: Vision seems like the logical starting point
> - **Correct**: Kotter insists **Step 1 (Sense of Urgency)** must come first. Without urgency, complacency kills the change effort. 75% of management must believe status quo is unacceptable.
> - [[Change Management]]

---

## Related Notes
- [[MOC - DAMA DMBOK2]] -> Weak Areas section
- [[testing_tutor/Data_Management_StudyVault/00-Dashboard/Quick Reference]]
