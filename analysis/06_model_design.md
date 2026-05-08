# Stage 6 — Model Selection & Baselines

## Purpose
Choose model families through disciplined baseline-first evaluation.

## Tools
- Claude for design framing
- Snowpark/Python for implementation

## Steps
1. Define baseline(s): naive, rules-based, and simple statistical model.
2. Select candidate model classes aligned to business constraints.
3. Define business-relevant metrics (for example: MAE on dollars, directional accuracy, calibration).
4. Train and evaluate all candidates on identical temporal splits.
5. Compare lift over baseline and operational complexity.
6. Document recommended model + fallback approach.

## Required outputs
- `model_design.md`
- Baseline performance table

## Exit criteria
- Chosen model outperforms baseline materially and is explainable for executives.
