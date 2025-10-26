# 缺失与保留（02_missingness）README

本目录汇总各指标（DV）的缺失与保留情况，包括：
- trial_counts_by_condition_all_DVs.csv：按条件的试次数与保留（所有DV汇总）
- participant_retention_all_DVs.csv：参与者层面的保留率分布（所有DV汇总）
- missingness_overview.csv：每个DV的总试次数、保留率、参与者数与试次数分位数
- LittleMCAR_summary.csv：各DV的 Little’s MCAR 检验结果（可评估则给出统计量/df/p值）

## 怎么统计的
- 条件试次数统计：对每个 DV 的 `*_trial_counts_by_condition.csv`，先构造条件标签（Visual:Auditory:Haptic），再按条件汇总 `n_total = Σn`，`n_valid = Σhave`，并得到 `n_excluded = n_total - n_valid`；随后合并到跨DV汇总表。
- 参与者保留分布：对每个 DV 的 `*_participant_retention.csv`，提取 `participant_id, valid_trials, total_trials`，计算 `excluded_trials = total_trials - valid_trials` 与 `retention_percent = 100×valid/total`，并汇总到跨DV表。
- 缺失总览：基于每个 DV 的两张表，汇总 `total_trials, valid_trials, excluded_trials, retention_rate`；参与者试次数的分布以中位数（median）和四分位 `q1, q3` 描述。
- MCAR 检验：解析 `*_LittleMCAR.txt`。若文本提示“不可评估”（变量数不足、样本过少、零方差或缺失模式不足），则记为 `Not-evaluable`；否则提取 `statistic, df, p.value` 并据 p 值给出决策。

## 怎么解读
- `retention_rate` 越高，说明缺失越少；`n_excluded` 反映缺失的规模。
- 参与者层面的 `retention_percent` 可帮助识别个体数据质量差异（如极端缺失）。
- 条件维度的试次数与保留可以检视是否存在某些实验条件下的系统性缺失。

## MCAR → MAR 口径
- 使用 Little’s MCAR 检验（α=0.05）。规则：
  - 若 `p >= 0.05`：不拒绝 MCAR（`MCAR_not_rejected`），可近似视为 MCAR。
  - 若 `p < 0.05`：拒绝 MCAR（`MCAR_rejected`），通常按 MAR 解释（在后续模型中依赖最大似然等方法处理缺失）。
- 对 `Not-evaluable` 的 DV：由于变量数/样本量/方差/缺失模式等限制无法评估 MCAR，保留为不可评估状态，分析与解释按稳健性原则（默认不做额外删减）。

## 复现入口
- 运行目录：`/Users/zhuixiaolv/Downloads/审稿人数据分析版/数据分析3.0`
- 命令：`Rscript build_missingness_summaries.R`
- 依赖：`dplyr, readr, stringr, purrr`（脚本内自动从 `Supplementary Materials/03_models/<DV>` 读取源文件）
- 输入期望：每个 DV 目录下存在：
  - `*_trial_counts_by_condition.csv`
  - `*_participant_retention.csv`
  - `*_LittleMCAR.txt`
- 输出位置：`/Users/zhuixiaolv/Downloads/审稿人数据分析版/Supplementary Materials/02_missingness`

## 列定义（简表）
- `trial_counts_by_condition_all_DVs.csv`：`DV, condition, n_total, n_valid, n_excluded`
- `participant_retention_all_DVs.csv`：`DV, participant_id, retention_percent, valid_trials, excluded_trials`
- `missingness_overview.csv`：`DV, total_trials, valid_trials, excluded_trials, retention_rate, participants_n, median_trials_per_participant, q1, q3`
- `LittleMCAR_summary.csv`：`DV, test_statistic, df, p_value, decision`
