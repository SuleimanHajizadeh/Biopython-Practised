---
title: Tukey HSD Post-Hoc Test
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - biostatistics
  - multiple-comparisons
  - post-hoc
  - fwer
sources:
  - "[[biostatistics/ANOVA_Drug_Enzyme_Activity_Project.ipynb]]"
  - "[[biostatistics/Intermediate_ANOVA_Tutorial.ipynb]]"
  - "[[biostatistics/Extended_ANOVA_Beginner_Project.ipynb]]"
---

# Tukey's Honestly Significant Difference (HSD)

**Tukey's HSD** is a single-step multiple comparison procedure used in conjunction with ANOVA to identify which specific pairs of group means differ significantly while controlling the **Family-Wise Error Rate (FWER)**.

---

## 1. The Problem of Multiplicity

Performing multiple pairwise $t$-tests across $k$ groups results in $\binom{k}{2}$ comparisons. The cumulative probability of making at least one Type I error (false positive) is:

$$\alpha_{cumulative} = 1 - (1 - \alpha)^m$$

For $k = 4$ groups ($m = 6$ comparisons), $\alpha_{cumulative} \approx 26.5\%$. Tukey's HSD calculates a studentized range distribution ($q$) threshold that keeps total error at $\alpha = 0.05$.

---

## 2. Python Implementation

```python
from statsmodels.stats.multicomp import pairwise_tukeyhsd

tukey = pairwise_tukeyhsd(
    endog=df["Enzyme_Activity"],
    groups=df["Dose_Group"],
    alpha=0.05
)

print(tukey.summary())
```

Example Output Interpretation:
```text
=====================================================
group1   group2   meandiff  p-adj   lower   upper  reject
-----------------------------------------------------
Control  High     18.45     0.001   12.10   24.80   True
Control  Low       3.12     0.482   -3.23    9.47  False
Low      High     15.33     0.001    8.98   21.68   True
=====================================================
```
- `reject = True` indicates statistically significant difference after adjustment.

---

## Connections & See Also
- [[One-Way-ANOVA]]: The precursor omnibus test.
- [[statsmodels]]: Library implementation of `pairwise_tukeyhsd`.
