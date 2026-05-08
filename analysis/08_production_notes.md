# 08_production_notes.md
Stage 8 — Productionization & MLOps

---

## Purpose
Deploy a **lean, reliable, and observable** analytics or ML pipeline that can safely influence business decisions.

This stage is not about scaling sophistication.
It is about:
- Reproducibility
- Observability
- Controlled failure
- Clear rollback paths

If the system cannot fail safely, it is not production‑ready.

---

## Core Stack
- Snowflake (storage, compute, inference)
- dbt (transforms and feature logic)
- Snowpark / Python (model execution)
- Git (version control and audit trail)

---

## Inputs
- Approved `07_validation.md`
- Go / go‑with‑constraints decision
- Selected model and defined fallback
- Locked KPI, unit of analysis, and cadence

---

## Production Readiness Checklist

### 1. Version All Logic in Git
Ensure the following are version‑controlled:
- Feature table SQL / dbt models
- Model training code
- Inference logic
- Thresholds and decision rules

Every production output must be traceable to a Git commit.

---

### 2. Reference an Immutable Training Snapshot
Explicitly record:
- Training data snapshot date or range
- Feature definitions used at training time
- Model artifact version or hash

Models must never be retrained implicitly.

Reproducibility is mandatory.

---

### 3. Define the Inference Pattern
Explicitly decide:
- Batch vs near‑real‑time inference
- Inference frequency
- Latency expectations

Align inference cadence with:
- Decision cadence
- Data freshness realities

Faster is not better if it is unnecessary.

---

### 4. Schedule Feature Refresh and Inference Runs
For each scheduled job, document:
- Trigger (time‑based, event‑based)
- Dependencies
- Expected runtime
- Failure behavior (retry, alert, skip)

Silent failures are unacceptable.

---

### 5. Log Inference Outputs
Persist inference results to a dedicated table, including:
- Model version
- Inference timestamp
- Input feature snapshot identifier
- Output score / prediction
- Decision flag (if applicable)

Logs are required for:
- Auditing
- Debugging
- Performance monitoring

---

### 6. Define Monitoring Signals
At minimum, track:
- Data freshness
- Feature distribution drift
- Output distribution drift
- Business KPI impact (where measurable)

Metrics should be:
- Simple
- Interpretable
- Actionable

Do not over‑instrument early.

---

### 7. Set Alert Thresholds
Define:
- What constitutes abnormal behavior
- Alert severity levels
- Who is notified and how

Alerts must trigger **action**, not just awareness.

---

### 8. Establish Rollback and Fallback Procedures
Explicitly document:
- How to disable the model
- How to revert to baseline or rules
- How long rollback takes
- Who has authority to initiate rollback

Rollback paths must be tested, not theoretical.

---

### 9. Define Model Retirement Criteria
Specify conditions under which the model will be:
- Retrained
- Re‑validated
- Retired entirely

Examples:
- Performance degradation
- Data schema changes
- Business process changes

Models do not live forever.

---

### 10. Document Known Production Risks
Summarize:
- Known failure modes
- Monitoring blind spots
- Residual uncertainty
- Manual checks required (if any)

These risks must be visible to stakeholders.

---

## Required Output
- `08_production_notes.md` documenting:
  - Deployment configuration
  - Model and data versions
  - Schedules and dependencies
  - Monitoring and alerting setup
  - Rollback and retirement procedures

This document is run‑specific and must be updated for each deployment.

---

## Exit Criteria
You may proceed only if:
- Pipeline runs on schedule
- Outputs are observable and traceable
- Alerts are defined and tested
- A rollback path exists and is understood

✅ Stage 8 complete. Proceed to `09_exec_narrative.md`.
