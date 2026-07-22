# Prompt Ladder

## Assignment Goal

This document demonstrates how a weak prompt can be improved step by step using prompt engineering. Each version introduces exactly one new layer and compares the output with the previous version.

---

# Baseline Prompt

### Prompt

```text
Analyze this dataset.
```

### Representative Output

> The dataset contains multiple columns and records. You can calculate summary statistics, visualize distributions, and explore relationships between variables.

### Notes

**What changed**

- No changes (baseline).

**What improved in the output**

- None. This is the starting point.

**What still failed**

- The response is generic and does not mention SEO or content refresh.

**What I would try next**

- Add a clear goal.

---

# Version 1 — Layer: Clear Goal

### Prompt

```text
Analyze this SEO dataset and identify pages that may need content refresh.
```

### Representative Output

> The model identifies pages that appear outdated based on SEO signals and recommends reviewing them for refresh.

### Notes

**What changed**

- Added a clear goal.

**What improved in the output**

- The response became focused on identifying refresh candidates instead of giving a generic dataset explanation.

**What still failed**

- It did not explain why pages were selected.

**What I would try next**

- Add project context.

---

# Version 2 — Layer: Context

### Prompt

```text
Analyze this SEO dataset from a content optimization project and identify pages that may need content refresh based on historical search performance.
```

### Representative Output

> The analysis prioritizes pages showing declining performance and suggests reviewing older content.

### Notes

**What changed**

- Added project context.

**What improved in the output**

- The recommendations became more relevant to an SEO content optimization workflow.

**What still failed**

- The output structure was inconsistent.

**What I would try next**

- Specify an output format.

---

# Version 3 — Layer: Output Format

### Prompt

```text
Analyze this SEO dataset.

Return the results as a Markdown table with the following columns:

- Page
- Reason
- Priority
- Recommended Action
```

### Representative Output

| Page | Reason | Priority | Recommended Action |
|------|--------|----------|--------------------|
| Example Page | Low CTR | High | Refresh content |

### Notes

**What changed**

- Added a required output format.

**What improved in the output**

- The response became much easier to read and compare.

**What still failed**

- Priority rankings were not always supported by evidence.

**What I would try next**

- Add quality criteria.

---

# Version 4 — Layer: Quality Criteria

### Prompt

```text
Analyze this SEO dataset.

Rank recommendations by expected business impact.

Explain every recommendation in one sentence.

Avoid unsupported assumptions.
```

### Representative Output

> High-impact pages are ranked first with short explanations describing the evidence used.

### Notes

**What changed**

- Added quality criteria.

**What improved in the output**

- The recommendations became more evidence-based.

**What still failed**

- Some explanations were still repetitive.

**What I would try next**

- Require verification.

---

# Version 5 — Layer: Verification Requirements

### Prompt

```text
Analyze this SEO dataset.

For every recommendation:

- cite the feature(s) used
- explain why the recommendation was made
- if evidence is insufficient, explicitly state that instead of guessing
```

### Representative Output

> Recommendation: Refresh Page A.
>
> Evidence: Low CTR, declining impressions, last updated over 180 days ago.
>
> Confidence: Medium.

### Notes

**What changed**

- Added verification requirements.

**What improved in the output**

- The model justified its recommendations instead of making unsupported claims.

**What still failed**

- Some recommendations became longer than necessary. This trade-off improved reliability but reduced brevity.

**What I would try next**

- Optimize the wording to balance detail and conciseness.

---

# Final Reusable Prompt

```text
You are an SEO content analyst.

Analyze the provided SEO dataset to identify pages that should be considered for content refresh.

For each recommendation:

- Identify the page.
- Explain which features support the recommendation.
- Rank recommendations by expected business impact.
- Provide a confidence level.
- If evidence is insufficient, explicitly state that instead of making assumptions.

Return the results as a Markdown table with the following columns:

| Page | Reason | Priority | Confidence | Recommended Action |
```

---

# Reflection

This exercise demonstrated that prompt quality improves most when changes are introduced one layer at a time. The biggest improvements came from defining a clear goal, adding context, specifying the desired output format, and requiring evidence-based recommendations. It also showed that not every change produces a perfect result immediately, and prompt engineering benefits from iterative evaluation rather than making many changes at once.