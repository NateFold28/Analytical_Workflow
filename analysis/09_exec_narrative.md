# 09_exec_narrative.md
Stage 9 — Delivery Layer & Executive Narrative

---

## Purpose
Make validated outputs **visible, interpretable, and actionable** for recurring decision forums — without requiring analyst mediation.

This stage answers:
- Can leaders trust what they are seeing?
- Do the numbers match what was validated?
- Is it clear what action to take (or not take)?

Delivery is successful when decisions can happen without explanation.

---

## Delivery Tools
- Streamlit in Snowflake (interactive understanding & diagnostics)
- Power BI (recurring leadership consumption)
- Copilot 365 (narratives, slides, emails — **consumption only**)

---

## Inputs
- Approved `07_validation.md`
- Deployed pipeline from `08_production_notes.md`
- Locked KPIs and definitions from `00_analysis_contract.md`

---

## Delivery & Narrative Checklist

### 1. Publish Interactive Diagnostic Views
Use Streamlit (or equivalent) to:
- Enable drill‑down by cohort, time, and segment
- Surface model drivers and diagnostics
- Support “why did this number change?” exploration

These views are for:
- Analysts
- Operators
- Curious executives

They are **not** the system of record.

---

### 2. Publish Stable KPI Views for Leadership
Use Power BI (or equivalent) to:
- Present a small number of **locked KPIs**
- Match definitions exactly from Stage 0
- Maintain consistent layout and scales over time

Leadership views should:
- Change slowly
- Avoid experimentation
- Minimize toggles and filters

Stability builds trust.

---

### 3. Enforce Metric Definition Consistency
Explicitly validate that:
- Dashboard metrics match dbt semantics
- Dashboard aggregates match model‑validated outputs
- Time windows and grains are consistent

If numbers differ across tools, stop and reconcile.

---

### 4. Validate Against Approved Validation Outputs
Cross‑check that:
- Published metrics align with validation‑approved results
- No additional filters or logic were introduced
- Default views reflect the intended decision context

Delivery layers must not silently reinterpret results.

---

### 5. Define Audience‑Specific Views
Prepare distinct narratives for:
- **Executives** — What changed? What decision is needed?
- **Finance** — How do numbers reconcile? What assumptions apply?
- **Operators** — What actions should be taken?

One dataset, multiple narratives — not multiple truths.

---

### 6. Prepare the Executive Narrative
Draft a concise narrative that covers:
- The decision being supported
- The primary KPI and recent movement
- Key drivers (in plain language)
- Confidence level and known risks
- Recommended action (or no action)

Avoid:
- Model internals
- Algorithm names
- Excess precision

---

### 7. Use Copilot as a Communication Accelerator
Copilot may be used to:
- Draft slides from approved metrics
- Generate executive summaries
- Prepare follow‑up emails

Copilot must **not**:
- Define metrics
- Alter conclusions
- Introduce new analysis

Copilot consumes truth — it does not create it.

---

### 8. Validate “No‑Analyst Needed” Consumption
Test whether:
- A leader can interpret the view without explanation
- A follow‑up question can be answered via drill‑down
- The decision implication is obvious

If explanation is required, the delivery layer is incomplete.

---

### 9. Capture Feedback and Misinterpretation Risk
Document:
- Common questions or confusion
- Metrics that invite misinterpretation
- Where narrative needs tightening

This feedback informs future iterations — not ad hoc fixes.

---

## Required Outputs
- Streamlit artifacts (interactive diagnostics)
- Power BI artifacts (recurring leadership views)
- Communication‑ready executive summary (slide or memo draft)

---

## Exit Criteria
You may proceed only if:
- Leadership can consume consistent metrics without analyst mediation
- Numbers reconcile across delivery tools
- The decision implication is clear
- Known limitations are visible and communicated

✅ Stage 9 complete. Proceed to `10_interpretation.md`.
