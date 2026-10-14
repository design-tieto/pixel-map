# Floor geometry

The map background is the vector drawing exported directly from the supplied PDF. Its paths, strokes, fills, furniture, rotations, labels, corridors, and planting details are retained from that source. The SVG page viewBox is cropped to the floor-plan area; no floor-plan shapes are redrawn or simplified.

- `floor-plan-source.svg.gz` is the original PDF SVG export compressed for delivery. The app decompresses it in the browser before displaying it.
- `desks.js` stores the 246 desk marker centers in the map's `0 0 850 779` overlay coordinate system.
- `floor-rooms.js` stores the room hotspot centers, hit areas, labels, and capacities in that same coordinate system.

When the source floor plan changes, replace the compressed vector export and review the marker overlays against it. Keep the PDF's geometry as the map background; use the overlay records only for interaction and search.
