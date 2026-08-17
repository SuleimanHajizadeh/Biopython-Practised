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

`Bio.SeqIO` is Biopython's standard sequence input/output interface. It provides uniform iterators, dictionary indexers, and writers for over 30 biological file formats (FASTA, FASTQ, GenBank, EMBL, SwissProt, ABI, etc.).

---

## Core Methods

### 1. `SeqIO.parse()` (Iterative Streaming)
Used for streaming files containing multiple records without loading everything into memory:

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

## Advanced Operations & Best Practices

### 4. Random Access: `SeqIO.index()` vs `SeqIO.to_dict()`
- **`SeqIO.to_dict()`**: Loads all records into a standard Python in-memory `dict`. Best for small-to-medium files (< 50MB).
- **`SeqIO.index()`**: Creates a lightweight, read-only dictionary-like index on disk using byte offsets. Ideal for multi-gigabyte FASTA/FASTQ databases.

```python
# Lightweight disk index
record_dict = SeqIO.index("large_genome.fasta", "fasta")
chr1 = record_dict["chr1"]
print(f"Chr1 Length: {len(chr1)}")
```

### 5. Format Conversion with `SeqIO.convert()`
High-performance direct conversion between formats without manual looping:

```python
count = SeqIO.convert("reads.fastq", "fastq", "reads.fasta", "fasta")
print(f"Converted {count} records from FASTQ to FASTA")
```

### 6. Working with FASTQ Quality Scores
FASTQ records store base quality scores inside `letter_annotations`:

```python
for record in SeqIO.parse("data/sample.fastq", "fastq"):
    qualities = record.letter_annotations["phred_quality"]
    avg_qual = sum(qualities) / len(qualities)
    if avg_qual >= 30:  # Q30 quality filter
        print(f"Passed: {record.id} (Avg Q: {avg_qual:.1f})")
```

### 7. Reading Compressed Files (Gzip / Bzip2)
`SeqIO` seamlessly reads from open file handles:

```python
import gzip

with gzip.open("reads.fastq.gz", "rt") as handle:
    for record in SeqIO.parse(handle, "fastq"):
        pass
```

---

## Connections & See Also
- [[Bio.Seq]]: Underlying biological sequence object stored in `record.seq`.
- [[Central-Dogma-Sequence-Operations]]: Manipulating sequences read via SeqIO.
- [[Biopython-Modern-API-Migration]]: Migration notes regarding `gc_fraction` vs legacy `GC`.
