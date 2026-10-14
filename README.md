# Pixel Office

Pixel Office is a static floor map for finding and sharing desk and meeting-room locations.

## Map source

The map background comes from the supplied Plan 4 / Vån 3 PDF's original SVG export. The SVG paths, fills, strokes, furniture, rotations, labels, corridors, and planting details are kept from the export. Only the SVG page viewBox is cropped to the plan; no architectural geometry is redrawn. The compressed SVG is decompressed by the browser before display.

Desk and room markers are separate interactive overlays in the app's `0 0 850 779` coordinate system. The datasets contain 246 desk markers and 34 room records; the desk count alone does not prove every marker is centered correctly.


## Location search and sharing

The room picker includes every room and named destination in a scrollable, searchable list with a live result count. The kitchen, coffee stations, and lounge are represented by one Kitchen destination. The sidebar identifies Arenastaden floor 3 and explains how to find or share a location; the map does not support booking.

## Verification

- Confirmed the compressed asset expands to valid SVG with a `216 77 666 618` viewBox and 152,854 PDF-exported paths.
- Confirmed 246 unique desk IDs and 34 unique room IDs.
- Rendered the PDF plan crop with desk and room marker centers overlaid for a full-map visual comparison.
- Checked the inline JavaScript syntax and `git diff --check`.
- Verified the deployed feature branch in Chrome: the PDF-derived plan loaded; searches for D001, D122, and D244 selected their desks; room 04F021 showed 10P; search selection preserved the manual zoom; manual zoom, map scrolling, and Reset worked.

GitHub Pages now publishes `feat/pixel-map-vector-trace`. The branch remains unmerged.
