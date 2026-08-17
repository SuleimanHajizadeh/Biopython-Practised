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
  - reading-frames
sources:
  - "[[practice_notebooks/2 dersCalisma.ipynb]]"
  - "[[practice_notebooks/Biopython ders 2.ipynb]]"
---

# Bio.Seq

The `Bio.Seq` module provides the core string-like sequence containers (`Seq`, `MutableSeq`) and biological transformation functions like transcription, translation, and complementation.

---

## Key Classes & Methods

### 1. `Seq` and `MutableSeq`
- **`Seq`**: Immutable string wrapper supporting standard Python string methods (slicing, `.count()`, `.find()`, `.startswith()`) plus biological operations.
- **`MutableSeq`**: Mutable sequence object allowing in-place modifications (slice assignment, `.append()`, `.extend()`, `.reverse()`).

```python
from Bio.Seq import Seq, MutableSeq

my_seq = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")

# In-place mutations
mut_seq = MutableSeq(my_seq)
mut_seq[0:3] = "GTG"
mut_seq.append("A")
print(f"Mutated Seq: {mut_seq}")
```

---

## Central Dogma Operations

Biological transformations can be called either as standalone functions or directly as methods on `Seq` instances:

```python
from Bio.Seq import Seq

dna = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")

# 1. Transcription (Coding DNA -> mRNA)
mrna = dna.transcribe()
# Output: AUGGCCAUUGUAAUGGGCCGCUGAAAGGGUGCCCGAUAG

# 2. Reverse Transcription (mRNA -> cDNA)
cdna = mrna.back_transcribe()

# 3. Complementation & Reverse Complementation
comp = dna.complement()
rev_comp = dna.reverse_complement()

# 4. Translation (mRNA/DNA -> Protein)
protein_all = dna.translate()                 # MAIVMGR*KGAR* (includes stop codons)
protein_orf = dna.translate(to_stop=True)     # MAIVMGR (halts at first stop)
protein_custom_stop = dna.translate(stop_symbol="@")
```

---

## Six-Frame Translation

Extracting all 6 reading frames (+1, +2, +3 on forward strand; -1, -2, -3 on reverse strand):

```python
def get_six_frames(dna_seq: Seq) -> dict:
    frames = {}
    for frame in range(3):
        # Forward frames (+1, +2, +3)
        frames[f"+{frame+1}"] = dna_seq[frame:].translate()
        # Reverse frames (-1, -2, -3)
        frames[f"-{frame+1}"] = dna_seq.reverse_complement()[frame:].translate()
    return frames
```

---

## Custom Codon Tables & Genetic Codes

Translation supports all NCBI genetic code tables via `Bio.Data.CodonTable`:

```python
from Bio.Data import CodonTable

# Inspect standard and mitochondrial tables
standard_table = CodonTable.unambiguous_dna_by_name["Standard"]
mito_table = CodonTable.unambiguous_dna_by_name["Vertebrate Mitochondrial"]

print("Standard Stop Codons:", standard_table.stop_codons)
print("Standard Start Codons:", standard_table.start_codons)

# Translate using mitochondrial table
mito_protein = dna.translate(table="Vertebrate Mitochondrial")
```

---

## Motif & Pattern Searching

```python
seq = Seq("AAAAAAATCGAAAA")

# Non-overlapping count
print(seq.count("AA"))  # 4

# Overlapping count
print(seq.count_overlap("AA"))  # 9

# Find motif start index
pos = seq.find("TCG")
print(f"Motif found at index: {pos}")
```

---

## Connections & See Also
- [[Bio.SeqIO]]: Parsing records to extract `Seq` instances.
- [[Central-Dogma-Sequence-Operations]]: Theoretical foundations of reading frames and the genetic code.
- [[Bio.Align.PairwiseAligner]]: Aligning sequence objects.
