# Wiki Changelog

A chronological, append-only log of all operations (ingests, queries, syntheses, lint passes) performed on this knowledge base.

---

## [2026-08-17] ingest | Repository Codebase Ingestion
- **Source Modules**: `biostatistics/`, `structural_biology/`, and `practice_notebooks/`.
- **Entities Ingested**:
  - [[Bio.SeqIO]], [[Bio.Seq]], [[Bio.Align.PairwiseAligner]], [[Bio.Align.Alignment]], [[Bio.Blast]], [[Bio.PDB]]
  - [[Gemmi]], [[MDAnalysis]], [[RDKit]], [[statsmodels]], [[pingouin]]
- **Concepts Ingested**:
  - [[One-Way-ANOVA]], [[Two-Way-ANOVA-and-Interaction]], [[Repeated-Measures-ANOVA]], [[Tukey-HSD-Post-Hoc]]
  - [[Pairwise-Sequence-Alignment]], [[Multiple-Sequence-Alignment-Coordinates]], [[Protein-Ligand-Interaction-Profiling]], [[Central-Dogma-Sequence-Operations]]
- **Syntheses Generated**:
  - [[Biopython-Modern-API-Migration]]: Best practices and deprecation migration guide.
  - [[Computational-Biochemistry-and-Stats-Pipeline]]: End-to-end integration architecture.
- **Index**: Updated [[wiki/index.md]] with all new cross-linked nodes.

---

## [2026-08-17] init | Repository Wiki Setup
- Initialized [AGENTS.md](file:///Users/macbookairm2/Documents/GitHub/Biopython-Practised/AGENTS.md) schema and conventions.
- Created `raw/` directory structure for immutable sources and `raw/assets/` for media.
- Created `wiki/` directory layout with [index.md](file:///Users/macbookairm2/Documents/GitHub/Biopython-Practised/wiki/index.md), entity, concept, and synthesis categories.
