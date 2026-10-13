# Pixel Office

Responsive static prototype for locating desks, rooms and landmarks on Kv Poolen, Plan 4 / Vån 3. It runs as a static website and requires no backend.

## Run / publish
Open index.html locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → main → /(root), after merging the prototype pull request.

## Current map and routing notes
- The SVG recreates the main curved footprint, two large open bays, meeting/focus room clusters, central lift lobby and desk zones from the supplied 2026-09-16 architectural drawing.
- Desk markers D001–D244 are individually selectable and searchable. The source plan does not assign individual IDs to desks, so these are app IDs.
- Room labels shown are transcribed from visible labels in the source drawing. This SVG is a hand-traced approximation, not a CAD/vector extraction. Verify every desk hotspot, room coordinate, door opening and path connection against the original PDF before operational use.
- Directions use a weighted graph of corridor waypoints and room/desk access assignments. This is better than a straight-line/schematic route, but the graph and access points still require on-floor or CAD validation before being treated as exact accessible directions.
- Location sharing is a URL fragment with a one-hour client-side expiry. There is no server-side revocation, directory, login or live presence.

## Next QA
Compare the SVG against the source PDF at high zoom. Adjust every room boundary, desk marker and doorway. Then walk-test sample routes from the lift lobby to representative rooms and desk clusters. Ensure routes never cross walls, furniture or restricted areas.
