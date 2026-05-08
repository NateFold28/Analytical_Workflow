# Stage 2 — Data Quality & Fitness

## Purpose
Prove the selected data is fit for the specific business decision.

## Primary tool
- Cortex Code

## Mandatory checks
1. **Row count trend** by day/week/month for anomalies.
2. **Null-rate trend** on keys, timestamps, and target fields.
3. **Uniqueness test** at expected grain.
4. **Cross-system reconciliation** for overlapping finance totals.
5. **Latency check** versus decision cadence.

## Steps
1. Write each check as a repeatable query with date filters.
2. Run checks for recent and historical windows.
3. Quantify deltas (not just pass/fail statements).
4. Flag blocking issues and define mitigation.
5. Record accepted limitations and business impact.

## Required output
- `data_quality_findings.md`

## Exit criteria
- Blocking defects are either fixed or formally accepted with impact notes.
