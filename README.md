# Pixel Office

Responsive static prototype for Kv Poolen, Plan 4 / Vån 3. No backend or build step is required.

## Run / publish
Open `index.html` locally or enable GitHub Pages from the repository root. On GitHub Pages, use Settings → Pages → Deploy from a branch → `main` → `/(root)`, after merging the prototype pull request.

## Floor-plan assets
- `assets/floor-plan-hires.jpg` is the high-resolution crop (2600 × 2409) from the supplied architectural PDF. This is the image the app should render.
- `assets/floor-plan.b64` is the old low-resolution thumbnail retained for reference only. Do not use it as the displayed map; it makes the floor plan blurry.
- Interactive targets use the coordinate frame in the SVG viewBox. Verify alignment after any change to image crop or aspect ratio.

## Interactions
- Room/space hotspots are currently point targets inferred from PDF text positions.
- The app has 243 candidate desk centre hotspots detected from vector shapes. The source drawing summary indicates 244 desks, so one candidate/desk discrepancy still needs verification. Desk IDs D001… are app IDs, not labels printed in the drawing.
- Users can manually choose a starting point, share a location link, and search supported desk, room and landmark identifiers.

## Navigation status
The corridor network is a provisional waypoint graph. A connected graph is not proof that routes are physically valid. Door openings and the final approach into rooms/desks still require geometry validation against the source drawing and ideally an on-floor walk-through. Treat current directions as a preview, not verified accessible wayfinding.

## Privacy
Location is encoded in a URL fragment and expires client-side after one hour. It is not server-side revocation. There is no central storage, login, colleague directory, or live presence.
