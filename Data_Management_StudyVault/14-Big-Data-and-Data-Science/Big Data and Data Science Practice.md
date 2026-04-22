---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 14"
keywords: "big data, data science, data lake, machine learning, predictive analytics, prescriptive analytics, visualization, MPP, Hadoop, MapReduce, sentiment analysis, ETL, ELT"
tags:
  - dmbok2
  - big-data
  - practice
---

# Big Data and Data Science -- Practice Questions

## Related Concepts

- [[Big Data and Data Science]]
- [[Data Architecture]]
- [[Data Quality]]
- [[Data Governance]]
- [[Metadata Management]]
- [[Data Integration and Interoperability]]
- [[Data Warehousing and BI]]

---

> [!hint]- Key Patterns (click to view)
> - The **Six V's** of Big Data (Volume, Velocity, Variety, Viscosity, Volatility, Veracity) are heavily tested -- especially distinguishing Viscosity from Volatility
> - **ETL vs. ELT** is a fundamental distinction with implications across the chapter
> - The **Analytics Progression** (Descriptive/Predictive/Prescriptive) maps to Hindsight/Insight/Foresight
> - **Data lake vs. data swamp** comes down to Metadata management
> - **Three types of machine learning** (supervised, unsupervised, reinforcement) and their examples
> - **MapReduce** steps: Map, Shuffle, Reduce
> - **Model training** concepts: over-fitting, K-fold cross-validation, training/validation/test sets
> - The Data Science process is **iterative** -- 7 steps that feed back into each other
> - **Services-Based Architecture** has three layers: batch, speed, serving
> - Data quality for Big Data **does** matter -- common misconception that it doesn't

---

### Question 1 [recall]

Which of the following is NOT one of the recognized "V's" of Big Data?

A) Volume
B) Velocity
C) Validity
D) Veracity

> [!answer]- Show Answer
> **C) Validity.** The six V's of Big Data are: **Volume** (amount of data), **Velocity** (speed of generation), **Variety/Variability** (multiple formats), **Viscosity** (difficulty to use or integrate), **Volatility** (how often data changes), and **Veracity** (trustworthiness). "Validity" is not one of the recognized V's. Note that Veracity (trustworthiness) is sometimes confused with Validity, but the DMBOK2 specifically uses the term Veracity.

---

### Question 2 [recall]

What is the key difference between ETL and ELT in the context of Big Data?

> [!answer]- Show Answer
> In **ETL** (traditional data warehousing), data is Extracted, **Transformed**, then Loaded -- meaning data is integrated and transformed as it enters the warehouse. In **ELT** (Big Data approach), data is Extracted, **Loaded**, then Transformed -- meaning data is ingested first and integrated/transformed later through use. This distinction has significant implications: ELT does not necessarily rely on or produce an enterprise data model, and there is a risk that knowledge about data can be lost if ingestion and use processes are executed in an ad hoc way without proper Metadata management.

---

### Question 3 [recall]

What are the three types of Machine Learning described in the DMBOK2?

> [!answer]- Show Answer
> 1. **Supervised learning**: Based on generalized rules; learns from labeled examples (e.g., separating SPAM from non-SPAM email)
> 2. **Unsupervised learning**: Based on identifying hidden patterns with no prescribed desired outcome -- commonly referred to as data mining
> 3. **Reinforcement learning**: Based on achieving a goal where performance is earned but not specifically teacher-recognized (e.g., beating an opponent at chess, driving a vehicle)

---

### Question 4 [recall]

Name the three steps of the MapReduce language used in distributed file-based solutions.

> [!answer]- Show Answer
> 1. **Map**: Identify and obtain the data to be analyzed
> 2. **Shuffle**: Combine the data according to the analytical patterns desired
> 3. **Reduce**: Remove duplication or perform aggregation to reduce the resulting data set to only what is required
>
> These steps can be combined in different tools in different ways, both in sequence and in parallel, to perform complex manipulations.

---

### Question 5 [recall]

What are the three layers of a Services-Based Architecture (SBA)?

> [!answer]- Show Answer
> 1. **Batch layer**: A data lake that serves as the batch layer, containing both recent and historical data (every transaction is an insert)
> 2. **Speed layer**: Contains only real-time data (all transactions are updates)
> 3. **Serving layer**: Provides an interface to join data from the batch and speed layers; abstracts data using Metadata
>
> The SBA provides both immediate (speed layer) and complete/accurate historical data (batch layer). Organizations address synchronization through trade-offs between completeness, latency, and complexity of merged views in the serving layer.

---

### Question 6 [application]

An organization has ingested hundreds of data sets into its data lake over the past year, but analysts report they cannot find relevant data, don't know the origin of data sets, and are unsure which data sets can be combined for analysis. What is the most likely root cause, and what should the organization do?

> [!answer]- Show Answer
> The most likely root cause is **poor Metadata management**. The data lake has become a **data swamp** -- messy, unclean, and inconsistent. According to the DMBOK2, "without Metadata management, a data lake quickly becomes a data swamp."
>
> The organization should:
> - Implement a critical Metadata management process as data is ingested, capturing origin, size, currency, content, and lineage
> - Create a master list of data sets with Metadata characterizing structure, content, quality, source, lineage, and intended uses
> - Use unique keys, semantic models, or data models to connect data sets so scientists know how to use the information
> - Profile data as it is ingested to provide analysts with at least partial Metadata
> - Establish governance over ingestion processes to prevent further degradation

---

### Question 7 [application]

A data science team is building a predictive model for customer churn. They train the model on their full data set and achieve 99.5% accuracy. When they deploy it to production, it performs poorly on new data. What happened, and how should they have approached model training?

> [!answer]- Show Answer
> The team likely suffered from **over-fitting** -- the model was trained against the entire data set and described noise instead of the underlying relationship. Training error consistently decreases with model complexity and can drop to zero, but this is not a useful estimate of test error.
>
> The correct approach is to:
> 1. **Randomly divide the data into three parts**: training set, validation set, and test set
> 2. Use the **training set** to fit the model
> 3. Use the **validation set** to predict error for model selection
> 4. Use the **test set** for assessment of generalization error of the final model
> 5. Apply **K-fold cross-validation**: randomly divide data into K groups, train on all but one group, test on the remaining, and determine generalization error based on all K folds
> 6. Avoid reusing the same test set repeatedly (underestimates true test error)
> 7. Use techniques like Bayesian co-selection, classifier inversion, or ensemble learning to optimize the feature mix

---

### Question 8 [application]

A retail company wants to use Big Data analytics to personalize product recommendations, combining purchase history, demographic data, web browsing behavior, and social media posts. What data source selection criteria should they apply, and what governance concerns must they address?

> [!answer]- Show Answer
> **Data source selection criteria** (per DMBOK2):
> - **Foundational data**: Include POS (point of sale) data as the foundational component
> - **Granularity**: Obtain data in its most granular form so it can be aggregated for multiple purposes
> - **Consistency**: Ensure data appears appropriately and consistently across visualizations
> - **Reliability**: Choose meaningful, credible, authoritative sources over time
> - **Inspect/Profile**: Test and profile new sources before adding to avoid unexpected changes in visualization outcomes
>
> **Governance concerns**:
> - **Privacy/Recombination risk**: The ability to rapidly ingest and integrate data from multiple sources enables recombination of data sets that were otherwise secured; analysis outcomes may violate privacy even when individual elements can only be inferred
> - **Bias risk**: Criteria used to select or filter data must be objectively managed to avoid biases or skews
> - **Data sharing agreements**: Contracts and terms for external data (social media, demographics)
> - **Ethical component**: Models can have unexpected results or unintentionally reflect biases of creators; ethical training is required for AI practitioners
> - **Security**: Securely provision appropriate levels of data; mask sensitive information for unauthorized communities

---

### Question 9 [analysis]

Compare and contrast the implications of adopting an ELT approach versus a traditional ETL approach for an organization's data management practices. Consider impacts on data modeling, Metadata management, data quality, and governance.

> [!answer]- Show Answer
> **Data Modeling**:
> - ETL relies on and produces an enterprise data model during the transformation phase, creating a structured, documented representation of data
> - ELT does not necessarily rely on or produce an enterprise data model; integration happens through particular uses (e.g., building predictive models drives integration of specific data sets)
> - Risk: much knowledge about data can be lost with ELT if processes are ad hoc
>
> **Metadata Management**:
> - ETL generates Metadata as a natural byproduct of the transformation process (mappings, lineage, business rules)
> - ELT requires **proactive Metadata management** during ingestion or the data lake becomes a swamp; the DMBOK2 calls this the most clear principle of Big Data management
> - Real-time feeds, data at rest, and computational elements all need lineage tracking
>
> **Data Quality**:
> - ETL typically includes data quality checks as part of the transformation pipeline
> - With ELT, DQ assessment must be done separately -- "just as in DW/BI, it is tempting to put data quality assessment last"
> - Without assessment, it may be impossible to know what the data represents or how to connect data sets
> - Most mature Big Data organizations scan input sources using DQ toolsets for Discovery, Classification, Profiling, and Mapping
>
> **Governance**:
> - ETL environments have well-established governance patterns tied to the transformation process
> - ELT environments require governance over sourcing, sharing, Metadata, enrichment, and access -- with less structural enforcement
> - Data velocity may lead people to think they don't have time for controls -- this is a "dangerous assumption"
> - Big Data governance must address recombination risks, ethical concerns, and visualization standards

---

### Question 10 [analysis]

An organization is debating whether data quality matters for Big Data. Some argue that the sheer volume compensates for quality issues. Evaluate this argument using DMBOK2 principles, and explain why data quality assessment is essential even in Big Data environments.

> [!answer]- Show Answer
> The argument that volume compensates for quality is fundamentally flawed, and the DMBOK2 directly addresses this: "Some people have raised the question of whether data quality even matters for Big Data. Common sense says it does. For analytics to be reliable, the underlying data must be reliable."
>
> **Why DQ matters for Big Data:**
>
> 1. **Reliability of analytics**: Models depend on both the quality of input data and the soundness of the model itself. Poor quality inputs produce unreliable outputs regardless of volume.
>
> 2. **Integration necessity**: Data feeds will almost never have identical structures and elements. Codes and linking data vary between providers. Without DQ assessment, mismatches go unnoticed until an analytic need attempts to merge those providers.
>
> 3. **Understanding content**: DQ assessment produces valuable Metadata necessary for any integration effort. Four key functions: **Discovery** (where information resides), **Classification** (what types of information based on patterns), **Profiling** (how data is populated and structured), **Mapping** (what other data sets can match).
>
> 4. **Model training**: Data quality directly affects model training. Population imbalances or data biases must be addressed with model offsets. Training against poor-quality data leads to over-fitting or systematically biased predictions.
>
> 5. **Ethical concerns**: Models can have unexpected results or unintentionally reflect biases. Poor quality data amplifies these risks. Filtering criteria must be objectively managed -- removing outliers or restricting domains can have material impact on results.
>
> 6. **Governance requirements**: Data quality measures are part of Big Data governance -- organizations need to measure deviation from expected results and maintain confidence in analyses.
>
> In summary, Big Data's volume does not compensate for quality issues -- it can actually amplify them. An initial DQ assessment is necessary to understand the data, and ongoing measurement ensures confidence in analyses.

---

> [!summary]- Pattern Summary (click to view)
> **High-frequency topics**: Six V's of Big Data, ETL vs. ELT, Analytics Progression (Descriptive/Predictive/Prescriptive), Data Lake vs. Data Swamp, Machine Learning types, MapReduce steps, SBA layers.
>
> **Common traps**: Confusing Veracity with Validity; thinking volume compensates for quality; assuming ELT eliminates the need for data modeling; overlooking privacy/recombination risks; equating model training accuracy with real-world performance (over-fitting).
>
> **Analysis patterns**: Questions typically ask you to evaluate trade-offs (ETL vs. ELT implications), apply governance principles to Big Data scenarios, or explain why established DM practices (like DQ and Metadata) remain essential in Big Data contexts. Look for questions that test whether you understand that Big Data requires *more* discipline, not less.
