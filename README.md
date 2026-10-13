# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. It runs as a static website and needs no backend.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## Map and desk hotspots
- The map displays `assets/floor-plan-hires.jpg`; the old `assets/floor-plan.b64` thumbnail is no longer loaded.
- Desk hotspots are based on PDF vector-shape centre candidates in the map's 850 × 779 coordinate frame. The data has 243 candidates while the drawing summary states 244 desks, so one position still requires verification.
- Desk targets now have a stronger green fill, dark outline and a larger hit area. Compare them with the source drawing if the crop or SVG viewBox changes.
- Room/space targets are point hotspots inferred from PDF text coordinates. They are not room-boundary or doorway traces.

## Shared location
A valid shared link automatically focuses the map on the location and displays a large labelled red pin with a pulsing halo. Reduced-motion preferences are respected. The fit control returns to the full map while keeping the destination visible. The URL's one-hour expiry is client-side only; there is no server-side revocation, central storage, login, colleague directory or live presence.

## Directions
- The corridor route uses Dijkstra over a 21-waypoint / 23-edge provisional graph and displays red directional arrows.
- Start/destination points are snapped to a corridor waypoint in the same broad floor zone to avoid some obviously wrong nearest-node connections across the central voids.
- This is still a corridor-route preview. Desk approach routes and actual door access points are not fully modelled, so the line does not yet prove a reliable door-to-door walking route. Do not claim operational wayfinding until each corridor edge, room entrance and desk approach has been checked against the source plan and representative routes have been walk-tested.

## Remaining validation
1. Reconcile 243 detected desk centres with the stated 244 desks, then validate each centre against the drawing.
2. Trace room boundaries and doorway access points as editable SVG geometry.
3. Connect every room/desk to a validated walkable aisle/corridor access point instead of relying on broad zone snapping.
4. Test routes from the elevator lobby and representative starts to destinations throughout all wings. Ensure no line crosses walls, furniture, room interiors without doors, lift shafts or the central voids.
5. Test valid/expired/malformed share links, auto-zoom, destination pin visibility, fit/reset, search, and mobile interaction.
