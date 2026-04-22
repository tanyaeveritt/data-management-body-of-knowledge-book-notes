---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 13"
keywords:
  - data quality
  - data quality dimensions
  - data profiling
  - root cause analysis
  - SPC
  - Shewhart
  - data cleansing
  - SLA
tags:
  - dmbok2
  - data-quality
---

# Data Quality
*Reading time: ~10 min*

## Overview Table (At a Glance)

| Aspect | Detail |
|---|---|
| **Definition** | Planning, implementation, and control of activities that apply quality management techniques to data, in order to assure it is fit for consumption and meets the needs of data consumers |
| **Goals** | (1) Develop a governed approach to make data fit for purpose; (2) Define standards and specifications for DQ controls as part of the data lifecycle; (3) Define/implement processes to measure, monitor, and report on DQ levels; (4) Identify and advocate for improvement opportunities |
| **Key Activities** | Define high quality data, define DQ strategy, identify critical data and business rules, perform initial assessment, identify/prioritize improvements, define goals, develop/deploy DQ operations |
| **Key Roles** | CDO, DQ Analysts, Data Stewards, Data Owners, DBAs, Data Professionals, DQ Managers, IT Operations, Data Integration Architects, Compliance Team |
| **Key Metrics** | Governance and conformance metrics, DQ measurement results, improvement trends, issue management metrics |

---

## Business Drivers

- Increasing the value of organizational data and opportunities to use it
- Reducing risks and costs of poor quality data (inability to invoice correctly, lost revenue, delayed M&A integration, increased fraud, bad decisions)
- Improving organizational efficiency and productivity
- Protecting and enhancing the organization's reputation

---

## Core Principles of Data Quality Management

1. **Criticality**: Focus on data most critical to the enterprise and its customers
2. **Lifecycle Management**: Manage quality across the data lifecycle, from creation to disposal
3. **Prevention**: Focus on preventing data errors, not just correcting records
4. **Root Cause Remediation**: Address root causes, not just symptoms; often requires process/system changes
5. **Governance**: DQ and governance must support each other
6. **Standards-Driven**: Requirements defined as measurable standards
7. **Objective Measurement and Transparency**: Measure objectively and consistently; share with stakeholders
8. **Embedded in Business Processes**: Business process owners are responsible for quality of data produced
9. **Systematically Enforced**: System owners must enforce DQ requirements
10. **Connected to Service Levels**: DQ reporting and issues management should be incorporated into SLAs

---

## Data Quality Dimensions

### DAMA UK Six Core Dimensions
1. **Completeness**: Proportion of data stored against the potential for 100%
2. **Uniqueness**: No entity recorded more than once based on how it is identified
3. **Timeliness**: Degree to which data represents reality from the required point in time
4. **Validity**: Data conforms to the syntax (format, type, range) of its definition
5. **Accuracy**: Degree to which data correctly describes the real-world object or event
6. **Consistency**: Absence of difference when comparing two or more representations against a definition

### Additional Dimensions (Commonly Tested)
- **Integrity / Coherence**: Referential integrity, internal consistency; orphan records, data loss
- **Reasonability**: Whether data patterns meet expectations (e.g., sales distribution by geography)
- **Timeliness Sub-concepts**: Data currency (most up-to-date), data latency (time between creation and availability)

### DQ Dimension Frameworks
- **Strong-Wang (1996)**: 15 dimensions in 4 categories -- Intrinsic DQ (accuracy, objectivity, believability, reputation), Contextual DQ (value-added, relevancy, timeliness, completeness, appropriate amount), Representational DQ (interpretability, ease of understanding, consistency, concise representation), Accessibility DQ (accessibility, access security)
- **Redman (1996)**: Dimensions rooted in data structure; categories: Data Model (content, level of detail, composition, consistency, reaction to change), Data Values (accuracy, completeness, currency, consistency), Representation (appropriateness, interpretability, portability, format precision, null values, storage efficiency)
- **English (1999)**: Inherent characteristics (definitional conformance, completeness, validity, accuracy to surrogate/reality, precision, non-duplication, equivalence, concurrency) and Pragmatic characteristics (accessibility, timeliness, contextual clarity, usability, derivation integrity, rightness)

---

## Critical Data

- Not all data is of equal importance; focus on data most important to the organization
- Data criticality assessed by whether it is required for: regulatory reporting, financial reporting, business policy, ongoing operations, business strategy
- **Master Data is critical by definition**
- Data elements assessed by: processes that consume them, reports they appear in, financial/regulatory/reputational risk

---

## Data Quality Business Rule Types

- **Definitional conformance**: Same understanding implemented properly across processes
- **Value presence and record completeness**: Conditions for acceptable/unacceptable missing values
- **Format compliance**: Patterns for data element values (e.g., telephone number formats)
- **Value domain membership**: Value from a defined set (e.g., 2-character state codes)
- **Range conformance**: Value within a defined numeric, lexicographic, or time range
- **Mapping conformance**: Value corresponds to equivalent values in other domains (e.g., 'AL' and '01' both map to 'Alabama')
- **Consistency rules**: Conditional assertions maintaining relationships between attributes (e.g., postal code + state)
- **Accuracy verification**: Compare to a system of record or verified source
- **Uniqueness verification**: Each real-world object has one and only one record
- **Timeliness validation**: Expectations for accessibility and availability of data

---

## Data Quality and Metadata

- Metadata is critical to managing data quality; it defines what the data represents
- Metadata provides the primary means of clarifying expectations (standards, requirements, definitions)
- A Metadata repository can house DQ measurement results for sharing across the organization
- Data quality rules and standards are a critical form of Metadata

---

## Data Quality Improvement Lifecycle (Shewhart / Deming Cycle)

The PDCA cycle applied to data quality:

1. **Plan**: Assess scope, impact, and priority of issues; evaluate alternatives; analyze root causes; determine cost/benefit
2. **Do**: Address root causes; plan ongoing monitoring; implement changes with process owners and technical teams
3. **Check**: Monitor data quality against requirements; if data meets thresholds, process is under control
4. **Act**: Address and resolve emerging quality issues; start new cycle for continuous improvement

New cycles begin when: measurements fall below thresholds, new data sets come under investigation, new requirements emerge, or business rules/standards change.

---

## Common Causes of Data Quality Issues

### Lack of Leadership
- Lack of awareness, governance, leadership/management, difficulty justifying improvements
- Root causes: inappropriate culture, organizational silos, lack of vision/strategy/policy

### Data Entry Processes
- Poorly designed interfaces (missing edits/controls, list entry placement, field overloading)
- Training issues (lack of process knowledge, incentivized for speed not accuracy)
- Changes to business processes not propagated to systems
- Inconsistent business process execution

### Data Processing Functions
- Incorrect assumptions about data sources; inadequate knowledge transfer when SMEs leave
- Stale business rules not periodically reviewed/updated
- Changed data structures without informing downstream consumers

### System Design
- Failure to enforce referential integrity (orphans, duplicates, default values)
- Failure to enforce uniqueness constraints (overstated aggregations)
- Coding inaccuracies/gaps in data mapping
- Data model inaccuracies (field length exceeded, incorrect key assignment)
- Field overloading (re-use of fields for different purposes)
- Temporal data mismatches (disparate date formats)
- Weak Master Data Management (unreliable sources)
- Data duplication (single source/multiple instances, multiple sources/single instance)

### Fixing Issues
- Manual data patches (scripts/commands directly on database, not through application interfaces)
- High risk of further errors, unintended consequences, security breaches
- Generally NOT undoable without full restore from backup
- **All changes should go through governed change management**

---

## Data Profiling

- Uses statistical techniques to discover the true structure, content, and quality of data
- Produces: counts of nulls, max/min values, max/min lengths, frequency distributions, data type/format analysis
- Cross-column analysis identifies overlapping/duplicate columns and embedded value dependencies
- Inter-table analysis explores overlapping value sets and foreign key relationships
- Profiling is a first step -- solving problems requires business process analysis, lineage analysis, and deeper investigation

---

## Data Processing for Quality

- **Data Cleansing/Scrubbing**: Transform data to conform to standards and domain rules; ideally decreases over time as root causes are resolved
- **Data Enhancement/Enrichment**: Adding attributes to increase quality and usability (timestamps, audit data, reference vocabularies, geographic/demographic/psychographic/valuation information)
- **Data Parsing and Formatting**: Analyzing data using rules to define content; extracting and rearranging tokens into standard representation
- **Data Transformation and Standardization**: Rule-based transformations mapping values to target representation; standardization employs context, linguistics, and idiom rules

---

## Data Quality Operations

### Manage DQ Rules
- Document consistently, define in terms of DQ dimensions, tie to business impact, back by data analysis, confirm with SMEs, make accessible to all consumers

### Measure and Monitor
- Two reasons: inform data consumers about quality levels, and manage risk of change
- Rules have standard/target/threshold for comparison
- Measurements at three granularity levels: data element, data record, data set
- Monitoring techniques: in-stream (edit checks, validation services, inspection between stages) and batch (direct queries, profiling tools)

### Issue Management
- Diagnose (trace lineage, identify root cause), formulate remediation options, resolve (assess costs/merits, implement)
- Track in incident tracking system with descriptions, root causes, options, and decisions
- Standardize DQ vocabulary, provide assignment process, manage escalation, manage resolution workflow

### Service Level Agreements
- Cover: data elements, business impacts, DQ dimensions, expectations, methods, thresholds, stewards to notify, timelines, escalation strategy

### Reporting
- DQ scorecard, trends, SLA metrics, issue management status, governance conformance, positive effects of improvements

---

## Statistical Process Control (SPC)

- Method to manage processes by analyzing measurements of variation in inputs, outputs, or steps
- Primary tool: **Control Chart** (time series graph with central line for average and upper/lower control limits)
- **Common Causes**: Inherent variation in the process; system is "in control"
- **Special Causes**: Unpredictable/intermittent; measurements outside control limits indicate special cause
- Used for control (establish baseline), detection (identify unexpected variation), and improvement (reduce common cause effects)

---

## Root Cause Analysis

- Root cause = factor that, if eliminated, would remove the problem itself
- Common techniques: Pareto analysis (80/20 rule), fishbone diagram, track and trace, process analysis, Five Whys

---

## Preventive vs. Corrective Actions

### Preventive
- Data entry controls, training data producers, defining/enforcing rules ("data firewall"), demanding quality from suppliers, governance/stewardship, formal change control

### Corrective
- **Automated correction**: Rule-based standardization without manual intervention (e.g., address correction)
- **Manually-directed correction**: Automated remediation with manual review before committing (scored confidence); appropriate for sensitive data like MDM
- **Manual correction**: Through controlled interface with audit trail; AVOID direct production database changes

---

## Exam/Test Patterns (Frequently Tested)

- DQ Management is a **program, not a project** -- includes project and maintenance work plus communications and training
- DAMA UK six core dimensions: completeness, uniqueness, timeliness, validity, accuracy, consistency
- Distinction between accuracy (real-world correctness) and validity (conformance to domain rules)
- Timeliness sub-concepts: currency (up-to-date) and latency (creation-to-availability delay)
- Shewhart/Deming PDCA cycle applied to data quality improvement
- Data profiling: first step, identifies issues but not root causes
- Prevention focus over correction: building quality into processes is cheaper than retrofitting
- Root cause analysis: Pareto, fishbone, Five Whys
- SPC: control chart, common causes vs. special causes
- DQ SLA components: data elements, dimensions, thresholds, stewards, escalation
- Common causes of DQ issues: leadership, data entry, data processing, system design, fixing issues
- Master Data is critical by definition

---

## Related Notes

- [[Data Governance]] -- DQ programs are more effective within governance; governance accelerates DQ work
- [[Reference and Master Data]] -- Master Data is critical by definition; MDM and DQ are deeply intertwined
- [[Metadata Management]] -- Metadata defines what data represents; DQ rules are a form of Metadata
- [[Data Warehousing and BI]] -- DW reveals source system quality issues; DQ feedback loops
- [[Data Integration and Interoperability]] -- Data cleansing, transformation, and standardization during integration
- [[Data Architecture]] -- System design issues cause DQ problems; architecture decisions impact quality
- [[Data Modeling and Design]] -- Model inaccuracies cause DQ issues; models define expected data structures
