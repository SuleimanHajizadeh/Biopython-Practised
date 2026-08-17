---
title: Bio.Blast
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - blast
  - ncbi
  - sequence-homology
sources:
  - "[[practice_notebooks/eight.ipynb]]"
---

# Bio.Blast

`Bio.Blast` provides programmatic access to NCBI's Basic Local Alignment Search Tool (BLAST), enabling remote online querying and XML parsing.

---

## 1. Remote Querying with `qblast`

```python
from Bio.Blast import NCBIWWW
from Bio import SeqIO

record = SeqIO.read("data/sample.fasta", "fasta")

# Query NCBI BLAST over the network
result_handle = NCBIWWW.qblast(
    program="blastn",
    database="nt",
    sequence=record.seq,
    hitlist_size=10,
    expect=0.001
)

# Save raw XML result
with open("blast_results.xml", "w") as out:
    out.write(result_handle.read())
result_handle.close()
```

---

## 2. Parsing BLAST XML with `NCBIXML`

```python
from Bio.Blast import NCBIXML

with open("blast_results.xml") as result_file:
    blast_records = NCBIXML.parse(result_file)
    
    for blast_record in blast_records:
        for alignment in blast_record.alignments:
            for hsp in alignment.hsps:
                if hsp.expect < 1e-5:
                    print(f"****Alignment****")
                    print(f"sequence: {alignment.title}")
                    print(f"length: {alignment.length}")
                    print(f"e-value: {hsp.expect}")
                    print(hsp.query[0:75] + "...")
                    print(hsp.match[0:75] + "...")
                    print(hsp.sbjct[0:75] + "...")
```

---

## Connections & See Also
- [[Bio.SeqIO]]: Supplying input sequences for BLAST.
- [[Pairwise-Sequence-Alignment]]: Local alignment algorithms that BLAST approximates heuristically.
