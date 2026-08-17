---
title: Two-Way ANOVA and Interaction Effects
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - biostatistics
  - interaction-plots
  - clinical-trials
  - synergism
sources:
  - "[[biostatistics/Advanced_ANOVA.ipynb]]"
  - "[[biostatistics/Interaction_Plot_Clinical_Trial.ipynb]]"
---

# Two-Way ANOVA & Interaction Effects

**Two-Way ANOVA** evaluates the simultaneous effects of two categorical factors (e.g., Treatment and Gender, or Drug A and Drug B) on a continuous dependent variable.

---

## 1. Main Effects vs. Interaction Effect

A two-way design tests three hypotheses:
1. **Main Effect of Factor A**: Does the mean outcome differ across levels of Factor A?
2. **Main Effect of Factor B**: Does the mean outcome differ across levels of Factor B?
3. **Interaction Effect ($A \times B$)**: Does the effect of Factor A depend on the level of Factor B?

---

## 2. Diagnosing Interaction Plots

In `Interaction_Plot_Clinical_Trial.ipynb`, interaction is visualized by plotting lines connecting group means:

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.pointplot(data=df_trial, x="Dose", y="Biomarker_Reduction", hue="Genotype", markers=["o", "s"], capsize=0.1)
plt.title("Genotype × Dose Interaction on Biomarker Reduction")
plt.show()
```

- **Parallel Lines**: No interaction. The effect of Dose is uniform across Genotypes.
- **Non-Parallel / Crossing Lines**: Significant interaction. The effectiveness of the dose depends on the patient's genotype.

---

## 3. Modeling in Python

```python
import statsmodels.api as sm
from statsmodels.formula.api import ols

model = ols("Biomarker_Reduction ~ C(Dose) * C(Genotype)", data=df_trial).fit()
table = sm.stats.anova_lm(model, typ=2)
print(table)
```

---

## Connections & See Also
- [[One-Way-ANOVA]]: Single factor baseline.
- [[Repeated-Measures-ANOVA]]: Handling multi-factor measurements within the same subjects.
- [[statsmodels]]: Formula syntax and Type II/III sum of squares.
