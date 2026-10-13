# Pixel Office — Codex project brief

Continue on `feat/pixel-office-prototype`. Do not merge the PR unless instructed.

## Scope
Find and share locations only: do not reintroduce routes, directions, or start/end selection.

## Desk map
- Use the centre points from the vector tracing data (`office_trace/desk-centres-poly.csv` in the local project workspace), which includes rotated desk rectangles in the curved corners.
- IDs must be assigned deterministically after spatial sorting: top-left corner first, across the top, down the right, across the bottom right-to-left, up the left, then interior desks row-by-row.
- The manual line of markers through the central open void must not return.
- There are 258 candidate centres. Audit them against physical desk surfaces, especially corners and any furniture inside meeting rooms; remove non-desk detections before claiming the inventory is complete.
- Keep one pink M marker per real MÖTE room.

## Interaction
- Click/search a location to highlight it with a pulse and show a share-only popover.
- Search dropdown lists matching desk IDs, meeting-room IDs and landmarks.
- Reset clears the selection, pulse, shared pin, popover, search dropdown, share dialog and zoom.
- Shared links expire client-side after one hour. Keep static GitHub Pages hosting.
