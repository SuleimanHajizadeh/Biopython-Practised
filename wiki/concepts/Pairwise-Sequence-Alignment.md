---
title: Pairwise Sequence Alignment
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - bioinformatics
  - sequence-alignment
  - dynamic-programming
  - needleman-wunsch
  - smith-waterman
sources:
  - "[[practice_notebooks/five.ipynb]]"
  - "[[practice_notebooks/2 dersCalisma.ipynb]]"
---

# Pairwise Sequence Alignment

**Pairwise sequence alignment** is the process of aligning two biological sequences (DNA, RNA, or protein) to identify regions of similarity that indicate functional, structural, or evolutionary relationships.

---

## 1. Global vs. Local Alignment

| Type | Algorithm | Best Used For | Dynamic Programming Boundary |
| :--- | :--- | :--- | :--- |
| **Global** | **Needleman-Wunsch** | Sequences of similar length with end-to-end homology | End-to-end alignment; gap penalties at ends |
| **Local** | **Smith-Waterman** | Finding conserved domains/motifs within divergent sequences | Zero floor on scores; aligns optimal sub-regions |

---

## 2. Scoring Parameters & Affine Gaps

The total alignment score is calculated as:

$$Score = \sum \text{Match/Mismatch Scores} - (g_{open} + k \cdot g_{extend})$$

- **Affine Gap Penalties**: Opening a gap ($g_{open}$) incurs a larger penalty than extending an existing gap ($g_{extend}$), reflecting the biological reality that single insertion/deletion events often involve multiple nucleotides/amino acids.
- **Substitution Matrices**: E.g., `BLOSUM62` (proteins) or match/mismatch scalars (nucleotides).

---

## 3. Implementation in Biopython

```python
from Bio.Align import PairwiseAligner, substitution_matrices

aligner = PairwiseAligner()
aligner.mode = "global"
aligner.substitution_matrix = substitution_matrices.load("BLOSUM62")
aligner.open_gap_score = -10.0
aligner.extend_gap_score = -0.5

alignments = aligner.align("MKWVTFISLLLLFSSAYSRG", "MKWVTFISLLFLFSSAYSRG")
print(alignments[0])
```

---

## Connections & See Also
- [[Bio.Align.PairwiseAligner]]: Biopython's C-accelerated engine.
- [[Bio.Align.Alignment]]: Coordinate-based alignment data structure.
- [[Multiple-Sequence-Alignment-Coordinates]]: Scaling beyond pairwise alignments.
