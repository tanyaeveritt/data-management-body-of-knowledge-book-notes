---
source_pdf: "DAMA-DMBOK2 PDF.pdf"
part: "Chapter 13"
keywords:
  - data quality
  - data quality dimensions
  - data profiling
  - root cause analysis
  - SPC
  - Shewhart Deming
  - PDCA
  - data cleansing
tags:
  - dmbok2
  - data-quality
  - practice
---

# Data Quality -- Practice Questions

## Related Concepts

- [[Data Quality]]
- [[Data Governance]]
- [[Reference and Master Data]]
- [[Metadata Management]]
- [[Data Warehousing and BI]]
- [[Data Integration and Interoperability]]
- [[Data Modeling and Design]]

---

> [!hint]- Key Patterns (click to view)
> - DQ Management is a PROGRAM, not a project -- ongoing commitment
> - DAMA UK 6 core dimensions: completeness, uniqueness, timeliness, validity, accuracy, consistency
> - Accuracy = matches real world; Validity = conforms to domain rules (data can be valid but inaccurate)
> - Timeliness has sub-concepts: currency (most up-to-date) and latency (time from creation to availability)
> - Shewhart/Deming PDCA: Plan-Do-Check-Act cycle for continuous improvement
> - Prevention is cheaper than correction; building quality in costs less than retrofitting
> - Root cause analysis: Pareto (80/20), fishbone diagram, Five Whys
> - SPC: control chart with upper/lower limits; common causes (inherent) vs. special causes (unexpected)
> - Three correction types: automated, manually-directed (scored confidence), manual (with audit trail)
> - Data profiling is the FIRST step; identifies issues but NOT root causes

---

### Q1. List the DAMA UK six core dimensions of data quality and briefly define each. [recall]

> [!answer]- Show Answer
> 1. **Completeness**: The proportion of data stored against the potential for 100%. Are all required data elements populated?
> 2. **Uniqueness**: No entity instance is recorded more than once based on how that thing is identified.
> 3. **Timeliness**: The degree to which data represents reality from the required point in time.
> 4. **Validity**: Data is valid if it conforms to the syntax (format, type, range) of its definition.
> 5. **Accuracy**: The degree to which data correctly describes the "real world" object or event being described.
> 6. **Consistency**: The absence of difference when comparing two or more representations of a thing against a definition.

---

### Q2. What is the difference between accuracy and validity? Can data be valid but inaccurate? [recall]

> [!answer]- Show Answer
> **Validity** = Data conforms to the syntax, format, type, and range of its definition. It meets the domain rules.
>
> **Accuracy** = Data correctly describes the real-world object or event.
>
> **Yes, data can be valid but inaccurate.** For example, a customer's postal code "90210" is a valid US ZIP code (it exists and has the correct format), but if the customer actually lives in ZIP code "10001," the data is valid but inaccurate. The value passes domain constraints but does not correctly represent reality.
>
> This distinction is important because many automated checks verify validity (format, range, domain membership) but cannot verify accuracy without comparing to a verified source or the real world.

---

### Q3. Name and describe the four stages of the Shewhart/Deming cycle as applied to data quality improvement. [recall]

> [!answer]- Show Answer
> 1. **Plan**: Assess the scope, impact, and priority of known DQ issues. Evaluate alternatives to address them. Analyze root causes. Understand cost/benefit and formulate a basic plan.
>
> 2. **Do**: Lead efforts to address root causes. For non-technical causes, work with process owners to implement changes. For technical causes, work with technical teams to ensure correct implementation without introducing new errors. Plan for ongoing monitoring.
>
> 3. **Check**: Actively monitor data quality against requirements. As long as data meets defined thresholds, process is under control. If data falls below acceptable thresholds, take additional action.
>
> 4. **Act**: Address and resolve emerging DQ issues. Restart the cycle for continuous improvement. New cycles begin when measurements fall below thresholds, new data sets come under investigation, new requirements emerge, or business rules change.
>
> Key insight: This is based on the scientific method. "The cost of getting data right the first time is cheaper than the costs of getting data wrong and fixing it later."

---

### Q4. A data quality team discovers that quarterly financial data files are consistently delivered 5 days late during quarter-end months, causing downstream DQ issues. Identify the root cause analysis technique being applied and describe what root cause was found. [application]

> [!answer]- Show Answer
> This is an example of **process analysis** combined with **track and trace** root cause analysis. The team analyzed the timing of data delivery, traced the pattern across months, and discovered a correlation with quarterly financial close activities.
>
> **Root cause**: A competing priority -- the team responsible for delivering the file also handles quarterly financial close processes, which take precedence. The file is delivered late during March, June, September, and December, impacting the quality of data for April, July, October, and January.
>
> **Root cause type**: This is a non-technical root cause related to **process scheduling and resource allocation**, not a data entry or system design issue.
>
> **Solution approach**: Address by scheduling file delivery appropriately, ensuring dedicated resources are available, or automating the file delivery process so it is not dependent on manual prioritization. This exemplifies the DMBOK2 point that "improving data quality goes beyond correcting errors" -- the root cause is a process issue, not a data issue.

---

### Q5. What is data profiling and what are five statistics it produces? Why is profiling only a "first step"? [recall]

> [!answer]- Show Answer
> **Data Profiling** is a form of data analysis that uses statistical techniques to discover the true structure, content, and quality of a collection of data.
>
> **Five statistics produced**:
> 1. **Counts of nulls** -- identifies null existence for assessment of allowability
> 2. **Max/Min value** -- identifies outliers (e.g., negatives where unexpected)
> 3. **Max/Min length** -- identifies outliers or invalids for fields with length requirements
> 4. **Frequency distribution of values** -- enables assessment of reasonability (e.g., distribution of country codes, frequently/infrequently occurring values, defaulted values)
> 5. **Data type and format** -- identifies non-conformance to format requirements and unexpected formats
>
> **Why it is only a first step**: Profiling identifies potential problems but does NOT identify root causes, nor does it determine the business impact of issues. Solving problems requires other forms of analysis: business process analysis, data lineage analysis, and deeper data analysis. Additionally, profiling results must be assessed by an analyst to determine whether data conforms to rules.

---

### Q6. What are the five common categories of causes of data quality issues identified in the DMBOK2? Give one specific example from each. [recall]

> [!answer]- Show Answer
> 1. **Lack of Leadership**: Many governance programs are driven solely by compliance rather than recognizing data's value as an asset. Lack of awareness, governance, and management commitment leads to unmaintained data.
>
> 2. **Data Entry Processes**: Poorly designed data entry interfaces without edits or controls let incorrect data enter the system. Example: drop-down list ordering that contributes to selection errors.
>
> 3. **Data Processing Functions**: Stale business rules that are not periodically reviewed lead to issues not being identified or producing false positives. Example: changed data structures in source systems without informing downstream consumers.
>
> 4. **System Design**: Failure to enforce referential integrity leads to orphan rows (included in some reports, excluded from others), duplicate data, and inability to upgrade. Example: turning off uniqueness constraints to improve performance, causing overstated aggregation results.
>
> 5. **Fixing Issues**: Manual data patches (scripts/commands applied directly to the database, not through application interfaces) have high risk of unintended consequences, changing more data than required, or not propagating patches to all affected historical data. Generally NOT undoable without full backup restore.

---

### Q7. An organization measures that its customer email address field is only 85% complete, but the business requires at least 98% to effectively support email marketing campaigns. Walk through how the DMBOK2 DQ improvement approach would address this. [application]

> [!answer]- Show Answer
> **Step 1 - Define High Quality Data**: Establish that "high quality" for this field means >= 98% completeness for usable email addresses, driven by the business need to send product information via email.
>
> **Step 2 - Define DQ Strategy**: Align email completeness improvement with business strategy (marketing effectiveness). Define measurement methods and improvement frameworks.
>
> **Step 3 - Identify Critical Data and Business Rules**: Email address is critical because incomplete data means lost potential sales. Rule: "Customer email address must be populated with a usable email address."
>
> **Step 4 - Perform Initial Assessment**: Profile the data to quantify: 85% completeness. Identify patterns -- are specific customer segments, entry channels, or time periods more affected? Develop hypotheses about root causes.
>
> **Step 5 - Identify and Prioritize Improvements**: Determine ROI: number of customers affected (15%), estimated revenue impact of missed email campaigns, cost of remediation. Root cause examples might be: optional field in the data entry form, lack of validation, no incentive for sales reps to collect emails.
>
> **Step 6 - Define Goals**: Improve from 85% to 98% through process improvements and system edits. Set interim targets.
>
> **Step 7 - Deploy DQ Operations**:
> - **Preventive**: Make email field mandatory in the CRM data entry interface; add format validation; train sales staff on importance
> - **Corrective**: Enrichment by purchasing email data from third-party vendors for existing records
> - **Monitor**: Measure completeness monthly; report trends; set up SLA with thresholds and escalation
>
> The value comes from the business benefit: fewer missed campaigns, less time correcting errors, higher customer engagement.

---

### Q8. Compare the three types of corrective actions for data quality issues. When is each most appropriate? [recall]

> [!answer]- Show Answer
> 1. **Automated Correction**: Rule-based standardization, normalization, and correction committed without manual intervention. Example: automated address correction using parsing, standardization, and reference tables.
>    - **When appropriate**: Well-defined standards, commonly accepted rules, known error patterns. Best for high-volume, low-risk corrections where rules are proven.
>
> 2. **Manually-Directed Correction**: Automated tools remediate data but require manual review before committing. Uses confidence scoring -- corrections above a threshold are committed automatically; those below go to a steward for review.
>    - **When appropriate**: Sensitive data sets requiring human oversight, such as MDM environments. Balances automation efficiency with accuracy assurance.
>
> 3. **Manual Correction**: Done through an interface with controls, edits, and audit trail. Direct production database changes are extremely risky and should be AVOIDED.
>    - **When appropriate**: Absence of tools or automation, or when the change is determined to require human judgment. Always through a controlled interface, never directly on production data.
>
> Over time, the amount of automated correction should decrease as root causes are resolved and corrected data is shared with upstream systems.

---

### Q9. An executive asks: "Why can't we just run a data cleansing project to fix all our data quality problems once and for all?" Using DMBOK2 principles, explain why this approach is insufficient. [analysis]

> [!answer]- Show Answer
> The DMBOK2 is clear that **Data Quality Management is a program, not a project**. A one-time cleansing project is insufficient for several reasons:
>
> **1. Root causes persist**: Cleansing addresses symptoms (bad data values) but not root causes (poor processes, bad system design, lack of governance). Without addressing root causes, the same issues will recur. "Improving the quality of data goes beyond correcting errors."
>
> **2. Prevention is the correct focus**: The DMBOK2 principle of prevention states that a DQ program should focus on preventing data errors, not just correcting records. A cleansing project is purely corrective.
>
> **3. Ongoing costs and risk**: "It costs money and introduces risk to continuously remediate data through cleansing." Each cleansing cycle has potential for errors and unintended consequences. The need for cleansing should DECREASE over time as root causes are resolved.
>
> **4. Quality degrades continuously**: Business processes change, new systems are introduced, personnel turn over, external data evolves. Without ongoing monitoring, measurement, and governance, quality will degrade after any one-time fix.
>
> **5. Cultural change is required**: "The long-term success of data quality improvement depends on getting an organization to change its culture and adopt a quality mindset." A one-time project does not change behaviors, training, incentives, or accountability.
>
> **6. PDCA is cyclical**: The Shewhart/Deming improvement cycle (Plan-Do-Check-Act) is inherently continuous. Check and Act stages require ongoing monitoring and response.
>
> **The correct approach**: A sustained DQ program that builds quality into processes from the beginning, addresses root causes, monitors data against standards continuously, reports on quality levels, manages issues through SLAs, and drives cultural change across the organization.

---

### Q10. What is Statistical Process Control (SPC) and how is it applied to data quality? Explain common causes vs. special causes. [analysis]

> [!answer]- Show Answer
> **SPC** is a method to manage processes by analyzing measurements of variation in process inputs, outputs, or steps. Originated in manufacturing (1920s), it is applied to DQ based on the assumption that **data is the product of a process** -- and a consistent process with consistent inputs produces consistent outputs.
>
> **Primary tool**: The **Control Chart** -- a time series graph with:
> - A central line for the average (measure of central tendency)
> - Calculated upper and lower **control limits** (variability bounds)
>
> **Common Causes**: Inherent variation in the process. When only common causes exist, the process is said to be "in (statistical) control." A range of normal variation is established as the **baseline**.
>
> **Special Causes**: Unpredictable or intermittent variation. Measurement results outside the control limits indicate a special cause -- something abnormal has occurred.
>
> **Application to DQ** (three stages):
> 1. **Control**: Measure the process, identify and eliminate special causes to establish a stable control state
> 2. **Detection**: Put measurements in place to detect unexpected variation as soon as it appears; early detection simplifies root cause investigation
> 3. **Improvement**: Use measurements to reduce unwanted effects of common causes, increasing efficiency
>
> **Example**: A monthly ETL process consistently produces data with 99.5% accuracy (common cause variation of +/- 0.3%). If one month accuracy drops to 97%, this is outside the control limits -- a special cause. Investigation might reveal a source system change or a late-arriving file.

---

> [!summary]- Pattern Summary (click to view)
> - DQ Management = program (ongoing), not project (one-time)
> - 6 core dimensions: completeness, uniqueness, timeliness, validity, accuracy, consistency
> - Accuracy vs. validity: data can be valid but inaccurate
> - Timeliness = currency (up-to-date) + latency (creation-to-availability)
> - Shewhart/Deming PDCA: Plan-Do-Check-Act; continuous improvement cycle
> - Prevention > correction; building quality in < retrofitting quality
> - Data profiling = first step only; identifies potential issues, NOT root causes
> - Root cause techniques: Pareto, fishbone, Five Whys, process analysis, track and trace
> - SPC: control chart, common (inherent) vs. special (unexpected) causes; baseline then detect
> - Three correction types: automated (rules), manually-directed (scored confidence + review), manual (audit trail, NEVER direct DB)
> - Manual data patches are STRONGLY discouraged -- high risk, generally not undoable
> - DQ SLA: elements, dimensions, thresholds, stewards, escalation, timelines
> - Master Data is critical by definition
> - DQ is more effective within a data governance program
