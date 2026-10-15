# Pixel Office

Pixel Office is a static floor map for finding and sharing desk and meeting-room locations.

## Floors and maps

The floor selector provides Arenastaden floors 1, 2, and 3. Floor 3 keeps its desk and coded meeting-room finder. Floors 1 and 2 use the searchable room finder and have no desk selection.

Floor 1's map is exported from the supplied PDF vector paths and text, cropped to the plan panel, and compressed for the browser. Floor 2's map uses the PDF-derived vector asset. Floor 3 keeps the source PDF's SVG export. The floor maps and their room overlays use the app's `0 0 850 779` coordinate frame.

Floor 1 contains 15 named rooms; Floor 2 contains 20 named rooms; Floor 3 contains 34 coded rooms and 246 desk markers. Room capacities are shown beside the room names on Floors 1 and 2. The room list also supports the numeric labels printed in the Floor 1 and Floor 2 source plans.

## Location search and sharing

The room picker includes every room and named destination in a scrollable, searchable list with a live result count. The kitchen, coffee stations, and lounge on Floor 3 are represented by one Kitchen destination. The sidebar explains how to find or share a location; the map does not support booking.

## Verification

- Rendered the supplied Floor 1 PDF and visually compared its floor geometry with the browser's Floor 1 vector map.
- Mapped all 15 Floor 1 room centers from the PDF room bounds into the app coordinate frame and checked the room count and numeric search aliases.
- Confirmed the Floor 1 and Floor 2 room lists and capacities in Chrome on localhost; both floors show 15 and 20 destinations respectively and hide desk selection.
- Confirmed the compressed Floor 1 SVG parses and contains the cropped plan geometry.
- Checked the inline JavaScript syntax and `git diff --check`.
