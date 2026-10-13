# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. It runs as a static website and needs no backend.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## Map assets and alignment
- `assets/floor-plan-hires.jpg` is the high-resolution plan image and should be the displayed map. The old `assets/floor-plan.b64` file is a low-resolution thumbnail and must not be used.
- Desk point coordinates are currently embedded in `index.html` and were derived from PDF vector geometry in the floor-plan coordinate frame (850 × 779). The 243 candidate centres were visually overlaid on the high-resolution crop during development; one desk remains unaccounted for compared with the 244-desk summary on the drawing.
- Desk markers are intended to sit on the desk rectangles; check them at high zoom if the image crop or viewBox changes. Keep dots large enough to select and clearly visible without obscuring furniture.
- Room/space hotspots are point targets inferred from PDF text positions, not accurate room polygons.

## Location sharing
Shared links carry the target location and an expiry timestamp. Opening a valid link zooms the map toward the selected location and displays a large animated pin with a label. Expiry is client-side only: no server-side revocation, central storage, login, colleague directory, or live presence.

## Directions status
The red arrow path uses a 21-waypoint / 23-edge corridor graph that avoids the two main central voids. This is a **route preview**, not yet verified door-to-door directions: selecting a desk/room currently associates it to a nearby corridor waypoint, and the exact approach connector is not fully modelled. Do not claim routes are operationally reliable until the corridor edges, room doorways, and desk approaches are traced and validated against the PDF (ideally also by walking representative routes).

## Remaining engineering work
1. Verify all 243 detected desk centres and resolve the mismatch with the 244-desk summary.
2. Trace room boundaries and door openings as editable vector geometry.
3. Add explicit access nodes/connectors from each desk and room doorway to the walkable corridor graph, so routes visibly and safely reach the target rather than ending at a nearby corridor node.
4. Test routes across each wing and confirm no route crosses walls, furniture, room interiors without a doorway, lift shafts, or the central open voids.
5. Smoke-test shared link focus/pin visibility, expiry, search, reset/full-map control, and responsive mobile layout.
