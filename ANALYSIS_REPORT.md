# 综合数据分析报告
---
Report generated on: 2025-10-26 00:10:37

参见总体摘要： /Users/zhuixiaolv/Downloads/审稿人数据分析版/_SUMMARY_REPORT.md

**复现信息**
SessionInfo: /Users/zhuixiaolv/Downloads/审稿人数据分析版/_SESSION_INFO.txt
随机种子文件: /Users/zhuixiaolv/Downloads/审稿人数据分析版/_SEED.txt

## EWM 排名稳定性 (Spearman)
| pair | spearman |
|:---------------:|:---------------:|
| EWM~Equal | 1.0000000 |
| EWM~PCA | 0.9970588 |
| EWM~ObjectiveOnly | 0.9558824 |
| Equal~PCA | 0.9970588 |
| Equal~ObjectiveOnly | 0.9558824 |
| PCA~ObjectiveOnly | 0.9529412 |

## DV: RT

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/time/shiyanshuju_modified_by_rules_xx.xlsx
Random-effects (used): (1 + Auditory_Factor + Haptic_Factor | Participant_ID)
Transform: boxcox
BoxCox lambda: -0.1
Shift: 0
MC policy: mixed

Marginal R2 = 0.177; Conditional R2 = NA
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 2128.64414 |   3.6766002 | 0.012 | 0.005 | 0.001 | 1.000 |
| Auditory_Factor | 1 |   29.01469 | 104.3094854 | < .001 | 0.782 | 0.655 | 1.000 |
| Haptic_Factor | 1 |   28.07238 |  40.2942356 | < .001 | 0.589 | 0.381 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 2130.63368 |   0.5714864 | 0.634 | 0.001 | 0.000 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 2130.40949 |  16.0917216 | < .001 | 0.022 | 0.012 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 2151.78973 |   8.8495036 | 0.003 | 0.004 | 0.001 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 2131.13305 |   1.0000850 | 0.392 | 0.001 | 0.000 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 0.884 |
| Flashing | 0.871 |
| Transparent | 0.904 |
| Transparent_Flashing | 0.888 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 0.946 |
| Yes | 0.828 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 0.918 |
| Yes | 0.856 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       17 -1362.1 -1265.1 698.03   -1396.1                     
full_ML   23 -1355.0 -1223.7 700.48   -1401.0 4.8959  6     0.5572

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       17 -1316.5 -1219.5 675.23   -1350.5                         
full_ML   23 -1355.0 -1223.7 700.48   -1401.0 50.498  6  3.736e-09 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)  
red       19 -1351.4 -1243.0 694.68   -1389.4                       
full_ML   23 -1355.0 -1223.7 700.48   -1401.0 11.599  4     0.0206 *
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar   AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       20 -1358 -1243.8 698.97     -1398                     
full_ML   23 -1355 -1223.7 700.48     -1401 3.0114  3     0.3899
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor | 32.3% | 29.4% | 35.3% | 1000 |
| Visual_Factor:Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Auditory_Factor:Haptic_Factor | 80.5% | 77.9% | 82.9% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 26.9% | 24.2% | 29.8% | 1000 |

**缺失数据评估**
```
# A tibble: 1 × 4
  statistic    df p.value missing.patterns
      <dbl> <dbl>   <dbl>            <int>
1      42.5    25  0.0160                3
```

**变换概览（Box-Cox 轮廓）**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/RT/RT_boxcox_profile.png)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/RT/RT_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/RT/RT_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/RT/RT_DIAG_resid_hist.png)

## DV: TRUST

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/xinren/subjective_data_xinren_cleaned_IQR.xlsx
Random-effects (used): (1 + Auditory_Factor + Haptic_Factor | Participant_ID)
Transform: boxcox
BoxCox lambda: 1.65
Shift: 0
MC policy: mixed

Marginal R2 = 0.395; Conditional R2 = 0.794
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 370.71338 |  1.9961843 | 0.114 | 0.016 | 0.000 | 1.000 |
| Auditory_Factor | 1 |  28.84920 | 85.5991297 | < .001 | 0.748 | 0.603 | 1.000 |
| Haptic_Factor | 1 |  29.18723 | 70.2413957 | < .001 | 0.706 | 0.544 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 370.70564 |  3.7762361 | 0.011 | 0.030 | 0.004 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 370.72183 |  0.3979268 | 0.755 | 0.003 | 0.000 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 370.97683 | 52.1603047 | < .001 | 0.123 | 0.076 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 370.70451 |  1.1427727 | 0.332 | 0.009 | 0.000 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 5.066 |
| Flashing | 5.107 |
| Transparent | 5.098 |
| Transparent_Flashing | 5.257 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 4.426 |
| Yes | 5.838 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 4.733 |
| Yes | 5.530 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)  
red       17 2065.8 2136.6 -1015.9    2031.8                       
full_ML   23 2062.9 2158.6 -1008.5    2016.9 14.902  6    0.02103 *
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       17 2055.7 2126.5 -1010.9    2021.7                     
full_ML   23 2062.9 2158.6 -1008.5    2016.9 4.7888  6     0.5712

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       19 2108.8 2187.8 -1035.4    2070.8                         
full_ML   23 2062.9 2158.6 -1008.5    2016.9 53.828  4  5.719e-11 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       20 2060.5 2143.7 -1010.2    2020.5                     
full_ML   23 2062.9 2158.6 -1008.5    2016.9 3.5284  3     0.3171
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 91.6% | 89.7% | 93.2% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor | 84.6% | 82.2% | 86.8% | 1000 |
| Visual_Factor:Haptic_Factor | 34.9% | 31.9% | 37.9% | 1000 |
| Auditory_Factor:Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 31.9% | 29.0% | 34.9% | 1000 |

**缺失数据评估**
```
# A tibble: 1 × 4
  statistic    df p.value missing.patterns
      <dbl> <dbl>   <dbl>            <int>
1      69.3    59   0.169                5
```

**变换概览（Box-Cox 轮廓）**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/TRUST/TRUST_boxcox_profile.png)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/TRUST/TRUST_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/TRUST/TRUST_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/TRUST/TRUST_DIAG_resid_hist.png)

## DV: SUS

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/SUS/sus_data_processed.xlsx
Random-effects (used): (1 + Auditory_Factor + Haptic_Factor | Participant_ID)
Transform: boxcox
BoxCox lambda: 1.3
Shift: 0
MC policy: mixed

Marginal R2 = 0.511; Conditional R2 = 0.654
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 365.81087 |   1.989260 | 0.115 | 0.016 | 0.000 | 1.000 |
| Auditory_Factor | 1 |  27.31524 | 191.145239 | < .001 | 0.875 | 0.795 | 1.000 |
| Haptic_Factor | 1 |  29.61515 | 103.881750 | < .001 | 0.778 | 0.650 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 365.81087 |   2.927853 | 0.034 | 0.023 | 0.001 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 365.69187 |   1.206245 | 0.307 | 0.010 | 0.000 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 375.23725 |  24.130128 | < .001 | 0.060 | 0.027 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 365.69187 |   1.214444 | 0.304 | 0.010 | 0.000 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 65.353 |
| Flashing | 66.439 |
| Transparent | 63.396 |
| Transparent_Flashing | 66.664 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 54.736 |
| Yes | 76.190 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 58.155 |
| Yes | 72.771 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)  
red       17 4830.4 4900.9 -2398.2    4796.4                       
full_ML   23 4829.7 4925.1 -2391.9    4783.7 12.707  6    0.04793 *
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       17 4825.0 4895.5 -2395.5    4791.0                     
full_ML   23 4829.7 4925.1 -2391.9    4783.7 7.2716  6     0.2965

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       19 4849.4 4928.2 -2405.7    4811.4                         
full_ML   23 4829.7 4925.1 -2391.9    4783.7 27.655  4  1.465e-05 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       20 4827.5 4910.4 -2393.7    4787.5                     
full_ML   23 4829.7 4925.1 -2391.9    4783.7 3.7532  3     0.2894
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 89.8% | 87.8% | 91.6% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor | 80.9% | 78.3% | 83.3% | 1000 |
| Visual_Factor:Haptic_Factor | 52.1% | 49.0% | 55.2% | 1000 |
| Auditory_Factor:Haptic_Factor | 99.6% | 99.0% | 99.9% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 34.5% | 31.6% | 37.5% | 1000 |

**缺失数据评估**
```
# A tibble: 1 × 4
  statistic    df p.value missing.patterns
      <dbl> <dbl>   <dbl>            <int>
1      102.    67 0.00401                6
```

**变换概览（Box-Cox 轮廓）**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/SUS/SUS_boxcox_profile.png)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/SUS/SUS_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/SUS/SUS_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/SUS/SUS_DIAG_resid_hist.png)

## DV: DALI

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/dali/processed_dali_data_for_lmm.csv
Random-effects (used): (1 + Auditory_Factor + Haptic_Factor | Participant_ID)
Transform: boxcox
BoxCox lambda: 0.9
Shift: 0
MC policy: mixed

Marginal R2 = 0.215; Conditional R2 = 0.682
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 377 |  0.9747120 | 0.405 | 0.008 | 0.000 | 1.000 |
| Auditory_Factor | 1 |  29 | 49.4266049 | < .001 | 0.630 | 0.438 | 1.000 |
| Haptic_Factor | 1 |  29 | 79.9961453 | < .001 | 0.734 | 0.583 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 377 |  1.6938592 | 0.168 | 0.013 | 0.000 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 377 |  0.3572814 | 0.784 | 0.003 | 0.000 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 377 | 29.5891430 | < .001 | 0.073 | 0.036 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 377 |  0.3689891 | 0.775 | 0.003 | 0.000 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 17.634 |
| Flashing | 17.113 |
| Transparent | 16.888 |
| Transparent_Flashing | 17.126 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 19.378 |
| Yes | 15.002 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 18.840 |
| Yes | 15.540 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L) Chisq Df Pr(>Chisq)
red       17 2463.8 2534.7 -1214.9    2429.8                    
full_ML   23 2469.4 2565.4 -1211.7    2423.4  6.35  6     0.3851

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       17 2459.7 2530.6 -1212.8    2425.7                     
full_ML   23 2469.4 2565.4 -1211.7    2423.4 2.2475  6     0.8956

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       19 2491.9 2571.2 -1227.0    2453.9                         
full_ML   23 2469.4 2565.4 -1211.7    2423.4 30.528  4  3.821e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor + Haptic_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       20 2464.6 2548.0 -1212.3    2424.6                     
full_ML   23 2469.4 2565.4 -1211.7    2423.4 1.1435  3     0.7666
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 55.6% | 52.5% | 58.7% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor | 44.8% | 41.7% | 47.9% | 1000 |
| Visual_Factor:Haptic_Factor | 16.3% | 14.1% | 18.7% | 1000 |
| Auditory_Factor:Haptic_Factor | 99.9% | 99.4% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 14.3% | 12.2% | 16.6% | 1000 |

**缺失数据评估**
```
MCAR 不可评估：变量数不足、样本数不足、零方差或缺失模式不足。
```

**变换概览（Box-Cox 轮廓）**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DALI/DALI_boxcox_profile.png)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DALI/DALI_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DALI/DALI_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DALI/DALI_DIAG_resid_hist.png)

## DV: NDRT

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/eyes/eye19_tracking_data_for_lmm.csv
Random-effects (used): (1 + Auditory_Factor | Participant_ID)
Transform: elogit
BoxCox lambda: NA
Shift: 0
MC policy: mixed

Marginal R2 = 0.180; Conditional R2 = 0.530
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 406 |  1.456412 | 0.226 | 0.011 | 0.000 | 1.000 |
| Auditory_Factor | 1 |  29 | 48.958939 | < .001 | 0.628 | 0.435 | 1.000 |
| Haptic_Factor | 1 | 406 | 19.790504 | < .001 | 0.046 | 0.019 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 406 |  5.234322 | 0.001 | 0.037 | 0.009 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 406 |  1.855202 | 0.137 | 0.014 | 0.000 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 406 | 21.595522 | < .001 | 0.051 | 0.021 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 406 |  5.157348 | 0.002 | 0.037 | 0.009 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 0.953 |
| Flashing | 0.954 |
| Transparent | 0.949 |
| Transparent_Flashing | 0.945 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 0.937 |
| Yes | 0.963 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 0.944 |
| Yes | 0.956 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       14 944.18 1002.6 -458.09    916.18                         
full_ML   20 925.10 1008.6 -442.55    885.10 31.072  6  2.456e-05 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC     BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)   
red       14 934.32  992.75 -453.16    906.32                        
full_ML   20 925.10 1008.58 -442.55    885.10 21.218  6   0.001676 **
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar   AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       16 953.8 1020.6 -460.90     921.8                         
full_ML   20 925.1 1008.6 -442.55     885.1 36.695  4  2.082e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 + Auditory_Factor | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)   
red       17 934.81 1005.8 -450.41    900.81                        
full_ML   20 925.10 1008.6 -442.55    885.10 15.708  3   0.001301 **
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 99.9% | 99.4% | 100.0% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 99.2% | 98.4% | 99.7% | 1000 |
| Visual_Factor:Auditory_Factor | 99.6% | 99.0% | 99.9% | 1000 |
| Visual_Factor:Haptic_Factor | 96.6% | 95.3% | 97.6% | 1000 |
| Auditory_Factor:Haptic_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 92.9% | 91.1% | 94.4% | 1000 |

**缺失数据评估**
```
MCAR 不可评估：变量数不足、样本数不足、零方差或缺失模式不足。
```

**变换概览（Box-Cox 轮廓）**
(图片缺失)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/NDRT/NDRT_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/NDRT/NDRT_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/NDRT/NDRT_DIAG_resid_hist.png)

## DV: DURVISIT

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/eyes/eye19_tracking_data_for_lmm.csv
Random-effects (used): (1 | Participant_ID)
Transform: log
BoxCox lambda: NA
Shift: 0
MC policy: mixed

Marginal R2 = 0.217; Conditional R2 = 0.397
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 372.0299 | 15.13319522 | < .001 | 0.109 | 0.060 | 1.000 |
| Auditory_Factor | 1 | 374.7957 | 50.29527027 | < .001 | 0.118 | 0.072 | 1.000 |
| Haptic_Factor | 1 | 372.7767 |  3.85895146 | 0.050 | 0.010 | 0.000 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 372.9720 | 10.48509824 | < .001 | 0.078 | 0.035 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 372.9736 |  1.28955184 | 0.278 | 0.010 | 0.000 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 373.9418 |  0.01266848 | 0.910 | 0.000 | 0.000 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 373.0362 |  1.60142986 | 0.189 | 0.013 | 0.000 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 288.384 |
| Flashing | 341.041 |
| Transparent | 310.112 |
| Transparent_Flashing | 486.957 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 428.889 |
| Yes | 284.358 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 374.582 |
| Yes | 338.665 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       12 707.53 755.90 -341.77    683.53                         
full_ML   18 683.70 756.26 -323.85    647.70 35.827  6  2.978e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar   AIC    BIC  logLik -2*log(L) Chisq Df Pr(>Chisq)
red       12 681.2 729.57 -328.60     657.2                    
full_ML   18 683.7 756.26 -323.85     647.7 9.497  6     0.1475

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L) Chisq Df Pr(>Chisq)
red       14 680.68 737.11 -326.34    652.68                    
full_ML   18 683.70 756.26 -323.85    647.70 4.978  4     0.2896
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar    AIC    BIC  logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       15 682.67 743.13 -326.33    652.67                     
full_ML   18 683.70 756.26 -323.85    647.70 4.9634  3     0.1745
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 59.5% | 56.4% | 62.6% | 1000 |
| Visual_Factor:Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Visual_Factor:Haptic_Factor | 69.3% | 66.3% | 72.1% | 1000 |
| Auditory_Factor:Haptic_Factor | 45.7% | 42.6% | 48.8% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 50.5% | 47.4% | 53.6% | 1000 |

**缺失数据评估**
```
# A tibble: 1 × 4
  statistic    df p.value missing.patterns
      <dbl> <dbl>   <dbl>            <int>
1      189.   176   0.239               16
```

**变换概览（Box-Cox 轮廓）**
(图片缺失)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DURVISIT/DURVISIT_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DURVISIT/DURVISIT_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/DURVISIT/DURVISIT_DIAG_resid_hist.png)

## DV: PUPIL

**模型与策略**

Data file: /Users/zhuixiaolv/Downloads/审稿人数据分析版/shujufenxi/eyes/eye19_tracking_data_for_lmm.csv
Random-effects (used): (1 | Participant_ID)
Transform: log
BoxCox lambda: NA
Shift: 0
MC policy: mixed

Marginal R2 = 0.069; Conditional R2 = 0.717
MC Policy: Policy: Tukey for multi-level factors; Holm for 2x2 simple-effects families.

**ANOVA (Type III)**
| term | df | DenDF | statistic | p.value | Eta2_partial | CI_low | CI_high |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 3 | 371.0807 | 12.6524199 | < .001 | 0.093 | 0.047 | 1.000 |
| Auditory_Factor | 1 | 371.5536 | 29.2809386 | < .001 | 0.073 | 0.036 | 1.000 |
| Haptic_Factor | 1 | 371.1587 |  1.0612441 | 0.304 | 0.003 | 0.000 | 1.000 |
| Visual_Factor:Auditory_Factor | 3 | 371.2498 |  7.4495042 | < .001 | 0.057 | 0.020 | 1.000 |
| Visual_Factor:Haptic_Factor | 3 | 371.1503 |  1.1208329 | 0.340 | 0.009 | 0.000 | 1.000 |
| Auditory_Factor:Haptic_Factor | 1 | 371.4242 |  0.3909793 | 0.532 | 0.001 | 0.000 | 1.000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 3 | 371.1848 |  0.4308120 | 0.731 | 0.003 | 0.000 | 1.000 |

**EMMs (回变换均值)**
视觉主效应: 平均值
| Visual_Factor | Mean |
|:---------------:|:---------------:|
| Baseline | 3.383 |
| Flashing | 3.403 |
| Transparent | 3.542 |
| Transparent_Flashing | 3.538 |
听觉主效应: 平均值
| Auditory_Factor | Mean |
|:---------------:|:---------------:|
| No | 3.532 |
| Yes | 3.401 |
触觉主效应: 平均值
| Haptic_Factor | Mean |
|:---------------:|:---------------:|
| No | 3.479 |
| Yes | 3.454 |

**Likelihood Ratio Tests (LRT)**
二阶交互 LRT:
```
=== LRT VA ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)    
red       12 -907.83 -859.46 465.91   -931.83                         
full_ML   18 -919.66 -847.10 477.83   -955.66 23.831  6  0.0005611 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=== LRT VH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Auditory_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       12 -926.90 -878.53 475.45   -950.90                     
full_ML   18 -919.66 -847.10 477.83   -955.66 4.7609  6     0.5748

=== LRT AH ===
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       14 -925.89 -869.46 476.95   -953.89                     
full_ML   18 -919.66 -847.10 477.83   -955.66 1.7627  4     0.7793
```
三阶交互 LRT:
```
Data: data
Models:
red: DV_trans ~ Visual_Factor + Auditory_Factor + Haptic_Factor + (1 | Participant_ID) + Visual_Factor:Auditory_Factor + Visual_Factor:Haptic_Factor + Auditory_Factor:Haptic_Factor
full_ML: f2
        npar     AIC     BIC logLik -2*log(L)  Chisq Df Pr(>Chisq)
red       15 -924.31 -863.85 477.16   -954.31                     
full_ML   18 -919.66 -847.10 477.83   -955.66 1.3424  3     0.7191
```

**功效分析（模拟）**
| term | power | lower | upper | nsim |
|:---------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| Visual_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Auditory_Factor | 100.0% | 99.6% | 100.0% | 1000 |
| Haptic_Factor | 21.0% | 18.5% | 23.7% | 1000 |
| Visual_Factor:Auditory_Factor | 99.0% | 98.2% | 99.5% | 1000 |
| Visual_Factor:Haptic_Factor | 39.5% | 36.5% | 42.6% | 1000 |
| Auditory_Factor:Haptic_Factor | 19.7% | 17.3% | 22.3% | 1000 |
| Visual_Factor:Auditory_Factor:Haptic_Factor | 17.6% | 15.3% | 20.1% | 1000 |

**缺失数据评估**
```
# A tibble: 1 × 4
  statistic    df p.value missing.patterns
      <dbl> <dbl>   <dbl>            <int>
1      209.   176  0.0448               16
```

**变换概览（Box-Cox 轮廓）**
(图片缺失)

**模型诊断图**
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/PUPIL/PUPIL_DIAG_qq.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/PUPIL/PUPIL_DIAG_rvf.png)
![](/Users/zhuixiaolv/Downloads/审稿人数据分析版/PUPIL/PUPIL_DIAG_resid_hist.png)

