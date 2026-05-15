# AI Use Case Intake Template

**Version:** 1.0  
**Owner:** AI Program Manager  
**Review cycle:** Quarterly  

Use this form to submit new AI use cases for evaluation and approval. All use cases must complete intake before development or deployment begins.

---

## Section 1: Use Case Overview

| Field | Response |
|-------|----------|
| **Use Case Name** | |
| **Submitted By** | |
| **Team / Department** | |
| **Date Submitted** | |
| **Target Launch Date** | |
| **Sponsoring Leader** | |

**Problem Statement**  
*What problem does this AI use case solve? What is the current state and pain point?*

> [Answer here]

**Proposed Solution**  
*Describe the AI-powered workflow or tool you want to build or deploy.*

> [Answer here]

**Success Metrics**  
*How will you measure whether this use case is working? Include quantitative targets where possible.*

| Metric | Baseline (Today) | Target |
|--------|-----------------|--------|
| | | |
| | | |

---

## Section 2: Technical Details

**AI Tool / Platform**  
☐ ChatGPT Enterprise  ☐ Microsoft Copilot  ☐ Custom GPT  ☐ Internal LLM API  ☐ Other: ___________

**Integration points** *(check all that apply)*  
☐ Salesforce / Service Cloud  ☐ Jira / Confluence  ☐ SharePoint  ☐ Outlook / Teams  ☐ GitHub  ☐ Other: ___________

**Automation level**  
☐ Human-in-the-loop (AI drafts, human approves before action)  
☐ Human-on-the-loop (AI acts, human can override)  
☐ Fully automated (AI acts without human review)  

*Note: Fully automated use cases require additional security review.*

---

## Section 3: Data & Privacy

**What data will the AI process?**  
☐ Customer PII (names, emails, phone numbers)  
☐ Customer account / contract data  
☐ Internal employee data  
☐ Product usage / telemetry data  
☐ Support ticket content  
☐ No sensitive data  

**Will customer data be sent to a third-party AI provider?**  
☐ Yes — specify provider and confirm DPA is in place: ___________  
☐ No — all processing is done locally or within our enterprise tenant  

**Data retention:**  
*How long is data stored by this AI system? Is it used for model training?*

> [Answer here]

---

## Section 4: Risk Assessment

Rate each risk area (Low / Medium / High):

| Risk Area | Rating | Notes |
|-----------|--------|-------|
| **Data privacy** — risk of exposing PII or sensitive data | | |
| **Accuracy** — risk of incorrect AI output causing customer harm | | |
| **Bias** — risk of unfair or discriminatory outcomes | | |
| **Dependency** — risk if the AI tool is unavailable | | |
| **Misuse** — risk of employees misusing the tool | | |
| **Compliance** — risk of violating regulatory requirements | | |

**Overall risk rating:** ☐ Low  ☐ Medium  ☐ High  

**Mitigation plan for any Medium or High risks:**

> [Answer here]

---

## Section 5: Governance & Controls

**Who has access to this AI tool?**

> [Answer here — be specific about roles/groups]

**RBAC / access controls in place:**  
☐ Role-based access configured  ☐ SSO / enterprise auth required  ☐ Audit logging enabled  ☐ Output review process defined  

**Escalation path if AI produces harmful or incorrect output:**

> [Answer here]

**Responsible AI checklist:**  
☐ Users will be informed they are interacting with or receiving AI-generated content  
☐ A human review step exists before AI output is sent to customers (or N/A documented)  
☐ Feedback mechanism exists to flag poor AI outputs  
☐ Use case aligns with our published responsible AI standards  

---

## Section 6: Approvals

| Approver | Role | Decision | Date |
|----------|------|----------|------|
| | AI Program Manager | ☐ Approved ☐ Revisions needed ☐ Rejected | |
| | IT Security | ☐ Approved ☐ Revisions needed ☐ Rejected | |
| | Legal / Compliance | ☐ Approved ☐ Revisions needed ☐ Rejected | |
| | Business Owner | ☐ Approved ☐ Revisions needed ☐ Rejected | |

**Approval Notes:**

> [Any conditions, required changes, or follow-up items]

---

*Template maintained by the AI Program Office. Questions? Contact the AI Program Manager.*
