# Prompt Portfolio

Three prompt pairs demonstrating the difference between weak and improved prompts across common business scenarios.

## Files

| File | Scenario | Technique Focus |
|---|---|---|
| `01-customer-service-bot.md` | Customer service response bot | Role, structure, negative examples, output constraints |
| `02-data-extraction-email.md` | Complaint email parser | Schema typing, enums, null handling, output-only format |
| `03-content-generation-announcement.md` | Product launch announcement | Audience definition, copywriting scaffold, anti-buzzwords |

## Core Principles Applied

1. **Assign a role** — who the model is shapes every output decision
2. **Structure the output** — numbered steps, JSON schema, or named sections beat open-ended requests
3. **Use negative examples** — banning specific patterns is more precise than asking for abstract qualities
4. **Handle the null case** — define what happens when information is missing
5. **Add variable placeholders** — `{{LIKE_THIS}}` turns a one-off prompt into a reusable template
6. **Constrain length** — word counts and field types enforce discipline and predictability

## Assignment Context

Built as part of the AI Automation Class — Prompt Portfolio practical assignment.
