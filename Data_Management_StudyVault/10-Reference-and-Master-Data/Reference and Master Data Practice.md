---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 10"
keywords:
  - reference data
  - master data
  - MDM
  - entity resolution
  - golden record
  - matching
tags:
  - dmbok2
  - master-data
  - practice
---

# Reference and Master Data -- Practice Questions

## Related Concepts

- [[Reference and Master Data]]
- [[Data Quality]]
- [[Data Governance]]
- [[Data Integration and Interoperability]]
- [[Data Architecture]]
- [[Data Modeling and Design]]
- [[Metadata Management]]

---

> [!hint]- Key Patterns (click to view)
> - Reference Data vs. Master Data: size, volatility, entity resolution requirement
> - Three hub architectures: Registry, Transaction Hub, Consolidated -- know trade-offs
> - Entity resolution: deterministic (rule-based) vs. probabilistic (statistical, self-improving)
> - Match-Link (cross-reference without merging) vs. Match-Merge (single reconciled record)
> - False Positive = different entities linked; False Negative = same entity not linked
> - Golden Record is not guaranteed 100% accurate; Trusted Source = "best version we have"
> - System of Record (creates/maintains) vs. System of Reference (provides reliable access)
> - Chisholm taxonomy: Metadata, Reference Data, Enterprise Structure Data, Transaction Structure Data, Transaction Activity Data, Transaction Audit Data

---

### Q1. What is the fundamental difference between Reference Data and Master Data? [recall]

> [!answer]- Show Answer
> **Reference Data** is used solely to characterize or classify other data, or to relate data to information beyond the organization (e.g., country codes, status codes). It consists of code-description pairs, is relatively small, less volatile, and does NOT require entity resolution.
>
> **Master Data** represents business entities (customers, products, employees) that provide context for transactions. It is larger, more complex, requires entity resolution (matching and merging), and must be managed for identity consistency across systems.
>
> Both are shared resources that provide context for transactional data and should be managed at the enterprise level.

---

### Q2. Name and describe the three basic data sharing hub architectures for Master Data. [recall]

> [!answer]- Show Answer
> 1. **Registry**: An index that points to Master Data in various systems of record. Easy to implement (few SOR changes), but requires complex queries and business rules in multiple places.
>
> 2. **Transaction Hub**: All Master Data exists within the hub, which IS the system of record. Provides better governance and a consistent source, but is costly to implement because update functionality must be removed from existing SORs.
>
> 3. **Consolidated (Hybrid)**: SORs manage Master Data locally. Data is consolidated into a common repository (system of reference) for sharing. Provides an enterprise view with limited SOR impact, but involves data replication and latency between hub and SORs.

---

### Q3. What is the difference between deterministic and probabilistic matching in entity resolution? [recall]

> [!answer]- Show Answer
> **Deterministic matching** relies on defined patterns and rules for assigning weights and scores. It is predictable -- the same rules always yield the same results. It works well out-of-the-box but is limited to situations anticipated by the rule developers.
>
> **Probabilistic matching** uses statistical techniques to assess the probability that two records represent the same entity. It learns from data samples and self-adjusts, so results may be nondeterministic. However, it can improve matching precision as more data is analyzed.
>
> The two approaches can be used together for better results.

---

### Q4. An organization discovers that "J. Smith" at "123 Main, Dataland, DA" and "John Smith" at "123 Main, Dataland, SQ 98765" share the same phone number. The MDM system links them as the same person. Later, it turns out they are different people. What type of error occurred, and how should the organization respond? [application]

> [!answer]- Show Answer
> This is a **false positive** -- two references that do NOT represent the same entity were linked with a single identifier (one identifier referring to more than one real-world entity).
>
> Response:
> - **Unmerge** the records by reversing the match, restoring the original identifiers. This is why maintaining match history is essential -- so matches can be undone.
> - **Review and tune** the matching rules (similarity thresholds) to reduce future false positives, though care must be taken not to increase false negatives.
> - **Analyze match rate metrics** to monitor the impact of rule changes.
> - Consider using **match-link** instead of **match-merge** for cases with lower confidence, so stewards can review before merging.

---

### Q5. What are the four Reference Data structures described in the DMBOK2? Provide an example for each. [recall]

> [!answer]- Show Answer
> 1. **Simple Lists**: Code-description pairs. Example: ISO country codes (US = United States, GB = United Kingdom).
>
> 2. **Cross-Reference Lists**: Translate between different code sets for the same concept. Example: US State codes mapped across USPS (CA), FIPS (06), and ISO (US-CA) standards.
>
> 3. **Taxonomies**: Hierarchical structures with parent-child relationships. Example: UNSPSC product classification (Floral Plants -> Rose Plants, Orchid Plants) or NAICS industry codes (Retail Trade -> Food and Beverage Stores -> Specialty Food Stores).
>
> 4. **Ontologies**: Complex taxonomies used for content management and characterizing data beyond the organization. Example: ontologies managing website content for classification and navigation.

---

### Q6. Why does the DMBOK2 caution against using the term "Golden Record"? What alternative term is preferred? [recall]

> [!answer]- Show Answer
> The term **Golden Record** implies a "single version of the truth" that is 100% complete and accurate. In practice, merging data from multiple sources rarely achieves this, especially in organizations with multiple systems of record. Promising data is "golden" when it is not can **undermine data consumer confidence**.
>
> The preferred term is **Trusted Source**, meaning "the best version we have." This puts emphasis on how data is defined and managed to reach a best version, and it helps different consumers (e.g., Finance vs. Marketing) see the component pieces of the "single version" relevant to them.

---

### Q7. A healthcare company must transition from ICD-9 to ICD-10 diagnostic codes. What type of Reference Data change is this, and what makes it particularly challenging? [application]

> [!answer]- Show Answer
> This is a **structural change to an external Reference Data set** -- not just a row-level update, but a fundamental change in format, granularity, and organization principles.
>
> Challenges:
> - **Different format**: ICD-10 codes are structured differently from ICD-9
> - **Different granularity**: ICD-10 is much more specific, conveying more information per code (68,000 ICD-10 codes vs. 13,000 ICD-9 codes)
> - **No simple one-to-one mapping**: Different values represent the same concepts with different levels of detail
> - **System changes required**: Applications, data entry interfaces, processing rules, and reports all need modification
> - **Historical data**: Reporting across the transition period requires crosswalk mappings
> - **Organizational planning**: The mandated use of ICD-10 in the US required significant advance planning for system and process changes
>
> The change request process should follow: Receive -> Identify Stakeholders -> Identify Impact -> Decide -> Update and Communicate.

---

### Q8. Compare Match-Link and Match-Merge reconciliation workflows. In what situations would you prefer each? [analysis]

> [!answer]- Show Answer
> **Match-Link**:
> - Identifies and cross-references records that relate to a master record WITHOUT updating the content of the cross-referenced record
> - Easier to implement and much easier to reverse
> - Acts on the cross-reference registry, not individual attributes
> - May be more difficult to present comprehensive information from multiple records
> - **Prefer when**: Data confidence is lower, reversibility is important, or the organization wants steward review before consolidating
>
> **Match-Merge**:
> - Matches records and merges data into a single, unified, reconciled, comprehensive record
> - If rules apply across data sources, creates a single record in each data store
> - Complex due to the need to determine which field from which source to trust
> - Costly to reverse if a false merge occurs
> - New sources can change trust rules over time
> - **Prefer when**: High confidence in matching, strong need for a unified record, and the organization can invest in governance to manage complexity
>
> **Key trade-off**: Match-merge provides a richer unified view but carries higher risk and reversal cost. Match-link is safer and more flexible but requires more work to assemble a complete picture. Organizations may use match-link as a stepping stone before committing to match-merge as matching rules mature.

---

### Q9. An enterprise has five source systems contributing customer data to an MDM hub. A vendor like Dun & Bradstreet offers a reference directory. How does using this directory reduce matching complexity? [analysis]

> [!answer]- Show Answer
> Without the reference directory, each of the 5 source systems would need to be compared against each other, yielding **10 comparison points** (combinatorial: 5 choose 2 = 10).
>
> With the reference directory as a common baseline, each source system is compared against the directory instead, yielding only **5 comparison points** (one per source).
>
> Additional benefits:
> - **Starting point for matching/linking**: The directory provides standardized identifiers (e.g., DUNS Number) for records
> - **Additional data elements**: Attributes not easily available at record creation (e.g., NAICS classification, company hierarchy information) improve entity resolution quality
> - **Enrichment**: The directory supplements internal data with verified external data, improving match confidence
> - **Traceability**: As records match and reconcile with the directory, the trusted record deviates with traceability to source records, contributing attributes, and transformation rules

---

> [!summary]- Pattern Summary (click to view)
> - Reference Data = classify/characterize; Master Data = business entities for transactions
> - MDM is a discipline (people + process + tech), NOT just a tool
> - Entity resolution is the central challenge of MDM: matching, identity management, affiliation
> - Three hub types: Registry (easy, complex queries), Transaction Hub (consistent, costly), Consolidated (hybrid)
> - Deterministic matching = rules, predictable; Probabilistic = statistical, self-improving
> - False positive = wrong link; False negative = missed link
> - Golden Record overpromises; Trusted Source is preferred
> - Reference Data structures: lists, cross-references, taxonomies, ontologies
> - Change management for Reference Data: receive, identify stakeholders, assess impact, decide, communicate
