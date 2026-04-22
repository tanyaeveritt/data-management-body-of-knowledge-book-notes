---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: all
keywords: quick reference, cheat sheet, DAMA, DMBOK2, data management
---

# DAMA DMBOK2 Quick Reference
*Reading time: ~7 min*

#dashboard #dmbok2 #quick-reference

---

## Ch 1: Data Management -> [[Data Management]]
| Concept | Key Point |
|---------|-----------|
| Data Management definition | Development, execution, supervision of plans/policies to deliver, control, protect, enhance data value |
| Data as asset | Unique properties -- not consumed when used, requires Metadata to manage |
| DAMA Wheel | Data Governance at center; 10 surrounding knowledge areas |
| Data Management Principles | Data is valuable, requires planning, cross-functional, lifecycle management |
| DIKW Pyramid | Data -> Information -> Knowledge -> Wisdom (criticized for implying data "just exists") |

## Ch 2: Data Handling Ethics -> [[Data Handling Ethics]]
| Concept | Key Point |
|---------|-----------|
| Ethical principles | Ownership, transparency, consent, currency, proportional use |
| Privacy law principles | Notice, choice/consent, proportionality, purpose limitation, data minimization |
| Risks of unethical handling | Financial penalties, reputational damage, loss of customer trust |
| Ethical data culture | Training, policies, accountability, ethical review boards |

## Ch 3: Data Governance -> [[Data Governance]]
| Concept | Key Point |
|---------|-----------|
| DG definition | Exercise of authority and control over management of data assets |
| Data Stewardship | Accountability for data quality at operational level |
| Data Owner vs Steward | Owner = business accountability; Steward = operational responsibility |
| Business Glossary | Standardized definitions of business terms across organization |
| DG Operating Framework | Policies + standards + processes + org structure + technology |

## Ch 4: Data Architecture -> [[Data Architecture]]
| Concept | Key Point |
|---------|-----------|
| Enterprise Data Model | Conceptual/logical models showing data subjects and relationships |
| Data flow diagrams | Show how data moves between systems and processes |
| Zachman Framework | 6x6 matrix classifying architecture artifacts by audience and question |
| TOGAF | Open Group Architecture Framework for enterprise architecture |

## Ch 5: Data Modeling and Design -> [[Data Modeling and Design]]
| Concept | Key Point |
|---------|-----------|
| Three model levels | Conceptual (what), Logical (how, DB-agnostic), Physical (how, DB-specific) |
| Normalization | 1NF -> 2NF -> 3NF: reduce redundancy, improve integrity |
| Dimensional modeling | Facts + Dimensions; star schema vs snowflake schema |
| Kimball vs Inmon | Kimball = bottom-up dimensional; Inmon = top-down normalized EDW |

## Ch 6: Data Storage and Operations -> [[Data Storage and Operations]]
| Concept | Key Point |
|---------|-----------|
| DBMS types | Relational, columnar, graph, document, key-value, spatial |
| ACID | Atomicity, Consistency, Isolation, Durability -- transaction guarantees |
| SCD types | Type 1 (overwrite), Type 2 (add row), Type 3 (add column) |
| Sharding | Horizontal partitioning of data across multiple databases |

## Ch 7: Data Security -> [[Data Security]]
| Concept | Key Point |
|---------|-----------|
| CIA triad | Confidentiality, Integrity, Availability |
| CRUD matrix | Maps data access rights by role to Create/Read/Update/Delete |
| Data masking | Obfuscating sensitive data for non-production environments |
| Encryption | At rest vs in transit; symmetric vs asymmetric keys |
| RBAC | Role-Based Access Control -- permissions assigned to roles, not individuals |

## Ch 8: Data Integration and Interoperability -> [[Data Integration and Interoperability]]
| Concept | Key Point |
|---------|-----------|
| ETL vs ELT | ETL = transform before load; ELT = load then transform in target |
| Data virtualization | Provides unified view without physically moving data |
| Enterprise Service Bus | Middleware for application-to-application messaging |
| Data lineage | Tracking data from origin through transformations to consumption |

## Ch 9: Document and Content Management -> [[Document and Content Management]]
| Concept | Key Point |
|---------|-----------|
| ECM | Enterprise Content Management -- lifecycle of unstructured content |
| Taxonomy | Hierarchical classification scheme for organizing content |
| Records management | Lifecycle: creation -> retention -> archival -> destruction |
| e-Discovery | Legal process for identifying and producing electronic records |

## Ch 10: Reference and Master Data -> [[Reference and Master Data]]
| Concept | Key Point |
|---------|-----------|
| Reference data | Classify/categorize other data; slowly changing (countries, currencies) |
| Master data | Core business entities shared across systems (customer, product) |
| MDM styles | Registry (index), Consolidation (hub), Coexistence, Centralized (transactional) |
| Golden record | Single trusted version of a master data entity |

## Ch 11: Data Warehousing and BI -> [[Data Warehousing and BI]]
| Concept | Key Point |
|---------|-----------|
| Inmon DW characteristics | Subject-oriented, integrated, nonvolatile, time-variant |
| Kimball star schema | Fact table (measures) surrounded by dimension tables |
| OLAP operations | Slice, dice, drill-down, drill-up, pivot |
| Data mart | Subset of DW focused on single business area |

## Ch 12: Metadata Management -> [[Metadata Management]]
| Concept | Key Point |
|---------|-----------|
| Three metadata types | Business, Technical, Operational metadata |
| Metadata repository | Central store for metadata; enables data catalog and lineage |
| Data lineage | Source-to-target mapping of data transformations |
| Impact analysis | Assessing downstream effects of changes using metadata |

## Ch 13: Data Quality -> [[Data Quality]]
| Concept | Key Point |
|---------|-----------|
| DQ dimensions | Accuracy, completeness, consistency, timeliness, uniqueness, validity |
| Data profiling | Statistical analysis of data to assess quality and structure |
| Root cause analysis | Finding underlying causes of data quality issues |
| SPC for data | Statistical Process Control applied to data quality monitoring |

## Ch 14: Big Data and Data Science -> [[Big Data and Data Science]]
| Concept | Key Point |
|---------|-----------|
| 5 Vs | Volume, Velocity, Variety, Veracity, Value |
| Data lake | Central repository storing raw data in native format |
| Machine learning types | Supervised, unsupervised, semi-supervised, reinforcement |
| Data science lifecycle | Question -> Acquire -> Prepare -> Analyze -> Report -> Act |

## Ch 15: Maturity Assessment -> [[Maturity Assessment]]
| Concept | Key Point |
|---------|-----------|
| CMM levels | 1-Initial, 2-Repeatable, 3-Defined, 4-Managed, 5-Optimizing |
| DCAM | Data Management Capability Assessment Model (EDM Council) |
| DMM | Data Management Maturity model (CMMI Institute) |
| Assessment purpose | Baseline current state, identify gaps, prioritize improvements |

## Ch 16: DM Organization and Roles -> [[DM Organization and Roles]]
| Concept | Key Point |
|---------|-----------|
| CDO role | Chief Data Officer -- executive accountability for data strategy |
| Operating models | Decentralized, Centralized, Federated, Hybrid, Network |
| Critical success factors | Executive sponsorship, clear vision, change management, communication |

## Ch 17: Change Management -> [[Change Management]]
| Concept | Key Point |
|---------|-----------|
| Kotter's 8 steps | Urgency -> Coalition -> Vision -> Communicate -> Empower -> Quick wins -> Consolidate -> Anchor |
| Guiding Coalition | Cross-functional leadership team driving the change |
| Navigation vs Planning | Change cannot be fully planned; must navigate and adapt |

---

## Must-Know Concepts
| Concept | Key Point | Reference |
|---------|-----------|-----------|
| DAMA Wheel | Data Governance central; 10 knowledge areas surround it | -> [[Data Management]] |
| DQ Dimensions | Accuracy, completeness, consistency, timeliness, uniqueness, validity | -> [[Data Quality]] |
| CIA Triad | Confidentiality, Integrity, Availability | -> [[Data Security]] |
| ACID Properties | Atomicity, Consistency, Isolation, Durability | -> [[Data Storage and Operations]] |
| Three Model Levels | Conceptual, Logical, Physical | -> [[Data Modeling and Design]] |
| Kimball vs Inmon | Bottom-up dimensional vs top-down normalized | -> [[Data Warehousing and BI]] |
| MDM Styles | Registry, Consolidation, Coexistence, Centralized | -> [[Reference and Master Data]] |
| Kotter's 8 Steps | Urgency through Anchoring change in culture | -> [[Change Management]] |
| CMM Levels | Initial -> Repeatable -> Defined -> Managed -> Optimizing | -> [[Maturity Assessment]] |

## Related Notes
- [[MOC - DAMA DMBOK2]]
- [[testing_tutor/Data_Management_StudyVault/00-Dashboard/Exam Traps]]
