# Pixel Office

Static responsive office map for Kv Poolen, Plan 4 / Vån 3. Find a desk or meeting room and share its location.

## Desk coordinates and IDs
- Desk centre candidates use the vector-tracing dataset in `office_trace/desk-centres-poly.csv`, which includes rotated/curved-corner desks missed by the earlier axis-aligned detector.
- Desk IDs are assigned deterministically after spatial sorting. The numbering starts at the top-left corner, proceeds across the top edge, down the right side, across the bottom toward the left, up the left side, then numbers interior desks row-by-row.
- Current traced candidate count: 258. This uses traced geometric centres, not the previously inserted manual points through the central open void.
- The count must still be checked against the drawing's stated inventory and candidates in meeting rooms/tables. Do not claim one-to-one completeness until visually audited.

## Finding and sharing
- Use `assets/floor-plan-hires.jpg` as the map image.
- Clicking a desk or meeting-room marker opens a compact share popover.
- Search offers a dropdown of matching desk IDs, room IDs, and landmarks.
- Share links expire client-side after one hour; there is no backend, authentication, or live colleague presence.
- The project deliberately has no walking directions or route functions.

## Remaining QA
1. Visually verify every traced centre against a real desk surface, particularly rotated curved-corner desks and furniture inside meeting rooms.
2. Compare the 258 candidate centres against the plan's stated desk count and remove non-desk shapes.
3. Confirm that the new D001 ordering begins at the top-left corner and stays stable across edits.
4. Test search, share links, reset, and mobile behaviour.
