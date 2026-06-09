# Prompt 1: Customer Service Response Bot

## Scenario
A bot that replies to customer complaints on behalf of a brand.

---

## Weak Prompt

```
Reply to customer complaints.
```

**Why it fails:**
- No role or persona — the model defaults to a generic, robotic tone
- No structure — every reply will look different
- No tone guidance — "professional," "empathetic," and "cold" are all valid
- No output constraint — replies can be 2 words or 2 paragraphs
- Not reusable — no variable slot for the actual complaint

---

## Improved Prompt

```
You are a friendly, empathetic customer support agent for Lumora — a premium home lighting brand.

When a customer sends a complaint:
1. Open by acknowledging their frustration (1–2 sentences, no hollow apologies like "I'm sorry you feel that way").
2. Restate the core issue in your own words to show you understood.
3. Provide a clear resolution or next step (e.g., replacement, refund, escalation).
4. Close with a warm, forward-looking sentence.

Tone: Professional but human. Avoid jargon. Keep each reply under 120 words.

{{CUSTOMER_COMPLAINT}}
```

**Why it works:**

| Principle | What changed |
|---|---|
| **Role + persona** | "Friendly support agent for Lumora" anchors tone and brand voice |
| **Structured output** | 4-step numbered format ensures every reply has the same shape |
| **Negative example** | Banning "I'm sorry you feel that way" blocks the model's most common hollow response |
| **Output constraint** | 120-word cap prevents padding — critical for chat UI and customer patience |
| **Variable placeholder** | `{{CUSTOMER_COMPLAINT}}` makes this template-ready for programmatic injection |

---

## Key Principle Demonstrated
> **Negative examples outperform vague tone instructions.**  
> "No hollow apologies like…" is more effective than "be empathetic" because it gives the model a concrete pattern to avoid rather than an abstract quality to aim for.
