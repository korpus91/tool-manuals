# Export to FBX and BVH | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

freemocap_blender_addon source (main, not yet re-checked against the running app)

More about how these docs are written

# Export to FBX and BVH

Both FBX and BVH export happen through the same Blender export step as the .blend scene itself, see open your recording in Blender for the prerequisites and the export flow. This page is about the format-specific options.

glTF isn't available yet

Despite what you may see referenced elsewhere, glTF export isn't implemented in the current build, only FBX and BVH are. If you need glTF specifically, that's worth raising with the project rather than assuming it's just undocumented.

## Choosing a format​

- FBX carries the mesh, the armature, and animation together, and is the more broadly supported format across 3D and game engine software (Unreal, Unity, Maya, and others).

- BVH carries just the skeletal animation (joint hierarchy and rotations over time), no mesh. It's the more common choice if you're retargeting the motion onto a character you already have rigged elsewhere, rather than bringing in FreeMoCap's own mesh.

## Format options​

Set alongside the rest of the Blender export configuration:

OptionWhat it does

Bone naming conventionDefault, Metahuman, or DAZ G8.1, match whichever rig you're retargeting onto

Rest pose typeSame three options, controls the pose bones are considered "neutral" in

Restore defaults after exportRestores original bone names and rest pose once the export finishes, on by default

FBX has two additional options: primary/secondary bone axis (which local axes the exported bones use, matters for matching a specific target rig's conventions) and add leaf bones (adds terminal bones at the end of chains like fingers, which some rigs expect and others don't).

## Next steps​

- Open your recording in Blender

- Find and read your output

- Choosing a format

- Format options

- Next steps
