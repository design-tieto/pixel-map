# Pixel Office — Codex implementation and validation brief

Continue on the existing `feat/pixel-office-prototype` branch. Do not create another branch or merge the pull request.

## Latest interaction changes
- Use `assets/floor-plan-hires.jpg`, never the legacy low-resolution `assets/floor-plan.b64` thumbnail.
- The main map workflow is now two clicks: first click selects the start, second click selects the destination and draws the route preview; a third click starts a new route.
- The separate `I'm here`, `Set as my starting point`, and `Show directions` buttons have been removed. There is one share action for the selected location.
- Meeting-room targets are visible pink circles with an `M` label and use centre coordinates of the currently inferred meeting-room rectangles. There are 32 candidates, but verify that each real room labelled `MÖTE` has exactly one target and that the ID/position is correct.
- Opening a shared link focuses the map on the selected room/desk and shows a large, labelled red pulsing pin. The recipient should click their current point once to preview a route to the shared destination. Ensure the shared destination remains the endpoint when starting point is selected.
- Route styling is now a smaller dashed line without giant arrowheads. Keep the exact selected destination marked with the pulsing pin.

## Source of truth
Use `260921 Plan 4 Vån 3 PROGRAMSKISS MAX MÖBL. INREDNING.pdf` as the authoritative plan. Preserve the real outline, desk centres, room boundaries, corridors, door openings and landmarks. Do not invent missing geometry.

## Priorities
1. Validate all desk markers against the current image/PDF. 243 candidate centres were found, while the drawing summary states 244 desks; identify the missing desk or any false-positive candidate.
2. Audit the meeting room list against the actual `MÖTE` labels and pink room rectangles. Place exactly one interactive location per meeting room, centred within each real meeting-room shape, and preserve the room ID printed in the source.
3. Replace guessed room/space dots with room-boundary polygons and doorway access points where feasible.
4. Replace nearest-waypoint snapping with explicit connections from a selected desk/room to a verified aisle/corridor access node.
5. Verify every graph edge against walkable space. Use Dijkstra/A* only over verified corridor/doorway links. The route must end at the selected destination via a real access path and must not cross walls, furniture, restricted rooms, voids or lift shafts.
6. Test two-click routes from multiple starting points to destinations in each wing. Test shared links (valid, expired, malformed), and ensure clicking the start point on a shared link doesn't replace the shared destination.
7. Keep responsive layout, keyboard access, reduced-motion support, one-hour client-side link expiry, and static GitHub Pages hosting.
8. Run JavaScript syntax checks and practical smoke tests. Document exactly what was verified; never claim accurate indoor routing until geometry and doors are validated.

## Acceptance criteria
- Each real desk and each real `MÖTE` room has one correctly positioned, selectable marker.
- First map click is start; second is destination; route appears without a separate directions button.
- A shared link opens focused on a clearly visible pulsing destination and recipient can click their position to preview the route.
- Route follows verified walkable corridors and enters/leaves rooms only via actual doors.
- No backend or build step is required.
