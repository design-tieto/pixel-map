# Pixel Office — implementation and validation prompt for Codex

Continue development on the existing `feat/pixel-office-prototype` branch. Do not create a new branch or merge the pull request.

## Immediate bug fix
The map looked blurry because `index.html` was displaying the small `assets/floor-plan.b64` thumbnail. The repository now contains `assets/floor-plan-hires.jpg` (2600 × 2409); use this high-resolution asset as the map's visual base. Confirm the running page loads it directly. Do not reintroduce the base64 thumbnail loader.

## Source of truth
Use the original PDF `260921 Plan 4 Vån 3 PROGRAMSKISS MAX MÖBL. INREDNING.pdf` from the conversation as the authoritative plan. The office outline, desks, room locations, corridors, door openings, and landmark positions must match that drawing. Keep its geometry unchanged while styling the interactive display as a clean, colorful pixel-art map.

## Tasks
1. Run the page and verify that the loaded map is sharp at normal desktop and mobile view sizes. Confirm there is no thumbnail scaling, crop distortion, or overlay coordinate drift.
2. Align all room hotspots to verified room positions. Preserve IDs exactly as printed in the drawing; do not invent room labels or capacities.
3. There are currently 243 candidate desk centres detected from the PDF's vector shapes, while the drawing summary says 244 desks. Review the source to find whether a desk was missed or a non-desk shape was counted. Keep IDs D001… as app-only IDs and assign them consistently after geometry QA.
4. Replace the current approximate/candidate desk and room dots with a clean pixel-art map layer where useful: desks are individual clickable furniture objects; meeting rooms have traced boundaries and door openings; corridors remain visible and navigable; landmarks such as coffee stations and lifts are easy to recognize. The high-resolution architectural image is the reference, not the desired final UI aesthetic.
5. Build the walkable graph from verified corridor segments, junctions, and door openings. Use Dijkstra/A* to find paths. All edges must be physically walkable. Add explicit doorway/access connectors to the chosen destination; do not draw the entire route only to the nearest arbitrary waypoint.
6. Smoke-test sample paths from the elevator lobby to destinations on each wing and across the floor. Make sure no route crosses walls, furniture, room interiors without a doorway, open voids, or lift shafts.
7. Test room/desk search, custom map pin placement, sharing link parsing, expired/malformed links, and one-hour client-side expiry. Keep the limitation clear: without a backend, links cannot be centrally revoked and there is no shared live presence.
8. Maintain responsive layout, keyboard interaction, legible labels, and no console errors.

## Acceptance criteria
- The live page uses `assets/floor-plan-hires.jpg`, not the thumbnail.
- The actual source footprint and room/desk placement are preserved.
- Room and desk hotspots align visually with their real source objects.
- Desk count discrepancy is resolved or explicitly documented.
- Routes follow verified corridors and doors to the destination access point.
- README contains exact tests performed and known limitations.
- Do not claim operationally reliable wayfinding until the geometry has been verified.
