# Floor geometry

The application uses `floor-map.svg`, a simplified vector trace made from the original architectural PDF. It does not load the floor-plan JPG.

- `floor-map.svg` contains traced floor zones, corridors, all 34 room blocks, and all 244 workstation blocks.
- `floor-rooms.js` stores each room block's SVG center and size plus the capacity shown in search.
- `desks.js` stores each desk block's SVG center, size, and rotation. The interactive green desk marker is rendered at the same center.

All geometry uses the `0 0 850 779` SVG coordinate system. When revising the floor, update the vector drawing and its geometry records together. Keep each marker's `x` and `y` equal to the center of its block.
