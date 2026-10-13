# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. No backend or build step is required.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## Map source and interactions
- `assets/floor-plan.b64` is a cropped image of the supplied architectural PDF, used as the map's visual base.
- Room/space hotspots are positioned from text coordinates extracted from the PDF.
- Desk hotspot candidates were detected from 243 repeated white, four-edge vector shapes matching the desk rectangle geometry in the PDF; their centres are mapped into the same plan coordinate system. IDs D001-D243 are app IDs assigned in extraction order, not identifiers printed on the drawing.
- The drawing summary states 244 desks (180 in the main area + 64 at Cards), while this geometry filter detects 243 desk-like surfaces. This one-desk mismatch remains unresolved; do not assume a complete 244-point inventory until that last position is identified.
- The background image is still a raster reference; hotspots are point targets, not full vector-traced room polygons.

## Navigation
- Directions use Dijkstra over a hand-entered corridor waypoint graph and route around the central open bays.
- Desk and room positions are mapped to the nearest corridor waypoint for now. The destination doorway/desk approach connector is not yet geometrically verified, so the highlighted route is a corridor-route preview, not fully verified accessible wayfinding.
- Before operational use, validate each corridor edge and doorway against the source drawing and a physical walk-through. Ensure routes do not pass through walls, furniture, lift shafts, or restricted areas.

## Temporary sharing and privacy
Location is encoded in a URL fragment and considered expired by this client after one hour. There is no server-side revocation, central storage, login, colleague directory or live presence.

## Remaining engineering work
1. Resolve the 243-vs-244 desk count mismatch and verify all desk centres.
2. Trace room boundaries and doorway access points as editable vector geometry.
3. Replace approximate room/desk-to-corridor nearest-node connections with validated doorway/path connectors.
4. Validate routes from the lift lobby to rooms in every wing, then test on desktop and mobile.
