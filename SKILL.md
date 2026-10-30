---
name: scifig
description: Unified scientific figure workflow for deciding between experimental data plots, scientific schematic reconstruction, journal-style figure recreation, and hybrid multi-panel figures. Use when creating, revising, analyzing, or learning visual conventions from research figures, especially Nature or Science papers.
metadata:
  short-description: Unified scientific data and schematic figure studio
---

# SciFig — Scientific Figures

Use this skill as the single entry point for scientific figure work. First identify the requested deliverable and then select one or more modes; do not force every request into a data plot or a schematic.

## Route the request

- **Data mode**: Excel/CSV/TSV or numerical results; inspect columns, sample size, distributions, uncertainty, groups, and outliers before choosing a plot. Prefer transparent displays of raw observations and use color-blind-safe palettes.
- **Schematic mode**: mechanism diagrams, material structures, process flows, interfaces, particles, grains, cracks, fibers, or other conceptual scientific graphics. Reconstruct with editable SVG/Python/Blender components when appropriate.
- **Journal-style mode**: recreate or redesign a figure based on a Nature, Science, or comparable paper. Separate visual grammar (layout, hierarchy, typography, palette, line weights, annotation style) from the paper's scientific content; never invent missing data.
- **Hybrid mode**: combine data panels and mechanism panels into one coherent figure with shared typography, palette, panel labels, and visual hierarchy.

## Core workflow

1. Clarify the scientific conclusion the figure must communicate, the source material available, and the intended output format.
2. Inspect source data or reference images before drawing. For reference figures, record panel structure, coordinate systems, legends, typography, palette, marks, annotations, and evidence-to-claim mapping.
3. Select the minimum set of panels that supports the conclusion. Flag ambiguity, missing values, image-quality limits, and any stylistic feature that cannot be inferred reliably.
4. Build an editable, reproducible artifact where practical. Use Python/R for quantitative plots and SVG/Python/Blender or suitable image tools for schematics.
5. Validate scientific correctness, readability at final publication size, axis and unit consistency, legend completeness, color accessibility, and export quality. Render and visually inspect the final output.

## Learning from paper figures

When the user supplies Nature/Science figures, first produce a style audit and reusable figure brief. Extract conventions rather than copying scientific claims: panel grammar, spacing, typography, color roles, stroke hierarchy, annotation placement, uncertainty display, and export characteristics. Apply those conventions only to the user's own data or mechanism.

For detailed style-learning fields and a reusable audit template, read [references/style-learning.md](references/style-learning.md).

For this user's confirmed panel-title, spacing, synthetic-data, and visual-review preferences, read [references/user-figure-conventions.md](references/user-figure-conventions.md) before composing or revising a multi-panel data figure. Default to panel letters without descriptive headings above each subplot. Keep essential axis labels, units, legends and uncertainty definitions.

For the Zotero-derived corpus and current Nature/Science style profile, read [references/zotero-figure-study/corpus.md](references/zotero-figure-study/corpus.md) and [references/zotero-figure-study/style-profile.md](references/zotero-figure-study/style-profile.md).

## Internal modules

The specialized workflows are retained under `modules/`. Their nested `SKILL.md` files may still appear in skill discovery; moving them alone does not hide them. Consult them when the routed task needs deeper implementation detail:

- `modules/nature-figure/` for journal-grade figure contracts, chart patterns, and export workflows.
- `modules/scipilot-figure-skill/` for data profiling, chart selection, plotting recipes, and visual QA scripts.
- `modules/research-figure-studio/` for the local Excel/CSV-to-SVG tool workflow.
- `modules/scientific-schematic-reconstruction/` for SVG/Python/Blender schematic reconstruction.

For Blender-based material-mechanism schematics, read the [Mg–H₂ Blender reconstruction case notes](references/mg-h2-blender-case-2026-10-30.md). Use them for Alloy density control, unified metallic materials, Blender/SVG division of labor, and revision QA; their object names and version numbers are specific to that case.

## Deliverables

Prefer editable source plus publication exports when possible: SVG/PDF for vector figures, PNG/TIFF at the requested resolution for raster delivery, and a short figure specification recording data sources, transformations, plotting choices, and unresolved limitations.

## Synthetic-data provenance rule

When a figure contains values generated by Codex for demonstration, layout testing, or style learning rather than user-provided measurements, add a visible but low-interference `DEMO · SYNTHETIC DATA` watermark to every preview/export by default. Reserve space for it and check that it does not collide with bottom-row labels. Also record `synthetic_data: true` in the figure specification/QA metadata and retain reproducible source data and the random seed. Supplying some real data does not remove the requirement while synthetic values remain in the figure. An explicit later user instruction can change the watermark preference; the artifact's data provenance must still be described accurately.
