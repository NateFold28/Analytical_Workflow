# Stage 3 — dbt Transformation Semantics

## Purpose
Translate dbt logic into business meaning and identify semantic risk.

## Tools
- Cortex for discovery
- Claude for semantic interpretation

## Steps
1. Pull only relevant model SQL and YAML metadata.
2. Explain each model in plain-language business terms.
3. Document joins and cardinality assumptions.
4. Identify risk patterns:
   - Fan-out joins
   - Late-arriving facts
   - Soft-delete handling
   - Snapshot edge behavior
5. Validate whether model grain aligns to Stage 0 contract.
6. Propose refactors where semantics are ambiguous.

## Required output
- `dbt_model_semantics.md`

## Exit criteria
- Business stakeholders can explain KPI lineage from source to output.
