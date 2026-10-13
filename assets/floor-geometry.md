# Floor geometry

The production map uses an SVG trace of the original architectural PDF. It does not load the floor-plan JPG.

- `floor-background.svg` contains the simplified floor zones and corridor areas.
- `floor-rooms.js` contains each room's traced rectangle, its center anchor, and the capacity shown in room search.
- `desks.js` contains the 244 desk blocks. Each block stores its own SVG center (`x`, `y`), size (`w`, `h`), and rotation (`angle`). The green desk marker is rendered at that same center.

All geometry uses the `0 0 850 779` SVG coordinate system. When revising the floor, update the vector background and the corresponding geometry records together. Keep each marker's `x` and `y` equal to the center of its block.
