---
title: pingouin
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biostatistics
  - repeated-measures
  - anova
  - sphericity
sources:
  - "[[biostatistics/Advanced_ANOVA.ipynb]]"
---

# pingouin

`pingouin` is an open-source statistical package in Python based on Pandas and NumPy, tailored for experimental biology, psychology, and neuroscience.

---

## Repeated Measures ANOVA Workflow

In `Advanced_ANOVA.ipynb`, `pingouin` is used for within-subject repeated measures designs:

```python
import pingouin as pg

# Repeated Measures ANOVA
rm_aov = pg.rm_anova(
    data=df_rm,
    dv='Value',
    within='Time',
    subject='Subject',
    detailed=True
)
print(rm_aov)
```

### Automatic Sphericity Assessment
Pingouin automatically reports **Mauchly’s test for sphericity** and provides Greenhouse-Geisser and Huynh-Feldt epsilon corrections when sphericity is violated.

---

## Connections & See Also
- [[Repeated-Measures-ANOVA]]: Conceptual overview of within-subject variance.
- [[statsmodels]]: Library used for standard ordinary least squares ANOVA.
