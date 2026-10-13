# Pixel Office — implementation and validation prompt for Codex

Continue on the existing `feat/pixel-office-prototype` branch. Do not create a new branch or merge the pull request.

## Current UX fixes
- The page must display `assets/floor-plan-hires.jpg`, never the blurry `assets/floor-plan.b64` thumbnail.
- Desk markers need to align with the real desk/table rectangles in that crop. Current candidate centres are embedded in `index.html` in the 850 × 779 viewBox coordinate system. Verify visually at high zoom before changing any image crop or the viewBox.
- Desk markers are larger and clearer now; keep idle desk targets visible but not overpowering. Room hotspots should stay low-clutter until selected.
- On a valid shared link, automatically zoom toward the target and display a large, red, animated pin with a readable label. Respect reduced-motion preferences. The map's fit control must return to the full floor.
- Route lines have arrowheads and the selected destination gets the large pin. The route is still a preview because room/desk access connectors are not yet fully modelled.

## Source of truth
Use the original PDF `260921 Plan 4 Vån 3 PROGRAMSKISS MAX MÖBL. INREDNING.pdf` from the conversation as authoritative. Preserve actual building outline, desk arrangement, room boundaries, corridors, doorways and landmarks. Styling can be pixel-art, but must not change geometry.

## Next priorities
1. Compare all desk markers with `assets/floor-plan-hires.jpg` and source PDF. Correct any offset/scale mismatch, and resolve why the drawing summary says 244 desks but current vector detection finds 243 candidate centres. Desk IDs D001… are app IDs, not printed labels.
2. Verify all room IDs/positions and draw room shapes and door openings as editable SVG geometry.
3. Replace nearest-waypoint-only routing with explicit walkable access nodes: each selected desk should be connected to a real aisle/corridor path; each room should connect at its actual doorway. Every edge must represent physically walkable space.
4. Use Dijkstra/A* over the verified graph. Draw the corridor route plus validated desk/room connectors, arrows and start/destination markers. Never route across walls, furniture, lift shafts, room interiors without door access, or the central open voids.
5. Test routes from multiple start locations to destinations in each wing, including rooms, perimeter desks and the shared elevator lobby. If a destination has no verified access node yet, say so rather than inventing a route.
6. Test shared URLs (valid, expired, malformed and custom pins), auto-zoom, blinking pointer, Fit map reset, search, desktop/mobile, and prefers-reduced-motion.
7. Update README with what was actually tested and remaining caveats.

## Acceptance criteria
- Image is sharp and desk dots align to real desk centres.
- A shared link opens focused on the correct location, with a large blinking/pulsing labelled pin.
- Directions visibly reach the selected destination through verified doorways and corridors.
- No route is claimed accurate until its actual path and destination access have been checked.
- Static hosting continues to work on GitHub Pages without a backend or build step.
