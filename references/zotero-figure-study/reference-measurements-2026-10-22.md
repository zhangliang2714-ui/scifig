# Reference figure: corrected measurement profile

Corrected 2026-10-23. Source: user-supplied 1384 × 1014 raster image, filename codex-clipboard-af4b8067-aac1-4ef6-b590-5cf3f18ee63b.png. These are conventions from ONE supplied figure, not universal Nature/Science requirements. The journal identity is not established from this crop alone.

## Correction to the previous version

The previous table mixed crop-local coordinates with whole-image coordinates and mistook some text positions for frame boundaries. Its B/D/E/F aspect ratios and resulting recommendations were incorrect and are superseded by this document. Use whole-image top-left coordinates consistently. Never apply crop-local coordinates directly to the original image.

## Frame centerlines (observed, approximately ±2 px)

| Panel | Whole-image (left, top, right, bottom), px | Width × height, px | Width / height |
|---|---|---|---|
| A | 153, 38, 451, 278 | 298 × 240 | 1.242 |
| B | 571, 38, 869, 278 | 298 × 240 | 1.242 |
| C | 1029, 38, 1327, 278 | 298 × 240 | 1.242 |
| D | 153, 370, 451, 610 | 298 × 240 | 1.242 |
| E | 571, 370, 869, 610 | 298 × 240 | 1.242 |
| F | 1029, 370, 1327, 610 | 298 × 240 | 1.242 |
| G | 153, 717, 451, 957 | 298 × 240 | 1.242 |
| H | 605, 717, 869, 957 | 264 × 240 | 1.100 |

H contains two adjacent sub-axes with different units; the stated box is the total envelope. I is a polygon radar, not a circular polar grid. Its envelope must be treated separately.

Frame-to-frame horizontal whitespace: 120 px between columns 1–2 and 160 px between columns 2–3 in the first two rows. Vertical frame-to-frame whitespace: 92 px then 107 px. These spaces contain ticks, titles, units and panel letters; they are not all blank padding.

## Text spacing: visual estimates, not original typesetting metadata

- Bottom tick glyphs begin approximately 10–13 px below the frame; x-axis title glyphs begin approximately 34–39 px below it (A/E). Measure to visible glyph bounds, not the text baseline.
- Left tick glyphs end approximately 12–17 px before the frame. Rotated axis titles usually have their nearest visible ink approximately 43–52 px from the frame, varying with tick width and math notation.
- Legend first-row visible ink starts about 10–15 px inside the top/left edges. Do not confuse the legend container padding with its visible glyph inset.
- Panel letters A/B/C start near x=77/493/949, y=27; D/E/F near y=347; G/H/I near y=695. Letters belong to the outer panel layout, not a fixed offset from every axes box.
- Approximate visible glyph height: tick and legend letters 13–16 px, axis titles 16–19 px, bold panel letters 24–28 px. Capital, lowercase and math glyphs differ; these are not font em sizes.
- Frame strokes look approximately 1 px wide. Raster antialiasing and resampling prevent recovery of an exact original vector stroke width.

## Reproduction settings (chosen, not measured font identity)

Canvas 1384 × 1014 px at 150 dpi; inches = pixels / dpi. Arial text, DejaVu Sans math fallback. Tick 7.6 pt, title 8.2 pt, legend 7.0 pt, panel letter 13 pt bold. At 150 dpi these em sizes correspond to 15.8 / 17.1 / 14.6 / 27.1 px, respectively; visible glyph height is smaller and must be checked by rendering. Frame 0.4 pt (~0.83 px), curve 0.55–0.75 pt, tick 0.35 pt. These pt values only apply to this chosen physical canvas. Rescaling to a publication width requires proportional adjustment and a new readability check.

Do not claim Arial is the exact source typeface or that screenshot pixels reveal the original point size. The PNG has no reliable publication-scale calibration.

## Repeatable reference-matching procedure

1. Preserve the original raster and its pixel dimensions. Crop by actual panel content, including both axes and labels, rather than slicing equal thirds.
2. Record frames in whole-image coordinates; store any crop origin explicitly. Verify detected lines visually so text baselines are not mistaken for spines.
3. Build fixed axes rectangles: [left/W, 1-bottom/H, width/W, height/H]. Preserve the canvas; avoid tight-bbox export, which changes margins and aspect.
4. Match frame geometry before adjusting text. Distinguish font em size, visible glyph bounds, baseline, and label-padding settings.
5. Use genuine independent axes for distinct units. Keep power consistent with voltage × current when generating a physically interpretable demonstration.
6. Inspect same-size source/reconstruction crops at 100% and enlarged scale. Check axis title spacing, legends, superscripts, panel letters, right axes and bottom-row text. Check rendered text bounds for canvas clipping; that check alone does NOT prove no internal overlaps.
7. Keep source observations separate from chosen implementation settings in JSON/Markdown. A single example is a reference-specific preset, not a global plotting constraint.

## Current artifact scope

The v3 figure demonstrates geometry and typography with synthetic values, not recovered experimental data. Catalyst names are retained only to test reference-like text widths. Curves, scatter IDs, error bars and radar values must not be cited as paper results. Exact marker density, radar tick annotations and font matching remain approximate.
