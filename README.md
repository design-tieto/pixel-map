# Pixel Office

Pixel Office is a static, responsive floor map for finding and sharing desk and meeting-room locations.

## Floor-plan coordinate audit

The original Plan 4 / Vån 3 architectural PDF and a clean high-resolution rendering were inspected in full, including enlarged crops of the upper-left, upper perimeter, right perimeter, lower-left, lower perimeter and central areas. The existing 258 SVG workstation candidates were plotted on the floor-plan image individually with index labels. Fourteen points were identified as non-workstation furniture in meeting, focus or ancillary spaces and removed (original candidate indices: 1, 2, 62, 66, 69, 70, 71, 72, 73, 74, 107, 124, 141, 142). The remaining 244 points retain their vector-derived centres rather than receiving any global offsets or manual shifts.

Desk IDs are regenerated deterministically from the retained points, beginning in the top-left corner and proceeding around the perimeter, then through interior desks. The source drawing's stated 244 workstations now matches the retained candidate count, but a count match is not independent proof of one-to-one completeness. The vector data still needs checking against individual furniture footprints where workstation symbols are ambiguous.

Meeting-room hotspots (32 labelled MÖTE spaces) were independently compared to the centre coordinates of their pink room rectangles in the PDF. Existing coordinates match those rectangle centres, so they were preserved without unnecessary shifts.

## Features

- Search desk and room IDs; click a location to share it.
- A selected location has a prominent pulsing marker.
- Shared links expire client-side after one hour.
- No booking, locking, directions, login, backend or live presence.

Built by Rashmi Borole.
