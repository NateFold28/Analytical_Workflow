# 00_analysis_contract.md
Stage 0 — Intake & Guardrails

---

## Purpose
Turn a vague stakeholder request into an explicit **analysis contract** before any data work begins.

The goal is not documentation — it is **alignment**:
- One decision
- One primary metric
- One unit of analysis
- One time horizon

If these are not locked, downstream analytics, ML, or AI work will drift.

---

## Timebox
One focused working session.

If this cannot be completed in one session, the request is not yet ready.

---

## Inputs
- Raw ask (email, Slack, meeting notes)
- Business context (quarter goals, known risks)
- Known constraints (policy, staffing, tooling)

---

## Primary Tool
LLM (Claude / Copilot / equivalent) for structured reasoning and gap detection.

---

## Analysis Contract Checklist

### 1. Capture the Ask (Verbatim)
- Paste the request exactly as received
- Do **not** paraphrase or clean it up

This preserves original intent and exposes ambiguity.

---

### 2. Identify the Actual Decision
You must be able to complete:

> “After seeing this analysis, someone will decide whether to ___.”

Rules:
- Exactly one decision
- Must result in an action
- Must be something the business can control

If multiple decisions are implied, split the work or stop.

---

### 3. Name the Decision Owner
Explicitly identify:
- Who will make the decision
- How they will consume the output (memo, dashboard, score, alert)

If no single owner exists, this is not yet an analytics or ML problem.

---

### 4. Lock the Primary KPI
Decide on **one** primary KPI and make it unambiguous:

- Exact formula (must be SQL‑expressible)
- Data grain (customer‑month, contract‑month, etc.)
- Directionality (higher vs lower is better)
- Plain‑language business meaning

If the KPI cannot be written clearly, stop here.

---

### 5. Define Secondary Diagnostics (3–5 max)
Identify supporting metrics that explain **why** the primary KPI moves.

Guidelines:
- Diagnostics explain the KPI; they do not replace it
- Each metric should map to a plausible business lever
- Avoid “interesting” metrics with no decision impact

---

### 6. Lock the Time Horizon
Explicitly decide:
- Lookback window
- Forecast or prediction window (if any)
- Any exclusions (onboarding periods, partial billing cycles)

The time horizon must align with how the business recognizes revenue and churn.

---

### 7. Lock the Unit of Analysis
Choose one unit (e.g., customer‑month, account‑quarter) and document:
- Why this unit matches the decision
- Known aggregation risks (e.g., Simpson’s paradox)

Changing the unit later invalidates prior work.

---

### 8. State Hard Constraints
List non‑negotiables, such as:
- Data freshness limits
- Approved data sources only
- Privacy or policy constraints
- Staffing or compute limits
- Required interpretability level (Finance‑safe vs black box)

---

### 9. Explicitly State What Is Out of Scope
Write down what this analysis will **not** attempt to do.

Examples:
- Excluded customer segments
- Metrics that will not be analyzed
- Predictions that will not be made

Out‑of‑scope items are considered closed unless this contract is revised.

---

### 10. Identify Risks and Misuse
Briefly consider:
- How could this analysis be misinterpreted?
- What decisions should **not** be made from it?
- Known data limitations or biases

If you cannot articulate risks, understanding is insufficient.

---

### 11. Agreement and Lock‑In
Before proceeding:
- Decision owner agrees with the KPI, unit, and scope
- Analyst / DS owner agrees the problem is well‑posed
- The contract is committed to Git

No sign‑off → no Stage 1 work.

---

## Required Output
- A committed `00_analysis_contract.md` capturing the above decisions

---

## Exit Criteria
You can proceed only if:
- The decision is singular and explicit
- The primary KPI and grain are unambiguous
- Time horizon and unit of analysis are locked
- Out‑of‑scope items are agreed upon
- Risks are acknowledged

✅ Stage 0 complete. Proceed to `01_data_landscape.md`.
