# Support & Services AI Prompt Library 📚

A curated library of production-ready prompt templates for AI-augmented **Customer Support, Professional Services, TAM, and Customer Operations** workflows.

Each prompt is designed for use with ChatGPT Enterprise, Microsoft Copilot, custom GPTs, or any LLM API. Templates follow a consistent structure with clearly marked variables, usage notes, and example outputs.

---

## 📁 Library Structure

```
prompts/
├── case-management/
│   ├── case-summarization.md
│   ├── troubleshooting-guide.md
│   └── escalation-triage.md
├── knowledge-base/
│   ├── kb-article-generation.md
│   └── faq-extraction.md
├── customer-communications/
│   ├── status-update-email.md
│   └── executive-summary.md
└── reporting/
    ├── weekly-metrics-digest.md
    └── qbr-prep.md

governance/
├── use-case-intake-template.md
├── risk-assessment-checklist.md
└── publishing-standards.md
```

---

## 🚀 Quick Start

1. Browse the `prompts/` folder and find the use case you need
2. Copy the prompt template
3. Replace all `{{VARIABLE}}` placeholders with your actual data
4. Paste into your AI tool of choice (ChatGPT, Copilot, Claude, etc.)
5. Review and edit the output before using it

---

## 📐 Prompt Template Format

Every prompt in this library follows this structure:

```
## [Prompt Name]
**Use case:** What this prompt is for
**Best model:** Which model works best
**Input required:** What you need to provide
**Output:** What you'll get back

### System Prompt
[Instructions that set the AI's role and behavior]

### User Prompt Template
[The template with {{VARIABLES}} to fill in]

### Example Output
[A realistic example of what good output looks like]

### Usage Notes
[Tips, gotchas, and when to use/not use this prompt]
```

---

## 🗂️ Prompt Categories

### Case Management
Prompts for faster, more consistent case handling:
- **Case Summarization** — structured summaries from raw ticket text
- **Troubleshooting Guidance** — step-by-step diagnostic plans from symptoms
- **Escalation Triage** — severity assessment and routing recommendations

### Knowledge Base
Prompts for scaling documentation:
- **KB Article Generation** — turn resolved cases into searchable articles
- **FAQ Extraction** — pull common questions from case history

### Customer Communications
Prompts for professional, consistent messaging:
- **Status Update Emails** — clear, empathetic incident communications
- **Executive Summaries** — concise business-level summaries for stakeholders

### Reporting
Prompts for data-driven insights:
- **Weekly Metrics Digest** — narrative summaries from raw metrics
- **QBR Prep** — structured talking points from account history

---

## 🏛️ Governance

The `governance/` folder contains templates for responsible AI deployment:

- **Use Case Intake** — standardized form for evaluating new AI use cases
- **Risk Assessment** — checklist for data security and compliance review
- **Publishing Standards** — guidelines for deploying GPTs in your organization

---

## Contributing

To add a new prompt:
1. Pick the right category folder (or create one)
2. Use the standard template format above
3. Test the prompt at least 3 times with real inputs
4. Document edge cases in Usage Notes
5. Submit a PR with a one-line description of the use case

---

## License

MIT — use freely, attribution appreciated.
