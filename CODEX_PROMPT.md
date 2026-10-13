# Pixel Office — Codex brief

Continue on `feat/pixel-office-prototype`. Do not create another branch or merge the pull request.

## Interaction model
- The side panel is removed. Clicking a desk, room or arbitrary point opens a compact action popover next to that location.
- Popover actions: `Share this as your location` and `Mark this my starting point`. After a start is marked, selecting another place offers `Use this as destination`.
- Search selection opens the same popover and moves the selected highlight to that result. Selecting another place should remove the previous selected marker.
- The selected desk/room indicator should be substantially larger than idle markers.
- Reset must clear selected/start/destination, route, pulsing pin, search, popover, share modal, zoom transform, focused viewBox and scroll position.
- A shared link opens on the shared destination with the pulsing pin. The recipient clicks their current location and marks it as the start; preview a route to the fixed shared destination.

## Map source and routing
- Display `assets/floor-plan-hires.jpg`, never the old thumbnail.
- There are 243 candidate desk centres versus 244 desks in the source summary; resolve this mismatch.
- Confirm exactly one marker per real `MÖTE` meeting room.
- Route graph remains provisional; model verified door and desk-aisle connectors before describing routes as reliable.
- Keep static GitHub Pages hosting and client-side one-hour links. Run JavaScript checks and smoke-test selection, search, reset, sharing and map-edge popovers.
