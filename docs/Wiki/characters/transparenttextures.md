# Transparent Textures

## Adding transparency
- Enable the [texture flag](../software/blender.md/#texture-flags) for transparency
- Use pure black wherever you want transparency in your texture

## Changing alpha color
- Change pure black to desired color
- Re-import character in GE Model Editor
- `Export Character File` and open the .bin in a hex editor
- Note your texture's `Palette Address` in GE Model Editor
- Go to the `Palette Address` of your texture in a hex editor
- Find your new color in hex (each color is 2 bytes long) and subtract 1
    - Texture64 can help with identifying the colors
- Import updated character file through the Game Configuration window