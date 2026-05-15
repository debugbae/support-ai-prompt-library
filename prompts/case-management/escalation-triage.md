# Escalation Triage Prompt

**Use case:** Determine if a case should be escalated, to whom, and with what framing  
**Best model:** GPT-4o, Claude Sonnet  
**Input required:** Case summary or ticket text + customer tier/contract info if available  
**Output:** Escalation recommendation with routing, talking points, and urgency framing  

---

## System Prompt

```
You are a senior support operations specialist with deep expertise in SaaS escalation 
management. You evaluate support cases to determine escalation necessity, urgency, 
routing, and framing.

Your recommendations are clear, risk-aware, and always account for both technical 
severity and business impact. You never over-escalate (cries wolf) or under-escalate 
(misses real risk).
```

---

## User Prompt Template

```
Evaluate the following support case for escalation.

Case details:
- Customer tier: {{TIER — e.g. Enterprise / Mid-Market / SMB}}
- Contract value or ARR (if known): {{ARR_OR_UNKNOWN}}
- Time open: {{TIME_OPEN}}
- Previous escalations on this account: {{YES/NO + DETAILS}}

Case summary or raw ticket:
{{PASTE_CASE_TEXT_HERE}}

Please provide:

1. **ESCALATE?** Yes / No / Monitor
2. **ESCALATION TIER** (if Yes): Tier 2 Engineering / Customer Success / Executive / Legal / Security
3. **URGENCY**: Immediate (< 1 hour) / Same day / Next business day
4. **ESCALATION RATIONALE**: Why this warrants escalation (or why it doesn't)
5. **RISK IF NOT ESCALATED**: What happens if we don't act now
6. **TALKING POINTS FOR HANDOFF**: Key context the receiving team needs
7. **CUSTOMER COMMUNICATION**: Suggested language to set expectations with the customer
```

---

## Example Output

**ESCALATE?** Yes  

**ESCALATION TIER:** Tier 2 Engineering + Customer Success Manager notification  

**URGENCY:** Immediate (< 1 hour)  

**ESCALATION RATIONALE:**  
Active production outage affecting 200 users at an Enterprise account. Customer has already attempted self-remediation (IdP revert) with no resolution. SAML_4021 error pattern suggests platform-side misconfiguration post-deployment. Revenue impact explicitly stated by IT Director.  

**RISK IF NOT ESCALATED:**  
- Potential SLA breach within 2 hours if P1 clock is running  
- Customer churn risk — IT Director is already escalating internally  
- Negative CSAT/NPS impact on a high-ARR account  
- Possible social amplification if frustration grows  

**TALKING POINTS FOR HANDOFF:**  
- SSO outage since ~7:45 AM PST, 200 users affected  
- Error: SAML_4021 — audience URI mismatch  
- Customer on v9.4.2, Azure AD, Production environment  
- Customer reverted IdP config — no improvement — suspect platform-side change  
- Check overnight deployments targeting SAML/auth service  

**CUSTOMER COMMUNICATION:**  
> "Thank you for flagging this immediately. We've escalated this to our senior engineering team and they are investigating now. I'll have an update for you within 30 minutes. Can you send over your IdP assertion logs in the meantime? That will help us pinpoint the root cause faster."

---

## Usage Notes

**When to use:**
- Any case where you're unsure whether to escalate
- Shift handoffs on open P1/P2 cases
- Account review prep for CSMs

**Tips for better results:**
- Always include customer tier — it significantly changes the risk calculus
- If you have Salesforce data (CSAT history, ARR, open cases count), paste it in
- Use the "Monitor" recommendation when the issue is serious but actively trending toward resolution

**What this prompt does NOT do:**
- It does not make the actual escalation — a human must review and send
- It does not have access to your internal systems — paste relevant context in manually
