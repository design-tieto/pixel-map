# Pixel Office — Codex implementation and validation brief

Continue on the existing `feat/pixel-office-prototype` branch. Do not create a new branch or merge the pull request.

## User feedback being addressed
- Keep the high-resolution map asset `assets/floor-plan-hires.jpg`; never reintroduce the old `assets/floor-plan.b64` thumbnail.
- Desk dots must align to real desk centres, be easy to see, and remain clickable. Current candidate coordinates were extracted from PDF vector geometry into the SVG 850 × 779 coordinate frame; there are 243 candidates compared with 244 desks in the drawing summary. Validate and resolve that discrepancy, and correct any real coordinate offsets.
- A shared-location link must open zoomed to the place, with a large, labelled, blinking/pulsing red location pin. Keep reduced-motion support. The Fit map action should retain the pin.
- Directions must not be presented as fully accurate yet. The current graph is a provisional corridor preview, and room/desk door-level access connectors are not verified.

## Source of truth
Use the original PDF `260921 Plan 4 Vån 3 PROGRAMSKISS MAX MÖBL. INREDNING.pdf` from the conversation as authoritative. Preserve building footprint, desk arrangements, rooms, corridor widths, doorways and landmarks. Pixel-art styling can simplify colours/shapes, but it must not change the geometry.

## Priority tasks
1. Visually verify all desk markers against the current high-resolution crop and source PDF. Resolve 243-versus-244 before claiming desk coverage is complete. IDs D001… are app IDs, not identifiers printed in the source.
2. Trace room boundaries, doors, corridors and landmarks as editable geometry with a common coordinate system.
3. Build the walkable graph from verified corridor centres, junctions and door openings. For every desk, add a safe route connector to its real aisle; for every room, route to the actual door. Do not connect using straight lines that pass through walls, furniture, room interiors without a door, lift shafts or central open voids.
4. Use Dijkstra/A* on verified weighted edges. Draw the path with arrows, start marker, final destination marker, and the necessary access connectors. If access geometry is not verified, label the result a preview or decline to draw the route.
5. Test starts/destinations in every wing and the elevator lobby. Verify that each route is physically walkable.
6. Test share URLs: valid, expired, malformed and custom pins; verify the location zoom, large pulsing marker, Fit map behaviour, accessible/reduced-motion state, search and mobile layout.
7. Run a smoke test and update README with exactly what was checked and what remains unverified.

## Acceptance
- Desk markers visibly and accurately sit on real desks.
- Shared links make the exact destination unmistakable, including after zoom and on mobile.
- Routes follow verified corridors and enter rooms through the correct door, or are explicitly labelled as unverified previews.
- Static GitHub Pages hosting remains supported with no backend.
