---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 8
keywords: data integration, interoperability, ETL, ELT, hub-and-spoke, canonical model, SOA, ESB, CDC, data lineage, data profiling
---

# Data Integration and Interoperability Practice

#dmbok2 #data-integration

## Related Concepts
- [[Data Integration and Interoperability]]
- [[Data Storage and Operations]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Metadata Management]]

> [!hint]- Key Patterns (click to view)
> - **ETL vs. ELT**: ETL transforms before loading (traditional); ELT loads raw data first, then transforms on target (Big Data/data lakes).
> - **Point-to-point** interfaces approach s-squared (systems squared) -- unmanageable at scale.
> - **Hub-and-spoke** reduces interfaces dramatically; justified at 3+ systems, critical at 100+.
> - **Canonical model**: Standard format so each system transforms only to/from the common model.
> - **Tight coupling** (synchronous, dependent) vs. **Loose coupling** (asynchronous, independent -- preferred).
> - **Data profiling**: Actual data ALWAYS differs from assumptions. Never skip it.
> - **CDC**: Only sends deltas, not entire datasets. Can be data-based or log-based.
> - **Batch delta** (changes since last send) vs. **Batch snapshot** (full point-in-time data).

---

### Q1. What does ETL stand for and what are the three basic steps? [recall]

> [!answer]- Show Answer
> **ETL** = **Extract, Transform, Load**
> 1. **Extract**: Select and extract required data from source systems; stage in physical store or memory
> 2. **Transform**: Make data compatible with target structure (format changes, structure changes, semantic conversion, de-duping, re-ordering)
> 3. **Load**: Physically store or present the transformed data in the target system
>
> ETL can be performed as batch (periodic schedule) or real-time (event-driven). The intermediate data may be physically staged on disk or virtually stored in memory.

---

### Q2. When would you use ELT instead of ETL? [recall]

> [!answer]- Show Answer
> Use **ELT** (Extract, Load, Transform) when the **target system has more transformation capability** than either the source or an intermediary system. The order is switched so that:
> - Data is loaded first into the target system in raw form
> - Transformations occur **after** loading, often as part of the target system's processing
>
> ELT is common in **Big Data environments** where raw data is loaded into a **data lake** (see Chapter 14). It allows source data to be instantiated as raw data, which can be useful for other processes beyond the original transformation purpose.

---

### Q3. An organization has 50 applications that need to share data with each other. Compare the point-to-point approach vs. hub-and-spoke. Which should they choose? [application]

> [!answer]- Show Answer
> **Point-to-point**: Each system connects directly to every other system. With 50 applications, the number of interfaces approaches **50 squared = 2,500** potential interfaces. This:
> - Overwhelms IT support capabilities
> - Creates inconsistencies when multiple systems need different versions of data
> - Impacts source system performance from multiple extracts
>
> **Hub-and-spoke**: All systems exchange data through a central hub. With 50 applications:
> - Only **50 interfaces needed** (each system connects to the hub)
> - Provides **consistent views** of data
> - Minimizes **performance impact** on source systems
> - Adding new systems only requires building one interface to the hub
>
> **They should choose hub-and-spoke.** Hub-and-spoke becomes cost-justified with even a small number of systems, but it is **critical** for managing portfolios of 100+ systems. With 50 systems, it is clearly the correct choice.

---

### Q4. What is a canonical data model and why is it important? [recall]

> [!answer]- Show Answer
> A **canonical data model** is a common model used by an organization that **standardizes the format** in which data will be shared. In a hub-and-spoke design, all systems transform data only to/from the canonical model, rather than to every other system's format.
>
> **Importance:**
> - **Limits the number of transformations**: Each system needs only one transformation (to/from canonical) instead of one per target system
> - **Significantly reduces complexity** and cost of data interoperability
> - Justifiable for **3+ systems**; critical for **100+ systems**
> - Although developing a shared format is a major undertaking, the long-term savings outweigh the cost
>
> Example: Rather than System A transforming to System B's format AND System C's format AND System D's format, System A only transforms to the canonical model once.

---

### Q5. What is the difference between tightly coupled and loosely coupled systems? Which is preferred? [recall]

> [!answer]- Show Answer
> - **Tightly coupled**: Systems have a **synchronous** interface; one waits for a response from the other. If one is unavailable, both are effectively unavailable. Business continuity plans must be the same for both.
> - **Loosely coupled**: Data is passed **without waiting for a response**. One system may be unavailable without causing the other to be unavailable. Implemented via services, APIs, or message queues.
>
> **Loosely coupled is preferred** because:
> - Systems can be replaced without rewriting interfacing systems
> - One system's failure doesn't cascade
> - SOA with an Enterprise Service Bus is an example
> - Interaction points are well-defined, enabling system independence

---

### Q6. A financial services company processes millions of securities trades daily. They need to detect fraudulent transactions in real-time as they occur. What DII concept best addresses this requirement, and what does it need? [application]

> [!answer]- Show Answer
> This requires **Complex Event Processing (CEP)**. CEP combines data from multiple sources to identify **meaningful events** (such as suspected fraudulent charges) and **automatically trigger real-time response**.
>
> **CEP requires:**
> 1. **Preparation of historical data** about individuals, organizations, or products and pre-population of predictive models
> 2. **Processing the real-time data stream** to fully populate the predictive model and identify meaningful events (threats)
> 3. **Executing triggered actions** in response to predictions (e.g., blocking a suspicious transaction)
>
> **Technical requirements:**
> - Ultra-low latency environment (in-memory databases, solid-state disk, streaming data)
> - Massive multi-processing to avoid bottlenecks
> - Rules to guide event processing and routing
> - A **business rules engine** so non-technical users can update predictive models without code changes
> - Often tied to Big Data due to volume and variety

---

### Q7. Why is data profiling critical before designing a data integration solution? [recall]

> [!answer]- Show Answer
> Data profiling is critical because **actual data structure and contents ALWAYS differ from what is assumed**. Sometimes differences are small, but other times they are large enough to **derail an integration effort**.
>
> Profiling helps integration teams by analyzing:
> - Data **format** as defined vs. inferred from actual data
> - Data **population** (levels of null, blank, or defaulted data)
> - Data **values** and correspondence to valid value sets
> - **Patterns and relationships** within the data set (cardinality rules)
> - **Relationships to other data sets**
>
> **If profiling is skipped**, information that should influence design will not be discovered until **testing or operations** -- when it is much more costly to address. Profile both sources AND targets to understand how to transform data to match requirements.

---

### Q8. What is data lineage and why is it becoming increasingly important? [recall]

> [!answer]- Show Answer
> **Data lineage** documents how data is acquired or created by the organization, where it moves and is changed, and how it is used for analytics, decision-making, or event triggering. Detailed lineage includes transformation rules and frequency of changes.
>
> It is increasingly important because:
> - **Emerging compliance standards** (e.g., Solvency II in Europe) require organizations to describe where data originated and how it has been changed
> - **Data sharing agreements** may stipulate limitations on data use -- knowing where data moves is necessary for compliance
> - **Impact analysis**: Forward and backward lineage is critical when making changes to data structures, flows, or processing
> - **Identifying improvement opportunities**: Analysis may reveal old transformations that are undone later, or code that can be simplified

---

### Q9. An ESB-based integration solution is experiencing data consistency issues. Target systems sometimes process master data transactions out of order. What is the root cause and how should it be fixed? [application]

> [!answer]- Show Answer
> The root cause is a **state management and process dependency** issue. In near-real-time ESB solutions, data coming into the target may not arrive in the exact order the target needs to build correct data.
>
> **Specific problem**: Master Data or dimensional data must be processed **prior to** transactional data that references it. If a transaction referencing a new customer arrives before the customer master record, it will fail or create inconsistencies.
>
> **Fix:**
> - The target application load process must **monitor state information and process dependencies**
> - Implement **orchestration rules** ensuring master/reference data is processed before dependent transactional data
> - Design the ESB to manage **message ordering** based on data type dependencies
> - Use a **canonical message model** that clearly distinguishes message types and priorities
> - Consider implementing **process controls** including exception logs, alerts, and job dependency charts with remediation options

---

### Q10. An organization is implementing an enterprise-wide data integration program. However, individual application teams resist centralizing their integration solutions, preferring to manage their own. The software vendors supporting those teams also encourage local tools. Analyze this organizational challenge and recommend an approach. [analysis]

> [!answer]- Show Answer
> **Root causes of resistance:**
> - Application teams perceive local management as **less costly** than enterprise solutions
> - Vendors prefer teams use their specific data integration tools (revenue motivation)
> - Local teams understand their own data better and fear losing control
>
> **Risks of decentralized approach:**
> - Multiple technologies require different skills, driving up **support costs**
> - Proliferation of point-to-point solutions creates **thousands of interfaces**
> - Inconsistent data formats and transformations across the organization
> - Inability to reuse integration components
>
> **Recommended approach:**
> 1. **Sponsor from enterprise level**: Implementation must be sponsored at a level with authority over solution design and technology purchase (e.g., IT enterprise architecture)
> 2. **Center of Excellence**: Build a central team specializing in enterprise DII design/deployment. Local teams collaborate with it.
> 3. **Positive incentives**: Fund integration technology centrally; provide shared support pools
> 4. **Negative incentives**: Refuse to approve implementation of new alternative integration technologies
> 5. **Hybrid responsibility**: Local teams take primary responsibility for managing solutions and resolving problems, escalating to the Center of Excellence when needed
> 6. **Business focus**: Ensure participants in every project include business-oriented people, not just tool experts -- otherwise projects become technology-focused and lose business goals
> 7. **Review all transformation mappings** with business SMEs in each involved system

---

> [!summary]- Pattern Summary (click to view)
> **Core Process**: ETL (Extract, Transform, Load) is fundamental to all DII. ELT reverses transform/load order for Big Data environments.
>
> **Interaction Models**: Point-to-point (s-squared problem) < Hub-and-spoke (central hub, preferred) < Publish-subscribe (push/pull).
>
> **Coupling**: Tight (synchronous, risky) vs. Loose (asynchronous, preferred). ESB and SOA implement loose coupling.
>
> **Latency Spectrum**: Batch > Micro-batch > CDC > Near-real-time > Asynchronous > Synchronous > Streaming.
>
> **Key Artifacts**: Canonical model (standard shared format), Data Sharing Agreements (MOUs), Data Lineage documentation, Metadata repositories.
>
> **Planning Essentials**: Data Discovery, Data Profiling (never skip!), Business Rules collection, Source-to-Target Mapping.
>
> **Governance**: Business stakeholders own transformation rules. SOA registry controls service catalog. Data integration solutions must be in same backup/recovery tier as most critical target system.
