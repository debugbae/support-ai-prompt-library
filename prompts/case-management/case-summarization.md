# Case Summarization Prompt

**Use case:** Generate a structured, actionable summary from a raw support ticket  
**Best model:** GPT-4o, Claude Sonnet, Llama 3 70B  
**Input required:** Raw ticket text (email, Salesforce case, Jira issue, etc.)  
**Output:** Structured summary with severity, impact, next action, and entity extraction  

---

## System Prompt

```
You are an expert support engineer assistant embedded in a SaaS support team.
Your job is to read raw customer support tickets and produce structured,
actionable summaries that help engineers respond faster and more effectively.

Always be objective, concise, and prioritize information that drives resolution.
Never invent details not present in the ticket. If information is missing, say so.
```

---

## User Prompt Template

```
Summarize the following support ticket into a structured format.

Return your response in this exact structure:

**ONE-LINE SUMMARY**
[Single sentence: who, what, severity signal]

**PROBLEM STATEMENT**
[2-3 sentences: what the customer is experiencing, since when, what they've already tried]

**SEVERITY ASSESSMENT**
[P1/P2/P3/P4] — [one sentence justification]
- P1: System down, data loss, security breach
- P2: Major feature broken, no workaround
- P3: Degraded functionality, workaround available  
- P4: Minor/cosmetic issue

**CUSTOMER IMPACT**
[What business outcome is being affected]

**SUGGESTED NEXT ACTION**
[The single most important thing the engineer should do first]

**INFORMATION GAPS**
[Bullet list of missing information that would help resolve the case faster]

**KEY DETAILS**
- Customer: 
- Product/Feature:
- Version/Environment:
- Error codes:

---
Ticket:
{{PASTE_TICKET_TEXT_HERE}}
```

---

## Example Output

**ONE-LINE SUMMARY**  
Acme Corp (Enterprise) reports a P1 SSO outage affecting 200 production users since 7:45 AM PST following a SAML configuration change.

**PROBLEM STATEMENT**  
All 200 users at Acme Corp are unable to log into the production platform following last night's SSO update. Users receive error SAML_4021 (invalid audience URI). The customer reverted their IdP configuration but the issue persists, suggesting the problem may be on the platform side.

**SEVERITY ASSESSMENT**  
**P1** — Active production outage, entire customer support team non-operational, direct revenue impact stated by customer.

**CUSTOMER IMPACT**  
Acme Corp's support team cannot process customer tickets, creating downstream SLA risk and potential contract exposure.

**SUGGESTED NEXT ACTION**  
Escalate immediately to Tier 2 engineering. Check whether any platform-side SAML audience URI configuration changed in the last 24 hours. Pull SAML logs if accessible.

**INFORMATION GAPS**  
- Were any platform-side changes deployed overnight?  
- Can the customer provide IdP assertion logs?  
- Is this affecting all Azure AD users or a subset?  
- What is the customer's contractual SLA tier?  

**KEY DETAILS**  
- Customer: Acme Corp (John Smith, IT Director)  
- Product/Feature: SSO / SAML Authentication  
- Version/Environment: v9.4.2, Production, Azure AD  
- Error codes: SAML_4021  

---

## Usage Notes

**When to use this prompt:**
- First-touch triage before assigning a case
- Handoffs between engineers or shifts
- Escalation documentation
- End-of-day case reviews

**Tips:**
- For very long tickets (>1000 words), summarize the most recent exchange first, then the original issue
- If the customer has sent multiple emails, combine them before pasting
- The P1/P2/P3/P4 assessment should inform your SLA clock — review your team's SLA policy before acting on it

**Limitations:**
- The model may miss subtle urgency signals in tone — always read the original ticket before acting on a P4 assessment
- Sensitive PII (SSNs, payment info) should be redacted before pasting into shared AI tools
