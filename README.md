# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. No backend or build step is required.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## Map source and interactions
- `assets/floor-plan.b64` is a cropped image of the supplied architectural PDF. It preserves the actual footprint, furniture, rooms, desk banks and corridors as the visual reference.
- Room/space hotspots are placed using room identifiers extracted from PDF text positions. The background drawing remains visible, so users can also click any exact point, including a desk, to place a custom pin.
- The PDF does not assign individual IDs to the 244 desks. The app does not invent D001–D244 hotspots; use manual pin placement until desk centres are individually surveyed and mapped.
- The map is an image with point hotspots, not yet a full vector tracing of every room polygon, desk centre or door opening.

## Navigation
- Directions use Dijkstra over a hand-entered corridor waypoint graph. The graph routes around the two large central voids and highlights only the corridor waypoint path.
- The selected room / custom pin is shown separately from the route. Specific doorway connectors from corridors to rooms, and all corridor links, still require validation against the source drawing (and ideally a walk-through). Treat the current route as an orientation preview, not verified accessible wayfinding.
- Do not represent route accuracy as operationally verified until the graph’s geometry, doorway edges, and destination access points have been checked.

## Temporary sharing and privacy
Location is encoded in a URL fragment and considered expired by this client after one hour. There is no server-side revocation, central storage, login, colleague directory or live presence.

## Remaining engineering work
1. Vector-trace all room boundaries and doors and position hotspots at doors as well as room labels.
2. Individually locate each real desk centre from the source/CAD data, then assign stable app IDs only after verifying the coordinates.
3. Validate the corridor graph and door connectors against the architecture, test routes from the lift lobby to rooms in every wing, and check mobile interactions.
