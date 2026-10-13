# Pixel Office

Responsive static office map for Kv Poolen, Plan 4 / Vån 3. Find a desk or meeting room and share its location.

## Interface
- Compact single-row search at the top; no title/logo or explanatory map heading.
- Map occupies the main viewport. Zoom out/in and reset (#) controls sit over its top-right corner.
- Selecting a desk, meeting room, or landmark opens a nearby share popover. The share dialog hides the popover and is scrollable on small mobile screens.
- Search dropdown lists matching desk IDs, meeting-room IDs and landmarks.
- No plant-area location is listed as a selectable landmark.
- Footer: “Built by Rashmi Borole” and “Not a booking system — you cannot book or lock desks or rooms.”

## Desk and room coordinates
- Uses `assets/floor-plan-hires.jpg` and traced desk centre candidates.
- Desk IDs are generated after stable spatial sorting. The intended order begins in the top-left corner and proceeds around the perimeter before the interior.
- Candidate positions still require a one-to-one visual audit against desk surfaces and every actual meeting room. Do not claim the inventory is exact until checked against the source drawing.

## Share links
Links expire client-side after one hour. No backend, authentication, database, server-side revocation, live colleague presence or booking/locking features.
