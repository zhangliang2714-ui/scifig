# User-confirmed figure conventions

Updated 2026-10-23 from reference reconstruction and simulated-data layout trials. These are this user's preferences and example-specific measurements, not universal Nature/Science requirements.

## Titles and explanation

- Default to A–I (or the required sequence) as panel identifiers. Do not add descriptive headings above each panel such as “Independent samples”, “Uptake kinetics”, or “Cycling stability”. The user clarified that all such headings were unwanted, not just one phrase.
- Do not replace these headings with unsolicited conclusion sentences. Put extended explanations in the figure caption or accompanying text.
- Keep scientific content needed to read the chart: axis labels, units, group legends, conditions and uncertainty/sample-size definitions. Removing headings does not authorize deleting these.
- Once headings are removed, reassess the space they occupied rather than automatically preserving an empty title band.

## Geometry and spacing

- Match the reference's plotting rectangles before tuning curves or decoration. A plot rectangle is bounded by its spines; its full panel includes tick labels, axis titles, legends and annotations.
- Store measurements in a single whole-image coordinate system, with top-left origin and explicit pixel units. For each crop, store its offset and convert local coordinates before comparing with the original. Do not confuse text rows with border lines.
- Crop panels with their labels and right axes intact; equal-third slicing can cut off content. Inspect same-scale source/reconstruction crops.
- Distinguish frame-to-frame spacing from the gap between visible text. Choose the smallest comfortable spacing that clears actual rendered text, including math superscripts and rotated labels.
- Preserve fixed-canvas exports when matching a reference. `bbox_inches='tight'` can change margins and canvas proportions.
- Read [the corrected raster measurements](zotero-figure-study/reference-measurements-2026-10-22.md) for the supplied nine-panel reference. Most rectangular frames are approximately 298 × 240 px (ratio 1.242); H's split-axis envelope is 264 × 240 px. Earlier claims of substantially different B/D/E/F ratios were erroneous.

### Nine-panel trial: a starting point, not a universal preset

| Setting | Trial result |
|---|---|
| Plot rectangles | 60 × 48 mm, ratio 1.25 |
| Original frame gaps | horizontal 27 mm, vertical 21 mm; user found layout too loose |
| Revised frame gaps | horizontal 17 mm, vertical 17 mm |
| Rejected intermediate | vertical 14 mm collided with preceding axis titles while panel headings were present |
| Revised canvas | 240 × 205 mm; a layout demonstration, not a prescribed publication size |
| Typography | Arial 7 pt base, 7.6 pt axis titles, 11 pt bold panel letters |
| Frame width | 0.5 pt |

The user has not approved these numbers as a universal standard. Without panel headings, a smaller vertical gap may work, but render and measure it first. Set the intended final publication width before choosing font sizes; shrinking this 240 mm demonstration to a journal column would also shrink its type.

## Typography and traceable measurements

- Record source observations separately from chosen reproduction settings. A screenshot supports approximate visible glyph heights and pixel gaps, not proof of font identity or original point size.
- Distinguish glyph ink bounds, font em size, text baseline and library label-padding values. Convert pt to px only at a stated DPI: px = pt × DPI / 72.
- Use consistent typography and deliberate hierarchy rather than setting every element to the same font size. Inspect math rendering, which may use a fallback font.

## Synthetic data and replication

- User-requested artificial data demonstrations must carry `DEMO · SYNTHETIC DATA` in all raster/vector previews and exports, including grayscale previews. Prefer reserved whitespace; keep it visible without covering scientific marks.
- Save raw CSVs, seed, generation assumptions and uncertainty definitions. Plot from those data rather than detached illustrative coordinates.
- Label repeated copies as a layout test, not independent experiments. Do not invent nine conclusions when three panels were copied three times.
- Keep repeated data and jitter identical when the purpose is exact replication. Read existing data when editing layout; avoid rerunning a data-generating script just to borrow its variables, which can overwrite unrelated outputs.
- Different units require correctly separated scales. Do not divide a power curve by an arbitrary constant to fit a voltage axis. Preserve algebraic consistency, such as power = current × voltage, for interpretable demonstrations.

## Verification and delivery

1. Profile data and choose chart forms appropriate to distributions, sample sizes and ordered axes. Use raw points for small groups and state SD/SEM/CI and n.
2. Render and actually inspect the exported image. Check full-canvas layout and enlarged difficult regions; a tool call that does not display the image is not visual inspection.
3. Check text bounds against the canvas, adjacent tick labels, neighboring panel text, legend/data collisions, right-hand axes, bottom labels and watermark. Passing a canvas-bound check alone does not prove no internal overlap.
4. For reference matching, compare at the same scale. For new data, confirm that geometry adapts to the new chart types. Inspect grayscale when color carries group identity; use markers/line styles as redundant encoding.
5. Export editable SVG/PDF and PNG. Report skipped checks honestly (for example, PDF font embedding could not be inspected without an available PDF parser).
6. Show the result inline with concise download links. State concrete fixes and remaining approximations; do not call a visual approximation an exact reconstruction.
