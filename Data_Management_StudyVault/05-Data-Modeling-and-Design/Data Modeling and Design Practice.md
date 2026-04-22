---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 5
keywords: practice, data modeling, normalization, dimensional, relational, CDM, LDM, PDM, NoSQL
---

# Data Modeling and Design Practice (12 questions)

#practice #data-modeling

## Related Concepts
- [[Data Modeling and Design]]
- [[Data Architecture]]
- [[Data Governance]]

> [!hint]- Key Patterns (click to view)
> | Keyword | Answer |
> |---------|--------|
> | Three model levels | **Conceptual, Logical, Physical** |
> | Six schemes | **Relational, Dimensional, OO, Fact-Based, Time-Based, NoSQL** |
> | 3NF rule | **"The key, the whole key, nothing but the key"** |
> | SCD Type 1/2/3 | **Overwrite / New Row / New Column** |
> | Data Vault entities | **Hubs, Links, Satellites** |
> | Star vs Snowflake | Star = denormalized dims; Snowflake = **normalized** |
> | PRISM | **Performance, Reusability, Integrity, Security, Maintainability** |

---

## Question 1 - Three Model Levels [recall]
> What are the three levels of data model detail, and how do they differ in terms of technology dependence?

> [!answer]- Show Answer
> (1) **Conceptual Data Model (CDM)** -- high-level data requirements; basic entities and relationships; **technology-independent**. Part of requirements planning. (2) **Logical Data Model (LDM)** -- detailed data requirements with attributes, normalized; still **technology-independent**. Part of requirements analysis. (3) **Physical Data Model (PDM)** -- detailed technical solution adapted to work within specific hardware, software, and network tools; **technology-dependent** (e.g., designed for Oracle, Teradata, etc.). Part of design activities.

---

## Question 2 - Six Modeling Schemes [recall]
> List the six data modeling schemes and identify which is best suited for operational systems vs. analytical systems.

> [!answer]- Show Answer
> The six schemes are: **Relational, Dimensional, Object-Oriented, Fact-Based, Time-Based, and NoSQL**. **Relational** is ideal for operational systems -- it aims for one fact in one place (removal of redundancy) and supports entering information quickly and storing it accurately. **Dimensional** is optimized for query and analysis of large amounts of data, structured to answer business questions about process performance. Time-Based (Data Vault, Anchor Modeling) is specifically for enterprise data warehouse needs.

---

## Question 3 - Normalization Levels [recall]
> Define First, Second, and Third Normal Forms. What mnemonic captures 3NF?

> [!answer]- Show Answer
> **1NF**: Ensures each entity has a valid primary key, every attribute depends on the PK, removes repeating groups, ensures each attribute is atomic (not multi-valued), and resolves many-to-many relationships. **2NF**: Ensures the minimal primary key -- every attribute depends on the **complete** primary key. **3NF**: Ensures no hidden primary keys -- each attribute depends on no attributes outside the key. The mnemonic is: **"the key, the whole key, and nothing but the key"** (echoing a courtroom oath). A "normalized model" typically means 3NF.

---

## Question 4 - Entity Categories [recall]
> What six interrogative-based categories does DMBOK2 use to classify entities? Give an example for each.

> [!answer]- Show Answer
> (1) **Who** -- person/organization of interest (Employee, Customer, Vendor); (2) **What** -- product/service (Product, Course, Book); (3) **When** -- calendar/time interval (Date, Semester, Fiscal Period); (4) **Where** -- location (Mailing Address, Website URL, IP Address); (5) **Why** -- event/transaction (Order, Complaint, Trade); (6) **How** -- documentation of events (Invoice, Contract, Purchase Order). Additionally, **Measurement** entities capture counts/sums (Sales, Balance).

---

## Question 5 - Key Types [recall]
> What is the difference between a surrogate key and a natural (business) key?

> [!answer]- Show Answer
> A **surrogate key** is a system-generated unique identifier (typically an integer counter) with **no business meaning**, not visible to end users. It serves technical functions: maintaining uniqueness, efficient navigation, and facilitating integration. A **natural (business) key** consists of one or more attributes that a business professional would use to retrieve a specific entity instance (e.g., email address, customer account number). Business keys and surrogate keys are **mutually exclusive**. Often the primary key is a surrogate key and the alternate keys are business keys.

---

## Question 6 - Dimensional Concepts [recall]
> Define grain, fact table, and dimension table. What percentage of space does each typically occupy?

> [!answer]- Show Answer
> **Grain**: The meaning or description of a single row in a fact table; the most detail any row will have. Defining grain is a key step in dimensional design. **Fact table**: Contains numeric measurements (amounts, quantities, counts); occupies approximately **90%** of database space; has large numbers of rows. **Dimension table**: Contains mostly textual descriptions; serves as entry points for queries ("query by" or "report by" constraints); accounts for about **10%** of total data. Dimensions are typically highly denormalized.

---

## Question 7 - SCD Types [recall]
> Describe the three main types of Slowly Changing Dimensions (SCD).

> [!answer]- Show Answer
> The three types are sometimes known by **ORC**: (1) **Type 1 -- Overwrite**: The new value overwrites the old value in place. No history is preserved. (2) **Type 2 -- New Row**: New values are written in a new row; the old row is marked as not current. Full history is preserved. (3) **Type 3 -- New Column**: Multiple instances of a value are listed in columns on the same row; a new value shifts existing values down, and the last value is discarded. Only limited history is preserved.

---

## Question 8 - Star vs Snowflake [application]
> A data warehouse team is debating between a Star Schema and a Snowflake Schema. What are the key differences, and when might each be preferred?

> [!answer]- Show Answer
> **Star Schema**: Each dimension is **collapsed (denormalized)** into a single flat table, with the fact table at the center. Benefits: simpler queries, faster joins, easier for business users to understand. Preferred when query simplicity and speed are priorities. **Snowflake Schema**: Dimensions are **not collapsed (normalized)** -- dimension hierarchies are in separate tables. Benefits: reduced data redundancy, more organized structure. Preferred when storage efficiency matters or when dimensional hierarchies are complex and frequently updated independently. In dimensional modeling terminology, collapsing dimensions = Star; not collapsing = Snowflake.

---

## Question 9 - Data Vault Architecture [application]
> Your organization needs a data warehouse that can handle changing business rules and historical data tracking. Explain how the Data Vault approach addresses this with its three entity types.

> [!answer]- Show Answer
> The Data Vault is a detail-oriented, time-based, uniquely linked set of normalized tables. Its three entity types: (1) **Hubs** represent the primary keys of main business concepts (e.g., Student, Course) -- they capture the core business identifiers. (2) **Links** provide transaction integration between hubs -- they capture the relationships (e.g., Attendance linking Student and Course). (3) **Satellites** provide descriptive context for hubs and can support **varying types of history** (e.g., Student Contact, Student Characteristics, Course Description). This separation means that when business rules change, only satellites or links are affected, while hubs remain stable. It is a **hybrid** approach combining the best of 3NF and star schema, designed specifically for enterprise data warehouses.

---

## Question 10 - PRISM Design Principles [application]
> Using the PRISM acronym, explain how you would evaluate a proposed database design for a multi-department CRM system.

> [!answer]- Show Answer
> **P (Performance)**: Ensure quick, easy access by approved users in a usable, business-relevant form, maximizing value. **R (Reusability)**: Ensure the structure allows multiple departments to use the data -- avoid coupling the database to a single application (e.g., don't design only for sales; marketing, support should also use it). **I (Integrity)**: Data must have valid business meaning regardless of context; enforce integrity constraints as close to the data as possible. **S (Security)**: Only authorized users access data; enforce privacy concerns of customers, partners, and regulators close to the data. **M (Maintainability)**: Ensure cost of creating, storing, maintaining, using, and disposing of data does not exceed its value; ensure fastest response to changing business requirements.

---

## Question 11 - Forward vs Reverse Engineering [analysis]
> Compare forward engineering and reverse engineering in data modeling. When would you use each approach?

> [!answer]- Show Answer
> **Forward engineering** builds a new application starting from requirements: CDM first (to understand scope and terminology), then LDM (to document the business solution), then PDM (to document the technical solution). Used for **new systems** or major redesigns. **Reverse engineering** documents an existing database: PDM first (to understand technical design), then LDM (to document the business solution the system meets), then CDM (to document scope and terminology). Used for **legacy system documentation**, migration planning, or when models are outdated. Most data modeling tools support reverse engineering from databases, though creating readable layouts still requires a modeler. A good practice is to reverse engineer at the end of each development iteration to ensure the PDM remains consistent with the LDM.

---

## Question 12 - Abstraction Trade-offs [analysis]
> An organization debates whether to use a generic "Party" supertype entity that covers both Individual and Organization, or keep them as separate entities. What are the trade-offs according to DMBOK2?

> [!answer]- Show Answer
> The **Party/Role structure** is an example of abstraction (generalization). Benefits: (1) **Reduces redundancy** -- common attributes (name, address, phone) are defined once in the supertype; (2) **Easier communication** of similarities across otherwise distinct entities; (3) **Broader applicability** -- easily handles future types (e.g., adding Government Agency as a new subtype). Trade-offs: (1) **Not all modelers/developers are comfortable** with abstraction; (2) Physical resolution requires choosing between **subtype absorption** (nullable columns in one table -- simpler but can be sparse) and **supertype partition** (separate tables per subtype -- cleaner but requires joins); (3) Must weigh the cost of developing/maintaining the abstract structure vs. the **rework required** if a simpler structure needs modification later. DMBOK2 notes that abstraction should be used judiciously based on the specific use case.

---

> [!summary]- Pattern Summary (click to view)
> | Keyword | Answer |
> |---------|--------|
> | Three model levels | **CDM, LDM, PDM** |
> | Six schemes | **Relational, Dimensional, OO, Fact-Based, Time-Based, NoSQL** |
> | 3NF mnemonic | **"The key, the whole key, nothing but the key"** |
> | SCD Type 2 | **New Row** (old marked not current) |
> | Data Vault entities | **Hubs, Links, Satellites** |
> | Star = denormalized; Snowflake = | **normalized dimensions** |
> | Grain | Meaning of **single row** in fact table |
> | Surrogate key | System-generated, **no business meaning** |
> | PRISM | **Performance, Reusability, Integrity, Security, Maintainability** |
> | Forward engineering order | **CDM -> LDM -> PDM** |
> | Reverse engineering order | **PDM -> LDM -> CDM** |
> | Fact table space | **~90%** of database |
