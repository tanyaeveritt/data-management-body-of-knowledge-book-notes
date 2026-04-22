---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 4
keywords: data architecture, enterprise data model, Zachman framework, data flow, roadmap, TOGAF
---

# Data Architecture (Importance: ★★★)
*Reading time: ~5 min*

#dmbok2 #data-architecture

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Identifying enterprise data needs and designing master blueprints to meet those needs |
| Goals | (1) Identify data storage/processing requirements, (2) Design structures meeting current/future needs, (3) Prepare to evolve with emerging tech |
| Three Components | Architecture **artifacts**, **activities**, and **behavior** |
| Key Deliverables | Enterprise Data Model (EDM), Data Flows, Data Value Chains, Implementation Roadmap |
| Frameworks | Zachman, TOGAF, FEAF, DoDAF |
| Architecture Domains | Business, Data, Application, Technology |

## What is Data Architecture?
Data Architecture is a bridge between **business strategy and technology execution**. It includes:
- **Artifacts** (outcomes): Models, definitions, data flows -- the master design documents
- **Activities**: Forming, deploying, and fulfilling architecture intentions
- **Behavior**: Collaborations, mindsets, and skills among roles affecting architecture

The most detailed artifact is the **formal enterprise data model** containing data names, definitions, conceptual/logical entities and relationships, and business rules.

## Enterprise Architecture Domains
| Domain | Purpose | Elements |
|--------|---------|----------|
| **Business** | How enterprise creates value | Models, processes, capabilities, services |
| **Data** | How data should be organized and managed | Data models, definitions, mappings, flows, APIs |
| **Application** | Structure/functionality of applications | Business systems, packages, databases |
| **Technology** | Physical technology enabling systems | Platforms, networks, security, integration tools |

Business architecture **establishes requirements** for other domains. Each domain influences and constrains the others.

## Enterprise Architecture Frameworks

### Zachman Framework
The most well-known EA framework -- a **6x6 ontology matrix**:
- **Columns** (communication interrogatives): What, How, Where, Who, When, Why
- **Rows** (reification transformations): Executive/Planner, Business Management/Owner, Architect/Designer, Engineer/Builder, Technician/Implementer, User/Participant

Each cell = a unique type of design artifact. The What (inventory/data) column from each perspective:
- **Executive**: Lists of business elements defining scope
- **Business Management**: Relationships between business concepts
- **Architect**: System logical models (unconstrained design)
- **Engineer**: Physical models (optimized for implementation constraints)
- **Technician**: Technology-specific component assemblies
- **User**: Actual functioning instances (no models)

## Enterprise Data Model (EDM)
A holistic, enterprise-level, implementation-independent conceptual or logical data model providing a **common consistent view of data** across the enterprise.

Built incrementally using layers:
- **Conceptual overview**: Enterprise subject areas
- **Subject area views**: Entities and relationships per area
- **Detailed logical views**: Partially attributed models
- **Application-specific**: Logical and physical models per project

Model relationships:
- **Vertical**: Models map across levels (conceptual -> logical -> physical)
- **Horizontal**: Entities may appear in multiple models at the same level as external links

Subject area discriminator principles: normalization rules, systems portfolios, data ownership, business value chains, or business capabilities.

## Data Flow Design
Data flows document how data moves through business processes and systems:
- Map relationships between data and applications, databases, network segments, business roles, locations
- Can be documented at subject area, business entity, or attribute level
- Represented as **matrices** (CRUD) or **data flow diagrams**
- End-to-end flows show origin, storage, use, and transformation

## Architecture Activities
Two viewpoints for managing complexity:
- **Quality-oriented**: Improving execution within business/IT cycles; preventing architecture deterioration
- **Innovation-oriented**: Transforming business/IT for new opportunities; disruptive technologies

Establishing a practice includes:
- **Strategy**: Select frameworks, state approaches, develop roadmap
- **Acceptance and culture**: Inform and motivate behavior changes
- **Organization**: Assign accountabilities and responsibilities
- **Working methods**: Define best practices within development projects
- **Results**: Produce artifacts within an overall roadmap

## Roadmap
A 3-5 year development path for Enterprise Data Architecture:
- Describes how target architecture becomes reality
- Guided by data management **maturity assessment**
- Business-data-driven: Start with most independent capabilities, resolve dependencies top to bottom
- Must be integrated into overall enterprise architecture roadmap

## Development Methodology Integration
- **Waterfall**: Include DA activities in sequential phases and tollgates
- **Incremental**: Create comprehensive data design in early iterations
- **Agile/Iterative**: Complete with data model, data capture, storage, distribution specs; strong architect-programmer working relationship essential

## Implementation Risks
- Lack of management support (especially during reorganizations)
- No proven record of accomplishment
- Apprehensive sponsor requiring all communications to pass through them
- Counter-productive executive decisions
- Culture shock among affected employees
- Inexperienced project leader
- Dominance of one-dimensional view (e.g., ERP owners dictating enterprise architecture)

## Data Architecture Governance
Activities include:
- **Overseeing projects** for compliance with DA standards
- **Managing architectural designs**, lifecycle, and tools
- **Defining standards** for how data is used
- **Creating data-related artifacts** for compliance

## Metrics
- **Architecture standard compliance rate**: How closely projects comply
- **Implementation trends**: Use/reuse/replace/retire measurements; project execution efficiency
- **Business value measurements**: Agility improvements, business quality, operational quality, environment improvements

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| DA three components | **Artifacts, Activities, Behavior** |
| Zachman matrix dimensions | **6 interrogatives (What/How/Where/Who/When/Why) x 6 perspectives** |
| Zachman "What" column | **Inventory/Data** column |
| EDM definition | **Holistic, enterprise-level, implementation-independent** conceptual/logical model |
| Four architecture domains | **Business, Data, Application, Technology** |
| DA roadmap timeframe | **3-5 years** |
| Quality vs Innovation orientation | Quality = prevent deterioration; Innovation = **disruptive technologies** |
| Subject area discriminator | Principles for forming subject area structure (normalization, capabilities, etc.) |
| DA two model types | **Enterprise Data Model (structures)** + **Data Flow Design (movement)** |
| Vertical vs Horizontal model links | Vertical = across levels; Horizontal = across models at **same level** |

## Related Notes
- [[Data Management]]
- [[Data Governance]]
- [[Data Modeling and Design]]
- [[Data Storage and Operations]]
- [[Metadata Management]]
