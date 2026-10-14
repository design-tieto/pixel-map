# Pixel Office — Codex brief

Continue on `feat/pixel-office-prototype`; don't merge without instruction.

## Scope
Find and share locations only. No directions, routes, start/end selection, desk booking, or room locking.

## UI
- Use a compact single-row search at top with no logo, title, intro row, or reset button outside the map.
- Let the map take most of the viewport. Put zoom out (-), zoom in (+), and reset (#) controls over the map at top-right.
- Keep the selectable desk circles centred on the desk surfaces and meeting-room M targets centred in their pink room footprints. Use the high-resolution source image; do not use the old thumbnail.
- Remove the Plant area as a selectable/searchable landmark.
- The share popup must not overlap the share modal on mobile: hide it before opening the modal, put the modal above it, and constrain the modal to the viewport with internal scrolling.
- Footer only: “Built by Rashmi Borole” and “Not a booking system — you cannot book or lock desks or rooms.”
- Keep search dropdown for desk and meeting-room IDs. Selection and shared destination markers must remain obvious.

## Hosting
Static GitHub Pages app. Share links expire client-side after one hour. No backend or live colleague presence.
