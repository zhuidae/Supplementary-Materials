# Exclusion Rules Applied

This document lists the “exclusion/clamping” rules actually executed in the current analysis, with rule name, threshold, applicable DVs, and execution order. If a DV is marked “none” here, it means we only perform non-exclusion transformations (e.g., Box–Cox, polarity normalization) for that DV.

## Global Notes
- Core exclusion rule: Winsorization (quantile clamping), used to suppress the influence of extreme values on downstream statistics and models.
- Non-exclusion steps (not counted in this list):
  - Box–Cox transform with positive shifting if necessary (ensure positivity). This is a transform; it does not delete rows.
  - Indicator polarity normalization (benefit/cost 0–1 scaling) for EWM and figures. This does not delete rows.
  - Missingness handling follows ML/LMM under a MAR interpretation (when MCAR is rejected). This is modelling, not a fixed threshold deletion rule.

## Rule Summary
- Rule name: `winsorize`
- Threshold: clamp to quantile interval `[0.05, 0.95]`
- Applicable DVs: `RT, TRUST, SUS, DALI`
- Execution order: preprocessing stage, before transformations/modelling (and before Box–Cox if configured for the DV)
- Source of truth: `Supplementary Materials/01_preprocessing/exclusion_rules.csv`

### Itemized
1) `winsorize` → threshold: `[0.05, 0.95]` → DV: `RT` → order: preprocessing first step (winsorize before transform/model)
2) `winsorize` → threshold: `[0.05, 0.95]` → DV: `TRUST` → order: preprocessing first step
3) `winsorize` → threshold: `[0.05, 0.95]` → DV: `SUS` → order: preprocessing first step
4) `winsorize` → threshold: `[0.05, 0.95]` → DV: `DALI` → order: preprocessing first step

## Remarks
- No fixed-threshold exclusion rules are applied to `NDRT, DURVISIT, PUPIL` in the current version. If future retention thresholds (participant/condition level) are introduced, please record rule name, threshold, applicable DVs, and execution order here.
- The MCAR→MAR interpretation is statistical inference: when MCAR is rejected, we treat missingness as MAR and rely on ML/LMM. We do not introduce extra row deletions, so this is not counted as an “exclusion rule”.
