---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 5
keywords: data modeling, conceptual model, logical model, physical model, normalization, dimensional, relational, NoSQL, Data Vault
---

# Data Modeling and Design (Importance: ★★★)
*Reading time: ~6 min*

#dmbok2 #data-modeling

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Discovering, analyzing, and scoping data requirements; representing them in a precise form (data model) |
| Goal | Confirm and document understanding of different perspectives to align with business requirements |
| Three Levels | Conceptual (CDM), Logical (LDM), Physical (PDM) |
| Six Schemes | Relational, Dimensional, Object-Oriented, Fact-Based, Time-Based, NoSQL |
| Four Components | Entities, Relationships, Attributes, Domains |
| Key Deliverables | Diagram, Definitions, Issues/Questions, Lineage |

## Four Types of Data Modeled
| Type | Description | Examples |
|------|-------------|----------|
| **Category** | Data to classify/assign types | Market categories, product colors, order status |
| **Resource** | Profiles of operational resources | Product, Customer, Supplier, Facility, Account |
| **Business Event** | Data from operational processes | Orders, Invoices, Withdrawals, Meetings |
| **Detail Transaction** | High-volume data from POS, IoT, social media | Clickstream, sensor data, RFID -- often called "Big Data" |

## Data Model Components

### Entities
A thing about which an organization collects information ("nouns of an organization"). Entity categories mapped to interrogatives:
- **Who**: Person/organization (Employee, Customer, Vendor)
- **What**: Product/service (Product, Course, Book)
- **When**: Calendar/time (Date, Semester, Fiscal Period)
- **Where**: Location (Address, URL, IP Address)
- **Why**: Event/transaction (Order, Complaint, Trade)
- **How**: Documentation of events (Invoice, Contract, Purchase Order)
- **Measurement**: Counts/sums (Sales, Item Count, Balance)

Entity definitions must exhibit: **Clarity**, **Accuracy**, **Completeness**.

### Relationships
Associations between entities. Cardinality options: **zero, one, or many** on each side.
- **Unary** (recursive): One entity (hierarchy or network)
- **Binary**: Two entities (most common)
- **Ternary**: Three entities
- **Foreign key**: Physical representation of a relationship in child entity

### Attributes
Properties that identify, describe, or measure an entity. Physical correspondents: column, field, tag, node.

### Keys (by construction)
- **Simple key**: One attribute (e.g., UPC, VIN)
- **Surrogate key**: System-generated integer, no business meaning, not visible to users
- **Compound key**: Two or more attributes together
- **Composite key**: One compound key + at least one other key/attribute

### Keys (by function)
- **Super key**: Any set of attributes that uniquely identifies an instance
- **Candidate key**: Minimal set uniquely identifying an instance
- **Primary key**: Chosen candidate key for unique identification
- **Alternate key**: Candidate key not chosen as primary
- **Business/Natural key**: Attributes a business professional would use to retrieve data

### Domains
The complete set of possible values for an attribute. Types:
- **Data Type**: Integer, Character(30), Date
- **Data Format**: Templates, masks (postal codes, phone numbers)
- **List**: Finite value set (e.g., {Open, Shipped, Closed, Returned})
- **Range**: Between min/max values
- **Rule-based**: Values must comply with calculated rules

## Six Modeling Schemes
| Scheme | Purpose | Key Notations |
|--------|---------|---------------|
| **Relational** | Operational systems; one fact in one place | IE, IDEF1X, Barker, Chen |
| **Dimensional** | Query/analysis of large data volumes | Star schema, Snowflake |
| **Object-Oriented** | Software modeling with encapsulation | UML Class Model |
| **Fact-Based** | Natural verbalization of business facts | ORM, FCO-IM |
| **Time-Based** | Chronological data association | Data Vault, Anchor Modeling |
| **NoSQL** | Non-relational storage | Document, Key-Value, Column, Graph |

### Dimensional Modeling Key Concepts
- **Fact table**: Numeric measurements (amounts, quantities, counts); ~90% of space
- **Dimension table**: Textual descriptions; entry points for queries; ~10% of space
- **Grain**: Meaning of a single row in a fact table (most detail level)
- **Slowly Changing Dimensions (SCD)**: Type 1 (Overwrite), Type 2 (New Row), Type 3 (New Column)
- **Conformed dimensions**: Built enterprise-wide for sharing across dimensional models
- **Conformed facts**: Standardized definitions across individual marts
- **Star schema**: All dimensions collapsed into single structures
- **Snowflake**: Dimensions not collapsed (normalized)

### Data Vault (Time-Based)
Three entity types:
- **Hubs**: Primary keys representing main business concepts
- **Links**: Transaction integration between hubs
- **Satellites**: Descriptive context of hub primary keys; support varying history types

### NoSQL Types
- **Document**: Business subject in one structure (e.g., MongoDB)
- **Key-Value**: Two columns -- key and value (simple to complex data)
- **Column-oriented**: Like RDBMS but handles complex data types (e.g., Cassandra)
- **Graph**: Nodes with undetermined connections; best for social networks, routes (e.g., Neo4J)

## Three Levels of Detail
| Level | Purpose | Technology | Key Activity |
|-------|---------|------------|--------------|
| **Conceptual (CDM)** | High-level scope; critical entities and relationships | Independent | Requirements planning |
| **Logical (LDM)** | Detailed data requirements with attributes; normalized | Independent | Requirements analysis |
| **Physical (PDM)** | Technical solution adapted to specific technology | Dependent | Design |

## Normalization
Rules for organizing data to eliminate redundancy:
- **1NF**: Valid primary key; atomic attributes; no repeating groups; resolve M:M
- **2NF**: Minimal primary key; every attribute depends on complete PK
- **3NF**: No hidden PKs; "the key, the whole key, and nothing but the key"
- **BCNF**: Resolve overlapping composite candidate keys
- **4NF**: Resolve M:M:M relationships in pairs
- **5NF**: All join dependencies use parts of primary keys

"Normalized model" usually means **3NF**. BCNF, 4NF, 5NF occur rarely.

## Abstraction (Generalization/Specialization)
- **Generalization**: Groups common attributes into **supertype** entities
- **Specialization**: Separates distinguishing attributes into **subtype** entities
- Subtype inherits all supertype properties
- Physical resolution: **Subtype absorption** (nullable columns in supertype table) or **Supertype partition** (supertype attributes in separate subtype tables)

## Physical Modeling Key Steps
1. Resolve logical abstractions (subtypes)
2. Add attribute details (data types, constraints, NOT NULL)
3. Add Reference Data objects (code tables, shared tables, or embedded constraints)
4. Assign surrogate keys (optional, based on natural key characteristics)
5. **Denormalize** for performance (combining tables, pre-calculating)
6. **Index** for performance (b-tree, bitmap, clustered, etc.)
7. **Partition** for performance (horizontal or vertical splits)
8. Create views

## Database Design Principles (PRISM)
- **P**erformance and ease of use
- **R**eusability (avoid coupling to single application)
- **I**ntegrity (valid business meaning; enforce constraints close to data)
- **S**ecurity (authorized access only; enforce close to data)
- **M**aintainability (cost must not exceed value)

## Data Model Scorecard (10 Categories)
Quality evaluation using 10 categories (total 100 points):
1. Capture requirements (15), 2. Completeness (15), 3. Match scheme (10), 4. Structural soundness (15), 5. Generic structures (10), 6. Naming standards (5), 7. Readability (5), 8. Definitions (10), 9. Enterprise consistency (5), 10. Metadata matches data (10)

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| Three model levels | **Conceptual, Logical, Physical** |
| Six modeling schemes | **Relational, Dimensional, Object-Oriented, Fact-Based, Time-Based, NoSQL** |
| "The key, the whole key, nothing but the key" | **Third Normal Form (3NF)** |
| SCD Type 2 | **New Row** (old row marked not current) |
| Data Vault three entities | **Hubs, Links, Satellites** |
| Star vs Snowflake | Star = **collapsed/denormalized** dimensions; Snowflake = **normalized** |
| Grain definition | Meaning of a **single row** in a fact table |
| Surrogate key characteristics | System-generated, no business meaning, **not visible to users** |
| PRISM acronym | **Performance, Reusability, Integrity, Security, Maintainability** |
| Conformed dimension purpose | **Shared across dimensional models** with consistent terminology |
| Four NoSQL types | **Document, Key-Value, Column, Graph** |

## Related Notes
- [[Data Management]]
- [[Data Architecture]]
- [[Data Governance]]
- [[Data Storage and Operations]]
- [[Metadata Management]]
- [[Data Quality]]
