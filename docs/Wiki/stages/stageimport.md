# Stage Importing

## Rooms and types

TODO

## Model proportions
### Blender

Proportion when exporting using default FBX settings: 1 m in Blender = 100 units in Smash 64. This means a vertex at (90, 0, 83) will be located at (9000, 0, 8300) in the game.

## Frequent Issues
- Stage elements are flickering: The geometry is probably too far away from the camera.
- Whole rooms move when the camera moves: The geometry extends too far away from 0,0,0.
- Vertex colors are not working: Unfortunately you'll have to try importing to a fresh ROM.
- Textures wrap when the camera moves: You have planes that are too big. Try subdividing huge geometry into smaller pieces.