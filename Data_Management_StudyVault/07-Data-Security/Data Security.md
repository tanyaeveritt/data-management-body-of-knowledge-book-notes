---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 7
keywords: data security, authentication, authorization, access control, encryption, masking, CRUD, risk classification, regulatory compliance, CISO
---

# Data Security (Importance: ★★★)
*Reading time: ~8 min*

#dmbok2 #data-security

## Overview Table (At a Glance)
| Item | Key Point |
|------|-----------|
| Definition | Planning, development, and execution of security policies and procedures to provide proper authentication, authorization, access, and auditing of data and information assets |
| Goals | 1) Enable appropriate and prevent inappropriate access 2) Comply with regulations for privacy, protection, confidentiality 3) Ensure stakeholder privacy needs are enforced and audited |
| Primary Business Drivers | **Risk reduction** and **business growth** |
| Key Framework | The **Four A's**: Access, Audit, Authentication, Authorization (plus Entitlement) |
| Key Principle | **Least Privilege**: A user should access only the information allowed by its legitimate purpose |
| Key Role | **CISO** (Chief Information Security Officer) in larger enterprises; data managers always involved |
| Inputs | Business goals/strategy, business rules/processes, regulatory requirements, enterprise architecture, enterprise data model |
| Deliverables | Security architecture, policies, standards, access controls, regulatory-compliant views, security classifications, audit reports |

## Business Drivers
- **Risk reduction**: Ensuring data is secure reduces risk and adds competitive advantage. Data security risks relate to regulatory compliance, fiduciary responsibility, reputation, and legal/moral responsibility.
- **Business growth**: Trusted e-commerce drives profit. Robust information security enables transactions and builds customer confidence.
- **Security as an asset**: Security classifications captured in Metadata become a strategic asset. Standard security Metadata optimizes data protection and guides business usage.

---

## Essential Concepts: Vulnerability, Threat, and Risk
- **Vulnerability**: A weakness or defect in a system that allows it to be attacked (e.g., out-of-date patches, weak passwords). Non-production environments are often more vulnerable than production.
- **Threat**: A potential offensive action; can be internal or external, malicious or unintentional. An occurrence is also called an **attack surface**.
- **Risk**: The possibility of loss. Calculated using probability, damage amount, effect on revenue, cost to fix, cost to prevent, and attacker intent.

### Risk Classifications
- **Critical Risk Data (CRD)**: Personal information aggressively sought; compromise harms individuals and results in financial harm, penalties, brand damage
- **High Risk Data (HRD)**: Actively sought due to potential direct financial value; provides competitive edge
- **Moderate Risk Data (MRD)**: Little tangible value to unauthorized parties but unauthorized use would negatively affect the company

---

## The Four A's (Plus Entitlement)
| Process | Description |
|---------|-------------|
| **Access** | Enable individuals with authorization to connect to systems in a timely manner |
| **Audit** | Review security actions and user activity for compliance with regulations and policies |
| **Authentication** | Validate that users are who they claim to be (passwords, tokens, fingerprints) |
| **Authorization** | Grant privileges to access specific views of data appropriate to the user's role |
| **Entitlement** | The sum total of all data elements exposed to a user by a single access authorization decision |

- **Monitoring**: Active (real-time alerts for suspicious activity) vs. Passive (snapshots over time for trend comparison)

---

## Data Integrity in Security Context
Data integrity = the state of being whole, protected from improper alteration, deletion, or addition. Sarbanes-Oxley regulations focus on protecting financial information integrity.

---

## Encryption Methods
| Method | Description |
|--------|-------------|
| **Hash** | Algorithms convert data to mathematical representation; used for verification (MD5, SHA) |
| **Private-key** | One key encrypts; both sender and recipient need it (DES, 3DES, AES, IDEA) |
| **Public-key** | Sender uses public key; receiver uses private key (RSA, Diffie-Hellman, PGP) |

---

## Obfuscation and Masking
Two types: **Persistent** (permanent, irreversible) and **Dynamic** (changes appearance without changing underlying data).

- **In-flight persistent masking**: Masked while moving between source and destination; very secure, re-runnable
- **In-place persistent masking**: Source and destination are the same; unmasked data overwritten; riskier if process fails

### Masking Methods
Substitution, Shuffling, Temporal variance, Value variance, Nulling/deleting, Randomization, Encryption, Expression masking, Key masking

---

## Network Security Concepts
- **Backdoor**: Hidden entry into a system bypassing password requirements; default passwords left unchanged are a common backdoor
- **Bot/Zombie**: Workstation taken over by a hacker; used for spam, attacks, fraud
- **Cookie**: Small data file for identifying returning visitors; raises privacy questions
- **Firewall**: Filters network traffic; may scan incoming/outgoing for restricted data (Data Loss Prevention)
- **Perimeter**: Boundary between organization's environments and exterior systems
- **DMZ**: De-militarized zone on edge of organization with firewalls on both sides
- **Super User Account**: Emergency-only administrator access; credentials highly secured and expire quickly
- **Key Logger**: Records all keystrokes and sends them to attacker
- **Penetration Testing**: Ethical hacker attempts to break in to identify vulnerabilities
- **VPN**: Uses encrypted tunnel through the internet for secure communication

---

## Types of Data Security
- **Facility Security**: First line of defense; locked data centers, access restricted to authorized employees
- **Device Security**: Mobile devices are inherently insecure; plan for BYOD, anti-malware, encryption, data wiping
- **Credential Security**: User ID + Password; **Single Sign-On** is optimal; two-factor identification for highly sensitive data
- **Electronic Communication Security**: Train users not to send sensitive data over email or social media

---

## Security Restrictions: Confidentiality vs. Regulation
| Aspect | Confidentiality | Regulation |
|--------|----------------|------------|
| Origin | **Internal** (organization decides) | **External** (laws, regulations, contracts) |
| Basis | "Need-to-know" | "Allowed-to-know" |
| Aggregation | Single level per data set (highest item determines level) | **Additive** -- multiple categories per data set |

### Confidentiality Levels
General Audiences > Internal Use Only > Confidential > Restricted Confidential > Registered Confidential

### Key Regulatory Families
- **PII** (Personally Identifiable Information): Name, address, government ID, account numbers, etc.
- **Financially Sensitive Data**: Insider data, SOX, GLBA
- **PHI** (Personal Health Information): HIPAA
- **Educational Records**: FERPA
- **PCI-DSS**: Credit card data (contractual, not governmental)

---

## System Security Risks
- **Abuse of Excessive Privilege**: Users given more access than needed; solution is query-level access control
- **Abuse of Legitimate Privilege**: Users circumvent application restrictions (e.g., using Excel to access database directly)
- **Unauthorized Privilege Elevation**: Exploiting software vulnerabilities to gain admin access; prevent with IPS + query-level access
- **Service/Shared Account Abuse**: Untraceable to a particular user; should be carefully controlled
- **SQL Injection**: Inserting unauthorized SQL into vulnerable channels; mitigate by sanitizing all inputs
- **Default Passwords**: Must be eliminated after every installation
- **Backup Data Abuse**: Encrypt all backups; securely manage decryption keys

---

## Social Engineering and Malware
- **Social Engineering**: Tricking people into providing information or access
- **Phishing**: Luring recipients into giving out private information; **Spear-phishing** targets specific executives
- **Malware types**: Adware, Spyware, Trojan Horse, Virus (needs host program), Worm (self-replicating across networks)

---

## Security Activities
1. **Identify requirements** (business + regulatory)
2. **Define security policy** (enterprise, IT, and data security policies; Data Governance Council reviews)
3. **Define standards** (confidentiality levels, regulatory categories, security roles)
4. **Assess current risks** (sensitivity, requirements, current protections)
5. **Implement controls and procedures** (access management, role assignment, monitoring, compliance)

### Role-Based Access Control
- **Role Assignment Grid**: Maps roles to data based on confidentiality and regulations
- **Role Assignment Hierarchy**: Organized so child roles further restrict parent role privileges
- Best practice: Assign each user to **only one role group** to avoid confusion

---

## Security in Special Contexts
- **Outsourced world**: "Anything can be outsourced except liability." Use SLAs, right-to-audit clauses, CRUD and RACI matrices.
- **Cloud environments**: Shared responsibility model; define chain of custody, ownership, custodianship. Same security policy applies to internal cloud architecture.
- **Document sanitization**: Clean tracked change history and Metadata from documents before sharing.

---

## Metrics
| Category | Examples |
|----------|----------|
| Security Implementation | % computers with recent patches, % employees passing security quiz, % audit findings resolved |
| Security Awareness | Risk assessment findings, formal feedback surveys, incident post-mortems |
| Data Protection | Criticality ranking, annualized loss expectancy, threat assessments, vulnerability assessments |
| Security Incidents | Intrusion attempts detected/prevented, ROI from prevented intrusions |
| Confidential Data Proliferation | Number of copies of confidential data (fewer = better) |

---

## Exam/Test Patterns (Frequently Tested)
| Scenario/Keyword | Answer |
|-------------------|--------|
| The Four A's of data security | Access, Audit, Authentication, Authorization (+ Entitlement) |
| Primary business drivers | **Risk reduction** and **business growth** |
| Least Privilege principle | User should access only information allowed by legitimate purpose |
| Confidentiality vs. Regulation origin | Confidentiality = internal; Regulation = external |
| Persistent vs. Dynamic masking | Persistent = permanent/irreversible; Dynamic = changes appearance without changing underlying data |
| In-flight vs. In-place masking | In-flight = masked during transit (more secure); In-place = source and destination same (riskier) |
| Risk classification levels | Critical Risk Data > High Risk Data > Moderate Risk Data |
| SQL Injection mitigation | Sanitize all inputs before passing to server |
| CRUD matrix purpose | Map data access needs and guide security role groups, parameters, permissions |
| Outsourcing and liability | "Anything can be outsourced except liability" |
| Role-based access best practice | Assign each user to only one role group |
| Penetration testing purpose | Ethical hacker identifies system vulnerabilities before release |
| DMZ definition | De-militarized zone on edge of organization with firewalls on both sides |
| NIST first step | Categorize all enterprise information |

## Related Notes
- [[Data Storage and Operations]]
- [[Data Governance]]
- [[Data Handling Ethics]]
- [[Metadata Management]]
- [[Data Integration and Interoperability]]
- [[Data Architecture]]
