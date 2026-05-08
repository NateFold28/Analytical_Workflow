# 02_data_quality.md
Stage 2 — Data Quality & Fitness

---

## Purpose
Determine whether the selected data is **fit for the specific business decision** defined in Stage 0.

This stage does **not** aim for perfect data.
It aims to answer:
- Is the data trustworthy enough for this decision?
- What risks remain?
- What limitations must be communicated?

If data quality issues materially undermine the decision, stop or re‑scope.

---

## Primary Tool
- Cortex Code (or equivalent SQL execution environment)

---

## Inputs
- Approved `00_analysis_contract.md`
- Completed `01_data_landscape.md`
- Locked KPI, grain, unit of analysis, and time horizon

---

## Mandatory Quality Checks
These checks must be run for **all critical KPI inputs**.

### 1. Row Count Trends
- Evaluate row counts by day / week / month
- Look for:
  - Sudden drops or spikes
  - Step changes aligned with deployments or migrations
  - Missing periods

Purpose: detect ingestion failures, schema changes, or backfills.

---

### 2. Null‑Rate Trends
Measure null rates over time for:
- Primary keys
- Foreign keys
- Timestamps
- Target / label fields
- Fields used in KPI filters

Purpose: catch silent data loss and late‑arriving data.

---

### 3. Uniqueness at Expected Grain
Verify uniqueness at the **locked unit of analysis**.

Examples:
- One row per customer‑month
- One row per contract‑month

Purpose: prevent double‑counting, leakage, and inflated metrics.

---

### 4. Cross‑System Reconciliation
Where overlapping finance data exists:
- Compare totals across systems (e.g., billing vs finance reporting)
- Quantify differences
- Identify known sources of divergence

Perfect alignment is not required — **understood differences are**.

---

### 5. Data Latency vs Decision Cadence
Evaluate:
- Data freshness
- Ingestion delays
- Backfill patterns

Compare against:
- How frequently the decision is made
- How quickly action must be taken

Purpose: ensure the data arrives soon enough to matter.

---

## Execution Checklist

### 6. Write Checks as Repeatable Queries
- Each check should be:
  - Parameterized by date
  - Re‑runnable
  - Explicit about grain

Avoid one‑off exploratory SQL that cannot be repeated.

---

### 7. Run Checks Across Time
Run checks for:
- Recent periods (to catch breakages)
- Historical periods (to catch structural issues)

This helps distinguish:
- New regressions
- Long‑standing limitations

---

### 8. Quantify Issues (Not Just Pass/Fail)
For each issue:
- Measure magnitude (percent affected, dollars impacted, rows lost)
- Identify affected segments if possible

Executives trust numbers more than labels like “minor” or “major.”

---

### 9. Classify Findings
Explicitly label each issue as:
- **Blocking** — invalidates the decision or KPI
- **Mitigatable** — can be corrected downstream
- **Acceptable** — known limitation with bounded impact

This classification is a judgment call — document the rationale.

---

### 10. Define Mitigations and Trade‑Offs
For blocking or mitigatable issues:
- Proposed fix or workaround
- Cost (time, complexity, bias risk)
- Residual risk after mitigation

If mitigation introduces bias or leakage risk, note it explicitly.

---

### 11. Record Accepted Limitations
For accepted issues:
- Describe the limitation
- State expected business impact
- Identify who accepted the risk (role, not just name)

These notes must travel with the analysis to executives.

---

## Required Output
- `02_data_quality_findings.md` documenting:
  - Checks performed
  - Quantified issues
  - Blocking vs accepted limitations
  - Mitigations and residual risks

---

## Exit Criteria
You may proceed only if:
- Blocking defects are resolved **or** explicitly accepted
- Data limitations are documented with business impact
- The decision owner understands remaining risk

✅ Stage 2 complete. Proceed to `03_dbt_semantics.md`.
