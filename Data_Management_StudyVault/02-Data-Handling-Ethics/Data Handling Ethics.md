---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 2
keywords: data ethics, privacy, GDPR, PIPEDA, bias, data handling, Belmont principles
---

# Data Handling Ethics (Importance: ★★)
*Reading time: ~4 min*

#dmbok2 #data-ethics

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Principles for how to procure, store, manage, interpret, analyze, and dispose of data ethically |
| Core Concern | Impact on people, potential for misuse, economic value of data |
| Belmont Principles | Respect for Persons, Beneficence, Justice |
| GDPR Principles | Fairness/Lawfulness/Transparency, Purpose Limitation, Data Minimization, Accuracy, Storage Limitation, Integrity/Confidentiality, Accountability |
| EDPS Four Pillars | Future-oriented regulation, Accountable controllers, Privacy-conscious engineering, Empowered individuals |
| Business Driver | Ethical handling is a **competitive advantage** and builds trust |

## Ethical Principles for Data
The **Belmont Principles** (adapted from bioethics) provide a foundation:
- **Respect for Persons**: Treat people with dignity and autonomy; extra care for those with diminished autonomy
- **Beneficence**: (1) Do not harm; (2) maximize benefits, minimize harms
- **Justice**: Fair and equitable treatment; no disproportionate impact on vulnerable groups
- Fourth principle added by the **Menlo Report** (US-DHS): **Respect for Law and Public Interest**

The EDPS (2015) added four pillars for digital ethics:
- Future-oriented **regulation** of data processing
- **Accountable** controllers of personal information
- **Privacy-conscious** engineering and design
- **Empowered** individuals

## Principles Behind Data Privacy Law
**GDPR** (EU, 2016) -- seven core principles:
- **Fairness, Lawfulness, Transparency** -- processed lawfully, fairly, transparently
- **Purpose Limitation** -- collected for specified, explicit, legitimate purposes
- **Data Minimization** -- adequate, relevant, limited to what is necessary
- **Accuracy** -- kept up-to-date; inaccurate data erased/rectified without delay
- **Storage Limitation** -- kept no longer than necessary
- **Integrity and Confidentiality** -- appropriate security against unauthorized processing
- **Accountability** -- controllers must demonstrate compliance

**PIPEDA** (Canada) principles: Accountability, Identifying Purposes, Consent, Limiting Collection/Use/Disclosure/Retention, Accuracy, Safeguards, Openness, Individual Access, Compliance Challenges.

**US FTC** (2012) Fair Information Practices: Notice/Awareness, Choice/Consent, Access/Participation, Integrity/Security, Enforcement/Redress.

## Risks of Unethical Data Handling
- **Timing**: Lying through omission/inclusion of data points (e.g., market timing in equity trades)
- **Misleading Visualizations**: Changing scale, leaving out data points, ignoring visual conventions
- **Unclear Definitions/Invalid Comparisons**: Using incomparable populations or misleading aggregations
- **Bias**: Data collection for pre-defined result, biased use, hunch-and-search, biased sampling, cultural/contextual bias
- **Transforming/Integrating Data**: Limited lineage knowledge, poor quality data, unreliable Metadata, undocumented remediation
- **Obfuscation/Redaction**: Aggregation can still expose PII; large datasets can re-identify anonymized individuals

## Types of Bias in Data
| Bias Type | Description |
|-----------|-------------|
| Pre-defined result | Analyst pressured to reach a predetermined conclusion |
| Biased use of collected data | Data manipulated to confirm a pre-determined approach |
| Hunch and search | Analyst uses only data confirming a hunch |
| Biased sampling | Method of selecting sample introduces systematic error |
| Context and Culture | Culturally-based biases require stepping outside the context |

## Establishing an Ethical Data Culture
Steps to build ethical data handling:
1. **Review current state** data handling practices -- understand degree of connection to ethical/compliance drivers
2. **Identify principles, practices, and risk factors** -- align with legal requirements, industry concerns
3. **Create ethical data handling strategy and roadmap** -- includes values statements, code of ethics, compliance framework, risk assessments, training plan
4. **Adopt a socially responsible ethical risk model** -- consider population selection, data capture methods, analytics focus, results accessibility
5. **Data ethics and governance** -- DG sets standards and policies; legal counsel tracks regulatory changes

Strategy components: Values statements, Ethical data handling principles, Compliance framework, Risk assessments, Training and communications, Roadmap, Auditing and monitoring approach.

## Online Data Ethics
Emerging ethical concerns include:
- **Ownership of data** -- rights to control personal data vs. social media and data brokers
- **Right to be Forgotten** -- erasure of information from the web
- **Identity** -- right to one correct identity and private identity
- **Freedom of speech** -- balancing expression vs. bullying, terror inciting, trolling

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| Three Belmont Principles | **Respect for Persons, Beneficence, Justice** |
| Menlo Report fourth principle | **Respect for Law and Public Interest** |
| GDPR seven principles | **Fairness/Lawfulness/Transparency, Purpose Limitation, Data Minimization, Accuracy, Storage Limitation, Integrity/Confidentiality, Accountability** |
| "Do not harm" principle | **Beneficence** |
| EDPS four pillars | **Regulation, Accountable controllers, Privacy engineering, Empowered individuals** |
| Misleading visualization | Changing **scale**, omitting data, ignoring visual conventions |
| Data mining snooping | Exhaustive correlations producing **statistically significant-looking random results** |
| PIPEDA origin | **Canada** -- Personal Information Protection and Electronic Documents Act |
| Ethical culture first step | **Review current state** data handling practices |

## Related Notes
- [[Data Management]]
- [[Data Governance]]
- [[Data Security]]
- [[Data Quality]]
- [[Metadata Management]]
