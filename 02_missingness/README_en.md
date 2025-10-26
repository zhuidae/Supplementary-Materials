# Missingness and Retention (02_missingness) README

This folder compiles missingness and retention products across all indicators (DVs):
- trial_counts_by_condition_all_DVs.csv: trial counts and retention aggregated by condition (all DVs)
- participant_retention_all_DVs.csv: participant-level retention distribution (all DVs)
- missingness_overview.csv: per-DV totals, retention rate, participants count, and trial-count quantiles
- LittleMCAR_summary.csv: Little’s MCAR test summary per DV (statistics/df/p-value when assessable)

## How It Is Computed
- Condition-level trial counts: for each DV’s `*_trial_counts_by_condition.csv`, build a condition label (Visual:Auditory:Haptic), then aggregate across participants: `n_total = Σn`, `n_valid = Σhave`, and `n_excluded = n_total - n_valid`; finally bind rows across DVs.
- Participant retention distribution: for each DV’s `*_participant_retention.csv`, extract `participant_id, valid_trials, total_trials`, compute `excluded_trials = total_trials - valid_trials` and `retention_percent = 100 × valid / total`, then bind rows across DVs.
- Missingness overview: per DV, summarise `total_trials, valid_trials, excluded_trials, retention_rate`; for the participant trial-count distribution, report median and quartiles `q1, q3`.
- MCAR testing: parse `*_LittleMCAR.txt`. If the text indicates “not assessable” (e.g., too few variables, insufficient sample size, zero variance, or missingness patterns too limited), record `Not-evaluable`; otherwise, extract `statistic, df, p.value` and determine the decision.

## How To Interpret
- Higher `retention_rate` indicates fewer missing values; `n_excluded` shows the magnitude of missingness.
- Participant-level `retention_percent` helps detect individual data quality differences (e.g., extreme missingness).
- Condition-level counts reveal whether certain experimental conditions carry systematic missingness.

## MCAR → MAR Policy
- We use Little’s MCAR test with α = 0.05. Decision rule:
  - If `p >= 0.05`: do not reject MCAR (`MCAR_not_rejected`). Treat as approximately MCAR.
  - If `p < 0.05`: reject MCAR (`MCAR_rejected`). Typically explain as MAR and handle by ML/LMM in modelling.
- For `Not-evaluable` DVs: the MCAR test cannot be assessed due to limitations (variables, sample size, variance, or missingness patterns). We keep the data as-is and rely on robust modelling; no ad hoc deletions are introduced.

## Reproduction Entry
- Working directory: `/Users/zhuixiaolv/Downloads/审稿人数据分析版/数据分析3.0`
- Command: `Rscript build_missingness_summaries.R`
- Dependencies: `dplyr, readr, stringr, purrr` (the script reads source files from `Supplementary Materials/03_models/<DV>`)
- Expected inputs under each DV folder:
  - `*_trial_counts_by_condition.csv`
  - `*_participant_retention.csv`
  - `*_LittleMCAR.txt`
- Output location: `/Users/zhuixiaolv/Downloads/审稿人数据分析版/Supplementary Materials/02_missingness`

## Column Definitions (Quick Guide)
- `trial_counts_by_condition_all_DVs.csv`: `DV, condition, n_total, n_valid, n_excluded`
- `participant_retention_all_DVs.csv`: `DV, participant_id, retention_percent, valid_trials, excluded_trials`
- `missingness_overview.csv`: `DV, total_trials, valid_trials, excluded_trials, retention_rate, participants_n, median_trials_per_participant, q1, q3`
- `LittleMCAR_summary.csv`: `DV, test_statistic, df, p_value, decision`
