---
source_pdf: DAMA-DMBOK2 PDF.pdf
part: Chapter 7
keywords: data security, authentication, authorization, encryption, masking, risk classification, CRUD, regulatory compliance, phishing, SQL injection
---

# Data Security Practice

#dmbok2 #data-security

## Related Concepts
- [[Data Security]]
- [[Data Storage and Operations]]
- [[Data Governance]]
- [[Data Handling Ethics]]
- [[Metadata Management]]

> [!hint]- Key Patterns (click to view)
> - **Four A's**: Access, Audit, Authentication, Authorization (+ Entitlement). Know what each means.
> - **Business drivers**: Risk reduction AND business growth -- they are complementary.
> - **Least Privilege**: Only the minimum access needed for a legitimate purpose.
> - **Confidentiality** (internal, need-to-know, single level per data set) vs. **Regulation** (external, allowed-to-know, additive categories).
> - **Persistent masking** (permanent, irreversible) vs. **Dynamic masking** (appearance changes, underlying data intact).
> - **In-flight** (masked during transit, more secure) vs. **In-place** (source = destination, riskier).
> - **Risk classifications**: CRD > HRD > MRD. Highest classification of any datum determines the classification of the entire aggregation.
> - **SQL Injection** mitigation: sanitize all inputs.
> - **Outsourcing**: "Anything can be outsourced except liability."

---

### Q1. What are the "Four A's" of data security, and what additional element has been included for effective regulatory compliance? [recall]

> [!answer]- Show Answer
> The **Four A's** are:
> 1. **Access**: Enable individuals with authorization to connect to systems in a timely manner
> 2. **Audit**: Review security actions and user activity for compliance with regulations and policies
> 3. **Authentication**: Validate that users are who they claim to be (passwords, tokens, biometrics)
> 4. **Authorization**: Grant individuals privileges to access specific views of data appropriate to their role
>
> The additional element is **Entitlement** -- the sum total of all data elements exposed to a user by a single access authorization decision. A responsible manager must decide a person is "entitled" before an authorization request is generated.

---

### Q2. What is the difference between a vulnerability, a threat, and a risk? [recall]

> [!answer]- Show Answer
> - **Vulnerability**: A weakness or defect in a system that allows it to be attacked (e.g., out-of-date patches, weak passwords). Some vulnerabilities are called exploits.
> - **Threat**: A potential offensive action against an organization. Can be internal or external, malicious or unintentional. An occurrence is also called an **attack surface**.
> - **Risk**: The possibility of loss. Calculated by considering probability, damage amount, effect on revenue, cost to fix, cost to prevent, and attacker intent. Risks can be prioritized by severity or likelihood.

---

### Q3. A healthcare organization needs to allow call center staff to verify patient identity using the last four digits of their SSN, without exposing the full number. What type of masking should they use, and why? [application]

> [!answer]- Show Answer
> They should use **dynamic data masking**. Dynamic masking changes the **appearance** of data to the end user without changing the underlying data. For example, SSN 123456789 would display as ***-**-6789 to the call center associate.
>
> This is preferable to persistent masking because:
> - The **underlying production data must remain intact** for other authorized uses
> - Call center staff need **partial access** to sensitive data, not full access
> - Dynamic masking provides real-time protection without creating separate masked copies
>
> Persistent masking would permanently alter the data and is used between production and non-production environments, not for this type of controlled access scenario.

---

### Q4. How does the confidentiality classification of a data set differ from its regulatory categorization? [recall]

> [!answer]- Show Answer
> | Aspect | Confidentiality | Regulation |
> |--------|----------------|------------|
> | **Origin** | Internal (organization decides) | External (laws, regulations, contracts) |
> | **Basis** | "Need-to-know" | "Allowed-to-know" |
> | **Aggregation** | **Single level** per data set (highest item determines level) | **Additive** -- a single data set may have multiple regulatory categories |
>
> Key principle: The highest security classification of any datum within a user entitlement determines the security classification of the entire aggregation. Regulatory categorizations, however, are additive -- all protection policies must be followed regardless of whether they originated internally or externally.

---

### Q5. An organization discovers that a developer has been accessing patient records through MS Excel, bypassing the web application's controls. What type of security risk is this, and how should it be addressed? [application]

> [!answer]- Show Answer
> This is an **abuse of legitimate privilege**. The developer has valid login credentials but is circumventing application restrictions by using an alternative tool (Excel) to access the database directly, retrieving data the web application was designed to restrict.
>
> **Solutions include:**
> - Database access control that not only applies to specific queries but also **enforces policies for end-point machines**
> - **Time of day** and **location monitoring**
> - Limits on the **amount of information downloaded**
> - Reducing the ability of any user to have unlimited access to all records unless specifically required by their job and approved by their supervisor
> - Ensuring database-level restrictions cannot be bypassed by alternative tools

---

### Q6. What is the principle of "Least Privilege" and why is it difficult to implement in practice? [recall]

> [!answer]- Show Answer
> **Least Privilege** means a user, process, or program should be allowed to access **only the information allowed by its legitimate purpose**. Without permission, a user should not see data or take action.
>
> It is difficult to implement because:
> - DBAs may not have **time or Metadata** to define granular access control for each user entitlement
> - Many users receive **generic default access** that far exceeds their job requirements
> - As **user roles change** over time, query policies must be updated
> - Manual definition of query-level access control is **time-consuming** for hundreds of users
> - **Automated tools** are usually necessary to make real query-level access control functional in large organizations

---

### Q7. Explain the difference between in-flight persistent masking and in-place persistent masking. Which is more secure? [recall]

> [!answer]- Show Answer
> - **In-flight persistent masking**: Data is masked **while moving** between source (typically production) and destination (typically non-production). Very secure because it does not leave an intermediate file with unmasked data. Also **re-runnable** if issues are encountered.
> - **In-place persistent masking**: Source and destination are the **same**. Unmasked data is read, masked, then overwrites the original. Riskier because if the masking process **fails mid-masking**, it can be difficult to restore data to a useable format.
>
> **In-flight masking is more secure** and will more securely meet project needs in general. In-place masking has a few niche uses but carries greater risk.

---

### Q8. A company is outsourcing its IT operations to a third-party vendor. What key data security mechanisms should be in place, and what fundamental principle applies? [application]

> [!answer]- Show Answer
> The fundamental principle is: **"Anything can be outsourced except liability."** The organization retains accountability even when transferring control.
>
> Key mechanisms include:
> - **Service Level Agreements (SLAs)** with data protection actions
> - **Limited liability provisions** in the outsourcing contract
> - **Right-to-audit clauses**
> - Clearly defined **consequences for breaching** contractual obligations
> - Frequent **data security reports** from the vendor
> - **Independent monitoring** of vendor system activity
> - Frequent and thorough **data security auditing**
> - **CRUD matrices** (Create, Read, Update, Delete) mapping data responsibilities across processes, applications, roles, and organizations
> - **RACI matrices** (Responsible, Accountable, Consulted, Informed) clarifying roles and separation of duties
> - Awareness of **legal differences** in contract law if the vendor is in another country

---

### Q9. What is SQL injection, and how should it be mitigated? [recall]

> [!answer]- Show Answer
> **SQL injection** is an attack where a perpetrator inserts unauthorized database statements into vulnerable SQL data channels (stored procedures, web application input spaces). These injected statements are passed to the database and executed as legitimate commands, potentially granting unrestricted access.
>
> SQL injection can also attack the DBMS itself by passing SQL commands as parameters of functions or stored procedures, allowing privilege escalation.
>
> **Mitigation**: **Sanitize all inputs** before passing them back to the server. This prevents unauthorized SQL from being interpreted and executed by the database.

---

### Q10. A data breach has occurred at a financial institution. The investigation reveals that an employee's laptop with an unencrypted customer database was stolen. Analyze the layers of security failure and recommend a comprehensive remediation plan. [analysis]

> [!answer]- Show Answer
> **Security failures at multiple layers:**
> 1. **Device Security failure**: No encryption on the laptop; no data-wiping capability
> 2. **Excessive Privilege**: Employee had access to entire customer database on a portable device
> 3. **Data proliferation**: Confidential production data was copied to a non-production endpoint
> 4. **Policy failure**: No policy restricting storage of sensitive data on portable devices
> 5. **Monitoring failure**: No detection of bulk data download
>
> **Comprehensive remediation plan:**
> - **Device security**: Mandate encryption on all portable devices; install anti-malware; implement remote wipe capability
> - **Access controls**: Implement query-level access restricting bulk downloads; enforce Least Privilege principle
> - **Monitoring**: Deploy automated monitoring for unusual download patterns (time, volume, location)
> - **Policy**: Create/enforce policies prohibiting storage of confidential data on personal devices; implement BYOD policies
> - **Classification**: Ensure all customer data is classified with appropriate confidentiality and regulatory categories (PII, PCI-DSS) in Metadata
> - **Training**: Mandatory security awareness training for all employees with testing
> - **Audit**: Implement regular audits of user entitlements; track confidential data proliferation as a metric
> - **Backup encryption**: Ensure all backup copies are encrypted with keys stored separately

---

> [!summary]- Pattern Summary (click to view)
> **Core Framework**: Data security is built on the Four A's (Access, Audit, Authentication, Authorization) plus Entitlement. The goal is to enable appropriate access while preventing inappropriate access.
>
> **Key Distinctions**:
> - Confidentiality (internal, single level) vs. Regulation (external, additive)
> - Persistent masking (permanent) vs. Dynamic masking (appearance only)
> - In-flight (transit, secure) vs. In-place (same location, riskier)
> - Active monitoring (real-time alerts) vs. Passive monitoring (trend snapshots)
> - CRD > HRD > MRD risk classifications
>
> **Critical Principles**: Least Privilege, Metadata-driven security, enterprise-wide consistency, collaboration between IT security and data management, "anything can be outsourced except liability."
>
> **Security Risks**: Excessive privilege, legitimate privilege abuse, privilege elevation, shared/service accounts, SQL injection, default passwords, backup abuse, social engineering, phishing, malware.
>
> **Regulatory families**: PII, Financially Sensitive (SOX/GLBA), PHI (HIPAA), Educational (FERPA), PCI-DSS.
