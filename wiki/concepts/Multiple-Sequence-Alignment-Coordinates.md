---
title: Multiple Sequence Alignment Coordinates
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - bioinformatics
  - msa
  - coordinates
  - data-structures
sources:
  - "[[practice_notebooks/four.ipynb]]"
  - "[[practice_notebooks/five.ipynb]]"
---

# Multiple Sequence Alignment (MSA) Coordinate Modeling

Modern computational biology packages represent sequence alignments not as padded character strings (with `-` characters inserted), but as integer coordinate paths across the original unaligned strings.

---

## 1. Why Coordinate Matrices?

Traditional string-based alignments have significant drawbacks:
1. Mutating strings destroys original sequence indices.
2. Large alignments consume excessive memory storing gap characters.
3. Converting between different coordinate frames (e.g. genomic vs. transcript vs. protein coordinates) is error-prone.

---

## 2. Matrix Structure in Biopython

An alignment coordinate matrix $C$ has dimensions $(N, K)$ where:
- $N$: number of sequences.
- $K$: number of alignment boundaries (columns where an indel starts, ends, or aligns).

```
Seq 0: [c_{0,0}, c_{0,1}, c_{0,2}, ...]
Seq 1: [c_{1,0}, c_{1,1}, c_{1,2}, ...]
...
```

If $c_{i, j+1} - c_{i, j} == 0$, sequence $i$ has a **deletion** across interval $j$.

---

## 3. Example Construction

```python
import numpy as np
from Bio.Align import Alignment

seqs = ["ACGTACGT", "AC--ACGT", "ACGT--GT"]
# Coordinate intervals define start/end of matched chunks
coords = np.array([
    [0, 2, 4, 8],
    [0, 2, 2, 6],
    [0, 4, 4, 6]
])

aln = Alignment(seqs, coords)
print(aln)
```

---

## Connections & See Also
- [[Bio.Align.Alignment]]: The class implementing this matrix logic.
- [[Pairwise-Sequence-Alignment]]: Pairwise alignment algorithms.
