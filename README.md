# Pixel Office

Responsive static office map for Kv Poolen, Plan 4 / Vån 3. It is suitable for GitHub Pages and needs no backend.

## Map and locations
- Uses `assets/floor-plan-hires.jpg`; do not load the old `assets/floor-plan.b64` thumbnail.
- There are 243 desk-position candidates from PDF vector geometry, while the drawing summary states 244 desks. One location remains to be verified.
- Pink `M` meeting-room targets are inferred from room rectangles. Confirm a one-to-one match to each real `MÖTE` room.
- Desk IDs such as D001 are app IDs, not printed labels. Room and desk markers remain point targets, not full vector-traced polygons.

## Interaction
- The side panel is removed. Clicking a desk, room or map point opens a small contextual action menu beside it.
- The menu lets a user share the selected place or mark it as their starting point. Once a start is set, another selected place offers `Use this as destination`.
- Search selection opens the same menu; clicking another map item transfers the highlight and menu to the newly selected item.
- Reset clears start/destination, route, pins, selected marker, popup, search query, share modal, zoom, pan and focused viewBox.
- A valid shared link focuses the map on the destination with a large pulsing pin. The recipient chooses their own point and marks it as the start to preview a route to the shared destination.
- Share links expire client-side after one hour. There is no server-side revocation, database, authentication or live presence.

## Directions status
The route uses a provisional corridor waypoint graph. It is not yet fully connected to validated room doors and desk aisles; route lines are previews, not verified door-to-door navigation. Validate all graph edges and target access paths against the PDF and ideally by walking representative routes.

## Remaining validation
1. Resolve the 243-versus-244 desk mismatch and verify desk centres.
2. Verify exactly one location target for every actual meeting room labelled `MÖTE`.
3. Trace room boundaries/doors and connect desks and rooms to verified walkable access nodes.
4. Test selection, search, reset after zoom/share/route, popup position near map edges, share-link expiry and routing across each wing.
