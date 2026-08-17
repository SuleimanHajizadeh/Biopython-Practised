---
title: Biological Data Formats & Parsers
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - bioinformatics
  - file-formats
  - parsers
  - sequence-formats
  - annotations
sources:
  - "[[data/raw/]]"
  - "[[practice_notebooks/four.ipynb]]"
  - "[[practice_notebooks/five.ipynb]]"
---

# Biological Data Formats & Parsers

Modern computational biology relies on standardized text and binary formats for sequence storage, annotations, multiple alignments, and coordinate transformations.

---

## 1. Sequence & Annotation Formats

| Format | Extension | Description | Biopython Parser |
| :--- | :--- | :--- | :--- |
| **FASTA** | `.fa`, `.fasta`, `.fna`, `.faa` | Raw nucleotide or amino acid sequences with `>` header | `SeqIO.parse(f, "fasta")` |
| **FASTQ** | `.fq`, `.fastq` | High-throughput sequencing reads with Phred quality scores | `SeqIO.parse(f, "fastq")` |
| **GenBank** | `.gb`, `.gbk` | Rich annotations, CDS, features, taxonomy, and sequence | `SeqIO.parse(f, "genbank")` |
| **EMBL** | `.embl` | European Molecular Biology Laboratory annotation format | `SeqIO.parse(f, "embl")` |

---

## 2. Multiple Sequence Alignment Formats

| Format | Extension | Features | Biopython Parser / Module |
| :--- | :--- | :--- | :--- |
| **ClustalW** | `.aln` | Consensus line (`*`, `:`, `.`), block alignments | `AlignIO.parse(f, "clustal")` |
| **Stockholm** | `.sth` | InterPro/Pfam standard with `#=GF` feature annotations | `AlignIO.parse(f, "stockholm")` |
| **Phylip** | `.phy` | Strict 10-char identifiers for phylogenetics | `AlignIO.parse(f, "phylip")` |
| **NEXUS** | `.nex` | Command blocks for MrBayes / PAUP* | `AlignIO.parse(f, "nexus")` |
| **GCG MSF** | `.msf` | Multiple Sequence Format from Wisconsin package | `AlignIO.parse(f, "msf")` |
| **Mauve XMFA** | `.xmfa` | eXtended Multi-FASTA for whole-genome alignments | `Bio.AlignIO.MauveIO` |

---

## 3. Genomic Coordinates & Intervals

| Format | Extension | Purpose | Tools |
| :--- | :--- | :--- | :--- |
| **BED** | `.bed`, `.bb` | 0-based, half-open genomic intervals (chr, start, end, name, score, strand) | `Bio.Align.bigbed`, `pybedtools` |
| **PSL** | `.psl` | BLAT and alignment coordinate match tables | `Bio.Align.psl` |
| **Chain** | `.chain` | Liftover coordinate mapping between genome assemblies (e.g. hg19 $\rightarrow$ GRCh38) | `Bio.Align.chain` |

---

## 4. Macromolecular Structure Formats

| Format | Extension | Purpose | Parser |
| :--- | :--- | :--- | :--- |
| **PDB** | `.pdb` | Legacy 80-column fixed-width format (capped at 99,999 atoms) | `Bio.PDB.PDBParser` |
| **mmCIF** | `.cif` | Modern wwPDB standard dictionary-based format without size limits | `Bio.PDB.MMCIFParser`, `gemmi` |
| **BinaryCIF** | `.bcif`, `.bcif.gz` | High-efficiency compressed binary mmCIF representation | `gemmi` |

---

## Connections & See Also
- [[Bio.SeqIO]]: Sequence parser and streamer.
- [[Bio.PDB]]: Structure parser for PDB/mmCIF.
- [[Gemmi]]: Fast C++ parser for mmCIF and BinaryCIF.
- [[Multiple-Sequence-Alignment-Coordinates]]: Coordinate-matrix data representation.
