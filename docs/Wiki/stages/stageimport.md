# Stage Importing

## Rooms and types

TODO

## Vertex Coloring

TODO

- Do not skip rooms!!!

### Blender

#### Previewing the model

From the game's source code: ingame camera fov: 38

#### Viewing and editing vertex colors

??? note "Vertex Paint mode"
    <figure markdown="span">
        ![Image title](vertexcoloring/vertexpaintmode.png)
        <figcaption>Use vertex paint mode to view and edit vertex colors.</figcaption>
    </figure>

??? note "Viewing the whole scene's vertex colors"
    <figure markdown="span">
        ![Image title](vertexcoloring/viewvertcolors.png)
        <figcaption>Use this view mode to render only vertex colors.</figcaption>
    </figure>

#### Baking lights to vertex colors

- Add lights to your scene
- Set a view to render only lights for preview

??? note "View scene lights"
    <figure markdown="span">
    ![Image title](vertexcoloring/viewmode.png)
    <figcaption>Use this view mode to render only diffuse colors (lights and shadows).</figcaption>
    </figure>

- Select one of your Room objects
- Go into Vertex Coloring mode
- Bake lights to vertex colors

??? note "Bake lights"
    <figure markdown="span">
    ![Image title](vertexcoloring/bakelights.png)
    <figcaption>Note we're baking direct Diffuse lights into Active Color Attribute (Vertex Colors).</figcaption>
    </figure>

## Transparent Textures

### Adding transparency
- Enable the [texture flag](../software/blender.md/#texture-flags) for transparency
- Use pure black wherever you want transparency in your texture

### Changing alpha color
- In Pixelformer, change the `Target color format` to `RGB color with alpha channel (32 bpp)` mode
    - If not using Pixelformer, you will need to follow [these](#multiple-alpha-colors) steps instead, even if using a single alpha color, as most other programs do not export .bmp alpha at all, or just not in a way that GE reads properly.
- Choose the color you want to use for transparency, set it's alpha to 0 and fill in all transparent areas with it
- Export texture as `A8:R8:G8:B8 (32 bpp)` with no other options ticked

### Multiple alpha colors
- Same steps as above, but with multiple alpha 0 colors instead of a single color
- Re-import stage in GE, note which colors are still non-transparent in-game
- Export stage file from Game Configuration and open the .bin in a hex editor
- Manually find where the palette address for your updated texture is
- Find hex value of each non-transparent color (each color is 2 bytes long) and subtract 1 from them

## Model proportions

### Blender
Proportion when exporting using default FBX settings: 1 m in Blender = 100 units in Smash 64. This means a vertex at (90, 0, 83) will be located at (9000, 0, 8300) in the game.

## Frequent Issues
- Stage elements are flickering: The geometry is probably too far away from the camera.
- Whole rooms move when the camera moves: The geometry extends too far away from 0,0,0.
- Textures wrap when the camera moves: You have planes that are too big. Try subdividing huge geometry into smaller pieces.
- Vertex colors are not working:
    - Your file should not be skipping Rooms. Check if you're skipping Room numbers and try again (Should go from 0, 1, 2, and so on)
    - Try a few more times. Sometimes it's random and should work in ~5 tries
    - If all else fails, you'll have to unfortunately try importing to a fresh ROM