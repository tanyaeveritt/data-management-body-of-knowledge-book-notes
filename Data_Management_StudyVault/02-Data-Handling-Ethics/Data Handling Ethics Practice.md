---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 2
keywords: practice, data ethics, GDPR, privacy, bias, Belmont principles
---

# Data Handling Ethics Practice (10 questions)

#practice #data-ethics

## Related Concepts
- [[Data Handling Ethics]]
- [[Data Governance]]
- [[Data Security]]

> [!hint]- Key Patterns (click to view)
> | Keyword | Answer |
> |---------|--------|
> | Three Belmont Principles | **Respect for Persons, Beneficence, Justice** |
> | Menlo Report addition | **Respect for Law and Public Interest** |
> | GDPR principles (7) | **Fairness/Lawfulness/Transparency, Purpose Limitation, Data Minimization, Accuracy, Storage Limitation, Integrity/Confidentiality, Accountability** |
> | PIPEDA country | **Canada** |
> | "Do not harm" | **Beneficence** |
> | First step to ethical culture | **Review current state practices** |

---

## Question 1 - Belmont Principles [recall]
> What are the three Belmont Principles adapted for data ethics, and what does each mean?

> [!answer]- Show Answer
> (1) **Respect for Persons** -- treat people with dignity and autonomy; extra care for those with diminished autonomy. (2) **Beneficence** -- first do not harm, then maximize possible benefits and minimize possible harms. (3) **Justice** -- fair and equitable treatment of people; no disproportionate effects on specific groups. These were originally from bioethics (US-HSS, 1979) and adapted for information management.

---

## Question 2 - GDPR Principles [recall]
> List the seven GDPR principles for data processing.

> [!answer]- Show Answer
> (1) **Fairness, Lawfulness, Transparency** -- data processed lawfully, fairly, transparently; (2) **Purpose Limitation** -- collected for specified, explicit, legitimate purposes; (3) **Data Minimization** -- adequate, relevant, limited to necessity; (4) **Accuracy** -- accurate and up-to-date; (5) **Storage Limitation** -- kept no longer than necessary; (6) **Integrity and Confidentiality** -- appropriate security; (7) **Accountability** -- controllers must demonstrate compliance.

---

## Question 3 - Menlo Report [recall]
> What fourth principle did the US Department of Homeland Security's Menlo Report add to the Belmont Principles?

> [!answer]- Show Answer
> The Menlo Report added **Respect for Law and Public Interest** as a fourth principle, adapting the Belmont Principles specifically to Information and Communication Technology Research.

---

## Question 4 - Types of Bias [recall]
> Name and briefly describe at least four types of bias that can be introduced in data handling.

> [!answer]- Show Answer
> (1) **Data collection for pre-defined result** -- analyst pressured to collect data to reach a predetermined conclusion. (2) **Biased use of collected data** -- data manipulated or selectively discarded to confirm a pre-determined approach. (3) **Hunch and search** -- analyst uses only data that confirms a hunch, ignoring other possibilities. (4) **Biased sampling methodology** -- bias introduced by the method used to select the sample set. (5) **Context and Culture** -- culturally or contextually based biases that require stepping outside the context for neutrality.

---

## Question 5 - Privacy Law Comparison [recall]
> What privacy framework does Canada use, and how does it differ from the US approach?

> [!answer]- Show Answer
> Canada uses **PIPEDA** (Personal Information Protection and Electronic Documents Act), which applies to every organization collecting personal information commercially. It has 10 principles including Accountability, Consent, and Individual Access. The Federal Privacy Commissioner handles complaints but fills an **ombudsman** role -- decisions are only recommendations, not legally binding. In contrast, the US FTC focuses on Fair Information Processing Principles (Notice, Choice, Access, Integrity, Enforcement) and relies on **enforcement/redress** mechanisms with sanctions for noncompliance.

---

## Question 6 - EDPS Pillars [recall]
> What four pillars did the European Data Protection Supervisor identify for an ethical information ecosystem?

> [!answer]- Show Answer
> (1) **Future-oriented regulation** of data processing and respect for privacy rights; (2) **Accountable controllers** who determine personal information processing; (3) **Privacy-conscious engineering** and design of data processing products and services; (4) **Empowered individuals**. The EDPS stated that privacy is a fundamental human right and challenged innovators to see dignity, privacy, and autonomy as a platform for sustainable digital development.

---

## Question 7 - Misleading Visualization Scenario [application]
> A BI analyst notices that a quarterly report uses a bar chart where the Y-axis starts at 95 instead of 0, making a 2% increase look dramatic. What ethical principles are being violated, and what should the analyst do?

> [!answer]- Show Answer
> This violates the principle of **transparency/truthfulness** in data presentation. Changing scale is a classic misleading visualization technique described in "How to Lie with Statistics" (Huff, 1954). The analyst has an ethical duty to alert appropriate governance or management functions. Per DMBOK2, BI staff are often the first to notice anomalies and should **report them** through escalation paths. The chart should be corrected to use an honest scale or at minimum include a clear axis break indicator with transparent labeling.

---

## Question 8 - Anonymization Risk [application]
> An organization plans to anonymize customer data before sharing it with a third-party analytics partner. Why might anonymization alone be insufficient, and what additional measures does DMBOK2 recommend?

> [!answer]- Show Answer
> Within **large data sets**, it is possible to combine data in ways that enable individuals to be **specifically identified**, even if input data sets have been anonymized. This risk arises from data aggregation, re-identification through combining datasets, and the sheer volume of Big Data. DMBOK2 recommends: (1) Analyze data for sensitive content when it first arrives; (2) Apply accepted protection methods (masking, marking, aggregation); (3) Establish **strong governance** and a commitment to ethical data handling; (4) Apply governance oversight specifically to BI, analytics, and Data Science studies. Anonymization alone is not a sufficient safeguard.

---

## Question 9 - Ethical Risk Model [analysis]
> A company wants to use predictive algorithms to identify "high-risk" customers for loan default. Using the DMBOK2 ethical risk model for sampling projects, what four areas should the project account for?

> [!answer]- Show Answer
> Per the ethical risk model (Figure 13), projects using personal data should account for: (1) **Identification** -- how populations are selected for study (demographic requirements, selection method); (2) **Behavior capture** -- how data will be captured (content, method, activities, sentiment, legal/ethical review); (3) **BI/Analytics/Data Science** -- what activities analytics will focus on (profiling, forecasting); (4) **Results** -- how results are made accessible (privileges granted/denied, biased treatment risks). Additionally, for predictive policing or criminal risk algorithms, there should be **greater precautions** for algorithmic transparency and accountability, and efforts to counter bias in training datasets, due to higher risk of violating ethical principles of justice or fairness.

---

## Question 10 - Data Integration Ethics [analysis]
> Why does DMBOK2 describe data integration as presenting ethical challenges, and what four fundamental problems does it identify?

> [!answer]- Show Answer
> Data integration presents ethical challenges because **data is changed as it moves between systems**, risking unethical or illegal handling. The four fundamental problems are: (1) **Limited knowledge of origin and lineage** -- if the organization cannot prove what the data represents; (2) **Poor quality data** -- without clear standards and measurement, consumers are at risk; (3) **Unreliable Metadata** -- inconsistent definitions, undocumented lineage, missing provenance tags; (4) **No documentation of remediation history** -- even well-intentioned data remediation may be illegal without formal, auditable change control. These problems compound because downstream activities can expose, misinterpret, or misuse data that was inadequately managed during integration.

---

> [!summary]- Pattern Summary (click to view)
> | Keyword | Answer |
> |---------|--------|
> | Belmont Principles | **Respect for Persons, Beneficence, Justice** |
> | Menlo Report addition | **Respect for Law and Public Interest** |
> | GDPR principle count | **7 principles** |
> | "Do not harm" | **Beneficence** |
> | PIPEDA country | **Canada** |
> | EDPS four pillars | **Regulation, Accountable controllers, Privacy engineering, Empowered individuals** |
> | Misleading viz technique | **Scale manipulation, data omission** |
> | Anonymization risk | **Re-identification in large datasets** |
> | Ethical risk model areas | **Identification, Behavior capture, Analytics, Results** |
> | Integration ethics problems | **Lineage, quality, Metadata, remediation history** |
