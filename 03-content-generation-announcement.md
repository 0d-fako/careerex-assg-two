# Prompt 3: Content Generation — Product Announcement

## Scenario
Generate a launch announcement for a new software product targeting B2B buyers.

---

## Weak Prompt

```
Write a product announcement for our new software.
```

**Why it fails:**
- No audience definition 
- No structure 
- No tone guidance 
- No word count, output length is unpredictable
- Not reusable 

---

## Improved Prompt

```
Write a product launch announcement for the following audience and product. Use the structure below exactly.

Product details:
{{PRODUCT_NAME}}, {{KEY_FEATURES_LIST}}, {{PRICING}}, {{LAUNCH_DATE}}

Audience: B2B SaaS buyers — pragmatic, skeptical of hype, value ROI over features.

Structure:
1. Hook (1 sentence): A bold, specific claim — NOT "We're excited to announce…"
2. Problem (2–3 sentences): The pain this product eliminates.
3. Solution (3–4 sentences): What it does and how — lead with outcomes, not features.
4. Social proof placeholder: [QUOTE or STAT]
5. CTA (1 sentence): One clear next action with a link placeholder.

Tone: Direct. Confident. No buzzwords (avoid: "game-changing", "revolutionary", "seamless").
Length: 180–220 words.
```

**Why it works:**

| Principle | What changed |
|---|---|
| **Audience definition** | "Pragmatic, skeptical of hype" gives the model a mental model of the reader |
| **Named scaffold** | Hook → Problem → Solution → Proof → CTA replicates proven copywriting frameworks |
| **Anti-buzzword list** | Banning specific words blocks the model's default marketing vocabulary |
| **Outcomes-first instruction** | "Lead with outcomes, not features" shifts from spec-listing to benefit-selling |
| **Word count range** | 180–220 words forces editorial discipline without feeling mechanical |
| **Template placeholders** | Variable slots and `[QUOTE or STAT]`|

---




