# 01_data_landscape.md
Stage 1 — Data Reconnaissance

---

## Purpose
Identify **what data exists**, **where it lives**, and **which models are authoritative** for the KPIs defined in Stage 0.

This stage answers:
- Do we have the data we think we have?
- Where is the single source of truth?
- What assumptions are embedded in existing models?

No transformation, modeling, or feature engineering should occur yet.

---

## Primary Tools
- Snowflake (data catalog, information schema)
- dbt artifacts (models, exposures, lineage)
- Cortex Code / IDE for inspection and notes

---

## Inputs
- Approved `00_analysis_contract.md`
- Locked primary KPI, grain, unit of analysis, and time horizon

---

## Data Reconnaissance Checklist

### 1. Enumerate Relevant Data Domains
List domains that plausibly touch the KPI or decision.

Common SaaS finance domains include:
- Finance / Revenue
- Billing / Invoicing
- Contracts / Subscriptions
- CRM / Accounts
- Product usage / telemetry
- Customer lifecycle / onboarding
- Support / success (if churn or expansion related)

Do not assume all domains are needed — list first, prune later.

---

### 2. Identify Candidate Source Tables per KPI Component
For each component of the primary KPI:
- List candidate raw tables
- Note system of origin (e.g., billing system, CRM, product DB)
- Flag whether the table is raw, lightly modeled, or business‑ready

At this stage:
- Prefer **authoritative sources** over convenience
- Do not resolve conflicts yet — just record them

---

### 3. Map Existing dbt Models
Identify dbt models that are:
- Upstream of the KPI
- Directly computing similar metrics
- Consumed by Finance or exec reporting

For each relevant model, capture:
- Model name
- Grain
- Business purpose (if known)
- Upstream dependencies
- Downstream consumers (dashboards, reports, apps)

---

### 4. Record Model Ownership and Freshness
For each critical table or model, explicitly note:
- Data owner (team or individual)
- Expected freshness / SLA
- Known backfills or delays
- Whether Finance considers it “trusted”

If ownership is unclear, treat that as a risk.

---

### 5. Check for Metric Definition Collisions
Look for:
- Same metric name defined in multiple places
- Slightly different filters or grains
- “Finance” vs “Analytics” versions of the same metric

Do not reconcile yet — just document discrepancies clearly.

Metric ambiguity here is a common source of executive mistrust later.

---

### 6. Validate Grain Alignment
For each table or model:
- Confirm its grain explicitly
- Compare against the locked unit of analysis
- Flag any implicit aggregation or duplication risk

Common SaaS pitfalls:
- Contract‑level data mixed with customer‑level metrics
- Usage events rolled up inconsistently
- Mid‑period contract changes

---

### 7. Assess Data Coverage vs Time Horizon
Check whether data exists for:
- The full lookback window
- The forecast or prediction window (if applicable)

Flag:
- Historical gaps
- Schema changes
- Product launches or pricing changes that affect comparability

---

### 8. Capture Unknowns and Follow‑Ups
Maintain a running list of:
- Tables you don’t understand yet
- Fields with unclear definitions
- Questions for data owners or Finance

These are **expected** — the goal is visibility, not resolution.

---

## Required Output
- `01_data_landscape.md` capturing:
  - Relevant domains
  - Candidate source tables
  - dbt models and lineage
  - Ownership and freshness assumptions
  - Known ambiguities and unknowns

---

## Exit Criteria
You may proceed only if:
- Every primary KPI input has at least one identified authoritative source
- Model grains are documented
- Ownership and freshness expectations are explicit
- Known conflicts or ambiguities are written down

✅ Stage 1 complete. Proceed to `02_data_quality.md`.
