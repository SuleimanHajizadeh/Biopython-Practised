---
title: statsmodels
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biostatistics
  - anova
  - regression
  - post-hoc
sources:
  - "[[biostatistics/Advanced_ANOVA.ipynb]]"
  - "[[biostatistics/Intermediate_ANOVA_Tutorial.ipynb]]"
  - "[[biostatistics/ANOVA_Drug_Enzyme_Activity_Project.ipynb]]"
---

# statsmodels

`statsmodels` is a Python package providing classes and functions for the estimation of many different statistical models, regression analysis, hypothesis testing, and ANOVA modeling.

---

## ANOVA Formulas & Output

### 1. Ordinary Least Squares (`ols`) Formulation
```python
import statsmodels.api as sm
from statsmodels.formula.api import ols

# One-way ANOVA model
model = ols("score ~ C(group)", data=df).fit()
anova_table = sm.stats.anova_lm(model, typ=2)
print(anova_table)

# Two-way ANOVA with Interaction
twoway_model = ols("Score ~ C(Treatment) * C(Gender)", data=df_tw).fit()
twoway_table = sm.stats.anova_lm(twoway_model, typ=2)
print(twoway_table)
```

### 2. Post-hoc Tukey HSD
```python
from statsmodels.stats.multicomp import pairwise_tukeyhsd

tukey = pairwise_tukeyhsd(endog=df['score'], groups=df['group'], alpha=0.05)
print(tukey.summary())
```

---

## Connections & See Also
- [[One-Way-ANOVA]]: Single factor variance modeling.
- [[Two-Way-ANOVA-and-Interaction]]: Multi-factor modeling with interaction terms.
- [[Tukey-HSD-Post-Hoc]]: Pairwise significance test.
- [[pingouin]]: Alternative high-level package for repeated measures.
