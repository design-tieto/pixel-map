# Codex follow-up prompt: make Pixel Office map accurate

Work in this repository and preserve the current responsive visual style and static-hosting approach.

The supplied source drawing is “KV POOLEN–INREDNING / Plan 4 Vån 3”, dated 2026-09-16. Treat it as the source of truth. Do not invent the building footprint, desk locations, room locations, corridors, room entrances or labels.

## Priorities
1. Replace the schematic inline SVG in index.html with a separate, clean SVG asset traced from the source floor-plan drawing. Keep the source drawing only as a reference if its image file is added to the repository.
2. Trace the overall curved building outline, central open areas, all corridors, room walls and door openings.
3. Place and label all 244 desk markers individually. IDs D001–D244 are app IDs; the architectural drawing does not individually number all desks. Use a maintainable data file with x/y coordinates.
4. Recreate all room IDs and landmark locations from the drawing. Preserve the exact IDs visible in the source.
5. Build a walkable graph from real corridor segments and doorways. Use A* or Dijkstra for shortest routes. Never route through walls, furniture or rooms without passing through an entrance.
6. Test search for room IDs, desk IDs and landmarks; test share links with valid, expired and malformed payloads; test route from a manually selected start to a destination.
7. Keep the app static: plain HTML/CSS/JavaScript/SVG, no backend, no framework or build step unless necessary. Location sharing should remain link-based and client-side for this version.
8. Keep the interface responsive and keyboard accessible. Clearly label any unverified coordinate or route instead of presenting it as accurate.

The drawing notes include 244 desks, 22 meeting rooms for four people, two for ten people, two for two people, focus rooms, coffee stations, elevators, lounge and other support spaces. Verify counts and labels against the supplied drawing rather than relying only on this summary.

## Done means
- Every intended desk/room can be selected and searched.
- Destination highlights accurately.
- Route uses traced walkable pathways and doors.
- No console errors; test desktop and mobile.
- Document the coordinate data format and validation process in README.md.