# Character Rig creation/update and importing

## Step 0) Important info
The rig you end up modifying must follow the basic character structure. It must have proper socket joints for the arms, legs and feet. The rig can also not be any larger than 32 bones. You are limited to HEX 20, Maya Room FBXASC0512, Blender Bone 32. 

## Step 1) After making your rig and exporting ONLY your skeleton structure. 
Import Rig
Select your rig and import it. The model should distort to the new rig. Now we need to make Smash 64 accept the new structure.

##Step 2) Update the skipped parts bitflag
for the sockets, we need to make sure the correct ones are set. Sockets are the joints on the mesh that can be considered "Containers" so to speak. There is a arm socket, leg socket, and ankle socket. We take the hex value provided and convert it into binary.
Hexadecimal → 1042520000000000
Binary → 00010000 01000010 01010010 00000000 00000000 00000000 00000000 00000000

If we look at this compared to the Bone structure for Mario (Not including top joint)
| Blender Bone   | Part #   | Maya Hex/Room    | Joint Name Function                      | Binary Bit Flag |
|----------------|----------|------------------|------------------------------------------|-----------------|
| 0              | Part00   | FBXASC048        | Main bone base                           | 0               | 
| 1              | Part01   | FBXASC049        | Hips (No Model attached)                 | 0               |
| 2              | Part02   | FBXASC050        | Chest                                    | 0               |
| 3              | Part03   | FBXASC051        | Socket Joint Left Arm                    | 1               |
| 4              | Part04   | FBXASC052        | Left Upper Arm mesh                      | 0               |
| 5              | Part05   | FBXASC053        | Left Lower Arm mesh                      | 0               |
| 6              | Part06   | FBXASC054        | Left Hand                                | 0               |
| 7              | Part07   | FBXASC055        | Neck (No model attached)                 | 0               |
| 8              | Part08   | FBXASC056        | Head                                     | 0               |
| 9              | Part09   | FBXASC057        | Socket Joint Right Arm                   | 1               |
| 10             | Part0A   | FBXASC0490       | Right Upper Arm mesh                     | 0               |
| 11             | Part0B   | FBXASC0491       | Right Lower Arm mesh                     | 0               |
| 12             | Part0C   | FBXASC0492       | Right Hand                               | 0               |
| 13             | Part0D   | FBXASC0493       | item joint (Where items are attached to) | 0               |
| 14             | Part0E   | FBXASC0494       | Socket Left Joint leg                    | 1               |
| 15             | Part0F   | FBXASC0495       | Left Upper Leg mesh                      | 0               |
| 16             | Part10   | FBXASC0496       | Left Lower Leg mesh                      | 0               |
| 17             | Part11   | FBXASC0497       | Left Ankle Joint                         | 1               |
| 18             | Part12   | FBXASC0498       | Left Foot                                | 0               |
| 19             | Part13   | FBXASC0499       | Socket Right Joint leg                   | 1               |
| 20             | Part14   | FBXASC0500       | Right Upper Leg mesh                     | 0               |
| 21             | Part15   | FBXASC0501       | Right Lower Leg mesh                     | 0               |
| 22             | Part16   | FBXASC0502       | Right Ankle Joint                        | 1               |
| 23             | Part17   | FBXASC0503       | Right Foot                               | 0               |
| 24             | Part18   | FBXASC0504       | Large item joint                         | 0               |

For Brain, the flags are updated as such

| Blender Bone   | Part #   | Maya Hex/Room    | Joint Name Function                      | Binary Bit Flag |
|----------------|----------|------------------|------------------------------------------|-----------------|
| 0              | Part00   | FBXASC048        | Main bone base                           | 0               |
| 1              | Part01   | FBXASC049        | Hips (No Model attached)                 | 0               |
| 2              | Part02   | FBXASC050        | Chest                                    | 0               |
| 3              | Part03   | FBXASC051        | Socket Joint Left Arm                    | 1               |
| 4              | Part04   | FBXASC052        | Left Upper Arm mesh                      | 0               |
| 5              | Part05   | FBXASC053        | Left Lower Arm mesh                      | 0               |
| 6              | Part06   | FBXASC054        | Left Hand                                | 0               |
| 7              | Part07   | FBXASC055        | item joint (Where items are attached to) | 0               |
| 8              | Part08   | FBXASC056        | Potential Witheld Magic Part             | 0               |
| 9              | Part09   | FBXASC057        | Neck (No model attached)                 | 0               |
| 10             | Part0A   | FBXASC0490       | Head                                     | 0               |
| 11             | Part0B   | FBXASC0491       | Hair mesh                                | 0               |
| 12             | Part0C   | FBXASC0492       | Cape upper Mesh                          | 0               |
| 13             | Part0D   | FBXASC0493       | Cape Lower Mesh                          | 0               |
| 14             | Part0E   | FBXASC0494       | Socket Joint Right Arm                   | 1               |
| 15             | Part0F   | FBXASC0495       | Right Upper Arm mesh                     | 0               |
| 16             | Part10   | FBXASC0496       | Right Lower Arm mesh                     | 0               |
| 17             | Part11   | FBXASC0497       | Right Hand                               | 0               |
| 18             | Part12   | FBXASC0498       | Staff Mesh                               | 0               |
| 19             | Part13   | FBXASC0499       | Potential Withheld Magic Part            | 0               |
| 20             | Part14   | FBXASC0500       | Socket Left Joint leg                    | 1               |
| 21             | Part15   | FBXASC0501       | Left Upper Leg mesh                      | 0               |
| 22             | Part16   | FBXASC0502       | Left Lower Leg mesh                      | 0               |
| 23             | Part17   | FBXASC0503       | Left Ankle Joint                         | 1               |
| 24             | Part18   | FBXASC0504       | Left Foot                                | 0               |
| 25             | Part19   | FBXASC0505       | Socket Right Joint leg                   | 1               |
| 26             | Part1A   | FBXASC0506       | Right Upper Leg mesh                     | 0               |
| 27             | Part1B   | FBXASC0507       | Right Lower Leg mesh                     | 0               |
| 28             | Part1C   | FBXASC0508       | Right Ankle Joint                        | 1               |
| 29             | Part1D   | FBXASC0509       | Right Foot                               | 0               |
| 30             | Part1E   | FBXASC0510       | Large item joint                         | 0               |

Binary → 00010000 00000010 00001001 01001000 00000000 00000000 00000000 00000000
Hexadecimal → 1002094800000000

##Step 3) Now we need to update the withheld parts section. 

So we need to modify the withheld bitflag
We have to take that withheld part and set it to the new bone structure.
"withheld part bitflag" convert it the hex to binary using https://www.asciitohex.com/
going down from the hierarchy, disable any joint you've added
ex  if you have arm arm 2 arm 3 head head 2 head3(new) arm arm2 arm 3 you'd disable it in the bit flag so it will look something like 111110111 where 0 is disabled and 1 is enabled

Our goal Is 2 fold. Making sure all withheld parts are accounted for and making sure all animations are mapped to the correct bones. This is a two step process. 

For the first step, we want to set ALL new added bones to withheld parts, being setting them to 0. Make sure it matches the old structure. Even if some bones have gain a new purpose (such as for Brian, the staff bone being the old item joint)

Lets Break these down again for instruction:

Withheld → FFFFFF0000000000
Binary → 11111111 11111111 11111111 00000000 00000000 00000000 00000000 00000000

| Blender Bone   | Part #   | Maya Hex/Room    | Joint Name Function                      | Binary Bit Flag |
|----------------|----------|------------------|------------------------------------------|-----------------|
| 0              | Part00   | FBXASC048        | Main bone base                           | 1               | 
| 1              | Part01   | FBXASC049        | Hips (No Model attached)                 | 1               |
| 2              | Part02   | FBXASC050        | Chest                                    | 1               |
| 3              | Part03   | FBXASC051        | Socket Joint Left Arm                    | 1               |
| 4              | Part04   | FBXASC052        | Left Upper Arm mesh                      | 1               |
| 5              | Part05   | FBXASC053        | Left Lower Arm mesh                      | 1               |
| 6              | Part06   | FBXASC054        | Left Hand                                | 1               |
| 7              | Part07   | FBXASC055        | Neck (No model attached)                 | 1               |
| 8              | Part08   | FBXASC056        | Head                                     | 1               |
| 9              | Part09   | FBXASC057        | Socket Joint Right Arm                   | 1               |
| 10             | Part0A   | FBXASC0490       | Right Upper Arm mesh                     | 1               |
| 11             | Part0B   | FBXASC0491       | Right Lower Arm mesh                     | 1               |
| 12             | Part0C   | FBXASC0492       | Right Hand                               | 1               |
| 13             | Part0D   | FBXASC0493       | item joint (Where items are attached to) | 1               |
| 14             | Part0E   | FBXASC0494       | Socket Left Joint leg                    | 1               |
| 15             | Part0F   | FBXASC0495       | Left Upper Leg mesh                      | 1               |
| 16             | Part10   | FBXASC0496       | Left Lower Leg mesh                      | 1               |
| 17             | Part11   | FBXASC0497       | Left Ankle Joint                         | 1               |
| 18             | Part12   | FBXASC0498       | Left Foot                                | 1               |
| 19             | Part13   | FBXASC0499       | Socket Right Joint leg                   | 1               |
| 20             | Part14   | FBXASC0500       | Right Upper Leg mesh                     | 1               |
| 21             | Part15   | FBXASC0501       | Right Lower Leg mesh                     | 1               |
| 22             | Part16   | FBXASC0502       | Right Ankle Joint                        | 1               |
| 23             | Part17   | FBXASC0503       | Right Foot                               | 1               |
| 24             | Part18   | FBXASC0504       | Large item joint                         | 0               |

Update the binary to this temporary bone structure.  

| Blender Bone   | Part #   | Maya Hex/Room    | Joint Name Function                      | Binary Bit Flag |
|----------------|----------|------------------|------------------------------------------|-----------------|
| 0              | Part00   | FBXASC048        | Main bone base                           | 1               |
| 1              | Part01   | FBXASC049        | Hips (No Model attached)                 | 1               |
| 2              | Part02   | FBXASC050        | Chest                                    | 1               |
| 3              | Part03   | FBXASC051        | Socket Joint Left Arm                    | 1               |
| 4              | Part04   | FBXASC052        | Left Upper Arm mesh                      | 1               |
| 5              | Part05   | FBXASC053        | Left Lower Arm mesh                      | 1               |
| 6              | Part06   | FBXASC054        | Left Hand                                | 1               |
| 7              | Part07   | FBXASC055        | item joint (Where items are attached to) | 0               |
| 8              | Part08   | FBXASC056        | Potential Witheld Magic Part             | 0               |
| 9              | Part09   | FBXASC057        | Neck (No model attached)                 | 1               |
| 10             | Part0A   | FBXASC0490       | head                                     | 1               |
| 11             | Part0B   | FBXASC0491       | Hair mesh                                | 0               |
| 12             | Part0C   | FBXASC0492       | Cape Upper Mesh                          | 0               |
| 13             | Part0D   | FBXASC0493       | Cape Lower Mesh                          | 0               |
| 14             | Part0E   | FBXASC0494       | Socket Joint Right arm                   | 1               |
| 15             | Part0F   | FBXASC0495       | Right Upper Arm mesh                     | 1               |
| 16             | Part10   | FBXASC0496       | Right Lower Arm mesh                     | 1               |
| 17             | Part11   | FBXASC0497       | Right Hand                               | 1               |
| 18             | Part12   | FBXASC0498       | Staff Mesh                               | 1               |
| 19             | Part13   | FBXASC0499       | Potential Withheld Magic Part            | 0               |
| 20             | Part14   | FBXASC0500       | Socket Left Joint leg                    | 1               |
| 21             | Part15   | FBXASC0501       | Left Upper Leg mesh                      | 1               |
| 22             | Part16   | FBXASC0502       | Left Lower Leg mesh                      | 1               |
| 23             | Part17   | FBXASC0503       | Left Ankle Joint                         | 1               |
| 24             | Part18   | FBXASC0504       | Left Foot                                | 1               |
| 25             | Part19   | FBXASC0505       | Socket Right Joint leg                   | 1               |
| 26             | Part1A   | FBXASC0506       | Right Upper Leg mesh                     | 1               |
| 27             | Part1B   | FBXASC0507       | Right Lower Leg mesh                     | 1               |
| 28             | Part1C   | FBXASC0508       | Right Ankle Joint                        | 1               |
| 29             | Part1D   | FBXASC0509       | Right Foot                               | 1               |
| 30             | Part1E   | FBXASC0510       | Large item joint                         | 0               |

Binary → 11111110 01100011 11101111 11111100 00000000 00000000 00000000 00000000
Hexadecimal → fe63effc00000000

Update the new withheld parts and close. This structure is specifically used to export old animations for us to reimport. Given we changed the rig, the editor is putting specific animations to the old bones, which will cause a crash. By using this temporary structure, we are exporting the animations in a way for the editor to place them on the correct bone.
Wxport all animations. As they are messed up and we need to reset them.
After that, we update the withheld attribute again to the final rigs proper withheld position. For Brian I added in two magic bones that would be called in for attacks. One on each arm. Those are truly withheld parts, so the new value would be

| Blender Bone   | Part #   | Maya Hex/Room    | Joint Name Function                      | Binary Bit Flag |
|----------------|----------|------------------|------------------------------------------|-----------------|
| 0              | Part00   | FBXASC048        | Main bone base                           | 1               |
| 1              | Part01   | FBXASC049        | Hips (No Model attached)                 | 1               |
| 2              | Part02   | FBXASC050        | Chest                                    | 1               |
| 3              | Part03   | FBXASC051        | Socket Joint Left Arm                    | 1               |
| 4              | Part04   | FBXASC052        | Left Upper Arm mesh                      | 1               |
| 5              | Part05   | FBXASC053        | Left Lower Arm mesh                      | 1               |
| 6              | Part06   | FBXASC054        | Left Hand                                | 1               |
| 7              | Part07   | FBXASC055        | item joint (Where items are attached to) | 1               |
| 8              | Part08   | FBXASC056        | Potential Witheld Magic Part             | 0               |
| 9              | Part09   | FBXASC057        | Neck (No model attached)                 | 1               |
| 10             | Part0A   | FBXASC0490       | head                                     | 1               |
| 11             | Part0B   | FBXASC0491       | Hair mesh                                | 1               |
| 12             | Part0C   | FBXASC0492       | Cape Upper Mesh                          | 1               |
| 13             | Part0D   | FBXASC0493       | Cape Lower Mesh                          | 1               |
| 14             | Part0E   | FBXASC0494       | Socket Joint Right arm                   | 1               |
| 15             | Part0F   | FBXASC0495       | Right Upper Arm mesh                     | 1               |
| 16             | Part10   | FBXASC0496       | Right Lower Arm mesh                     | 1               |
| 17             | Part11   | FBXASC0497       | Right Hand                               | 1               |
| 18             | Part12   | FBXASC0498       | Staff Mesh                               | 1               |
| 19             | Part13   | FBXASC0499       | Potential Withheld Magic Part            | 0               |
| 20             | Part14   | FBXASC0500       | Socket Left Joint leg                    | 1               |
| 21             | Part15   | FBXASC0501       | Left Upper Leg mesh                      | 1               |
| 22             | Part16   | FBXASC0502       | Left Lower Leg mesh                      | 1               |
| 23             | Part17   | FBXASC0503       | Left Ankle Joint                         | 1               |
| 24             | Part18   | FBXASC0504       | Left Foot                                | 1               |
| 25             | Part19   | FBXASC0505       | Socket Right Joint leg                   | 1               |
| 26             | Part1A   | FBXASC0506       | Right Upper Leg mesh                     | 1               |
| 27             | Part1B   | FBXASC0507       | Right Lower Leg mesh                     | 1               |
| 28             | Part1C   | FBXASC0508       | Right Ankle Joint                        | 1               |
| 29             | Part1D   | FBXASC0509       | Right Foot                               | 1               |
| 30             | Part1E   | FBXASC0510       | Large item joint                         | 0               |

Binary → 11111111 01111111 11101111 11111100 00000000 00000000 00000000 00000000
Hexadecimal → ff7feffc00000000
And then reimport all the animations again. This will fix the animations, even if some are rotated odd. 

##Step 4) Fixing the Withheld Parts Table.
For this next section, we will be making changes to the bone structure though the editor and through HEX editing. It is important to note for this section and the special parts section later that Smash 64 in-engine will add +4 to the bone ids. This means that when we are adding/editing the rig values, we will need to add +4 to the bone id.

For example, if I am setting the item joint pointer, and it is bone 07, 
then I will set the value to 07+04 = 0B.

Now we want to fix the Withheld parts table. 

Click Edit attribute

We are going to modify the withheld parts section. 
There will be many parts present in the section, so lets break them down.
| Part        | Animation Flag                                                   |
|-------------|------------------------------------------------------------------|
| Part 0000   | Part that correspond to Animation Flags 0x80000000, DONT CHANGE  |
| Part 0001   | Part that correspond to Animation Flags 0x40000000, DONT CHANGE  |
| Part 0002   | Part that correspond to Animation Flags 0x20000000, DONT CHANGE  |
| Part 0003   | This part is associated with the Large Item joint. It is always the final bone in the rig. If we look back to our rig structures above, for MARIO, the large item joint was Part18, which means the value present should be Part18+04 = Part1C. For our rig, it would be Part1E+04 = Part22 |

For added withheld parts, such as Brian's Potential Witheld Magic Parts, i.e. the ones we set the bitflag to 0 for in prior steps, we need to also set the bone part correct using the above method. While we are updating the correct bone part, remember that the newly added withheld parts also need their parent bones values updated. 

For all added withheld parts, the Unknown values are always the same and are as follows:
Unknown 1 - this is always 00000001
Unknown 2 - this is always 00000000
Make sure to update each part.

| Part        | Animation Flag                                                   |
|-------------|------------------------------------------------------------------|
| Part 0004   | For our rig, Potential Withheld Magic Part, it would be Part08+04 = Part0C. The Parent joint for the added withheld part is Part06+04 = Part0A |
| Part 0005   | For our rig, Potential Withheld Magic Part, it would be Part13+04 = Part17. The Parent joint for the added withheld part is Part12+04 = Part016 |

Withheld Parts 0003 corresponds to the animation flag 0x10000000, these animation flags are what is responsible for telling the animation to use that withheld part... so for Withheld Parts 0004 the flag would be 0x08000000, and then 0x04000000 for Withheld Parts 0005 etc.

This is important to know for later. Here is a table explaining the concept:
| Part        | Animation Flag                                                   |
|-------------|------------------------------------------------------------------|
| Part 0000   | Part that correspond to Animation Flags 0x80000000               |
| Part 0001   | Part that correspond to Animation Flags 0x40000000               |
| Part 0002   | Part that correspond to Animation Flags 0x20000000               |
| Part 0003   | Part that correspond to Animation Flags 0x10000000               |
| Part 0004   | Part that correspond to Animation Flags 0x80000000               |
| Part 0005   | Part that correspond to Animation Flags 0x40000000               |
| Part 0006   | Part that correspond to Animation Flags 0x20000000               |
| Part 0007   | Part that correspond to Animation Flags 0x10000000               |
| Part 0008   | Part that correspond to Animation Flags 0x80000000               |
| Etc.        |                                                                  |

##Step 5) Hex editing the character file to fix Unknown Value points

Now we have done most of the work needed in the editor, we must modify the character main file. This will resolve the final issues of the rig.
To get the character main file, we need to go to either the Animation editor and click export main file

or go to the Game configuration window and export the main file from there

Game configuration is how we will import the file after we make our changes.
Export the "Parse DisplayLists to TextFile" button in the "Special Functions" section of the Edit Model window, this text file has some important info in it we can use later.

in the CharacterDisplayLists.txt file we saved earlier, scroll down to the "Unknown Value Pointers" section:


in this section we are looking for XXXX (0330): ... Head Part? (-4), this is where the Head Bone ID is defined for dynamic textures, XXXX is the offset in the file so in Brians case we go to 0198 and change the instances of Part08+04 = Part0C to Part0A+04=Part0E since the head bone was changed.

Load the characterMain.bin file we exported into HxD. Also set the word size to 4. Makes it eaiser to read and modify.

Find the offset we found from the CharacterDisplayLists.txt. For Brian, it was 0198.
HxD is read as the all the numbers up to the last one being the row, i.e. 019X, and the X being the offset. Given X is 8, we are modifying the third column. As we see, 0C is present, which was Mario's head. We replace that with 0E, which is Brian's head.

If you see multiple 0C values, it means there are multiple textures that are referenced and all need to be updated. Here is an example from a different character rig associated with Brian. 
This character file is based on Link. Link has three dynamic textures on his body, being his Both his eyes and his mouth. All those are separate textures, meaning that you have to update the head bone in the three locations. 

If one wants to add more dynamic textures to a character, One needs to shift pointers in the rom. For Brian, I do not have any extra dynamic textures, as I only swap his face texture. 

For completion sake, I am listing the steps for adding a new dynamic texture hypothetically. If we were to add a new dynamic texture, we need to modify the bone in the character file, adding in the bone and the pointers. 

Looking at the Head texture location from before, we see that 0E0000 is your face dynamic texture inherited by Mario. 
0E - model part 
00 - number of iterations through the texture hierarchy 
00 - not sure but seems to match second byte 

If we want another Dynamic face texture, we would insert 0E0101 to the file. Adding multiple dynamic textures would increase the two trailing bytes, i.e. 0E0202, 0E0303, etc. After adding in the new dynamic textures, pad the word til it is 0x4 bytes total.
| 0E00 0000                  | 0E00000E 01010000           |
| 0E00000E 01010000          | 0E00000E 01010E02 02000000  |
| 0E00000E 01010E02 02000000 | 0E00000E 01010E02 020E0303  |

Inserting one new dynamic texture would look something like this.
Notice how all the values after the inserted words have now changed. This means the pointers in the entire file have moved. This needs to be fixed. There is a provided pointerfix script created by Fray that will update all the pointers in your file. Save the character.bin and run the bass program. You have to provide the following in the script.

filename - just the name of the file, not including extension
offset - offset within the file where you are inserting new data
shift - size of the insertion (probably needs to be in increments of 0x4) 
internal_offset - "Internal File Table Offset" in the editor's game configuration window 
external_offset - "Internal File Resource Offset" in the editor's game configuration window 


Get the internal offsets from game configuration

the command would look like this: fix_pointers(brianmain, 0x198, 0x4, 0x114, 0x0)

If we were to add in multiple dynamic textures, 0x4 would change from 0x4 to 0x8, or 0x12 depending on how many were added.

If you want a dynamic texture on a bone other then the head, add it to the character file in the same location, and run the pointer fix application.

i.e. 0E000015 00000000
Step 6) Hex editing the character file to fix Unknown Value Data
This next section has to do with fixing joints associated with damage types, fixing the shield pose and other rig problems. The format will always be "XXXX (YYYY):" where XXXX is the offset in the file, and YYYY is where that piece of data is in relation to the Attribute Offset, so we mostly care about XXXX. This will help us find where in the file are the parts that we need to change.

these are irrelevant and can be ignored,
XXXX (0290): ????????
XXXX (0294): ????????
XXXX (0298): ????????

we're not sure exactly what these are for but they need to be updated if the rig is modified or certain damage types will crash the game,
XXXX (02A4): head bone id + 4
XXXX (02A8): left wrist bone id + 4
XXXX (02AC): right shin bone id + 4
XXXX (02B0): left shin bone id + 4
XXXX (02B4): right wrist bone id + 4
XXXX (02B8): 00000000 (from here and below is always 0 and can be ignored)
XXXX (02BC): 00000000
XXXX (02C0): 00000000
XXXX (02C4): 00000000
XXXX (02C8): 00000000
XXXX (02CC): 00000000

these are pointers to the shield pose file, if you import a new shield pose then the editor will automatically set up the shield pose pointers 
XXXX (02D8): ????????
XXXX (02DC): ????????
XXXX (02E0): ????????
XXXX (02E4): ????????
XXXX (02E8): ????????
XXXX (02EC): ????????
XXXX (02F0): ????????
XXXX (02F4): ????????
XXXX (02F8): ????????

this final section defines parts used by the slope contour command, and item/shield parts, they need to be updated if the rig is modified
XXXX (02FC): left leg socket bone id + 4
XXXX (0300): ????????
XXXX (0304): right leg socket bone id + 4
XXXX (0308): ????????
XXXX (030C): left shoulder socket bone id + 4
XXXX (0310): ????????
XXXX (0314): right shoulder socket bone id + 4
XXXX (0318): ????????
XXXX (031C): ????????
XXXX (0320): ????????
-
XXXX (0334): "heavy item joint" + 4
-
XXXX (033C): item joint + 4
The way this works is by replacing the bone in the old file with the updated rigs position. This means that if a bone did not move, the value would remain the same. Conversely, if the bone has a different position in the hierarchy, it gets updated.

Lets compare the rigs again:

| Blender Bone | Part # | Mario Rig                        | Brian Rig                                |
|--------------|--------|----------------------------------|------------------------------------------|
| 0            | Part00 | Main bone base                   | Main bone base                           |
| 1            | Part01 | Hips (No Model attached)         | Hips (No Model attached)                 |
| 2            | Part02 | Chest                            | Chest                                    |
| 3            | Part03 | Socket Joint Left Arm            | Socket Joint Left Arm                    |
| 4            | Part04 | Left Upper Arm mesh              | Left Upper Arm mesh                      |
| 5            | Part05 | Left Lower Arm mesh              | Left Lower Arm mesh                      |
| 6            | Part06 | Left Hand                        | Left Hand                                |
| 7            | Part07 | Neck (No model attached)         | item joint (Where items are attached to) |
| 8            | Part08 | Head                             | Potential Witheld Magic Part             |
| 9            | Part09 | Socket Joint Right Arm           | Neck (No model attached)                 |
| 10           | Part0A | Right Upper Arm mesh             | Head                                     |
| 11           | Part0B | Right Lower Arm mesh             | Hair mesh                                |
| 12           | Part0C | Right Hand                       | Cape upper Mesh                          |
| 13           | Part0D | item joint                       | Cape Lower Mesh                          |
| 14           | Part0E | Socket Left Joint leg            | Socket Joint Right Arm                   |
| 15           | Part0F | Left Upper Leg mesh              | Right Upper Arm mesh                     |
| 16           | Part10 | Left Lower Leg mesh              | Right Lower Arm mesh                     |
| 17           | Part11 | Left Ankle Joint                 | Right Hand                               |
| 18           | Part12 | Left Foot                        | Staff Mesh                               |
| 19           | Part13 | Socket Right Joint leg           | Potential Withheld Magic Part            |
| 20           | Part14 | Right Upper Leg mesh             | Socket Left Joint leg                    |
| 21           | Part15 | Right Lower Leg mesh             | Left Upper Leg mesh                      |
| 22           | Part16 | Right Ankle Joint                | Left Lower Leg mesh                      |
| 23           | Part17 | Right Foot                       | Left Ankle Joint                         |
| 24           | Part18 | Large item joint                 | Left Foot                                |
| 25           | Part19 |                                  | Socket Right Joint leg                   | 
| 26           | Part1A |                                  | Right Upper Leg mesh                     |
| 27           | Part1B |                                  | Right Lower Leg mesh                     |
| 28           | Part1C |                                  | Right Ankle Joint                        |
| 29           | Part1D |                                  | Right Foot                               |
| 30           | Part1E |                                  | Large item joint                         |
| 31           | Part1F |                                  |                                          |
| 32           | Part20 |                                  |                                          |
| 33           | Part21 | NOT A REAL PART                  | NOT A REAL PART                          |
| 34           | Part22 | NOT A REAL PART                  | NOT A REAL PART                          |


We have to remember that the values we are reading are the bones actual position in the rig +4. This means the following needs to happen:

Left Leg socket bone id + 4
| Mario    | Mario Bone-4 | Brian-4  | Brian    |
|----------|--------------|----------|----------| 
| 00000017 | 00000013     | 00000019 | 0000001D |

Do this process for all values. If a bone did not move, leave it alone. If it did, update it.

For Brian, this would mean the following:
| Rig Part Information     | Mario's Rig Values      | Brian's Rig updated Values                      |
|--------------------------|-------------------------|-------------------------------------------------|
| head bone id + 4         | 0734 (02A4): 0000000C   | 0734 (02A4): 0000000E                           |
| left wrist bone id + 4   | 0738 (02A8): 0000000F   | 0738 (02A8): 00000014                           |
| right shin bone id + 4   | 073C (02AC): 00000014   | 073C (02AC): 0000001A                           |
| left shin bone id + 4    | 0740 (02B0): 00000019   | 0740 (02B0): 0000001F                           |
| right wrist bone id + 4  | 0744 (02B4): 00000009   | 0744 (02B4): 00000009 (did not change position) |


if you import a new shield pose then the editor will automatically set up the shield pose pointers. the only time you'd need to update them is if you import a new model file over a ROM that doesn't have your sheild pose
XXXX (02D8): ????????
XXXX (02DC): ????????
XXXX (02E0): ????????
XXXX (02E4): ????????
XXXX (02E8): ????????
XXXX (02EC): ????????
XXXX (02F0): ????????
XXXX (02F4): ????????
XXXX (02F8): ????????

Final section for Brian would mean the following:
| Rig Part Information              | Mario's Rig Values      | Brian's Rig updated Values                      |
|-----------------------------------|-------------------------|-------------------------------------------------|
| Left leg socket bone id + 4       | 078C (02FC): 00000017   | 078C (02FC): 0000001D                           |
| ????????                          | 0790 (0300): 42739062   | 0790 (0300): 42739062                           |
| Right leg socket bone id + 4      | 0794 (0304): 00000012   | 0794 (0304): 00000018                           |
| ????????                          | 0798 (0308): 42739062   | 0798 (0308): 42739062                           |
| Left shoulder socket bone id + 4  | 079C (030C): 0000000D   | 079C (030C): 00000012                           |
| ????????                          | 07A0 (0310): 420FA6E9   | 07A0 (0310): 420FA6E9                           |
| Right shoulder socket bone id + 4 | 07A4 (0314): 00000007   | 07A4 (0314): 00000007 (did not change position) |
| XXXX (0318): ????????             | 07A8 (0318): 420F8B44   | 07A8 (0318): 420F8B44                           |
| XXXX (031C): ????????             | 07AC (031C): 42480000   | 07AC (031C): 42480000                           |
| XXXX (0320): ????????             | 07B0 (0320): 3F060A92   | 07B0 (0320): 3F060A92                           |
| -                                 | -                       | -                                               |
| "heavy item joint" + 4            | 07C4 (0334): 0000001C   | 07C4 (0334): 00000022                           |
| -                                 | -                       | -                                               |
| item joint + 4                    | 07CC (033C): 00000011   | 07CC (033C): 0000000B (moved to the other hand) |

With all of this information, update the character bin file with the new bone values. 
Make sure to save.

##Step 7) Fix the hurt boxes
There are two approaches that can be taken to fix the bounding boxes. I am going to list both approaches here, but remember, we only need to do one. If you do the export from the editor approach, you need to do the bounding boxes after re-importing the modified character bin file. 

###Step 7A) Hex editing the hurt boxes
begin by opening the CharacterDisplayLists.txt file we saved, at the top of the file you will see Main File: (file id) Offset XXXX, this "Offset" is the attribute offset and if we add 0x104 to that we'll have the offset of the first hurtbox:

For Brian, this looks like: Main File: 00CB Offset 0490, 
that means that the first hurt box is found at: 0490+0104 = 0594
The format for hurtboxes looks like this 
00000006 00000001 00000001 00000000 41200000 40800000 42CE0000 42E00000 42BE0000

It can be broken down as follows:
00000006 - bone (remember that this value is the bone +4)
00000001 - damage animation that hurtbox uses 0 = low, 1 = mid, 2 = high 
00000001 - boolean for grabable hurtbox 0 = can't be grabbed, 1 = can be grabbed 
00000000 41200000 40800000 - float32 x/y/z offset 
42CE0000 42E00000 42BE0000 - float32 x/y/z size 

For Mario, this first bone is attached to chest. Brian's rig leaves that bone the same. So the bone value does not need updating. The size may however. Increase or decrease the sizes and position as needed. This can only be checked inside Smash Remix itself. 

the hurtboxes all appear back to back in the file and there's 11 total, if a character doesn't use all 11 you'll see FFFFFFFF 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000 where they end. Mario uses only 10 of the hurt boxes. Whilst Fox uses all 11 hurtboxes.
They often have the following order and format:
LOWER BODY 
UPPER BODY 
HEAD 
RIGHT SHOULDER 
LEFT SHOULDER 
RIGHT FOREARM 
LEFT FOREARM 
RIGHT LEG 
LEFT LEG 
RIGHT SHIN 
LEFT SHIN

Lets look back at our rig again.
| Blender Bone | Part # | Mario Rig                        | Brian Rig                                |
|--------------|--------|----------------------------------|------------------------------------------|
| 0            | Part00 | Main bone base                   | Main bone base                           |
| 1            | Part01 | Hips (No Model attached)         | Hips (No Model attached)                 |
| 2            | Part02 | Chest                            | Chest                                    |
| 3            | Part03 | Socket Joint Left Arm            | Socket Joint Left Arm                    |
| 4            | Part04 | Left Upper Arm mesh              | Left Upper Arm mesh                      |
| 5            | Part05 | Left Lower Arm mesh              | Left Lower Arm mesh                      |
| 6            | Part06 | Left Hand                        | Left Hand                                |
| 7            | Part07 | Neck (No model attached)         | item joint (Where items are attached to) |
| 8            | Part08 | Head                             | Potential Witheld Magic Part             |
| 9            | Part09 | Socket Joint Right Arm           | Neck (No model attached)                 |
| 10           | Part0A | Right Upper Arm mesh             | Head                                     |
| 11           | Part0B | Right Lower Arm mesh             | Hair mesh                                |
| 12           | Part0C | Right Hand                       | Cape upper Mesh                          |
| 13           | Part0D | item joint                       | Cape Lower Mesh                          |
| 14           | Part0E | Socket Left Joint leg            | Socket Joint Right Arm                   |
| 15           | Part0F | Left Upper Leg mesh              | Right Upper Arm mesh                     |
| 16           | Part10 | Left Lower Leg mesh              | Right Lower Arm mesh                     |
| 17           | Part11 | Left Ankle Joint                 | Right Hand                               |
| 18           | Part12 | Left Foot                        | Staff Mesh                               |
| 19           | Part13 | Socket Right Joint leg           | Potential Withheld Magic Part            |
| 20           | Part14 | Right Upper Leg mesh             | Socket Left Joint leg                    |
| 21           | Part15 | Right Lower Leg mesh             | Left Upper Leg mesh                      |
| 22           | Part16 | Right Ankle Joint                | Left Lower Leg mesh                      |
| 23           | Part17 | Right Foot                       | Left Ankle Joint                         |
| 24           | Part18 | Large item joint                 | Left Foot                                |
| 25           | Part19 |                                  | Socket Right Joint leg                   | 
| 26           | Part1A |                                  | Right Upper Leg mesh                     |
| 27           | Part1B |                                  | Right Lower Leg mesh                     |
| 28           | Part1C |                                  | Right Ankle Joint                        |
| 29           | Part1D |                                  | Right Foot                               |
| 30           | Part1E |                                  | Large item joint                         |
| 31           | Part1F |                                  |                                          |
| 32           | Part20 |                                  |                                          |
| 33           | Part21 | NOT A REAL PART                  | NOT A REAL PART                          |
| 34           | Part22 | NOT A REAL PART                  | NOT A REAL PART                          |


The hurt boxes bone placements and updates are as follows:
00000006 00000001 00000001 00000000 41200000 40800000 42CE0000 42E00000 42BE0000
0000000C 00000002 00000001 00000000 42880000 41000000 43140000 430C0000 430A0000
0000000E 00000001 00000000 41700000 00000000 00000000 42100000 42480000 42480000
00000008 00000001 00000000 41700000 00000000 00000000 42100000 42480000 42480000
0000000F 00000001 00000000 41F00000 00000000 00000000 42680000 42580000 42580000
00000009 00000001 00000000 41F00000 00000000 00000000 42680000 42580000 42580000
00000018 00000000 00000000 41B00000 00000000 00000000 42680000 42860000 42860000
00000013 00000000 00000000 41B00000 00000000 00000000 42680000 42860000 42860000
00000019 00000000 00000000 41E00000 00000000 00000000 42840000 429C0000 42980000
00000014 00000000 00000000 41E00000 00000000 00000000 42840000 429C0000 42980000
FFFFFFFF 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000

|                      | Mario     | Mario Bone-4 | Brian-4        | Brian                              |
|----------------------|-----------|--------------|----------------|------------------------------------|
| Chest                | 00000006  | 00000002     | 00000002       | 00000006 (did not change position) |
| Head                 | 0000000C  | 00000008     | 0000000A       | 0000000E                           |
| Right Upper arm mesh | 0000000E  | 0000000A     | 0000000F       | 00000013                           |
| Left Upper arm mesh  | 00000008  | 00000004     | 00000004       | 00000008 (did not change position) |
| Right Lower arm mesh | 0000000F  | 0000000B     | 00000010       | 00000014                           |
| Left Lower arm mesh  | 00000009  | 00000005     | 00000005       | 00000009 (did not change position) |
| Right Upper Leg mesh | 00000018  | 00000014     | 0000001A       | 0000001E                           |
| Left Upper Leg mesh  | 00000013  | 0000000F     | 00000015       | 00000019                           |
| Right Lower Leg Mesh | 00000019  | 00000015     | 0000001B       | 0000001F                           |
| Left Lower Leg Mesh  | 00000014  | 00000010     | 00000016       | 0000001A                           |
| Empty                | FFFFFFFF  | FFFFFFFF     | FFFFFFFF       | FFFFFFFF                           |

It is important to fix the bounding box sizes, but for the sake of a solid rig, I am skipping those adjustments for now. There is a seperate section associated with how to adjust the hurt boxes. 

Make sure to update every bone to the new values.

###Step 7B) Using an IDE to modify the hurt boxes (DO THIS BEFORE YOU DO HEX EDITS)
Now that the rig is set up with the proper bones and withheld parts, we have to fix the bounding boxes. Export the bounding box, load into Maya. 
Tweak the boxes, unbind them from the current bones and rebind them to the correct bones. We need to move them to the correct bones. the best approach is to export the model before all the editing. and use it as a reference. Line up the old bones to the new ones, move the box. tweak the size and re-import when done. The best way to remove the rig, but not the box is to goto edit, delete by type history and it will unbind all the boxes. Do this and re import over the character as needed. DO THIS BEFORE YOU DO HEX EDITS.

##Step 8) Importing the modified Character Bin
Once all values are changed. Save the modified file and reimport. To do this, first save your currently edited rom. It is best to not override you original rom. Make a copy.

Now goto game configuration
Choose your modified rom. Then location the character you are overridings main file
Click inject File and choose the file you hex edited.
Once injected, write a new rom. One can choose to override the current rom, but remember, if you made a mistake in which file you changed, you will have to do all prior steps again.

##Step 9) Adjusting the Hurt boxes
I like using bizhawk to do it because you can add all the float32 coordinates to a ram watch and then change the type to float
you have to freeze them and reset training mode for the change to be visible tho
800D81BD 0049 is a gs code that turns hitbox display on
then I would go to 800D6300 which is the main file table, find the file id for the main file and next to it is a pointer to where it's loaded in memory
go to that pointer and scroll down to where the hurtboxes are, then you can select them all and add them to a RAM watch, and change the display type to float
and then freeze them all
then you can freely poke/edit the values and just reset training mode to see it take effect
once you are done you can make a savestate to make sure the frozen values stick, and then load the savestate and copy/paste the hurtboxes out of RAM into the character file
that's how I have always done it anyway, I guess it's kind of a tedious process if you haven't done it before tho

##Step 10) Fix the Shield pose
https://joaorb64.github.io/smash64-modding-wiki/Wiki/characters/shieldpose/#base-shield-pose

Follow these instructions provided by Shino.

##Step 11) Import the characters model data.
This rom should be known as your base rom. File sizes get larger and larger the more times you add/tweak change the characters model. Even if you are fixing a color import. Keep this rom and never override it. As if you decided to modify your model, you will go back to this rom.
Go back to the animation editor:

Click import and add textures:
Follow the steps to import your character. Then save.

Now it is the moment of truth. Lets test the character.

##Step 12) Special Parts
Now that we have the charter model inside the rom, lets also import special parts. Special parts can be alternate models for your character (such as a head swap or a different hand), or can be a model that is hidden and only called in for specific actions (such as Ness's yoyo or Fox's gun.) To set up a special parts, one has to take the character rig, attach the special part to the correct bone in the desired location and then export the rig with just that part attached. Do this for all special parts one wants to import.

Once you have all the model parts exported to separate fbx files,  we need to step through the process to add each part systematically. 

###Step 12a) Special Parts that already exist
If the bone in question has an old special part that can be replaced, click import from obj if added if the textures have already been imported in a prior step or click import from object and add if you have to add the new textures.
Follow the prompts. (i.e. select textures, model and special textures)

This will replace the model that is already present. If you notice for example on our rig, Special part 06 has Extra 00 Hi and Extra 00 low. This is the high poly model for the special part and the low poly model for the special part. Make sure to import for both.


###Step 12b) Adding new special parts
Lets look at the rig again to figure out what needs to be added:
| Blender Bone | Part # | Function                                 | Special Part additions    |
|--------------|--------|------------------------------------------|---------------------------|
| 0            | Part00 | Main bone base                           |                           |
| 1            | Part01 | Hips (No Model attached)                 |                           |
| 2            | Part02 | Chest                                    |                           |
| 3            | Part03 | Socket Joint Left Arm                    |                           |
| 4            | Part04 | Left Upper Arm mesh                      |                           |
| 5            | Part05 | Left Lower Arm mesh                      |                           |
| 6            | Part06 | Left Hand                                | Flat Hand Special Part    |
| 7            | Part07 | item joint (Where items are attached to) | Wisp Special Part         |
| 8            | Part08 | Potential Witheld Magic Part             |                           |
| 9            | Part09 | Neck (No model attached)                 |                           |
| 10           | Part0A | head                                     |                           |
| 11           | Part0B | Hair mesh                                |                           |
| 12           | Part0C | Cape upper mesh                          |                           |
| 13           | Part0D | Cape Lower mesh                          |                           |
| 14           | Part0E | Socket Joint Right Arm                   |                           |
| 15           | Part0F | Right Upper Arm mesh                     |                           |
| 16           | Part10 | Right Lower Arm mesh                     |                           |
| 17           | Part11 | Right Hand                               |                           |
| 18           | Part12 | Staff mesh                               |                           |
| 19           | Part13 | Potential Withheld Magic Part            |                           |
| 20           | Part14 | Socket Left Joint leg                    |                           |
| 21           | Part15 | Left Upper Leg mesh                      |                           |
| 22           | Part16 | Left Lower Leg mesh                      |                           |
| 23           | Part17 | Left Ankle Joint                         |                           |
| 24           | Part18 | Left Foot                                |                           |
| 25           | Part19 | Socket Right Joint leg                   |                           |
| 26           | Part1A | Right Upper Leg mesh                     |                           |
| 27           | Part1B | Right Lower Leg mesh                     |                           |
| 28           | Part1C | Right Ankle Joint                        |                           |
| 29           | Part1D | Right Foot                               |                           |
| 30           | Part1E | Large item joint                         | Chest Special Part        |

First, find the bone you want to add the special part to and select it in the drop down menu in the special part section of the animation editor. 
Click Add special part with the correct bone in the drop down menu to add the space for the part.
Given this special part is the first to be added to this specific bone, we just need to follow the standard import steps to add the new model. 
 
If you are adding a new special part to a bone that already has a model attached to it, when you click add special part, a pop up will appear and extra steps need to be followed:

This popup it telling us that we need to add a moveset command to any moveset to complete the import. 

This window will eventually pop up. One has to click on a command, select “Set Model Form Part” from the Add drop down menu, and add in the correct bone and set the value to 1. 

This is one of the few times the editor does not use HEX, but we still have to add +4 to the bone. So, for reference:
| Blender Bone | Part # | Part   | Value  |
|--------------|--------|--------|--------|
| 30           | Part1E | 34     | 1      |

Notice in the screenshot that the bone is 34, which then shows the part number and the Hex number in the command window. This is a good gage for if you have put in the correct bone. If you mess up on this step, you need to redo the entire model because you are shooting for the smallest character file one can.

Once the command is added, just click the X to close the window. It will automatically add the model and special part to the correct bone.

Repeat this process for every special part you plan to add.

If you are adding in more special parts to the same bone, the values you use need to be incremented.
The first new addition needs to be value of 1. Whilst the next would be 

If you want to add in more, the value increases (per the instructions above.)
i.e. If we add another special part to Bone 1E, we would have to set the value to 2. And a third special part would have the value of 3.