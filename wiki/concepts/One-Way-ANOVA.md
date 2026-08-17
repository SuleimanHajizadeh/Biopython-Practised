---
title: One-Way ANOVA
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - biostatistics
  - hypothesis-testing
  - variance
  - f-statistic
sources:
  - "[[biostatistics/ANOVA_Drug_Enzyme_Activity_Project.ipynb]]"
  - "[[biostatistics/Extended_ANOVA_Beginner_Project.ipynb]]"
  - "[[biostatistics/Intermediate_ANOVA_Tutorial.ipynb]]"
---

# One-Way Analysis of Variance (ANOVA)

**One-Way ANOVA** is an omnibus hypothesis test used to determine whether there are statistically significant differences among the means of three or more independent (unrelated) groups.

---

## 1. Mathematical Formulation

ANOVA partitions the total sum of squares ($SS_{Total}$) into between-group variance ($SS_{Between}$) and within-group variance ($SS_{Within}$):

$$SS_{Total} = SS_{Between} + SS_{Within}$$

The test statistic is the $F$-ratio:

$$F = \frac{MS_{Between}}{MS_{Within}} = \frac{SS_{Between} / (k - 1)}{SS_{Within} / (N - k)}$$

- $H_0$: $\mu_1 = \mu_2 = \dots = \mu_k$ (all group means are equal)
- $H_1$: At least one group mean is different.

---

## 2. Experimental Example: Drug Effects on ALT Enzyme Activity

In `ANOVA_Drug_Enzyme_Activity_Project.ipynb`, Alanine Aminotransferase (ALT) enzyme activity is measured across 4 drug concentration regimes (Control, Low, Medium, High):

```python
from scipy.stats import f_oneway

# Quick F-test
f_stat, p_val = f_oneway(control, low_dose, med_dose, high_dose)
print(f"F-statistic: {f_stat:.3f}, p-value: {p_val:.4e}")
```

If $p < 0.05$, we reject $H_0$ and follow up with a post-hoc comparison test.

---

## 3. Assumptions Checklist
1. **Normality**: Residuals of the response variable should follow a normal distribution (Shapiro-Wilk test).
2. **Homoscedasticity**: Homogeneity of variances across groups (Levene's test).
3. **Independence**: Observations are independently sampled.

---

## Connections & See Also
- [[Tukey-HSD-Post-Hoc]]: Post-hoc testing to find pairwise group differences.
- [[Two-Way-ANOVA-and-Interaction]]: Extending ANOVA to multiple independent variables.
- [[statsmodels]]: Implementing detailed ANOVA summaries in Python.
