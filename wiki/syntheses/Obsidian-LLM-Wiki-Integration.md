---
title: Obsidian & LLM Wiki Integration Guide
type: synthesis
created: 2026-08-17
updated: 2026-08-17
tags:
  - obsidian
  - llm-wiki
  - workflow
  - knowledge-graph
  - methodology
sources:
  - "[[AGENTS.md]]"
  - "[[DOCUMENTATION.md]]"
---

# Obsidian & LLM Wiki Integration Guide

This guide explains how **Obsidian** and the **LLM Agent** collaborate to build a compounding, interlinked personal knowledge vault.

---

## 1. The Core Philosophy

Traditional RAG (Retrieval-Augmented Generation) is **stateless and ephemeral**: every query searches raw chunks from scratch, re-deriving connections that are immediately forgotten when the conversation ends.

The **LLM Wiki pattern** makes knowledge **persistent and compounding**:
- The LLM incrementally compiles raw sources into structured, interlinked markdown pages in `wiki/`.
- Every new source enriches existing pages, updates cross-references, flags contradictions, and strengthens syntheses.
- Obsidian provides a local, graphical interface to navigate and visualize this living knowledge network.

---

## 2. The Roles: User, LLM, and Obsidian

| Component | Role | What it does |
| :--- | :--- | :--- |
| **User (You)** | **Architect & Explorer** | Curates raw sources (`raw/`), guides research questions, directs analyses. |
| **LLM Agent** | **Librarian & Synthesizer** | Reads sources, generates frontmatter, creates `[[wikilinks]]`, updates `index.md`, logs actions. |
| **Obsidian** | **IDE & Visual Graph** | Live Markdown rendering, graph view, interactive link navigation, backlink analysis. |

---

## 3. Navigating This Vault in Obsidian

### A. Graph View (`Cmd/Ctrl + G`)
- Open the Graph View to see the visual topology of your knowledge base.
- **Hubs**: Pages like [[Bio.Seq]], [[Bio.PDB]], [[One-Way-ANOVA]], and [[Biological-Data-Formats]] will have numerous radiating edges.
- **Color Groups**: In Graph Settings $\rightarrow$ Groups, color by path:
  - `path:wiki/entities` $\rightarrow$ Green
  - `path:wiki/concepts` $\rightarrow$ Blue
  - `path:wiki/syntheses` $\rightarrow$ Purple

### B. Index-First Browsing
- Pin **[[wiki/index.md]]** as your home dashboard. It gives you a structured overview of all entities, concepts, and syntheses.

### C. Live Hover Previews
- Hold `Cmd` (Mac) or `Ctrl` (Windows/Linux) and hover over any `[[wikilink]]` to preview the page without opening it in a new tab.

### D. Backlink Pane
- Open the right sidebar in Obsidian and inspect **Backlinks** to see which concepts reference the active entity.

---

## 4. Recommended Obsidian Plugins (Optional Enhancements)

1. **Dataview**: Run SQL-like queries on page frontmatter (e.g. list all pages with tag `#biostatistics`).
2. **Omnisearch** or **qmd**: Fast semantic/hybrid search across all markdown documents.
3. **Marp Slides**: Generate presentation slide decks directly from wiki pages.

---

## Connections & See Also
- [[AGENTS.md]]: The formal operational rules and schema.
- [[Biopython-Modern-API-Migration]]: Example synthesis page.
- [[Computational-Biochemistry-and-Stats-Pipeline]]: Example pipeline synthesis.
