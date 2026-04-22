---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 4
keywords: practice, data architecture, Zachman, enterprise data model, data flow, roadmap
---

# Data Architecture Practice (10 questions)

#practice #data-architecture

## Related Concepts
- [[Data Architecture]]
- [[Data Governance]]
- [[Data Modeling and Design]]

> [!hint]- Key Patterns (click to view)
> | Keyword | Answer |
> |---------|--------|
> | DA three components | **Artifacts, Activities, Behavior** |
> | Zachman matrix | **6x6 (interrogatives x perspectives)** |
> | Four architecture domains | **Business, Data, Application, Technology** |
> | EDM | **Enterprise-level, implementation-independent** model |
> | DA roadmap | **3-5 years** |
> | Two DA specification types | **Enterprise Data Model + Data Flow Design** |

---

## Question 1 - Three Components [recall]
> What are the three essential components of Data Architecture according to DMBOK2?

> [!answer]- Show Answer
> (1) **Artifacts** (outcomes) -- models, definitions, data flows at different levels of abstraction, which are the master design documents. (2) **Activities** -- forming, deploying, and fulfilling Data Architecture intentions. (3) **Behavior** -- collaborations, mindsets, and skills among the various roles that affect the enterprise's Data Architecture. Together these three form the complete picture of Data Architecture.

---

## Question 2 - Architecture Domains [recall]
> Name the four Enterprise Architecture domains and explain which one establishes requirements for the others.

> [!answer]- Show Answer
> The four domains are: (1) **Business Architecture** -- how the enterprise creates value (models, processes, capabilities); (2) **Data Architecture** -- how data should be organized and managed; (3) **Application Architecture** -- structure and functionality of applications; (4) **Technology Architecture** -- physical technology enabling systems. **Business Architecture** establishes requirements for the other domains. Each domain influences and constrains the others, requiring collaborative development.

---

## Question 3 - Zachman Framework [recall]
> Describe the two dimensions of the Zachman Framework and give the six column headings.

> [!answer]- Show Answer
> The Zachman Framework is a **6x6 ontology matrix** with two dimensions: (1) **Columns** -- the six communication interrogatives: **What** (inventory), **How** (process), **Where** (distribution), **Who** (responsibility), **When** (timing), **Why** (motivation). (2) **Rows** -- the six reification transformations representing perspectives: Executive (planner), Business Management (owner), Architect (designer), Engineer (builder), Technician (implementer), User (participant). Each cell represents a unique type of design artifact.

---

## Question 4 - Enterprise Data Model [recall]
> What is an Enterprise Data Model (EDM), and what four levels of detail does it typically include?

> [!answer]- Show Answer
> An EDM is a **holistic, enterprise-level, implementation-independent** conceptual or logical data model providing a common, consistent view of data across the enterprise. Four levels: (1) **Conceptual overview** of the enterprise's subject areas; (2) **Subject area views** showing entities and relationships for each area; (3) **Detailed, partially attributed logical views** of subject areas; (4) **Application/project-specific** logical and physical models. All levels are linked both vertically (across levels) and horizontally (across models at the same level).

---

## Question 5 - Data Flow Design [recall]
> What does Data Flow Design document, and what two common representation formats are used?

> [!answer]- Show Answer
> Data Flow Design defines the requirements and master blueprint for **storage and processing** across databases, applications, platforms, and networks. It maps the movement of data to business processes, locations, business roles, and technical components. Two common formats: (1) **Two-dimensional matrices** showing what data processes create and use (CRUD), which clarify data acquisition responsibilities and dependencies; (2) **Data flow diagrams** depicting data flows between systems in traditional high-level visual format.

---

## Question 6 - Roadmap Development [recall]
> What timeframe does a DA roadmap typically cover, and what drives the sequencing of capabilities in a business-data-driven roadmap?

> [!answer]- Show Answer
> A DA roadmap describes the architecture's **3-5 year** development path. In a business-data-driven roadmap, sequencing starts with business capabilities that are **most independent** (least dependency on others) and ends with those most dependent. For example, Product Management and Customer Management have no dependencies and constitute **Master Data**, so they come first. Higher-dependency items like Invoice Management (which depends on Customer and Sales Order) come later. This follows the overall business data origination order.

---

## Question 7 - Agile DA Integration [application]
> Your organization uses Agile/Scrum methodology. How should Data Architecture activities be integrated into this approach?

> [!answer]- Show Answer
> Per DMBOK2, Agile methods should be **completed with specifications for data models, data capture, data storage, and data distribution**. Key recommendations: (1) Have an **outlined subject area model** at an overall level while participating at a detail level in agile sprints; (2) Ensure data architects are **engaged early** in development initiatives, as these evolve rapidly; (3) Build a strong working relationship between **programmers and data architects** where both comply with standards; (4) The Enterprise Data Architecture will evolve **incrementally** through sprints; (5) DevOps experience shows improved data design when architects and programmers collaborate closely.

---

## Question 8 - Quality vs Innovation [application]
> An Enterprise Data Architect is asked to support both legacy system improvement and a new IoT initiative. How should these be approached differently?

> [!answer]- Show Answer
> DMBOK2 distinguishes two architecture orientations: (1) **Quality-oriented** (legacy improvement) -- focuses on improving execution within business/IT cycles; prevents architecture deterioration, reducing "interface spaghetti" and data inconsistencies. This aligns with traditional DA work -- incremental improvements, standardization, governance compliance, and long-term goals. (2) **Innovation-oriented** (IoT initiative) -- focuses on transforming business/IT for new opportunities using disruptive technologies. This requires a **shorter-term perspective**, possibly unproven business logic, and interaction with people outside typical IT contacts (e.g., product development, business designers). Both require separate approaches but should share the same enterprise-level architecture standards.

---

## Question 9 - Implementation Risks [analysis]
> What are the most significant risks when initiating a Data Architecture practice for the first time, and how can the "lack of management support" risk be mitigated?

> [!answer]- Show Answer
> Key risks include: lack of management support, no proven track record, apprehensive sponsor, counter-productive executive decisions, culture shock, inexperienced project leader, and dominance of a one-dimensional view (e.g., ERP owners dictating enterprise architecture). To mitigate **lack of management support**: Enlist **more than one** member of top-level or senior management who understand DA benefits. This way, if reorganization occurs and one decision maker departs, the architecture process can **survive reorganization** through remaining supporters. The key insight is that any reorganization will affect the process, and multiple sponsors provide resilience.

---

## Question 10 - Vertical and Horizontal Model Linkage [analysis]
> Explain the difference between vertical and horizontal linkages in an Enterprise Data Model, using a concrete example.

> [!answer]- Show Answer
> **Vertical linkages** trace an entity from top to bottom across abstraction levels. For example, a table "MobileDevice" in a project-specific physical model links to a MobileDevice entity in the project logical model, which links to MobileDevice in the Product subject area of the Enterprise Logical Model, to a Product conceptual entity in the Subject Area Model, and finally to the Product entity in the Enterprise Conceptual Model. **Horizontal linkages** connect entities across models at the same level. For example, a "Product Part" entity may appear in the Product subject area models AND in Sales Order, Inventory, and Marketing subject areas as external links. Horizontal links enable cross-subject-area consistency while vertical links enable traceability from business concepts to physical implementation.

---

> [!summary]- Pattern Summary (click to view)
> | Keyword | Answer |
> |---------|--------|
> | DA three components | **Artifacts, Activities, Behavior** |
> | Zachman columns | **What, How, Where, Who, When, Why** |
> | Four EA domains | **Business, Data, Application, Technology** |
> | Business architecture role | **Establishes requirements** for other domains |
> | EDM characteristic | **Enterprise-level, implementation-independent** |
> | Roadmap timeframe | **3-5 years** |
> | Two DA specification types | **EDM (structures) + Data Flow Design (movement)** |
> | Quality vs Innovation | Quality = incremental; Innovation = **disruptive, shorter-term** |
> | Subject area formation | **Normalization rules** usually most effective |
> | Model linkage: vertical | Across levels; horizontal = across models at **same level** |
