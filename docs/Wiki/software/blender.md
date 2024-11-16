# Blender

- First/last animation frames: the game doesn't display the new animation until the 2nd frame, and doesn't display the last frame either. One exception would be a move with a frame 1 hitbox that connects: the hitlag will use the first animation frame. Because of that, most of the time you'll want to use your idle pose (or corresponding aerial pose) as first and last animation frames.

- Animations must be animated at 60 fps but exported as 30fps to import correctly

- To avoid animating special parts, hide them by hitting H during pose mode

## Texture Flags
You can set these flags on a per-material basis by adding them to the material's name

Texture repeat mode flags, S = Side, T = Top:

- \_ClampS
- \_ClampT
    - Clamp is same as Extend in Blender
- \_MirrorS
- \_MirrorT
    - Mirror is the same as Mirror in Blender

Other flags:

- \_EnvMapping
    - Metal Mario style environment mapping
- \_CullBoth
    - Disables backface culling
- \_Transparent
    - Enables transparency on texture, default alpha color is pure black
        - If you want to change the alpha color, refer to related sections for [Stage](../stages/stageimport.md/#changing-alpha-color) or [Character](../characters/transparenttextures.md/#changing-alpha-color) textures