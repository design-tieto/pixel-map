# Pixel Office

Static, responsive office map for Kv Poolen, Plan 4 / Vån 3. Find a desk or meeting room and share its location. No backend or build step is required.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root.

## Finding and sharing
- The map displays `assets/floor-plan-hires.jpg`; do not use the blurry `assets/floor-plan.b64` thumbnail.
- Clicking a desk, meeting room, landmark, or arbitrary point opens a small popover beside it with one action: `Share this as your location`.
- Search has a dropdown of matching desk IDs, meeting-room numbers, and landmarks. Selecting a result focuses the map, highlights that place, and opens the share popover.
- Shared links expire client-side after one hour. A valid link focuses the map on the location and shows a prominent pulsing pin. No server-side revocation, database, authentication, or live colleague presence is included.
- Twenty manually positioned corner/curved-edge desk targets were added from the user's screenshot. These placements need visual QA against individual desk rectangles.
- The map currently shows 263 selectable desk targets. The source summary states 244 desks; reconcile extra candidates, duplicates and any false-positive locations before claiming a complete one-to-one desk inventory.
- Pink `M` targets represent inferred meeting-room candidates and need a one-to-one audit against actual rooms labelled `MÖTE`.

## Scope
Walking directions, route graphs, route previews, and start/end-point selection have been removed. Pixel Office is only for finding and sharing locations.

## Remaining validation
1. Check the added corner targets against the source image and reconcile the desk count against 244 physical desks.
2. Confirm exactly one target for each meeting room.
3. Test dropdown search, selecting a result, sharing links, expiry, popup placement, and reset after focused shared links.
