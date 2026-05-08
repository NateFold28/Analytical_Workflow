# Stage 4 — Feature Discovery & Feature Contracts

## Purpose
Define reproducible, time-aware feature tables before any model training.

## Non-negotiable rules
1. One row per entity per time unit.
2. No lookahead bias.
3. No hidden business-logic leakage from target fields.
4. Fully rebuildable from versioned SQL.

## Build sequence
1. Create target entity-time index table first.
2. Join lagged and contemporaneous signals with explicit effective dates.
3. Add data-quality assertions for primary/foreign keys.
4. Add feature freshness metadata fields.
5. Publish feature dictionary with definitions and owners.

## Required outputs
- `fct_customer_finance_monthly.sql`
- `fct_revenue_risk_signals.sql`
- `feature_dictionary.md`

## Exit criteria
- Feature generation is deterministic and replayable for any historical cutoff date.
