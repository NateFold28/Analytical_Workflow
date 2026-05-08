# 06_model_design.md
Stage 6 — Model Selection & Baselines

---

## Purpose
Select an appropriate modeling approach through **disciplined, baseline‑first evaluation**.

This stage answers:
- Do we need a model at all?
- If so, what level of complexity is justified?
- Does the model materially improve decision quality over simple alternatives?

Complexity must earn its way in.

---

## Tools
- LLM (Claude / Copilot) for design framing and critique
- Snowpark / Python for implementation and evaluation
- scikit‑learn (default)
- Advanced models only if justified (e.g., XGBoost, LightGBM)

---

## Inputs
- Approved `00_analysis_contract.md`
- Completed `05_eda.md`
- Explicit hypotheses and validation plans
- Locked KPI, time horizon, and unit of analysis

---

## Model Selection Checklist

### 1. Define Baselines First (Mandatory)
Before any ML model, define at least:
- **Naive baseline**  
  (e.g., last period value, global average, persistence model)
- **Rules‑based baseline**  
  (simple thresholds, heuristics, business rules)
- **Simple statistical model**  
  (e.g., linear regression, logistic regression)

If a model cannot beat these, it should not ship.

---

### 2. Clarify the Decision Interface
Explicitly define:
- What the model outputs (score, probability, forecast)
- How that output will be used in a decision
- What action thresholds or rankings imply

A model without a clear decision interface is incomplete.

---

### 3. Select Candidate Model Families
Choose candidate models based on:
- Interpretability requirements
- Data volume and stability
- Hypotheses from EDA
- Operational constraints (latency, retraining, monitoring)

Default progression:
1. Linear / generalized linear models
2. Regularized models
3. Tree‑based models

Escalate only with justification.

---

### 4. Define Business‑Relevant Evaluation Metrics
Metrics must reflect **decision quality**, not abstract accuracy.

Examples:
- MAE or MAPE on dollars
- Directional accuracy (right sign, right direction)
- Calibration (reliability curves, Brier score)
- Segment‑level performance (by cohort)

Avoid optimizing metrics executives cannot interpret.

---

### 5. Use Identical, Time‑Aware Splits
All baselines and candidates must be evaluated using:
- The same temporal splits
- No future leakage
- The same feature availability assumptions

If splits differ, comparisons are invalid.

---

### 6. Compare Lift Over Baseline
For each candidate:
- Quantify improvement over the best baseline
- Evaluate consistency across time and segments
- Identify where the model helps and where it fails

Small average lift with high variance is a red flag.

---

### 7. Evaluate Operational Complexity
For each candidate model, consider:
- Explainability to Finance and executives
- Sensitivity to data drift
- Retraining frequency
- Monitoring and alerting burden
- Failure modes and fallback options

Operational risk matters as much as performance.

---

### 8. Stress‑Test Assumptions
Check:
- Performance stability across time slices
- Sensitivity to feature removal
- Behavior under edge cases

Models that are brittle should not advance.

---

### 9. Select Recommended Model and Fallback
Document:
- Chosen model
- Why it is preferred over baselines
- Explicit fallback approach if the model fails or degrades
- Conditions under which the model should be disabled

A fallback is not optional.

---

### 10. Document Why ML Is (or Is Not) Justified
Explicitly answer:
- Why a baseline is insufficient
- What additional value the model provides
- What risks remain

If ML is not justified, document that conclusion clearly.

---

## Required Outputs
- `06_model_design.md` capturing:
  - Baselines and their performance
  - Candidate models evaluated
  - Business‑relevant metrics
  - Complexity and risk assessment
  - Final recommendation and fallback
- Baseline and model performance comparison table

---

## Exit Criteria
You may proceed only if:
- The chosen model materially outperforms baselines
- Improvements are stable across time and cohorts
- The model is explainable to business stakeholders
- A clear fallback strategy is defined

✅ Stage 6 complete. Proceed to `07_validation.md`.
``
