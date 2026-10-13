# Pixel Office

A responsive, static prototype for finding rooms, desks and landmarks on the Kv Poolen floor. No backend or build step is required.

## Run locally
Open `index.html` in a modern browser. For link sharing, Clipboard API is most reliable on HTTPS (GitHub Pages) or localhost.

## Publish with GitHub Pages
1. In repository Settings → Pages, select **Deploy from a branch**.
2. Choose `main` (after merging this branch) and `/(root)`.
3. Save. The site will be published at `https://design-tieto.github.io/pixel-map/`.

## Current prototype limitations
- The interactive SVG is a schematic starter, not a survey-accurate trace of the supplied architectural PDF.
- Desk identifiers D001+ are generated for the prototype and do not yet represent all 244 desks or their exact positions.
- Routing is a visual preview along a schematic corridor spine, not yet a verified accessible walking route.
- Shared location expiry is enforced by the client link parser; it is not server-side revocation and links can be copied.
- No colleague directory, live presence, login or central storage is included.

## Next build step
Trace the architectural source into accurate room polygons, 244 desk coordinates, entrances, corridors and walkable path nodes. Add a graph-based routing algorithm after the map geometry is verified.