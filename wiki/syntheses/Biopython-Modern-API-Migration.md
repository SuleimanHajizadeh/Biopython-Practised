---
title: Biopython Modern API Migration Guide
type: synthesis
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - api-migration
  - deprecation
  - best-practices
sources:
  - "[[practice_notebooks/1 dersCalisma.ipynb]]"
  - "[[practice_notebooks/2 dersCalisma.ipynb]]"
  - "[[practice_notebooks/five.ipynb]]"
---

# Biopython Modern API Migration Guide

Across the notebooks in this repository, several legacy Biopython patterns were observed and updated. This guide consolidates key breaking changes and recommended modern APIs in Biopython 1.78+.

---

## 1. GC Content Calculation

- ❌ **Legacy (Deprecated/Removed)**:
  ```python
  from Bio.SeqUtils import GC
  gc = GC(my_seq)  # Returns percentage 0 - 100
  ```
- ✅ **Modern**:
  ```python
  from Bio.SeqUtils import gc_fraction
  gc = gc_fraction(my_seq) * 100.0  # Returns fraction 0.0 - 1.0
  ```

---

## 2. Pairwise Sequence Alignment

- ❌ **Legacy (Deprecated in 1.80+)**:
  ```python
  from Bio import pairwise2
  alignments = pairwise2.align.globalxx(seqA, seqB)
  ```
- ✅ **Modern (`PairwiseAligner`)**:
  ```python
  from Bio.Align import PairwiseAligner
  aligner = PairwiseAligner()
  aligner.mode = "global"
  aligner.match_score = 1.0
  aligner.mismatch_score = 0.0
  alignments = aligner.align(seqA, seqB)
  ```

---

## 3. Alphabet Module Removal

- ❌ **Legacy (Removed in 1.78)**:
  ```python
  from Bio.Alphabet import generic_dna
  seq = Seq("ATGC", generic_dna)
  ```
- ✅ **Modern**:
  ```python
  from Bio.Seq import Seq
  seq = Seq("ATGC")  # Plain sequence string wrapper; alphabets no longer required
  ```

---

## 4. Summary Matrix

| Task | Legacy Pattern | Modern Replacement | Wiki Entity |
| :--- | :--- | :--- | :--- |
| **GC calculation** | `Bio.SeqUtils.GC()` | `Bio.SeqUtils.gc_fraction()` | [[Bio.SeqIO]] |
| **Pairwise Alignment** | `Bio.pairwise2` | `Bio.Align.PairwiseAligner` | [[Bio.Align.PairwiseAligner]] |
| **Substitution Matrices** | `Bio.SubsMat` | `Bio.Align.substitution_matrices` | [[Bio.Align.PairwiseAligner]] |
| **Alignments structure** | list of tuples | `Bio.Align.Alignment` | [[Bio.Align.Alignment]] |
