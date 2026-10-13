# Pixel Office

Pixel Office is a static floor map for finding and sharing desk and meeting-room locations.

## Map source

The map background comes from the supplied Plan 4 / Vån 3 PDF's original SVG export. The SVG paths, fills, strokes, furniture, rotations, labels, corridors, and planting details are kept from the export. Only the SVG page viewBox is cropped to the plan; no architectural geometry is redrawn. The compressed SVG is decompressed by the browser before display.

Desk and room markers are separate interactive overlays in the app's `0 0 850 779` coordinate system. The datasets contain 244 desk markers and 34 room records; the desk count alone does not prove every marker is centered correctly.

## Verification

- Confirmed the compressed asset expands to valid SVG with a `216 77 666 618` viewBox and 152,854 PDF-exported paths.
- Confirmed 244 unique desk IDs and 34 unique room IDs.
- Rendered the PDF plan crop with desk and room marker centers overlaid for a full-map visual comparison.
- Checked the inline JavaScript syntax and `git diff --check`.

The feature branch has not yet been verified in Chrome or Edge as a running app. The public site may continue to serve its configured branch until deployment settings include this feature branch.
