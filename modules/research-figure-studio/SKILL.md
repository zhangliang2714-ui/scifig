---
name: research-figure-studio
description: Build or extend local scientific data figure tools that import Excel/CSV, render editable A4 SVG charts, use Nature-style palettes, and export borderless SVG/PNG without requiring API calls for basic plotting.
---

# Research Figure Studio

Use this skill when the user wants to create, reuse, or extend a local scientific plotting tool in any workspace.

## Core Rule

Data figures are generated locally by default. Do not require OpenAI API calls for ordinary plotting such as bar, line, scatter, box, or heatmap charts.

API or AI features may be optional enhancements, but the baseline workflow must work offline after dependencies are installed.

## Preferred Stack

- Vite + React + TypeScript for the UI.
- Tauri for desktop packaging when the machine has the Windows/Rust/MSVC toolchain.
- SheetJS/xlsx for Excel and CSV import.
- D3 for scales, axes, statistics, and chart geometry.
- React SVG for editable chart layers on an A4 canvas.
- canvg for SVG to PNG export.
- Local prompt parsing for text-to-chart configuration.

## Figure Requirements

- Use an A4 canvas with portrait and landscape modes.
- Store chart elements as editable SVG.
- Support SVG export and 300/600 dpi PNG export.
- Exported figures must not include editor-only borders, selected-object outlines, page guide rectangles, dashed placeholders, or UI overlays.
- Use local Nature-style, color-blind-friendly, and print-friendly palettes.
- Keep axis text, title, legend, scale range, font size, line width, object position, and object size editable.

## Existing Reference Project

Locate the user's local Vite/React plotting project before editing. That application is not bundled with this skill; the filenames below describe the reference architecture, not guaranteed files in the current workspace.

Important files:

- `DATA_FIGURE_TOOLING.md`: local plotting decisions and extension rules.
- `src/localPrompt.ts`: local text prompt to chart config parsing.
- `src/ChartRenderer.tsx`: SVG renderers for supported chart types.
- `src/App.tsx`: A4 canvas, import, editing, layer, and export UI.
- `src/palettes.ts`: local scientific palettes.

## Current Chart Types

- `bar`
- `line`
- `scatter`
- `box`
- `heatmap`

When adding chart types, update:

1. `src/types.ts`
2. `src/ChartRenderer.tsx`
3. `src/localPrompt.ts`
4. The chart controls in `src/App.tsx`

## Local Prompt Examples

```text
画散点图，x 为 dose，y 为 response，按 batch 分组，Nature 配色
```

```text
画箱线图，x 为 group，y 为 response，显示图例
```

```text
画柱状图，x 为 group，y 为 response，误差线为 sd，色盲友好配色
```

## Implementation Guidance

- If the target workspace is empty, scaffold the reference stack and copy the local plotting approach.
- If the target workspace already has a frontend, integrate the plotting modules into the existing style rather than replacing the app.
- Do not add API-key fields for baseline data plotting.
- If a visual helper border is useful while editing, render it as a UI overlay outside exported SVG content or hide it before export.
- Keep generated chart SVG clean enough for publication editing in Illustrator, Inkscape, PowerPoint, or manuscript tools.
