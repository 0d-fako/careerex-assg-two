# Prompt 2: Data Extraction — Complaint Email Parser

## Scenario
Extract structured key information from a customer complaint email for routing, triage, and CRM logging.

---

## Weak Prompt

```
Extract information from this complaint email.
```

**Why it fails:**
- No fields specified — the model decides what "information" means
- No output format — returns prose, tables, or bullet points at random
- No type constraints — categories are invented on the fly (e.g., "kind of annoyed" vs "frustrated")
- No null handling — missing fields are either omitted or hallucinated
- Not machine-readable — output can't be parsed by downstream code

---

## Improved Prompt

```
You are a data extraction engine. Read the complaint email below and extract the following fields into a JSON object. Return ONLY the JSON — no explanation, no preamble.

Fields to extract:
- customer_name (string | null)
- order_id (string | null)
- complaint_category: one of ["shipping", "product_defect", "billing", "customer_service", "other"]
- sentiment: one of ["frustrated", "angry", "neutral", "disappointed"]
- urgency: "high" | "medium" | "low"
- requested_resolution (string | null)
- key_dates: array of ISO date strings mentioned

If a field cannot be determined, use null.

{{EMAIL_BODY}}
```

**Why it works:**

| Principle | What changed |
|---|---|
| **Role as engine** | "Data extraction engine" shifts the model from conversational to deterministic mode |
| **Typed schema** | Every field has a name, type, and constraint — no invention allowed |
| **Constrained enums** | `["shipping", "billing", ...]` prevents arbitrary label creation |
| **Null handling** | Explicit `null` instruction removes ambiguity — missing ≠ hallucinated |
| **Output-only instruction** | "Return ONLY the JSON" prevents prose wrapping that breaks parsers |
| **Separated input** | `{{EMAIL_BODY}}` clearly divides instructions from data, reducing prompt injection risk |

---

## Expected Output Shape

```json
{
  "customer_name": "Adaeze Okafor",
  "order_id": "ORD-20482",
  "complaint_category": "shipping",
  "sentiment": "frustrated",
  "urgency": "high",
  "requested_resolution": "Full refund or reshipment within 48 hours",
  "key_dates": ["2026-06-02", "2026-06-07"]
}
```

---

## Key Principle Demonstrated
> **Null handling is as important as field definition.**  
> Without "use null if unknown," the model fills gaps with plausible-sounding values — which is far more dangerous than an honest blank when data feeds a CRM or routing system.
