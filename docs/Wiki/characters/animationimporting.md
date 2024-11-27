# Animation Importing

The simplest way to import animations is by overwriting the base character's animation by yours for the target action. This makes it easier to get the correct animation flags and can help with animation sizes if you're trying to make something similar to vanilla 64.

## Special bones (do not animate!)
Some of the model's bones should not be animated because they work as internal control bones (special parts).
If you animate those bones, the editor will warn you and will still import, but these bones will NOT animate. With that, some poses will look wrong.
It's recommended that you hide all special bones in your 3d software when animating to avoid animating special parts by mistake.

Export the animation as FBX in your 3d software. Make sure to not add leaf bones and to export using the correct fps  
Select the animation you want to overwrite in vanilla  
Make sure you have the animation flags set as needed  
Import your FBX file  
Preview the animation to check for any issues

## Animation durations
TODO, dropping values here for now

### Ledge getup options

All characters have the same total time for these animations. You can have different combinations, though.
It always starts with a shared quick/slow animation, followed by each option's animations.

Captain Falcon:
cliffQuick 19 (shared)
cliffClimbQuick1 9
cliffClimbQuick2 6
attack1 7
attack2 33 = 40
escape1 5
escape2 21 = 26

cliffSlow 50 (shared)
cliffClimbSlow1 7
cliffClimbSlow2 12
attack1 18	
attack2 24 = 42
escape1 12
escape2 29 = 41

## Possible issues

- The model looks broken: this happens in cases such as:
    - Changing animation flags after importing the animation - in these cases, just reimport
    - Imported animation's bones don't match your model - either you exported your FBX file with extra bones by accident or forgot to import your new skeleton, in case you're editing the model's bones.
- The animation is too long/short: check your 3d software's fps settings when exporting the FBX
- The game is crashing: your animation is probably too long. Make the animation shorter or decrease the number of keyframes. Note that your 3d software might also be keying all bones on all frames, (which happens by default in Blender).
- Some poses do not look right: you might have animated [Special Bones](#special-bones-do-not-animate).