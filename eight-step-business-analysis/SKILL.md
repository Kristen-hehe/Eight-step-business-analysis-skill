---
name: eight-step-business-analysis
description: Analyze an uploaded structured business dataset using an 8-step management-analysis workflow. Generate each step's prompt, execute the steps sequentially using only the supplied dataset, clearly separate facts from assumptions, and produce a management-ready report containing all prompts and answers.
---

# Eight-Step Business Analysis Skill

## Purpose

Use this skill whenever the user uploads a structured business dataset and asks for a management-oriented analysis similar to the prior East/West/Product or E-commerce case studies.

The workflow must:

1. Inspect the uploaded dataset first.
2. Adapt the prompts to the dataset's actual dimensions and measures.
3. Preserve the exact structure of the eight prompt templates below.
4. Execute the prompts sequentially.
5. Use only the uploaded dataset unless the user explicitly permits external information.
6. Clearly distinguish facts, interpretations, hypotheses, and recommendations.
7. Produce a final report containing every step's prompt followed by its answer.
8. If the user requests a document, generate a downloadable Word report containing all eight prompts and answers.

---

# Core Rules

- Use ONLY the uploaded dataset.
- Do not introduce external facts, benchmarks, market information, or causal claims.
- Do not infer causes during descriptive steps.
- Quantify changes where the dataset supports calculation.
- Use the dataset's real field names and business dimensions.
- Adapt generic terms such as `Region`, `Category`, `Product`, and performance metrics to the uploaded dataset.
- Never fabricate missing values.
- If a metric definition, unit, or reconciliation appears inconsistent, flag it under **What to Validate Next**.
- Clearly separate:
  - **Observations** = directly supported facts.
  - **Insights** = business interpretation of observed patterns.
  - **Hypotheses** = plausible but unproven explanations.
  - **Recommended Actions** = management responses based on insights/hypotheses.
- Maintain a concise, senior-management-friendly tone.
- If the user has requested English-only output, answer in English only. Otherwise follow the user's current language preference.

---

# Step 0 — Inspect and Adapt

Before running Step 1:

1. Read the dataset structure.
2. Identify:
   - time field(s),
   - major business dimensions,
   - segment/group fields,
   - product/category fields,
   - performance metrics,
   - revenue/sales metrics,
   - any obvious data-quality issues.
3. Determine the closest equivalents to:
   - `Region`,
   - `Category/Product`,
   - `Orders`,
   - `Average Order Value`,
   - `Revenue`.
4. If the dataset uses different dimensions or measures, substitute those terms in the prompts while preserving the prompt structure.
5. Select the most meaningful divergence for Step 5 only after Steps 2–3 establish it.

Do not ask the user to rewrite the prompts unless the dataset is genuinely unusable.

---

# Step 1 — Full Business Analysis

## Prompt Template

> You are a business analyst supporting senior management.
>
> Use ONLY the uploaded dataset.
>
> Output format must include:
>
> (1) Observations
>
> (2) Insights
>
> (3) Hypotheses
>
> (4) Recommended Actions
>
> (5) What to Validate Next
>
> Clearly separate facts from assumptions.

## Execution Requirements

- Observations must contain only dataset-supported facts.
- Insights may interpret patterns but must not claim causes.
- Hypotheses must be explicitly labeled as assumptions requiring validation.
- Recommended actions should follow from the observed patterns and hypotheses.
- What to Validate Next should identify missing evidence needed before stronger conclusions are made.

---

# Step 2 — Trend Summary

## Prompt Template

> Summarise the key performance trends by [PRIMARY GROUP] and [CATEGORY / PRODUCT] over the [TIME PERIOD].
>
> Focus on direction of change (increase/decrease/stable) in [KEY METRIC 1], [KEY METRIC 2], and [KEY METRIC 3].
>
> Do not explain causes yet.

## Adaptation Rules

Replace:
- `[PRIMARY GROUP]` with Region, Market, Channel, Segment, Store Type, etc.
- `[CATEGORY / PRODUCT]` with the dataset's relevant product/category dimension.
- `[TIME PERIOD]` with the dataset's actual period.
- metrics with the three most decision-relevant performance measures available.

## Execution Requirements

- Focus on increase / decrease / stable.
- Quantify start-to-end changes where useful.
- Do not explain causes.

---

# Step 3 — Group Comparison

## Prompt Template

> Compare performance between [GROUP A] and [GROUP B] for each [CATEGORY / PRODUCT].
>
> Highlight where performance diverges
>
> most and quantify the differences in [KEY METRIC 1], [KEY METRIC 2], and [KEY METRIC 3] where possible.

## Adaptation Rules

- Use the most important two comparable groups in the dataset.
- If there are more than two groups, select the most decision-relevant comparison or compare all groups while identifying the largest divergence.
- Preserve the two-paragraph prompt structure.

## Execution Requirements

- Identify the strongest divergence.
- Quantify percentage changes and percentage-point gaps where possible.
- Do not explain causes.

---

# Step 4 — Convert Observations into Business Insights

## Prompt Template

> Convert the observations into 3 business insights.
>
> Each insight must explain:
>
> (a) what changed,
>
> (b) why it matters to the business,
>
> (c) which decision area it affects.

## Execution Requirements

Each insight must explicitly contain:
1. **What changed** — evidence-based pattern.
2. **Why it matters** — business significance, without inventing external facts.
3. **Decision area** — e.g. regional planning, pricing, product strategy, inventory, customer management, channel allocation.

Do not present hypotheses as facts.

---

# Step 5 — Generate Hypotheses

## Prompt Template

> Generate 3 plausible hypotheses explaining why [UNDERPERFORMING AREA] is declining in [GROUP A] but growing in [GROUP B].
>
> Label each as a hypothesis and state what data would be needed to confirm it.

## Adaptation Rules

- Replace the bracketed terms using the clearest divergence identified in Step 3.
- If the dataset does not contain a decline-vs-growth pattern, adapt only the factual comparison phrase while preserving the rest of the prompt structure as closely as possible.
  Example:
  - "declining faster in Group A than Group B"
  - "growing in Group A but remaining stable in Group B"

## Execution Requirements

For each hypothesis provide:
- **Hypothesis**
- **Why it is plausible based on the observed pattern**
- **Data needed to confirm**

Possible data categories may include only as validation needs, not as assumed facts:
- pricing,
- promotions,
- traffic,
- conversion,
- customer segments,
- inventory,
- stock-outs,
- channel mix,
- unit sales,
- repeat purchase,
- product mix.

---

# Step 6 — Management Responses

## Prompt Template

> Based on the insights and hypotheses, propose 3 actionable management responses.
>
> For each action, include:
>
> • Objective
>
> • What to do
>
> • Expected impact
>
> • Key risk
>
> • Metric to monitor

## Execution Requirements

Each response must include all five fields.

Actions should:
- be specific,
- be feasible,
- relate directly to identified patterns,
- avoid treating unvalidated hypotheses as confirmed causes,
- favor diagnostic or test-and-learn actions when evidence is limited.

---

# Step 7 — Prioritization

## Prompt Template

> Prioritize the actions using Impact vs Effort vs Risk (High / Medium / Low).
>
> Recommend the top 2 actions management should take in the next quarter.

## Execution Requirements

Create a concise prioritization table with:
- Action
- Impact
- Effort
- Risk
- Priority

Then recommend the top two actions.

Prioritization should be based only on:
- magnitude of observed performance issue,
- breadth of affected business area,
- reversibility,
- evidence available,
- execution complexity implied by the action.

Do not invent cost estimates.

---

# Step 8 — Executive Summary

## Prompt Template

> Write a concise executive
>
> summary (max 6 bullets)
>
> covering:
>
> • Key performance issue
>
> • Why it matters now
>
> • Top 2 recommended actions
>
> • Risks to watch
>
> • What data must be validated next

## Execution Requirements

- Maximum 6 bullets.
- Include the most relevant quantitative evidence.
- Preserve the distinction between facts and hypotheses.
- Make the summary suitable for senior management.
- Do not add any new analysis that was not established in Steps 1–7.

---

# Final Report Structure

When all eight steps are complete, compile the output in this order:

# Business Analysis Report

## Dataset Overview
- File name
- Time period
- Main dimensions
- Main metrics
- Any material data-quality notes

## Step 1
### Prompt
[Exact adapted prompt]

### Answer
[Step 1 answer]

## Step 2
### Prompt
[Exact adapted prompt]

### Answer
[Step 2 answer]

## Step 3
### Prompt
[Exact adapted prompt]

### Answer
[Step 3 answer]

## Step 4
### Prompt
[Exact adapted prompt]

### Answer
[Step 4 answer]

## Step 5
### Prompt
[Exact adapted prompt]

### Answer
[Step 5 answer]

## Step 6
### Prompt
[Exact adapted prompt]

### Answer
[Step 6 answer]

## Step 7
### Prompt
[Exact adapted prompt]

### Answer
[Step 7 answer]

## Step 8
### Prompt
[Exact adapted prompt]

### Answer
[Step 8 answer]

---

# Quality Checks Before Finalizing

Before delivering the report, verify:

1. Every numerical claim is supported by the uploaded dataset.
2. Percentage changes are calculated correctly.
3. Step 2 contains no causal explanation.
4. Step 3 highlights the largest divergence.
5. Step 4 contains exactly 3 business insights.
6. Step 5 contains exactly 3 hypotheses and validation data for each.
7. Step 6 contains exactly 3 actions and all five required fields.
8. Step 7 uses High / Medium / Low for Impact, Effort, and Risk and recommends exactly 2 actions.
9. Step 8 contains no more than 6 bullets.
10. Facts and assumptions are clearly separated throughout.
11. The final report includes all eight adapted prompts and all eight answers.
12. Any data-quality or unit inconsistencies are explicitly flagged rather than silently corrected or ignored.

---

# Trigger Examples

Use this skill when the user says things like:

- "Run the same 8 steps on this dataset."
- "Generate the prompts and answers for this dataset."
- "Do the East/West/Product-style analysis on this file."
- "Create the 8-step management analysis report."
- "Use the previous business analysis workflow."
- "Analyze this dataset and give me all prompts and answers."

---

# Default Behavior

If the user uploads a dataset and invokes this skill without further instructions:

1. Inspect the dataset.
2. Adapt the eight prompts.
3. Execute all eight steps sequentially.
4. Present the complete analysis.
5. If the user requests a document and document generation is available, create a downloadable Word report containing all prompts and answers.
