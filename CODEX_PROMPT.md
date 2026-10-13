# Pixel Office — Codex project brief

Continue on `feat/pixel-office-prototype`. Do not create another branch or merge the pull request unless asked.

## Product scope
Pixel Office is only for finding and sharing locations on the office map. Remove directions completely: no route graph, start/end-point selection, route preview, routing arrows or directions UI.

## Interaction
- Clicking a desk, meeting room, landmark, or map point opens a compact popover next to that location with one action: `Share this as your location`.
- Only the current selection is highlighted. Selected desks and rooms use a large pulsing marker.
- Search provides a dropdown of matching desk IDs, meeting-room IDs/numbers and landmarks while typing. Selecting a result focuses the map, highlights it, and opens the same share popover.
- Reset clears selection/pulse, shared-location pin, popover, query/dropdown, share dialog, zoom/viewBox and scroll.
- Shared links expire client-side after one hour. Opening a valid link focuses the map and shows a prominent pulsing, labelled pin. No backend or live presence.

## Map accuracy
- Use `assets/floor-plan-hires.jpg`, never `assets/floor-plan.b64`.
- Twenty manually positioned candidate points were added for corner/curved-edge desks in response to the user's screenshot. Check every one against the source furniture. Current target count is 263 versus 244 in the drawing summary; reconcile duplicates/false-positive points.
- Verify exactly one marker for each real room labelled `MÖTE`.
- Keep static GitHub Pages support. Test dropdown search, selection, share links and reset.
