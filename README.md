# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. No backend or build step is required.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## Map and locations
- The map uses the high-resolution `assets/floor-plan-hires.jpg` image; the old `assets/floor-plan.b64` thumbnail must not be loaded.
- There are 243 desk-position candidates extracted from PDF vector geometry. The drawing summary says 244 desks, so one position remains to be found and verified.
- Meeting-room targets are visible pink `M` markers, positioned at the centre of the inferred pink room rectangles. They represent the 32 currently identified `MÖTE` room candidates; confirm room IDs and ensure each actual meeting room has exactly one target.
- Room targets are point hotspots, not fully traced room polygons. Desk IDs such as D001 are app IDs, not printed labels in the architectural plan.

## Interaction
- Map clicks now define the route: first click = start; second click = destination and route preview. A third click starts a new route selection.
- The separate “I'm here”, “Set as my starting point”, and “Show directions” actions have been removed. Select a single place and use “Share this location” to share it.
- Opening a shared link focuses the map on the shared target and shows a large pulsing, labelled red pin. The recipient then clicks their current point once to request a route preview to the shared destination.
- The share URL expires client-side after one hour. There is no central presence, server-side revocation, database or authentication.

## Directions status
- The route is a provisional corridor preview using a 21-waypoint / 23-edge hand-entered graph. It no longer uses large route arrowheads.
- The line currently shows the corridor waypoint path; its exact approach to a clicked desk or room is not fully modelled. Room doors, desk aisles and destination connectors have not been validated end to end, so do not treat the route as reliable door-to-door wayfinding yet.
- A connected graph is not proof that its edges are physically walkable. Validate every route edge and room access point against the PDF, and walk-test representative routes before describing routing as reliable.

## Remaining validation
1. Resolve the 243-versus-244 desk mismatch and verify every desk marker centre.
2. Confirm the 32 meeting-room targets correspond one-for-one to actual rooms labelled `MÖTE`; correct IDs/locations as needed.
3. Trace room boundaries, door openings and aisle/corridor access points in editable SVG/data.
4. Connect each desk and meeting room to a verified walkable access node; never route through walls, furniture, room interiors without a door, lift shafts or central voids.
5. Test manual two-click routing, routes to rooms on all wings, shared-link targeting/expiry, search, reset, keyboard access and responsive layout.
