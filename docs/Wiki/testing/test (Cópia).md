# Creating GFX based on Falcon Punch graphics

Original Descriptor
Source: https://github.com/VetriTheRetri/ssb-decomp-re/blob/7e437d81a74fcd03e72847934b2e4e44e43ea380/src/ef/efmanager.c#L827
```
efCreateDesc dEFFalconPunchEffectDesc =
{
    EFFECT_FLAG_USERDATA,                   // Flags
    15,                                     // DL Link
    &gFTDataCaptainSpecial3,                // Texture file

    // DObj transformation struct 1
    {
        0x50,                               // Main matrix transformations
        OMMtx_Transform_RotRpyR,            // Secondary matrix transformations
        0x00                                // ???
    },

    // DObj transformation struct 2
    {
        OMMtx_Transform_Null,               // Main matrix transformations
        OMMtx_Transform_Null,               // Secondary matrix transformations
        0x00                                // ???
    },

    func_ovl2_800FD5D8,                     // Proc Update
    func_ovl0_800CB4B0,                     // Proc Render

    &lEFFalconPunchDObjSetup,               // DObj Setup attributes offset (?)
    &lEFFalconPunchMObjSub,                 // MObjSub offset
    0x0,                                    // AnimJoint offset
    &lEFFalconPunchMatAnimJoint             // MatAnimJoint offset
};
```

- Edit Falcon Punch effect in vanilla using GE.
- You can export Falcon Punch, add textures using Special textures, then reimport the model.
- If the graphic ends up dark ingame, you should update the shading color in GE to white.

- Open game in emulator, add breakpoint at `0x80101ED8` = `dEFFalconPunchEffectDesc`
- Right at the start of the function, it loads the address to A0. It has the whole struct. Copy any offsets from there

Example:
```
punch_anim_struct_TEST:
    dw  0x020F0000
    dw  Character.TEST_file_8_ptr
    dw  0x501C0000
    OS.copy_segment(0xA9AF8, 0x0008)
    dw  my_update_routine_ // Here, I'm overwriting the ProcRender function
    dw  0x00000040 // copied from the game's memory when playing ROM
    dw  0x000001A0 // copied from the game's memory when playing ROM
    dw  0x00000000 // copied from the game's memory when playing ROM
    dw  0x000001FC // copied from the game's memory when playing ROM
```