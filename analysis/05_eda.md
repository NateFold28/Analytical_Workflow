# 05_eda.md
Stage 5 — Exploratory Data Analysis (EDA)

---

## Purpose
Evaluate whether the data contains **stable, decision‑relevant signal** and convert observations into **explicit, testable hypotheses** before any modeling work begins.

EDA is not for finding impressive charts.
EDA is for deciding:
- What is safe to model
- What should not be modeled
- What assumptions must be validated later

---

## Tools
- Snowflake Python Notebooks
- Snowpark / pandas
- Streamlit (optional, read‑only preview)

---

## Inputs
- Approved `00_analysis_contract.md`
- Completed `01_data_landscape.md`
- Completed `02_data_quality.md`
- Completed `03_dbt_semantics.md`
- Locked KPI, unit of analysis, and time horizon

---

## EDA Guardrails (Read First)

During EDA:
- Do **not** create final features
- Do **not** tune models
- Do **not** optimize metrics
- Do **not** use future information relative to the decision point

All analysis must respect time ordering and grain.

---

## EDA Checklist

### 1. Profile Distributions Over Time
For key variables (inputs and outcome):
- Examine distributions by time (month / quarter)
- Look for:
  - Structural shifts
  - Long tails
  - Clipping or saturation effects

Purpose: understand stability, not maximize correlation.

---

### 2. Segment by Decision‑Relevant Cohorts
Profile behavior across cohorts that matter to the business, such as:
- Customer tenure
- Contract type or plan
- Product mix
- Revenue bands

Check whether relationships are consistent or segment‑specific.

---

### 3. Measure Feature and Outcome Drift
Evaluate drift over time for:
- Major candidate features
- The target variable / KPI

Look for:
- Gradual trends vs sharp breaks
- Drift aligned with product, pricing, or policy changes

Unstable features are high‑risk for modeling.

---

### 4. Validate Cohort‑Level Consistency
Check whether:
- Relationships hold across cohorts
- Effects reverse or disappear in subgroups

This helps surface:
- Simpson’s paradox
- Hidden confounders
- Segment‑specific behavior

---

### 5. Run Simple Stability Checks
Using time‑aware splits:
- Compare basic correlations or summary statistics across periods
- Avoid global correlations across all time

Purpose: assess whether observed relationships persist.

---

### 6. Perform Leakage “Sniff Tests”
Explicitly test for leakage by:
