# KB Article Generation Prompt

**Use case:** Turn a resolved support case into a reusable knowledge base article  
**Best model:** GPT-4o, Claude Sonnet, Gemini Pro  
**Input required:** Resolved case thread or case summary + resolution details  
**Output:** Structured KB article ready for review and publishing  

---

## System Prompt

```
You are a technical writer embedded in a SaaS support team. Your job is to convert 
resolved support cases into clear, scannable knowledge base articles that help 
customers self-serve and reduce case volume.

Write for a technical but non-expert audience (e.g., IT admins, ops teams). 
Use plain language, numbered steps, and clear headings. Every article should 
answer: What is the problem? Who does it affect? How do I fix it?
```

---

## User Prompt Template

```
Convert the following resolved support case into a knowledge base article.

Resolved case details:
{{PASTE_CASE_THREAD_OR_SUMMARY_HERE}}

Resolution:
{{DESCRIBE_WHAT_FIXED_IT}}

Write the article in this format:

# [Clear, searchable title — describe the symptom, not the cause]

**Applies to:** [Product / Feature / Version range]  
**Last updated:** [Today's date]  
**Estimated time to resolve:** [X minutes]

## Symptoms
[Bullet list of what the customer sees/experiences]

## Cause
[Plain-language explanation of why this happens]

## Resolution
[Numbered step-by-step fix]

## Verification
[How to confirm the issue is resolved]

## Prevention
[Optional: how to avoid this in the future]

## Related Articles
[Leave as placeholder: [Link 1], [Link 2]]
```

---

## Example Output

# Users Receive "SAML_4021: Invalid Audience URI" Error After SSO Configuration Change

**Applies to:** Platform v9.x and above, Azure AD SAML integrations  
**Last updated:** 2024-03-15  
**Estimated time to resolve:** 15–30 minutes  

## Symptoms
- Users unable to log in via SSO after an IdP or platform configuration change  
- Error message displayed: `SAML assertion failed: invalid audience URI (Error code: SAML_4021)`  
- Issue persists even after reverting the IdP configuration  
- Affects all users in the affected SSO group simultaneously  

## Cause
The SAML_4021 error occurs when the Audience URI in the SAML assertion from the Identity Provider (IdP) does not match the Service Provider (SP) Entity ID configured on the platform side. This mismatch commonly occurs when:
- A platform update changes the expected SP Entity ID
- The IdP configuration references an outdated or incorrect entity ID
- The SP metadata was re-generated and not re-imported into the IdP

## Resolution

1. **Log in to the platform** using an account with Administrator access (use break-glass credentials if SSO is your only login method).

2. **Navigate to** Settings → Security → SSO Configuration.

3. **Copy the current SP Entity ID** displayed on the page.

4. **Log in to your IdP** (e.g., Azure AD, Okta, PingFederate).

5. **Open your SAML Enterprise Application** configuration.

6. **Update the Audience URI / SP Entity ID** field to match exactly what you copied in Step 3.

7. **Save the configuration** in your IdP.

8. **Test SSO login** with a non-admin test account.

## Verification
A successful login via SSO without encountering the SAML_4021 error confirms the issue is resolved. If the error persists, collect the SAML assertion trace from your IdP and contact Support.

## Prevention
- After any platform version upgrade, re-download the SP metadata from Settings → Security → SSO Configuration and re-import it into your IdP.
- Enable SSO configuration change notifications so your team is alerted to platform-side changes that may affect your integration.

## Related Articles
- [How to configure SAML SSO with Azure AD](#)
- [Downloading SP Metadata for IdP Configuration](#)
- [Break-glass admin account setup](#)

---

## Usage Notes

**When to use:**
- Any resolved P1/P2 case where the solution isn't already documented
- Cases that required more than 2 engineer hours to solve
- Issues that appear more than once in your case history

**Before publishing:**
- Have a second engineer review the steps for accuracy
- Verify the product/version applicability range
- Run the article through your style guide checker if you have one
- Remove any customer-specific information (company names, emails, account IDs)

**SEO tip:** Title the article after the symptom or error message, not the internal root cause. Customers search for what they see, not what caused it.
