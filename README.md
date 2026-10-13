# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. It runs as a static website and needs no backend.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## What is source-based now
- `assets/floor-plan.b64` is a cropped image of the supplied architectural drawing. The interactive map loads this as its visual base so the actual building footprint, furniture, rooms and desk groupings are visible.
- Room/space hotspots are placed using extracted text positions from the PDF. The source drawing repeats some identifiers and does not individually number desks.
- People can click a desk or any other point on the map to place a temporary pin and share it by link.

## Important limits
- The architectural image is an accurate reference image, not a vector-traced CAD model. Hotspots are point targets, not traced room polygons.
- Individual desk IDs D001–D244 are not currently offered as labelled hotspots because those IDs do not exist in the source drawing and the exact 244 desk-centre coordinates have not yet been validated.
- Routing uses a corridor waypoint graph and displays the route along the graph, stopping at corridor waypoints. Corridor segments, doorway connections and destination access points still need visual/on-floor validation; do not treat routes as operationally verified wayfinding yet.
- Shared location expiry is enforced client-side by the URL parser after one hour. It is not server-side revocation. No central storage, directory, login or live presence is included.

## Next QA / finish
1. Trace room polygons and individual desk centres from the architectural drawing in an editable SVG/data layer.
2. Audit every route node and edge against the actual corridor paths, lift lobby and door openings.
3. Add destination door access points and ensure route connectors do not pass through walls, furniture, private rooms or restricted space.
4. Validate representative routes from the lift lobby and manual pins to rooms in each wing, then test on desktop and mobile.
