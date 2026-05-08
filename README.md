# Analytical Workflow Operating System

This repository is the canonical, versioned operating system for repeatable analytics + ML delivery.

## Where to house this folder

Keep this workflow in a **dedicated Git repository** (this repo), separate from project-specific dbt, ML, or BI repos. Project repos should reference these standards; they should not redefine them.

## Canonical modular structure

- `analysis/00_analysis_contract.md`
- `analysis/01_data_landscape.md`
- `analysis/02_data_quality.md`
- `analysis/03_dbt_semantics.md`
- `analysis/04_features/feature_table_design_standard.md`
- `analysis/05_eda.md`
- `analysis/06_model_design.md`
- `analysis/07_validation.md`
- `analysis/08_production_notes.md`
- `analysis/09_exec_narrative.md`
- `analysis/10_interpretation.md`
- `analysis/templates/*`

## How to use

1. Start every request in `analysis/00_analysis_contract.md`.
2. Execute stages `01` through `10` in order.
3. Store run-specific artifacts under `/analysis/` using the stage templates.
4. Treat each stage file as the source of truth for prompts, quality bars, and sign-off criteria.

## Versioning

Track workflow changes through Git commits and tags (for example: `os-v1.0`, `os-v1.1`).
