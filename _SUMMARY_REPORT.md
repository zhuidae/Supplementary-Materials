# Analysis Pipeline: Summary Report
---
Report generated on: 2025-10-26 19:05:23.097727

## 1. Linear Mixed-Effects Model (LMM) Specifications

* **RT**: Final model included random effects: `(1 + Auditory_Factor + Haptic_Factor | Participant_ID)`
* **TRUST**: Final model included random effects: `(1 + Auditory_Factor + Haptic_Factor | Participant_ID)`
* **SUS**: Final model included random effects: `(1 + Auditory_Factor + Haptic_Factor | Participant_ID)`
* **DALI**: Final model included random effects: `(1 + Auditory_Factor + Haptic_Factor | Participant_ID)`
* **NDRT**: Final model included random effects: `(1 + Auditory_Factor | Participant_ID)`
* **DURVISIT**: Final model included random effects: `(1 | Participant_ID)`
* **PUPIL**: Final model included random effects: `(1 | Participant_ID)`

## 2. Missing Data Assessment

* **RT**: Little's MCAR test p-value = 0.0160 **(Warning: p < .05, data may not be Missing Completely at Random)**
* **TRUST**: Little's MCAR test p-value = 0.1687 (p >= .05, assumption of MCAR is met)
* **SUS**: Little's MCAR test p-value = 0.0040 **(Warning: p < .05, data may not be Missing Completely at Random)**
* **DALI**: Little's MCAR test was not run (e.g., no missing data or package unavailable).
* **NDRT**: Little's MCAR test was not run (e.g., no missing data or package unavailable).
* **DURVISIT**: Little's MCAR test p-value = 0.2395 (p >= .05, assumption of MCAR is met)
* **PUPIL**: Little's MCAR test p-value = 0.0448 **(Warning: p < .05, data may not be Missing Completely at Random)**

## 3. Post-Hoc Power Analysis Summary

* **RT**: Visual_Factor (Power=100.0%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=100.0%); Visual_Factor:Auditory_Factor (Power=32.3%); Visual_Factor:Haptic_Factor (Power=100.0%); Auditory_Factor:Haptic_Factor (Power=80.5%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=26.9%)
* **TRUST**: Visual_Factor (Power=91.6%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=100.0%); Visual_Factor:Auditory_Factor (Power=84.6%); Visual_Factor:Haptic_Factor (Power=34.9%); Auditory_Factor:Haptic_Factor (Power=100.0%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=31.9%)
* **SUS**: Visual_Factor (Power=89.8%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=100.0%); Visual_Factor:Auditory_Factor (Power=80.9%); Visual_Factor:Haptic_Factor (Power=52.1%); Auditory_Factor:Haptic_Factor (Power=99.6%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=34.5%)
* **DALI**: Visual_Factor (Power=55.6%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=100.0%); Visual_Factor:Auditory_Factor (Power=44.8%); Visual_Factor:Haptic_Factor (Power=16.3%); Auditory_Factor:Haptic_Factor (Power=99.9%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=14.3%)
* **NDRT**: Visual_Factor (Power=99.9%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=99.2%); Visual_Factor:Auditory_Factor (Power=99.6%); Visual_Factor:Haptic_Factor (Power=96.6%); Auditory_Factor:Haptic_Factor (Power=100.0%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=92.9%)
* **DURVISIT**: Visual_Factor (Power=100.0%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=59.5%); Visual_Factor:Auditory_Factor (Power=100.0%); Visual_Factor:Haptic_Factor (Power=69.3%); Auditory_Factor:Haptic_Factor (Power=45.7%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=50.5%)
* **PUPIL**: Visual_Factor (Power=100.0%); Auditory_Factor (Power=100.0%); Haptic_Factor (Power=21.0%); Visual_Factor:Auditory_Factor (Power=99.0%); Visual_Factor:Haptic_Factor (Power=39.5%); Auditory_Factor:Haptic_Factor (Power=19.7%); Visual_Factor:Auditory_Factor:Haptic_Factor (Power=17.6%)

## 4. EWM Ranking Sensitivity Analysis
Spearman rank correlation (Rho) between different weighting methods.

| Comparison                 | Spearman's Rho |
|:---------------------------|:---------------|
| EWM~Equal                  | 0.9147         |
| EWM~PCA                    | 0.9324         |
| EWM~ObjectiveOnly          | 0.6441         |
| Equal~PCA                  | 0.9971         |
| Equal~ObjectiveOnly        | 0.7382         |
| PCA~ObjectiveOnly          | 0.7294         |
