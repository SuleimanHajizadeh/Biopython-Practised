---
title: Bio.Align.Alignment
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - alignment-data-structure
  - coordinates
sources:
  - "[[practice_notebooks/four.ipynb]]"
  - "[[practice_notebooks/five.ipynb]]"
---

# Bio.Align.Alignment

`Bio.Align.Alignment` is the unified alignment container in modern Biopython. Instead of storing gap characters (`-`) directly inside modified sequence strings, it stores original sequences along with a **coordinate matrix** defining path intervals.

---

## Coordinate Representation

An alignment of $N$ sequences with $K$ segments is represented by an $(N, K)$ NumPy integer matrix:

```python
import numpy as np
from Bio.Align import Alignment

sequences = ["CCGGTTTTT", "AGTTTAA", "AGGTTT"]

# Coordinates define start and end indices for contiguous aligned segments
coordinates = np.array([
    [1, 3, 4, 7, 9],
    [0, 2, 2, 5, 5],
    [0, 2, 3, 6, 6]
])

alignment = Alignment(sequences, coordinates)
print(alignment)
```

Output:
```text
target            1 CGG-TTTT 8
                  0 |||-|||-- 8
query1            0 AG--TTTA 6
                  0 |||-|||-- 8
query2            0 AGG-TTT- 6
```

---

## Advantages of Coordinate-Based Alignments
1. **Memory Efficiency**: The raw sequences remain unmodified and can be shared across multiple alternative alignment paths.
2. **Slicing & Sub-alignments**: Alignments can be sliced directly by column or row index.
3. **Format Export**: Converts cleanly to SAM, BAM, PAF, FASTA, or Stockholm formats.

---

## Connections & See Also
- [[Bio.Align.PairwiseAligner]]: The engine producing `Alignment` instances.
- [[Multiple-Sequence-Alignment-Coordinates]]: Theory and mechanics of coordinate matrices.
