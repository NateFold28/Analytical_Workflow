# Stage 5 — Exploratory Data Analysis

## Purpose
Validate signal quality and generate testable hypotheses before modeling.

## Tools
- Snowflake Python Notebooks
- Streamlit (optional early preview)

## Steps
1. Profile distributions by time and key cohorts.
2. Measure drift for major features and outcome variables.
3. Check cohort-level behavior consistency.
4. Compare simple correlations across periods (stability check).
5. Run leakage sniff tests using time-split logic.
6. Convert observations into explicit hypotheses with validation plans.

## Required outputs
- `eda_summary.md`
- Saved figures/charts used in conclusions

## Exit criteria
- Each proposed model feature has a documented rationale and risk note.
