# Stage 8 — Productionization & MLOps

## Purpose
Deploy a lean but reliable analytics/ML pipeline.

## Core stack
- Snowflake
- dbt
- Snowpark
- Git

## Production checklist
1. Version feature table SQL and model code in Git.
2. Reference immutable training snapshot/date range.
3. Schedule feature refresh and inference runs.
4. Log inference outputs and model version to monitoring table.
5. Track performance metrics against alert thresholds.
6. Define rollback and model retirement procedure.

## Required output
- `08_production_notes.md` (run-specific deployment notes)

## Exit criteria
- Pipeline runs on schedule with observable health and rollback path.
