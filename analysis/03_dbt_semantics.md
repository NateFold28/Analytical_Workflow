# 03_dbt_semantics.md
Stage 3 — dbt Transformation Semantics

---

## Purpose
Translate dbt transformations into **explicit business meaning** and identify **semantic risks** that could invalidate the KPI or decision defined in Stage 0.

This stage answers:
- What does each model *actually* mean in business terms?
- What assumptions are embedded in joins, filters, and snapshots?
- Where could semantics drift from Finance’s understanding?

SQL that runs is not sufficient.  
Semantics must be defensible.

---

## Primary Tools
- dbt artifacts (model SQL, YAML, lineage)
- Cortex / IDE for inspection
- LLM (Claude / Copilot) for plain‑language interpretation

---

## Inputs
- Approved `00_analysis_contract.md`
- Completed `01_data_landscape.md`
- Completed `02_data_quality.md`
- Identified KPI source models

---

## dbt Semantics Checklist

### 1. Pull Only Relevant Models
Limit scope to:
- Models directly computing the primary KPI
- Models upstream of those outputs
- Shared intermediate models used by Finance reporting

Avoid reviewing the entire project — focus on **decision‑critical lineage**.

---

### 2. Explain Each Model in Business Terms
For every relevant model:
- Describe what one row represents
- Describe what business question the model answers
- State what is included and excluded

The explanation must be understandable without SQL.

If a model cannot be explained clearly, it is a semantic risk.

---

### 3. Document Model Grain Explicitly
For each model:
- State its grain in plain language
- Compare it to the Stage 0 unit of analysis
- Note where aggregation or duplication occurs

Implicit grain changes are a common source of KPI distortion.

---

### 4. Inspect Joins and Cardinality Assumptions
For every join:
- Identify join type (inner, left, etc.)
- State expected cardinality (1:1, 1:M, M:M)
- Explain what happens when records are missing

Explicitly flag:
- Fan‑out risk
- Accidental filtering via inner joins
- Assumptions about data completeness

---

### 5. Identify Known Semantic Risk Patterns
Actively look for and document:

- Fan‑out joins inflating metrics
- Late‑arriving facts changing historical values
- Soft‑delete handling (or lack thereof)
- Snapshot logic and edge behavior
- Hard‑coded filters that encode business policy
- Implicit “current state” assumptions

These patterns are common and expected — silence is the risk.

---

### 6. Review Time Logic and Period Alignment
Check:
- How time is defined (event time vs load time)
- Period boundaries (month start/end)
- Treatment of partial periods
- Alignment with revenue and churn recognition

Time semantics must match Finance’s mental model.

---

### 7. Validate KPI Lineage End‑to‑End
Trace the primary KPI from:
- Raw source tables
- Through intermediate dbt models
- To final output

At each step:
- Confirm business meaning is preserved
- Note where assumptions are introduced

If lineage cannot be clearly narrated, stop.

---

### 8. Check Alignment With Stage 0 Contract
Explicitly validate:
- Grain matches the locked unit of analysis
- Filters match the defined KPI scope
- Time horizon logic is consistent

Any deviation requires either:
- A refactor, or
- A revision to the Stage 0 contract

---

### 9. Propose Semantic Refactors (If Needed)
Where semantics are unclear or risky:
- Suggest model splits or renames
- Propose clearer grains or explicit aggregations
- Recommend documentation or tests to lock meaning

Do not refactor for elegance — refactor for clarity.

---

### 10. Identify Downstream Risk
Assess how semantic issues could affect:
- EDA conclusions
- Feature engineering
- Model targets or labels
- Executive narratives

Explicitly state which risks are acceptable and which are not.

---

## Required Output
- `03_dbt_semantics.md` capturing:
  - Business explanations of key models
  - Grain and join assumptions
  - Identified semantic risks
  - Proposed refactors or clarifications

---

## Exit Criteria
You may proceed only if:
- Business stakeholders can explain KPI lineage from source to output
- Model grains and assumptions are explicit
- Known semantic risks are documented and accepted or mitigated

✅ Stage 3 complete. Proceed to `05_eda.md`.
