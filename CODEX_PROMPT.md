# Accurate floor-plan and routing QA

Continue on this feature branch. Use the supplied source file named “Plan 4 Vån 3 PROGRAMSKISS MAX MÖBL. INREDNING.pdf” as the source of truth.

1. Compare index.html's inline SVG to the PDF at high zoom and correct the outer building trace, all room locations and identifiers, corridors, door openings, desk footprints and landmark coordinates.
2. Inspect and correct all 244 generated desk hotspot coordinates. D001–D244 are app IDs, not IDs printed on the source plan. Make them distinct, stable, and place them on real desks only.
3. Refine the corridor graph and each room/desk access association. Graph edges must follow genuinely walkable corridors and doorways; do not route through rooms, walls, desks, lift shafts, voids or storage.
4. Use Dijkstra or A* over weighted nodes; draw a route as a path along edges and only short access connectors at the start/destination. Add route QA cases from elevator lobby to multiple rooms, desk clusters and landmarks on different wings.
5. Verify all visible labels against the source; do not silently invent room IDs or capacities. Preserve the playful style, responsive interface, keyboard access, search and one-hour link sharing.
6. Smoke-test at desktop and mobile widths. Ensure no console errors, all 244 desks are searchable/selectable, expired links fail, and malformed URLs do not break the app.

The existing SVG is an intentionally approximate trace based on the visible architectural page, not a measured CAD export. Do not claim routing is operationally accurate until the geometry and doors have been checked against the drawing and representative paths validated.
