# Pixel Office — instructions for Codex

## Working mode
- Work in this repository on `feat/pixel-office-prototype`; keep changes on this branch unless the user says otherwise.
- Make commits on this branch and keep the existing pull request open. Do not merge without the user's explicit approval.
- Use the supplied architectural PDF as the source of truth. Do not replace missing information with invented floor-plan geometry.
- Before finishing a task, inspect the diff, validate JavaScript syntax, and run the app locally or do the closest available smoke test. Report what was actually tested.

## Product intent
Pixel Office is a playful, responsive office map for Kv Poolen, Plan 4 / Vån 3. Users manually select a desk or map point, share a location link that expires client-side after one hour, search rooms/landmarks/desks, and get directions from a manually selected starting point.

## Tech constraints
- Keep this a static site suitable for GitHub Pages: HTML, CSS, JavaScript, and SVG/image assets.
- No backend, database, authentication or live colleague directory in this version.
- Preserve mobile responsiveness and keyboard accessibility.
- Avoid adding build tools/frameworks unless there is a clear need.

## Source map assets
- `assets/floor-plan-hires.jpg` is the high-resolution crop of the actual plan and must be the displayed architectural reference image.
- Do not use `assets/floor-plan.b64` as the displayed image. It is a small thumbnail and causes the blur shown in the user's screenshot.
- The existing SVG `viewBox="0 0 850 779"` uses a coordinate frame intended to align with the cropped plan. When changing the crop, viewBox, or preserveAspectRatio, update all overlay coordinates consistently.
- Use the original uploaded PDF named `260921 Plan 4 Vån 3 PROGRAMSKISS MAX MÖBL. INREDNING.pdf` for verification where available. Never upscale a thumbnail and call it a resolution fix.

## Current limitations to resolve
- The current page has room/space point hotspots and 243 desk-centre candidates detected from PDF vector geometry. The drawing summary indicates 244 desks, so resolve that discrepancy from the source before claiming all desks are covered.
- Some room hotspots were inferred from PDF text positions; verify room IDs, positions, and capacities against the plan.
- The corridor graph is a provisional waypoint graph. Validate every edge and every destination access connector against corridors and doorway openings. Do not let routes pass through walls, furniture, room interiors, lift shafts or the central open voids.
- A connected graph does not prove a route is physically valid. Test representative routes to destinations in each wing.

## Priority order
1. Fix and verify the high-resolution image source so the map is crisp.
2. Align map overlay coordinates to that source image.
3. Improve map legibility: keep idle room targets invisible, desk markers subtle, and selected markers obvious.
4. Verify room IDs and all desk centre positions. Reconcile 243 detected centres with the 244-desk source summary.
5. Validate graph and door access geometry, then test share-link expiry, search and responsive interaction.
6. Update README with concrete validation results and remaining limitations.

## User-facing honesty
Do not call room positions, desk positions, route distances, accessible routes, or the map “accurate” unless the relevant source alignment and geometry have actually been verified. If a detail is unknown, say so and leave it unfilled rather than inventing it.
