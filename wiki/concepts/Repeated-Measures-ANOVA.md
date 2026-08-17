---
title: Repeated Measures ANOVA
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - biostatistics
  - repeated-measures
  - longitudinal
  - sphericity
sources:
  - "[[biostatistics/Advanced_ANOVA.ipynb]]"
---

# Repeated Measures ANOVA

**Repeated Measures ANOVA** (within-subject ANOVA) is used when the same experimental units (e.g. patients, cell cultures) are measured across multiple time points or conditions.

---

## 1. Why Not Independent ANOVA?
Standard ANOVA assumes that all observations are independent. In longitudinal or repeated-treatment experiments, within-subject correlation violates this assumption. Repeated Measures ANOVA isolates subject-to-subject baseline variability, reducing unexplained error variance ($SS_{Error}$) and increasing statistical power.

---

## 2. The Sphericity Assumption & Mauchly's Test

Repeated Measures ANOVA requires **sphericity**: the variances of the differences between all possible pairs of within-subject conditions must be equal.

- If Sphericity is **violated** ($p < 0.05$ on Mauchly's test), degrees of freedom must be adjusted using:
  - **Greenhouse-Geisser ($\epsilon$)**: Conservative correction, best when $\epsilon < 0.75$.
  - **Huynh-Feldt ($\epsilon$)**: Less conservative, best when $\epsilon \ge 0.75$.

---

## 3. Implementation with `pingouin`

```python
import pingouin as pg

res = pg.rm_anova(
    data=df_longitudinal,
    dv="Enzyme_Activity",
    within="TimePoint",
    subject="PatientID",
    detailed=True
)
print(res)
```

---

## Connections & See Also
- [[One-Way-ANOVA]]: Independent group comparisons.
- [[Two-Way-ANOVA-and-Interaction]]: Mixed between-within designs.
- [[pingouin]]: Python library for repeated measures and sphericity checks.
