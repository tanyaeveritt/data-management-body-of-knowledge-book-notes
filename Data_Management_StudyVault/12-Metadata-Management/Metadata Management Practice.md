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
tags:
  - dmbok2
  - metadata
  - practice
---

# Metadata Management -- Practice Questions

## Related Concepts

- [[Metadata Management]]
- [[Data Governance]]
- [[Data Quality]]
- [[Data Warehousing and BI]]
- [[Data Integration and Interoperability]]
- [[Data Architecture]]
- [[Data Modeling and Design]]

---

> [!hint]- Key Patterns (click to view)
> - Three Metadata types: business (content/condition), technical (systems/structures), operational (processing/access)
> - Library analogy: no Metadata = no card catalog = cannot find or use data
> - Business glossary serves 3 audiences: business users, stewards, technical users
> - Four architectures: centralized (copies in one repo), distributed (real-time retrieval, no repo), hybrid (common repo + delegate to sources), bi-directional (feedback to sources)
> - Lineage: "As Implemented" (from code) vs. "As Designed" (from specifications); stitching connects pieces
> - MetaModel = a data model OF the Metadata repository
> - Metadata for Big Data: tag on ingest, profile, identify PII

---

### Q1. Name the three types of Metadata and give two examples of each. [recall]

> [!answer]- Show Answer
> **Business Metadata** (content and condition of data):
> - Definitions and descriptions of data sets, tables, and columns
> - Business rules, transformation rules, calculations, and derivations
>
> **Technical Metadata** (technical details, systems, and data movement):
> - Physical database table and column names
> - ETL job details and source-to-target mapping documentation
>
> **Operational Metadata** (processing and access details):
> - Batch job execution logs and history of extracts/results
> - Query access patterns, frequency, and execution time
>
> Note: These categories describe where Metadata originates, not strict usage boundaries -- technical staff use business Metadata and vice versa.

---

### Q2. What is the DMBOK2's library analogy for Metadata, and why is it effective? [recall]

> [!answer]- Show Answer
> The analogy: **An organization without Metadata is like a library without a card catalog.** Without a catalog, readers wouldn't know how to find a specific book or topic. The catalog provides necessary information (which materials exist and where they are shelved) and enables discovery using different starting points (subject area, author, title).
>
> The analogy is effective because it illustrates that:
> - Without Metadata, an organization doesn't know what data it has, what it represents, where it originates, how it moves, who has access, or what quality means
> - Metadata enables multiple discovery paths (like subject, author, or title in a catalog)
> - Just as a large library is unusable without a catalog, large organizations with lots of data are unable to function effectively without Metadata
> - The analogy extends to unstructured data: books/magazines in a library are examples of unstructured data that need Metadata for findability

---

### Q3. Name the four Metadata architecture types and state the key trade-off for each. [recall]

> [!answer]- Show Answer
> 1. **Centralized**: Single Metadata repository with copies from all sources.
>    - *Trade-off*: High availability and global search, but complex sync processes and costly maintenance
>
> 2. **Distributed**: Single access point, no persistent repository; retrieves from sources in real time.
>    - *Trade-off*: Always current with minimal batch processing, but no global search, no user-defined Metadata, dependent on source availability
>
> 3. **Hybrid**: Central repository stores critical/user-added Metadata; delegates to sources for detail.
>    - *Trade-off*: Balances currency and enhanced Metadata with global search, but source availability limits detailed queries
>
> 4. **Bi-directional**: Changes in any part feed back to the original source via the repository (broker).
>    - *Trade-off*: Enables source correction from the repository, but extremely complex change management; must trap and resolve changes systematically

---

### Q4. A company's DW team discovers that the same data element is named differently in three source systems. They want to trace how this element is transformed as it moves from source to DW to reports. What Metadata concept should they use, and what two approaches can guide the discovery? [application]

> [!answer]- Show Answer
> They should use **Data Lineage** -- specifically, they need both:
> - **"As Implemented" lineage**: Extracted from programming code in data integration tools, showing actual transformations applied
> - **"As Designed" lineage**: From mapping specification documents, showing intended transformations
> - **Stitching**: The process of connecting lineage pieces from various tools into a holistic visualization from source to final destination
>
> **Two discovery approaches**:
> 1. **Business focus**: Start from the target location (reports/DW) and trace back to the source systems. Limits scope to the specific data element, enabling consumers to understand what happens to it as it moves. If coupled with data quality measurements, can pinpoint where system design adversely impacts quality.
>
> 2. **Technical focus**: Start at source systems, identify all immediate consumers, then identify subsequent consumers layer by layer. Enables answering discovery questions like "Where is social security number?" or impact analysis like "What systems are impacted if column width changes?" More comprehensive but more complex to manage.

---

### Q5. What is a MetaModel and why is it valuable? [recall]

> [!answer]- Show Answer
> A **MetaModel** is a data model for the Metadata repository -- it defines the structure, entities, and relationships used to store Metadata. It is created as one of the first design steps after the Metadata strategy is complete and business requirements are understood.
>
> Different levels may be developed:
> - A **high-level conceptual model** explaining relationships between systems
> - A **lower-level model** detailing attributions to describe elements and processes
>
> **Value**:
> - Serves as a planning tool and a means of articulating requirements
> - Guides the physical implementation of the Metadata repository
> - Is itself a valuable source of Metadata (meta-Metadata)
> - Ensures the repository design is generic and enterprise-aligned, not merely reflecting source system database designs

---

### Q6. A business glossary has been created but adoption is low -- business users rarely access it, and definitions are often incomplete. What governance improvements does the DMBOK2 suggest? [application]

> [!answer]- Show Answer
> **For improving adoption and quality**:
> - **Simplify search**: The simpler the search, the more likely content will be used; ease of use is critical
> - **Prioritize robust content**: The most important characteristic is that it contains comprehensive, accurate content -- this is more valuable than interface features
> - **Implement governance lifecycle**: Require terms to progress through status gates: candidate -> approved -> published -> replaced/retired
> - **Assign Data Stewards**: Make stewards responsible for development, use, operations, and reporting; including managing term associations and categorization
> - **Track and report**: Generate reports on new terms not yet reviewed, pending status terms, and terms missing definitions or other attributes
> - **Do not "print the glossary"**: Content is not static; always use the live system
> - **Create a feedback mechanism**: Allow consumers to inform the Metadata Management team of incorrect or out-of-date content
>
> **Organizational/cultural**:
> - Socialize the value of Metadata to encourage business use AND contribution of business expertise
> - Ensure staff know how to access and use Metadata
> - Hold process owners accountable for Metadata quality (Metadata is often a by-product of modeling, SDLC, business process definition)

---

### Q7. Describe the differences between a Data Dictionary and a Business Glossary. [recall]

> [!answer]- Show Answer
> **Data Dictionary**:
> - Defines the structure and contents of data sets, often for a single database, application, or warehouse
> - Manages names, descriptions, structure, characteristics, storage requirements, default values, relationships, uniqueness, and other attributes of every data element in a model
> - Contains table/file definitions
> - Embedded in database tools for creation, operation, manipulation of data
> - More technical in nature; must be extracted from database or modeling tools to be shared
>
> **Business Glossary**:
> - Documents and stores an organization's business concepts and terminology, definitions, and relationships between terms
> - Serves three audiences: business users, Data Stewards, and technical users
> - Includes attributes like term name, definition, acronym, synonyms, responsible business unit, taxonomy association, conflicting definitions, algorithms, lineage, authoritative source
> - Focused on enterprise understanding; requires governance and stewardship
>
> **Relationship**: Logical data model content often feeds the data dictionary, which in turn can inform the business glossary. Both are sources of Metadata, but they serve different purposes and audiences.

---

### Q8. Why is managing Metadata for a data lake especially important, and what minimum set of Metadata should be captured on ingestion? [application]

> [!answer]- Show Answer
> **Why it's especially important**:
> - Data lakes ingest data from diverse sources in varying formats (structured, semi-structured, unstructured)
> - Unlike data warehouses that integrate data before landing, data lakes ingest data BEFORE integration
> - Without Metadata tagging on ingestion, the data lake becomes a "data swamp" -- ingested data cannot be found, understood, or trusted later
>
> **Minimum Metadata attributes for each ingested object**:
> - **Name**: Identifier for the data set
> - **Format**: Structure/type of the data
> - **Source**: Where the data came from
> - **Version**: Which version of the data
> - **Date received**: When it was ingested
>
> This produces a **catalog of data lake contents**.
>
> **Additional capabilities**:
> - Profiling engines can identify data domains, relationships, and quality issues during ingestion
> - Tags can identify sensitive/private data (PII) automatically
> - Data scientists may add confidence scores, textual identifiers, and behavior cluster codes post-ingestion

---

### Q9. An organization has rapidly growing Metadata from many new source systems. They need user-defined Metadata, global search capability, and near-real-time Metadata for some systems. Which architecture is most appropriate, and why would the alternatives fall short? [analysis]

> [!answer]- Show Answer
> The **Hybrid Metadata Architecture** is most appropriate.
>
> **Why Hybrid fits**:
> - Stores user-defined Metadata and critical standardized items in a central repository (meeting the user-defined requirement)
> - Enables global search across the centralized common Metadata (meeting the global search requirement)
> - Delegates to source systems for detailed Metadata, providing near-real-time retrieval (meeting the currency requirement)
> - The DMBOK2 specifically notes that organizations with rapidly-changing operational Metadata, those needing consistent/uniform Metadata, and those experiencing substantial Metadata growth benefit most from hybrid architecture
>
> **Why alternatives fall short**:
> - **Centralized**: Would support user-defined Metadata and global search, but with rapidly growing sources, complex sync processes become costly and Metadata may not be current enough (latency between syncs)
> - **Distributed**: Provides real-time Metadata but does NOT support user-defined Metadata (no persistent repository) and does NOT support global search across sources
> - **Bi-directional**: More sophisticated but introduces extreme complexity for change management -- the organization would need to manage feedback to ALL rapidly growing sources, which is impractical at their scale

---

> [!summary]- Pattern Summary (click to view)
> - Three Metadata types: business (what the data means), technical (how it's stored/moved), operational (how it's processed/accessed)
> - Business glossary: three audiences, governance lifecycle, robust content over interface polish
> - Data dictionary: structure/contents for a specific database; business glossary: enterprise concepts/terminology
> - Four architectures: centralized, distributed, hybrid, bi-directional -- choose based on currency needs, growth rate, search requirements, and budget
> - Lineage: "As Implemented" (code) vs. "As Designed" (specs); business focus (target-back) vs. technical focus (source-forward); stitching connects pieces
> - MetaModel = data model OF the Metadata repository
> - Data lake Metadata: tag on ingest (name, format, source, version, date); profile to find PII
> - ISO/IEC 11179: standard for Metadata registry and data element standardization
> - To be data-driven, an organization must be Metadata-driven
