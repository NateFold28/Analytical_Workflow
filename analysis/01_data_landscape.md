# Stage 1 — Data Reconnaissance

## Purpose
Map what data exists and which models define critical business metrics.

## Primary tool
- Cortex Code

## Steps
1. Enumerate domain schemas (finance/revenue/billing/CRM/product).
2. List candidate source tables for each KPI component.
3. Identify dbt models upstream/downstream of KPI outputs.
4. Record each model's grain, freshness expectation, and owner.
5. Document naming collisions or conflicting metric definitions.
6. Capture unknowns requiring data-owner follow-up.

## Required output
- `data_landscape.md`

## Exit criteria
- Every KPI input has a known authoritative table/model.
- Model ownership and freshness assumptions are documented.
