---
title: Central Dogma Sequence Operations
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - bioinformatics
  - transcription
  - translation
  - genetic-code
sources:
  - "[[practice_notebooks/2 dersCalisma.ipynb]]"
  - "[[practice_notebooks/Biopython ders 2.ipynb]]"
---

# Central Dogma Sequence Operations

Computational implementation of biological sequence information transfer: **DNA Replication/Transcription $\rightarrow$ RNA Processing $\rightarrow$ Translation into Proteins**.

---

## 1. Strandedness and Complementation

- **Coding Strand (Sense)**: $5' \rightarrow 3'$, matches mRNA sequence (with T instead of U).
- **Template Strand (Antisense)**: $3' \rightarrow 5'$, used by RNA polymerase.
- **Reverse Complement**: Necessary when analyzing genes on the negative chromosomal strand.

```python
from Bio.Seq import Seq, reverse_complement

coding_dna = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG")
rev_comp = reverse_complement(coding_dna)
```

---

## 2. Transcription & Translation Rules

```python
from Bio.Seq import transcribe, translate

# DNA to mRNA
mrna = transcribe(coding_dna)

# Standard Translation (stops at first stop codon if to_stop=True)
protein_complete = translate(mrna, to_stop=False)  # includes '*' characters
protein_orf = translate(mrna, to_stop=True)       # truncates at first '*'
```

---

## 3. Alternative Genetic Codes

Not all organisms and organelles use the Standard genetic code (NCBI Table 1):
- **Vertebrate Mitochondrial (Table 2)**: `AGA` and `AGG` are stop codons instead of Arginine; `AUA` codes for Methionine.
- **Bacterial, Archaeal and Plant Plastid (Table 11)**: Alternative start codons (`GUG`, `UUG`) initiate as Formylmethionine.

---

## Connections & See Also
- [[Bio.Seq]]: The primary container and utility module.
- [[Bio.SeqIO]]: Reading genomic sequences for downstream translation.
