---
title: Bio.SeqIO
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - sequence-io
  - fasta
  - fastq
  - genbank
sources:
  - "[[practice_notebooks/firstHomeWork.ipynb]]"
  - "[[practice_notebooks/1 dersCalisma.ipynb]]"
  - "[[practice_notebooks/four.ipynb]]"
---

# Bio.SeqIO

`Bio.SeqIO` is Biopython's standard sequence input/output interface. It provides uniform iterators and writers for over 30 biological file formats (FASTA, FASTQ, GenBank, EMBL, SwissProt, ABI, etc.).

---

## Core Methods

### 1. `SeqIO.parse()` (Iterative Streaming)
Used for files containing multiple records. Returns an iterator of `SeqRecord` objects:

```python
from Bio import SeqIO
from Bio.SeqUtils import gc_fraction

for record in SeqIO.parse("data/sequences.fasta", "fasta"):
    print(f"ID: {record.id}")
    print(f"Length: {len(record.seq)} bp")
    print(f"GC Content: {gc_fraction(record.seq) * 100:.2f}%")
```

### 2. `SeqIO.read()` (Single Record)
Reads a file containing strictly **one** record. Throws a `ValueError` if the file contains zero or multiple records:

```python
record = SeqIO.read("single_gene.gb", "genbank")
print(record.name, record.description)
```

### 3. `SeqIO.write()`
Writes an iterable of `SeqRecord` objects to an output file:

```python
count = SeqIO.write(records, "filtered_output.fasta", "fasta")
print(f"Saved {count} records")
```

---

## Connections & See Also
- [[Bio.Seq]]: Underlying biological sequence object stored in `record.seq`.
- [[Central-Dogma-Sequence-Operations]]: Manipulating sequences read via SeqIO.
- [[Biopython-Modern-API-Migration]]: Migration notes regarding `gc_fraction` vs legacy `GC`.
