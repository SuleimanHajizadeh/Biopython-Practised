---
title: Bio.Seq
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - sequence-manipulation
  - translation
  - codon-tables
sources:
  - "[[practice_notebooks/2 dersCalisma.ipynb]]"
  - "[[practice_notebooks/Biopython ders 2.ipynb]]"
---

# Bio.Seq

The `Bio.Seq` module provides core string-like sequence containers (`Seq`, `MutableSeq`) and biological transformation functions like transcription, translation, and complementation.

---

## Key Classes & Methods

### `Seq` and `MutableSeq`
- `Seq` objects are **immutable** string wrappers (analogous to Python `str`).
- `MutableSeq` allows in-place modifications (slice assignment, `.append()`, `.reverse()`).

```python
from Bio.Seq import Seq, MutableSeq

my_seq = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")
mut_seq = MutableSeq(my_seq)
mut_seq[0] = "C"
print(mut_seq)
```

### Central Dogma Transformations
```python
from Bio.Seq import transcribe, back_transcribe, translate, reverse_complement

dna = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")

# Transcription: DNA (coding strand) -> mRNA
mrna = transcribe(dna)  # AUGGCCAUUGUAAUGGGCCGCUGAAAGGGUGCCCGAUAG

# Reverse transcription: mRNA -> cDNA
cdna = back_transcribe(mrna)

# Reverse complement
rev_comp = reverse_complement(dna)

# Translation: DNA/mRNA -> Protein
protein = translate(dna, to_stop=False)
```

### Codon Tables
Translation can specify custom genetic codes using `Bio.Data.CodonTable`:

```python
from Bio.Data import CodonTable

standard_table = CodonTable.unambiguous_dna_by_name["Standard"]
mito_table = CodonTable.unambiguous_dna_by_name["Vertebrate Mitochondrial"]
print(standard_table.stop_codons)
```

---

## Connections & See Also
- [[Bio.SeqIO]]: Parsing records to extract `Seq` instances.
- [[Central-Dogma-Sequence-Operations]]: Conceptual guide to reading frames and translation.
- [[Bio.Align.PairwiseAligner]]: Aligning biological sequences.
