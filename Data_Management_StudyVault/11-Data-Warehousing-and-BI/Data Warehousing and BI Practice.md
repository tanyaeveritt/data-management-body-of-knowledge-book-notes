---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 11"
keywords:
  - data warehouse
  - business intelligence
  - Inmon
  - Kimball
  - OLAP
  - star schema
  - CDC
  - data mart
tags:
  - dmbok2
  - data-warehousing
  - practice
---

# Data Warehousing and BI -- Practice Questions

## Related Concepts

- [[Data Warehousing and BI]]
- [[Data Integration and Interoperability]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Reference and Master Data]]
- [[Metadata Management]]
- [[Data Quality]]

---

> [!hint]- Key Patterns (click to view)
> - Inmon = normalized, subject-oriented, integrated, time-variant, non-volatile; CIF architecture
> - Kimball = dimensional model (star schema), facts + dimensions, conformed dims via bus
> - DW Bus Matrix: rows = business processes, columns = subject areas (dimensions)
> - ODS: 30-90 days, volatile, low latency; DW: years of history, non-volatile, higher latency
> - CDC methods ordered by complexity: time-stamp (low) -> log table -> DB log -> message (extreme) -> full load (simple but slow)
> - Near-real-time: trickle feeds (source accumulation), messaging (bus accumulation), streaming (target accumulation)
> - OLAP types: ROLAP (relational), MOLAP (multi-dimensional), HOLAP (hybrid)
> - Guiding principle: "Summarize and optimize last, not first"

---

### Q1. What are Inmon's four defining characteristics of a data warehouse? [recall]

> [!answer]- Show Answer
> 1. **Subject-oriented**: Organized by major business entities (e.g., Customer, Product), not by function or application
> 2. **Integrated**: Unified and cohesive -- consistent key structures, encoding, definitions, and naming conventions across all data
> 3. **Time-variant**: Stores data as it exists at set points in time; querying a time period always produces the same result
> 4. **Non-volatile**: Records are not updated as in operational systems; new data is appended, preserving history
>
> Inmon also notes that a DW contains both **aggregate and detail data** and is **historical** in nature.

---

### Q2. How does the Kimball dimensional model (Star Schema) differ from the Inmon normalized model? [recall]

> [!answer]- Show Answer
> **Inmon (CIF)**:
> - Uses a **normalized relational model** in the central DW layer
> - Stores all atomic data in a single enterprise DW
> - Data flows from the DW to dependent data marts
>
> **Kimball (Dimensional)**:
> - Uses a **dimensional model** (Star Schema) with **facts** (quantitative measures) and **dimensions** (descriptive attributes)
> - The DW is composed of **departmental data marts** integrated via **conformed dimensions** (the "bus")
> - DW Bus Matrix identifies conformed dimension candidates by mapping business processes to subject areas
> - Focus is on efficient end-delivery of analytical data; more user-oriented
>
> Both approaches recognize that: warehouses store data from other systems, organize it to increase value, make data accessible for analysis, and serve authorized stakeholders.

---

### Q3. What is the DW Bus Matrix and how is it used? [recall]

> [!answer]- Show Answer
> The **DW Bus Matrix** is a planning tool that shows the intersection of:
> - **Rows**: Business processes that generate fact data (e.g., Sales, Inventory, Orders)
> - **Columns**: Data subject areas representing dimensions (e.g., Date, Product, Store, Vendor)
>
> Where multiple business processes use the same dimension, that dimension is a candidate for a **conformed dimension**. For example, if Sales, Inventory, and Orders all use Date and Product, those are conformed dimension candidates.
>
> The bus matrix is used to:
> - Represent long-term data content requirements independent of technology
> - Scope manageable development increments
> - Communicate the release roadmap to stakeholders
> - Ensure enterprise-level integration through the conformed dimensions bus

---

### Q4. A company has three source systems that each use different timestamp formats. The DW team is choosing a CDC method. They need fast loads, can tolerate some data overlap, but cannot track deletes. Which CDC method best fits? [application]

> [!answer]- Show Answer
> The **Time-stamped Delta Load** method is the best fit:
> - **Complexity**: Low
> - **Speed**: Fast for both fact and dimension loads
> - **Overlap**: Yes (some data may already be present in the target)
> - **Deletes**: No (does NOT track deletes)
>
> The requirement states that they need fast loads and can tolerate overlap, but cannot track deletes -- this exactly matches the Time-stamped Delta profile. The source systems stamp changes with system date/time, and the DW extracts only changes since the last load.
>
> If they later need delete tracking, they would need to move to Log Table Delta (medium complexity, tracks deletes) or Database Transaction Log (high complexity, tracks deletes).

---

### Q5. Compare an Operational Data Store (ODS) with a Data Warehouse. When would you use each? [recall]

> [!answer]- Show Answer
> | Characteristic | ODS | Data Warehouse |
> |---|---|---|
> | **Data window** | Current or near-term (30-90 days) | Historical (often years) |
> | **Volatility** | Data is volatile (updated) | Data is non-volatile (appended) |
> | **Latency** | Low latency, supports operational use | Higher latency |
> | **Refresh speed** | Can be refreshed quickly | Slower to refresh |
> | **Primary use** | Operational reporting, tactical decisions | Strategic analysis, compliance, BI |
>
> **Use an ODS when**: Near-real-time integrated data is needed for operational decisions, or to audit the data warehouse.
>
> **Use a DW when**: Historical analysis, trend reporting, compliance reporting, or strategic BI is needed. The DW is the primary source for data marts and cubes.
>
> Many organizations have merged their ODS into the existing DW or data mart architecture as real-time integration techniques have improved.

---

### Q6. What are the three OLAP architecture types (ROLAP, MOLAP, HOLAP) and name three common OLAP operations? [recall]

> [!answer]- Show Answer
> **OLAP Architecture Types**:
> 1. **ROLAP (Relational OLAP)**: Implements multi-dimensionality in 2D tables of an RDBMS; uses star schema joins
> 2. **MOLAP (Multi-dimensional OLAP)**: Uses proprietary, specialized multi-dimensional database technology
> 3. **HOLAP (Hybrid OLAP)**: Combination of ROLAP and MOLAP; part of data stored in each; varies by designer control
>
> **Common OLAP Operations** (any 3 of 5):
> 1. **Slice**: Subset corresponding to a single value for one dimension
> 2. **Dice**: Slice on more than two dimensions (multiple consecutive slices)
> 3. **Drill down/up**: Navigate from most summarized (up) to most detailed (down)
> 4. **Roll-up**: Compute aggregations across one or more dimensions using a formula
> 5. **Pivot**: Change the dimensional orientation of a report or page display

---

### Q7. A DW team notices that source system data is clean internally but causes integration problems when combined. The DW is often the first place where these quality issues surface. What should the team do, and how does this relate to DW guiding principles? [application]

> [!answer]- Show Answer
> This is a common scenario: data may be of high quality within its sources, but differences between sources (structure, formats, value representations) cause integration problems in the DW.
>
> **Actions**:
> - **Profile the source data** to understand discrepancies between sources before attempting integration
> - **Collaborate with Data Quality and Data Governance teams** and SMEs to understand data context
> - **Establish a data quality feedback loop**: Identify issues, inform source system owners, and hold them accountable for fixes
> - **Document data remediation rules** so they can be governed
> - **Design the DW integration layer** to handle known inconsistencies through transformation rules
> - **Ensure end-to-end Metadata** so data consumers can answer "What does this mean?" and "Where did this come from?"
>
> **Related guiding principles**:
> - **"Build Metadata with the warehouse"**: Capture lineage and transformation logic as part of development
> - **"Collaborate"**: Work with Data Governance, Data Quality, and other initiatives
> - **"Promote transparency and self-service"**: Provide context (Metadata) so consumers understand the data
> - **"Start with the end in mind"**: Let business priorities drive what gets integrated and how

---

### Q8. What are the three approaches to near-real-time data integration in a DW, and how do they differ in where data accumulates? [recall]

> [!answer]- Show Answer
> 1. **Trickle Feeds (Source Accumulation)**: Rather than nightly batch, run batch loads more frequently (hourly, every 5 minutes) or when a threshold is reached (e.g., 300 transactions). Data accumulates at the **source** until the next feed. Must ensure feed ordering if a batch takes longer than the interval.
>
> 2. **Messaging (Bus Accumulation)**: Small packets (messages, events, transactions) are published to a **bus** in real-time as they occur. Target systems subscribe and process packets incrementally. Source and target systems are independent. DaaS frequently uses this method. Data accumulates on the **bus**.
>
> 3. **Streaming (Target Accumulation)**: The **target** system collects data as it is received into a buffer/queue and processes it in order. Results or aggregates may later feed the warehouse. Data accumulates at the **target**.
>
> The key differentiator is **where data is held while waiting to be processed**: source, bus, or target.

---

### Q9. Why does the DMBOK2 recommend "summarize and optimize last, not first"? What risks arise from premature summarization? [analysis]

> [!answer]- Show Answer
> The principle means: **build on atomic (detail) data first**, then aggregate and summarize only to meet specific requirements and ensure performance -- never to replace the detail.
>
> **Reasons**:
> - Atomic data is the foundation; it supports any type of analysis, even those not yet anticipated
> - Summarized data serves specific, known use cases but cannot answer new questions
> - If you only store summaries, you lose the ability to drill down, investigate anomalies, or recompute aggregates when business rules change
>
> **Risks of premature summarization**:
> - **Loss of analytical flexibility**: Cannot perform ad-hoc analysis at the detail level
> - **Inability to trace or audit**: Cannot verify summaries against source detail
> - **Grain changes**: If future requirements need finer grain, the data is not available
> - **Incorrect aggregations**: If business rules change (e.g., how revenue is calculated), pre-aggregated data cannot be recalculated
> - **Masked data quality issues**: Problems in atomic data are hidden by aggregation
>
> The Data Vault approach specifically addresses this by retaining history inside the vault, making it possible to reload facts when later increments introduce grain changes.

---

> [!summary]- Pattern Summary (click to view)
> - Inmon: normalized, subject-oriented, integrated, time-variant, non-volatile; CIF with central DW feeding dependent data marts
> - Kimball: dimensional model (star schema), facts + dimensions, conformed dimensions via bus; DW = collection of integrated data marts
> - Data Vault: normalized atomic history, supports grain changes, virtualizable presentation layer
> - DW Bus Matrix maps business processes (facts) to subject areas (dimensions); identifies conformed dimension candidates
> - ODS = near-term, volatile, low latency; DW = historical, non-volatile, higher latency
> - CDC methods differ by complexity, speed, overlap handling, and delete tracking
> - Near-real-time: trickle (source), messaging (bus), streaming (target) -- accumulation location is key
> - OLAP: slice, dice, drill, roll-up, pivot; ROLAP/MOLAP/HOLAP architectures
> - Build on atomic data first; summarize last -- never sacrifice detail for premature optimization
