# Adding external files to characters

A lot of times you can just replace files that are not being used anymore in the character's `main` file `reqlist`. So for a character based on Captain Falcon, you have pointers to Falcon Punch Graphic and Blue Falcon on his reqlist that can be replaced by the new file ID and will work.

## Adding extra external files to a character

Sometimes you need to add more files than you have easy slots. That's when editing the `main` file is needed.

First, export the character's `main` file, `reqlist`, and `ParseTree`.

In the `ParseTree` you'll notice the file has 2 lists: one for internal files, and one for external files. Here, we're interested in external files. All these 4 digit pointers at the beginning of each line point towards an entry in `main.bin`, in the format `XXXX * 4 = Address in main.bin`. And if you go in your main file, you'll notice that in `XXXX * 4` you'll find the reference to the next pointer in the list, and so on until the last file where you'll have a `FFFF` demarking that's the last element in the linked list.

To add an extra external file, you'll have to:

- At the end of the file, add the new last entry we're adding to the external file reqlist. Here we have to start with `FFFF` because it's going to be the last entry in the list. Follow that with `4 * YYYY` where `YYYY` is the pointer to what you want to import from the external file.
    - If the file you're adding has a reqlist, `0000` will do (projectile hitbox file for example). That would mean adding `FFFF0000` at the end of the file.
    - If your file has `InternalFileTableOffsetBytes`, like Falcon Punch based GFX, use that value multiplied by 4.
- Get the address to the final element in the external file list from the ParseTree. Multiply what's in the ParseTree by 4 to get the actual address you have to go.
- Go into the `main.bin` file at the address you calculated. You'll know it's correct because you'll find `FFFF` at this address since it's the last file in the list.
- Update this `FFFF` to be the address where you added your `FFFF` entry before divided by 4. This means that what was the last entry is now pointing towards your new last entry.
- Open the `reqlist` and add a new entry at the end pointing towards your external file.