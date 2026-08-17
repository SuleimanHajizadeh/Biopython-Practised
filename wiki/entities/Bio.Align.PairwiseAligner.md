---
title: Bio.Align.PairwiseAligner
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - alignment
  - dynamic-programming
  - needleman-wunsch
  - smith-waterman
sources:
  - "[[practice_notebooks/five.ipynb]]"
---

# Bio.Align.PairwiseAligner

`Bio.Align.PairwiseAligner` is the modern, high-performance C-accelerated alignment engine in Biopython, replacing the deprecated `Bio.pairwise2` module.

---

## Configuration & Usage

```python
from Bio.Align import PairwiseAligner, substitution_matrices

aligner = PairwiseAligner()

# Alignment mode: 'global' (Needleman-Wunsch) or 'local' (Smith-Waterman)
aligner.mode = "global"

# Scoring parameters
aligner.match_score = 2.0
aligner.mismatch_score = -1.0
aligner.open_gap_score = -2.5
aligner.extend_gap_score = -0.5

# Alternatively, load a substitution matrix
aligner.substitution_matrix = substitution_matrices.load("BLOSUM62")
```

## Running Alignments

### 1. Optimal Alignment Score
```python
score = aligner.score("HEAGAWGHEE", "PAWHEAE")
print(f"Alignment Score: {score}")
```

### 2. Alignment Generator
```python
alignments = aligner.align("HEAGAWGHEE", "PAWHEAE")

for alignment in alignments:
    print(alignment)
    print(f"Score: {alignment.score}")
    print(f"Coordinates:\n{alignment.coordinates}")
```

---

## Key Differences from Legacy `pairwise2`
| Feature | `pairwise2` (Deprecated) | `PairwiseAligner` (Modern) |
| :--- | :--- | :--- |
| **Speed** | Pure Python / C hooks (slower) | Optimized C-extension |
| **Output Type** | Tuples `(seqA, seqB, score, start, end)` | `Alignment` object with coordinates |
| **Matrix Loading** | Manual matrix dicts | `Bio.Align.substitution_matrices` |

---

## Connections & See Also
- [[Pairwise-Sequence-Alignment]]: Conceptual foundations of dynamic programming alignment.
- [[Bio.Align.Alignment]]: Understanding the coordinate representation of alignments.
- [[Biopython-Modern-API-Migration]]: Migrating from `pairwise2` to `PairwiseAligner`.
