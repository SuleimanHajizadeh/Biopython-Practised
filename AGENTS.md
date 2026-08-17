# AGENTS.md — LLM Wiki Schema & Operating Guidelines

This repository follows the **LLM Wiki Pattern**: a persistent, compounding, interlinked markdown knowledge base built and maintained by LLM agents in collaboration with the user.

---

## 1. Architecture & Core Layers

1. **`raw/` (Immutable Sources)**:
   - Contains all raw inputs: clipped web articles, research papers, Markdown notes, data files, and transcripts.
   - **Rule**: Agents may read and reference raw sources, but **never modify or delete** files in `raw/`.
   - Media attachments and images go to `raw/assets/`.

2. **`wiki/` (Persistent Knowledge Graph)**:
   - LLM-managed layer consisting of interconnected markdown documents.
   - Subdirectories:
     - `wiki/entities/`: Specific tools, libraries, proteins, genes, databases, organizations, or individuals.
     - `wiki/concepts/`: Fundamental ideas, computational methods, biological mechanisms, workflows, protocols.
     - `wiki/syntheses/`: Cross-cutting analyses, thematic deep-dives, evolving research theses, and filed query answers.
     - `wiki/index.md`: Catalog of all wiki pages organized by topic with one-line summaries.
     - `wiki/log.md`: Append-only chronological ledger of all agent operations.

3. **`AGENTS.md` (The Schema)**:
   - This document. Governs wiki conventions, page templates, frontmatter specifications, and agent workflows.

---

## 2. Page & Syntax Conventions

- **Wikilinks**: Use standard Obsidian wikilinks: `[[Page Name]]` or `[[Path/To/Page|Custom Title]]`.
- **Frontmatter**: Every wiki page must include YAML frontmatter:
  ```yaml
  ---
  title: Page Title
  type: entity | concept | synthesis | source-summary
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  tags:
    - tag1
    - tag2
  sources:
    - "[[raw/source_name.md]]"
  ---
  ```
- **Cross-Referencing**: When writing or updating a page, actively link related concepts and entities using `[[...]]`. Keep high connectivity across the graph.

---

## 3. Core Operational Workflows

### Workflow A: Ingest Source (`Ingest`)
When a new source is added to `raw/` or provided in the prompt:
1. **Read & Extract**: Read the source completely. Identify novel facts, entities, mechanisms, methodology, and how it connects with existing wiki pages.
2. **Draft/Update Wiki Pages**:
   - Create or update relevant pages in `wiki/entities/`, `wiki/concepts/`, or `wiki/syntheses/`.
   - Maintain bidirectional links between entities and concepts.
   - If new data contradicts prior notes, explicitly highlight the discrepancy/debate in the relevant page.
3. **Update Master Index (`wiki/index.md`)**:
   - Add/update the entry for each affected page with a concise one-line summary.
4. **Append to Log (`wiki/log.md`)**:
   - Add an entry with format: `## [YYYY-MM-DD] ingest | <Source Title>` summarizing what was added/updated.

---

### Workflow B: Query & Synthesize (`Query`)
When the user asks a question against the wiki:
1. **Locate Context**: Read `wiki/index.md` and inspect relevant pages across `wiki/`.
2. **Synthesize**: Formulate an answer synthesizing multiple sources, referencing wiki pages with `[[...]]` links.
3. **Compound Value**: If the answer produces a valuable synthesis, comparison table, or novel insight, offer to or automatically save it into `wiki/syntheses/<topic>.md`, update `wiki/index.md`, and log the action.

---

### Workflow C: Lint & Health Check (`Lint`)
Periodically inspect the health and cohesion of the wiki:
1. **Orphans & Dead Links**: Identify pages with 0 incoming links or broken wikilinks.
2. **Stale / Conflicting Claims**: Check if newer sources supersede older summaries.
3. **Knowledge Gaps**: Highlight key concepts or entities mentioned frequently in text but lacking their own dedicated page.
4. **Log**: Record the lint pass in `wiki/log.md`.
