# Stage 0 — Intake & Guardrails

## Purpose
Convert a vague executive ask into an explicit analysis contract before any data or modeling work starts.

## Timebox
15–30 minutes.

## Inputs
- Raw ask (email/Slack/meeting notes)
- Business context and constraints

## Primary tool
- Claude (Desktop) for structured drafting

## Steps
1. Copy the ask verbatim into your working notes.
2. Write the target decision the analysis must support.
3. Define one primary KPI with exact formula and grain.
4. Define secondary diagnostics (max 3–5) that explain KPI movement.
5. Lock time horizon (lookback + forecast window).
6. Lock unit of analysis (customer-month, contract-month, account-quarter, etc.).
7. List hard constraints (data freshness, policy, staffing, budget).
8. Write explicit out-of-scope bullets.
9. Add approval section and get stakeholder sign-off.
10. Commit the contract to Git before moving to Stage 1.

## Required output
- `analysis_contract.md` (or run-specific variant)

## Exit criteria
- KPI and grain are unambiguous.
- Decision owner is identified.
- Out-of-scope list is accepted.
