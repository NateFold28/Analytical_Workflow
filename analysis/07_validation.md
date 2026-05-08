# Stage 7 — Validation, Robustness & Risk

## Purpose
Confirm model reliability before any production decision support.

## Must-have tests
1. Temporal cross-validation
2. Backtesting against known outcomes
3. Sensitivity testing on key assumptions
4. Stress scenario stability checks
5. Explainability review for non-technical stakeholders

## Steps
1. Run validation battery and store all metrics by fold/window.
2. Identify weakest segments and failure modes.
3. Set acceptance thresholds and compare actuals.
4. Record go/no-go decision with rationale.

## Required output
- `model_validation_report.md`

## Exit criteria
- Model passes thresholds; otherwise stop and iterate.
