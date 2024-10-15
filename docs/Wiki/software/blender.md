# Blender

- First/last animation frames: the game doesn't display the new animation until the 2nd frame, and doesn't display the last frame either. One exception would be a move with a frame 1 hitbox that connects: the hitlag will use the first animation frame. Because of that, most of the time you'll want to use your idle pose (or corresponding aerial pose) as first and last animation frames.

- Animations must be animated at 60 fps but exported as 30fps to import correctly

- To avoid animating special parts, hide them by hitting H during pose mode