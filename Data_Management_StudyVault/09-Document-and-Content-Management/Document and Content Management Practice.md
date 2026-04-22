---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 9
keywords: document management, content management, records management, e-discovery, taxonomy, controlled vocabulary, ECM, GARP, ontology, unstructured data
---

# Document and Content Management Practice

#dmbok2 #content-management

## Related Concepts
- [[Document and Content Management]]
- [[Data Storage and Operations]]
- [[Data Security]]
- [[Data Integration and Interoperability]]
- [[Metadata Management]]

> [!hint]- Key Patterns (click to view)
> - **80% of stored data** is unstructured (outside relational databases).
> - **Taxonomy** = closed-world assumption; **Ontology** = open-world assumption (relationships can be inferred).
> - **GARP**: 8 principles -- Accountability, Integrity, Protection, Compliance, Availability, Retention, Disposition, Transparency.
> - **ANSI 859 control levels**: Formal > Revision > Custody (based on data criticality).
> - **Content delivery**: Push (scheduled, RSS) vs. Pull (user-initiated) vs. Interactive (real-time exchange).
> - **E-discovery (EDRM)**: 8 phases from Identification through Presentation; data volume decreases as relevance increases.
> - **Vital Record**: Required to resume operations after a disaster.
> - **Precision** (relevant among retrieved) vs. **Recall** (retrieved among all relevant).
> - **Folksonomy**: Social tagging; not authoritative but reflects actual user vocabulary.

---

### Q1. What percentage of stored data is estimated to be unstructured, and where is it typically found? [recall]

> [!answer]- Show Answer
> Estimated **80% of all stored data** is maintained outside relational databases (unstructured). This includes:
> - Word processing documents, email, social media, chats
> - Flat files, spreadsheets, XML files
> - Transactional messages, reports, graphics
> - Digital images, microfiche, video recordings, audio recordings
> - Paper files
>
> The term "unstructured" is somewhat misleading as there is often some structure in documents (e.g., chapters, headers). Some prefer "non-tabular" or "semi-structured." The fundamental principles of data management apply to both structured and unstructured data.

---

### Q2. What are the ARMA GARP principles? [recall]

> [!answer]- Show Answer
> **GARP** (Generally Accepted Recordkeeping Principles) is a framework from ARMA International with **8 principles**:
> 1. **Accountability**: Assign senior executive; adopt policies; ensure auditability
> 2. **Integrity**: Guarantee authenticity and reliability of records
> 3. **Protection**: Ensure reasonable protection for personal/sensitive information
> 4. **Compliance**: Comply with applicable laws and binding authorities
> 5. **Availability**: Maintain information for timely, efficient, accurate retrieval
> 6. **Retention**: Retain for appropriate time considering all requirements
> 7. **Disposition**: Provide secure and appropriate disposition per policies and laws
> 8. **Transparency**: Document policies and processes in an available/understandable manner
>
> ARMA also has a **5-level Maturity Model**: Sub-Standard > In Development > Essential > Proactive > Transformational.

---

### Q3. A pharmaceutical company is responding to a lawsuit and has 90 days to produce relevant electronic documents. Describe the e-discovery process they should follow using the EDRM model. [application]

> [!answer]- Show Answer
> Following the **EDRM (Electronic Discovery Reference Model)**, the 8 phases are:
> 1. **Identification**: Perform Early Case Assessment (assess legal case for pertinent info like keywords, date ranges) and Early Data Assessment (identify types/locations of relevant data, interview custodians and IT personnel)
> 2. **Preservation**: Place identified potentially relevant data on a **legal hold** to prevent destruction
> 3. **Collection**: Acquire and transfer data from the company to legal counsel in a **legally defensible manner**
> 4. **Processing**: De-duplicate, search, and analyze to determine which items move forward
> 5. **Review**: Identify documents for response and privileged documents to withhold; depends heavily on **Metadata**
> 6. **Analysis**: Understand circumstances, facts, and potential evidence to formulate strategy
> 7. **Production**: Turn over to opposing counsel in agreed formats (native, near-native, image, or fielded data). Lineage is important -- no one wants to be accused of altering data.
> 8. **Presentation**: Display ESI at depositions, hearings, and trials
>
> **Key**: As e-discovery progresses, **data volume decreases** while **relevance increases**. The company should have had a **data map** and **litigation response playbook** prepared proactively.

---

### Q4. What is the difference between a taxonomy and an ontology? [recall]

> [!answer]- Show Answer
> Two key differences:
>
> | Aspect | Taxonomy / Data Model | Ontology |
> |--------|----------------------|----------|
> | **Structure** | Provides data content classifications with clear entity-attribute relationships | Entity, attribute, and content concepts can be **completely mixed**; differences identified through Metadata |
> | **Assumption** | **Closed-world**: What is defined is what is known -- nothing else | **Open-world**: Possible relationships are **inferred** based on existing relationships; something not explicitly declared can be true |
>
> Taxonomies evolved under **Library Sciences**. Today both taxonomy and ontology management fall under the **semantics management** space. Ontologies are the primary knowledge representation for the **Semantic Web** and use languages like RDFS and OWL.

---

### Q5. What are the three levels of document control defined by ANSI Standard 859, and when is each appropriate? [recall]

> [!answer]- Show Answer
> ANSI 859 defines three control levels based on data criticality:
> 1. **Formal control**: Most rigorous. Requires formal change initiation, thorough impact evaluation, decision by a change authority, and full status accounting. Used for: financial data, DD 250s, statements of work.
> 2. **Revision control**: Less formal. Requires notifying stakeholders and incrementing versions when changes occur. Used for: budgets, proposals in process, schedules.
> 3. **Custody control**: Least formal. Merely requires safe storage and a means of retrieval. Used for: action item lists, agendas, meeting notices.
>
> Criteria for determining control level: cost of providing/updating the asset, project impact of changes, consequences of change, need to reuse the asset, and maintenance of change history.

---

### Q6. An organization retains all electronic records indefinitely because "electronic space is cheap." Analyze the risks of this approach. [analysis]

> [!answer]- Show Answer
> This is a common but **risky** approach. The DMBOK2 identifies multiple problems:
>
> **Legal and regulatory risks:**
> - Information retained past legally required timeframes **remains discoverable for litigation**. Older unpurged records may contain damaging content that could have been lawfully disposed.
> - Some data becomes a **liability** if kept longer than specified (see also Chapter 6 on data purging).
>
> **Operational risks:**
> - Without proper **classification and Metadata**, unmanaged unstructured data cannot be inventoried or organized
> - Data without Metadata can be **misinterpreted** or **mishandled**, presenting privacy concerns
> - Finding relevant records becomes exponentially harder without a functional retention program
>
> **Cost risks:**
> - While raw storage is cheap, the **cost of reviewing** massive volumes during e-discovery is enormous
> - Managing, backing up, and securing growing volumes has compound costs
>
> **Recommended alternative:**
> - Implement a **retention and disposition policy** with clear timeframes based on legal, regulatory, fiscal, and operational requirements
> - Apply ARMA GARP **Retention** and **Disposition** principles
> - Classify records and apply appropriate retention schedules
> - Remove non-value-added information proactively

---

### Q7. What is a controlled vocabulary and what is the range of complexity from simplest to most complex? [recall]

> [!answer]- Show Answer
> A **controlled vocabulary** is a defined list of explicitly allowed terms used to index, categorize, tag, sort, and retrieve content. The range from simplest to most complex:
>
> 1. **Term/Pick Lists**: Simple lists with no relationships between terms
> 2. **Synonym Rings**: Sets of roughly equivalent terms (search one, find all)
> 3. **Authority Lists**: One preferred term with variants (e.g., Library of Congress Subject Headings)
> 4. **Taxonomies**: Naming structures for organizing topics and enabling navigation/search
> 5. **Thesauri**: Combine synonym lists and taxonomies; hierarchical + associative + equivalent relationships
> 6. **Ontologies**: Most complex. Represent concepts and relationships within a domain; primary knowledge representation for the Semantic Web
>
> Controlled vocabularies constitute a type of **Reference Data** and can also be thought of as **Metadata**. They should ideally be aligned with entity names and definitions in an enterprise conceptual data model.

---

### Q8. What is the difference between precision and recall in information retrieval? [recall]

> [!answer]- Show Answer
> - **Precision**: The proportion of **retrieved** documents that are **actually relevant**. (How accurate are the results?)
> - **Recall**: The proportion of **all relevant** documents that are **actually retrieved**. (How complete are the results?)
>
> Example: A search returns 100 documents. 80 are relevant (precision = 80%). But there were actually 200 relevant documents total (recall = 80/200 = 40%).
>
> Both are used as KPIs for measuring ECM search retrieval performance.

---

### Q9. A company is implementing an Enterprise Content Management system. The project lead argues that the technology selection should come first. Is this correct? [application]

> [!answer]- Show Answer
> **No, this is incorrect.** The DMBOK2 is clear that **content, not technology, should drive decisions** for ECM implementation.
>
> The correct approach:
> 1. Start with a **content strategy** including an inventory of current state and gap assessment
> 2. Define how content will be **prioritized, organized, and accessed**
> 3. Develop **content handling policies** (retention, e-discovery, sensitive data)
> 4. Define **information architecture** (controlled vocabularies, taxonomies, navigation maps, Metadata maps)
> 5. **Then** select technology that meets the content requirements
>
> Content requirements should **drive** technology decisions, not the other way around. The workflow should be configured around **organizational needs** to show value. Technology-first approaches risk implementing solutions that don't match the organization's actual content management needs.

---

### Q10. A multinational corporation needs to manage documents that contain terms used differently across business units (e.g., "post-employment" vs. "post-retirement" vs. "post employment"). How should they address this using vocabulary management techniques? [analysis]

> [!answer]- Show Answer
> They should implement a **multi-layered vocabulary management** approach:
>
> 1. **Establish a preferred term**: Designate one official term (e.g., "Postemployment") through a governance process with a decision-making body
> 2. **Define synonym rings**: Create relationships between variants ("Post-Employment," "Post Employment," "Post Retirement") so that searching on any term retrieves content tagged with any of the variants
> 3. **Define related term relationships**: Link associated but not equivalent terms
> 4. **Create vocabulary views**: Subsets of the controlled vocabulary relevant to specific business units (e.g., Marketing view doesn't include Finance-only terms)
> 5. **Consider micro-controlled vocabularies**: If specific business units need highly specialized terms not in the general vocabulary, create extensions mapped to the hierarchical structure of the broader vocabulary
> 6. **Implement automated flagging and routing rules**: With the volume of data generated, even well-defined taxonomies require automation to enforce correct term usage
> 7. **Assign vocabulary stewards**: Define who adds terms and arbitrate when stakeholder feedback conflicts
>
> This prevents the alternative: vocabularies defined in silos, project by project, leading to higher integration costs and data quality issues. The ANSI/NISO Z39.19-2005 standard provides detailed guidelines.

---

> [!summary]- Pattern Summary (click to view)
> **Core Distinction**: Document (container) vs. Content (data inside). Content management focuses on organizing, categorizing, and structuring information resources. Records management is a subset with special legal/regulatory requirements.
>
> **Key Facts**: 80% of stored data is unstructured. 90% of documents created today are electronic.
>
> **Vocabulary Hierarchy** (simple to complex): Pick Lists > Synonym Rings > Authority Lists > Taxonomies > Thesauri > Ontologies.
>
> **Taxonomy vs. Ontology**: Closed-world (what's defined is what's known) vs. Open-world (relationships can be inferred).
>
> **ARMA GARP**: 8 principles (Accountability, Integrity, Protection, Compliance, Availability, Retention, Disposition, Transparency). Maturity Model: 5 levels from Sub-Standard to Transformational.
>
> **E-Discovery (EDRM)**: 8 phases. Volume decreases as relevance increases. Legal Hold Notification prevents data destruction.
>
> **Control Levels (ANSI 859)**: Formal > Revision > Custody, based on criticality.
>
> **Markup/Exchange**: XML (structured + unstructured), JSON (lightweight, web-centric), RDF (Semantic Web triples), Schema.org (search engine markup).
>
> **Governance Drivers**: Legal compliance, defensible disposition, proactive e-discovery, sensitive information security, email and Big Data risk management.
