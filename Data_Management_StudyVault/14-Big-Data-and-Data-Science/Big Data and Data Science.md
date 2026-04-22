---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 14"
keywords: "big data, data science, data lake, machine learning, predictive analytics, prescriptive analytics, visualization, MPP, Hadoop, MapReduce, sentiment analysis, data mining, ELT, services-based architecture"
tags:
  - dmbok2
  - big-data
---

# Big Data and Data Science
*Reading time: ~10 min*

## Overview Table (At a Glance)

| Aspect | Details |
|---|---|
| **Definition** | The collection (Big Data) and analysis (Data Science, Analytics, and Visualization) of many types of data to find answers and insights for questions not known at the start of analysis |
| **Goals** | 1) Discover relationships between data and business; 2) Support iterative integration of data sources; 3) Discover new factors affecting business; 4) Publish data using visualization in an appropriate, trusted, ethical manner |
| **Inputs** | Business strategy and goals, Build/Buy/Rent decision tree, IT standards, data sources |
| **Activities** | (P) Define strategy and business needs, Choose data sources; (D) Acquire and ingest sources, Develop hypotheses and methods, Integrate/align data, Explore data using models; (O) Deploy and monitor |
| **Deliverables** | Big Data strategy and standards, data sourcing plan, acquired data sources, initial data analysis and hypotheses, data insights and findings, enhancement plan |
| **Suppliers** | Big Data platform architects, data scientists, data producers, data suppliers, information consumers |
| **Participants** | Ingestion architects, data SMEs, analytic design lead, DM managers, metadata specialists |
| **Consumers** | Business partners, business executives, IT executives |
| **Tools** | Distributed file-based solutions, columnar compression, MPP shared-nothing architectures, in-memory computing, in-database algorithms, data visualization toolsets |
| **Metrics** | Data usage metrics, response/performance metrics, data loading/scanning metrics, learnings and stories |

---

## Business Drivers

- The desire to find and act on business opportunities discovered through diversified data sets
- Big Data stimulates innovation by making larger data sets available for exploration
- Data Science can define predictive models that anticipate customer needs and enable personalized products/services
- Machine learning algorithms can automate complex activities, improving organizational efficiency, reducing costs, and mitigating risks

---

## Key Principles

- Organizations should carefully manage **Metadata related to Big Data sources** to maintain an accurate inventory of data files, their origins, and their value
- Big Data management requires **more discipline** than relational data management due to wide variation in sources and formats
- Without Metadata management, a data lake quickly becomes a **data swamp**

---

## The Six V's of Big Data

- **Volume**: Amount of data -- often billions of records, exceeding 100 TB into Petabyte/Exabyte range
- **Velocity**: Speed at which data is captured, generated, or shared -- often real-time
- **Variety / Variability**: Multiple formats; data structure is often inconsistent within or across data sets
- **Viscosity**: How difficult the data is to use or integrate
- **Volatility**: How often data changes occur and how long the data remains useful
- **Veracity**: How trustworthy the data is

---

## Data Science Concepts

### Analytics Progression

| DW / Traditional BI | Data Science: Predictive | Data Science: Prescriptive |
|---|---|---|
| Descriptive / Hindsight | Insight | Foresight |
| "What happened? Why?" | "What is likely to happen?" | "What should we do to make things happen?" |

### The Data Science Process (7 Iterative Steps)

1. **Define Big Data Strategy and Business Needs** -- requirements with measurable tangible benefits
2. **Choose Data Sources** -- identify gaps, evaluate data for worth and reliability
3. **Acquire and Ingest Data Sources** -- obtain and onboard data sets, capture critical Metadata
4. **Develop Data Hypotheses and Methods** -- explore via profiling, visualization, mining; define model algorithm inputs
5. **Integrate / Align Data for Analysis** -- leverage trusted sources; apply integration and cleansing techniques
6. **Explore Data Using Models** -- apply statistical analysis and machine learning; validate, train, and evolve the model
7. **Deploy and Monitor** -- deploy useful models to production for ongoing monitoring

### Data Science Dependencies

- **Rich data sources** with potential to show invisible patterns
- **Information alignment and analysis** techniques to combine data sets
- **Information delivery** through models and mathematical algorithms
- **Presentation of findings** so insights can be shared

---

## Machine Learning

- Explores construction and study of learning algorithms
- Three types:
  - **Supervised learning**: Based on generalized rules (e.g., spam classification)
  - **Unsupervised learning**: Based on identifying hidden patterns (data mining)
  - **Reinforcement learning**: Based on achieving a goal (e.g., game playing)
- Ethical implications: deep learning neural networks can function as **"black boxes"** -- the need for transparency increases as functionality evolves
- Machine learning automates costly R&D by performing trial-and-error passes on vast data sets

---

## Analytical Techniques

### Sentiment Analysis
- Automated methods retrieving insights from unstructured/semi-structured data (social media, blogs, news)
- Uses Natural Language Processing (NLP) to detect sentiment and changes in sentiment
- Words alone don't tell the whole story -- context interpretation is required

### Data and Text Mining
- Data mining reveals patterns using algorithms -- a subset of unsupervised learning
- Text mining classifies content automatically into ontologies
- Key techniques: **Profiling**, **Data Reduction**, **Association**, **Clustering**, **Self-Organizing Maps** (Kohonen Maps)

### Predictive Analytics
- Sub-field of supervised learning; models data elements and predicts future outcomes via probability estimates
- Triggering factors: customer actions, data streams, news feeds, sensor data
- Simplest form: the **forecast** (regression analysis with smoothing)

### Prescriptive Analytics
- Takes predictive analytics further to define actions that will **affect** outcomes
- Anticipates what, when, and why; can suggest how to take advantage of opportunities or avoid risks
- Continually takes in new data to re-predict and re-prescribe

### Operational Analytics
- Integration of real-time analytics into operations (also called streaming analytics)
- Tracks real-time streams, derives conclusions from predictive models, triggers automatic responses/alerts

### Unstructured Data Analytics
- Combines text mining, association, clustering, and other techniques to codify large unstructured data sets
- Scanning and tagging adds "hooks" to unstructured data for filtering and linking

---

## Big Data Architecture

### ETL vs. ELT -- Critical Distinction
- **Traditional DW**: Extract, **Transform**, Load (ETL) -- data integrated as it enters
- **Big Data**: Extract, **Load**, Transform (ELT) -- data ingested then integrated through use
- ELT does not necessarily rely on or produce an enterprise data model

### Data Lake
- Environment where vast amounts of varied data can be ingested, stored, assessed, and analyzed
- Purposes: Data Science mining, central raw data storage, historical DW data, online archive, streaming data with pattern identification
- **Risk**: Without Metadata management, a data lake becomes a **data swamp**

### Services-Based Architecture (SBA)
- Three layers: **Batch layer** (data lake with historical data), **Speed layer** (real-time data only), **Serving layer** (interface joining batch and speed layers)
- All analytic computations performed on data in both batch and speed layers
- Organizations address synchronization through trade-offs between completeness, latency, and complexity

### Data Mashups
- Combine data and services to create visualization for insight or analysis
- Relate data sources by common elements; ideal during discovery/exploration phases

---

## Tools and Technologies

### MPP Shared-Nothing Architecture
- Data partitioned across multiple processing servers, each with dedicated memory
- No disk sharing or memory contention -- linearly scalable
- Enabled **in-database analytical functions** (K-means Clustering, Regression) at the processor level

### Distributed File-Based Databases (Hadoop)
- Inexpensive storage for large amounts of data in any format (structured, semi-structured, unstructured)
- **MapReduce** language with three steps: **Map** (identify data), **Shuffle** (combine by pattern), **Reduce** (remove duplication/aggregate)

### In-Database Algorithms
- Mathematical and statistical functions at the computing node level
- Open-source libraries for machine learning, statistics; computation close to the data

### Statistical Computing Languages
- **R**: Open source scripting language for statistical computing and graphics
- Supports linear/nonlinear modeling, time-series, classification, clustering
- Models developed in R can be implemented across platforms

---

## Data Source Selection Criteria

- **Foundational data**: Consider foundational components (e.g., POS in sales analysis)
- **Granularity**: Obtain data in its most granular form
- **Consistency**: Select data that appears appropriately across visualizations
- **Reliability**: Choose meaningful and credible sources over time
- **Inspect/Profile**: Test changes before adding new data sets

---

## Data Visualization

- Facilitates understanding by presenting data in visual summaries (charts, graphs)
- Can be static (published reports) or interactive (drilling, filtering)
- Advanced tools: small multiples, spark lines, heat maps, histograms, waterfall charts, bullet graphs
- Visualizations should **tell a story** and be supported by explanatory text
- Risk: misleading visualizations -- ethical component applies

---

## Model Development Lifecycle

### Model Training
- Execute model against data repeatedly to verify assumptions
- Avoid **over-fitting** by training against a limited data fold
- Address population imbalances with model offsets
- Optimizing feature mix: Bayesian co-selection, classifier inversion, rule induction, ensemble learning
- Identifying **outliers/anomalies** is critical to model evaluation

### Model Evaluation
- Divide data into three parts: **training set**, **validation set**, **test set**
- Use **K-fold cross-validation** to avoid underestimating true test error
- Training error consistently decreases with model complexity -- not a useful estimate of test error

---

## Big Data Governance

- Big Data requires governance over: **Sourcing**, **Sharing**, **Metadata**, **Enrichment**, **Access**
- Visualization channels must be managed and coordinated across the portfolio
- Data Science standards should include: tools standards, data set process standards, processes for neutral presentation to avoid biased results

### Data Security Concerns
- Recombination: ability to reconstitute sensitive/private data must be managed
- Analysis outcomes may violate privacy even when individual data elements can only be inferred
- Encryption techniques can obfuscate information while preserving patterns

### Data Quality for Big Data
- Quality measures: **Discovery**, **Classification**, **Profiling**, **Mapping**
- Without assessment, it may be impossible to know what Big Data represents or how to connect data sets
- Integration will be necessary and data feeds are unlikely to have identical structures

---

## Implementation Guidelines

- Strategy must align with organizational objectives
- Assess organizational readiness: business relevance, business readiness, economic viability, prototype feasibility
- Consider leasing a Big Data platform for finite exploration before ingesting into organizational data lake
- Data velocity is not an excuse to skip controls -- managing ingestion is critical

### Key Cross-Functional Roles
- **Big Data Platform Architect**: Hardware, OS, filesystems, services
- **Ingestion Architect**: Data analysis, systems of record, data modeling/mapping
- **Metadata Specialist**: Metadata interfaces, architecture, and contents
- **Analytic Design Lead**: End-user analytic design and best practice guidance
- **Data Scientist**: Architecture and model design consultation, statistical/computational theory

---

## Exam/Test Patterns (Frequently Tested)

- The **Six V's** of Big Data (Volume, Velocity, Variety, Viscosity, Volatility, Veracity)
- **ETL vs. ELT** distinction and implications for data management
- **Analytics Progression**: Descriptive (hindsight) vs. Predictive (insight) vs. Prescriptive (foresight)
- **Data lake vs. data swamp** -- the role of Metadata management
- **Three types of machine learning**: supervised, unsupervised, reinforcement
- **MapReduce** three steps: Map, Shuffle, Reduce
- **MPP shared-nothing** architecture characteristics and benefits
- **Over-fitting** and how to avoid it (K-fold cross-validation)
- **Services-Based Architecture** three layers: batch, speed, serving
- **Data Science process** -- 7 iterative steps
- Risks of **recombination** of data sets and privacy implications
- Role of **data quality** in Big Data -- why it still matters
- **Data visualization** principles and risk of misleading visualizations
- **Sentiment analysis** limitations -- context is needed beyond keywords

---

## Related Notes

- [[Maturity Assessment]]
- [[DM Organization and Roles]]
- [[Change Management]]
- [[Data Governance]]
- [[Data Quality]]
- [[Data Architecture]]
- [[Data Integration and Interoperability]]
- [[Metadata Management]]
- [[Data Warehousing and BI]]
- [[Data Security]]
- [[Data Management]]
