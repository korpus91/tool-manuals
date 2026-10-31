# See what you made | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

this site's own find-your-data.md and blender.md

More about how these docs are written

# See what you made

Right after a recording finishes, two questions matter: did it actually track your movement, and where did everything go.

## The fastest check: did Blender open​

If Blender was detected on your system, FreeMoCap opens a scene automatically when processing finishes: a skeleton moving through the motion you just recorded. Look for the obvious stuff first, does it move the way you moved, are all your limbs where they should be, is anything flying off into space or frozen in place. That's enough to tell you whether the whole pipeline worked, before you look at any actual data.

If Blender wasn't detected, or didn't open automatically, see open your recording in Blender.

## If you want to check without Blender​

Every recording also gets an annotated video: your original footage with the detected keypoints drawn directly on top. It's in the recording's annotated_videos/ folder (see find and read your output for the full layout), and it's the fastest way to sanity-check 2D tracking by eye without needing Blender at all.

## What "worked" looks like, and what didn't​

Good signs: keypoints in the annotated video sit on the actual joints and move smoothly frame to frame. In Blender, the skeleton's proportions look roughly human and its motion matches what you did.

Signs something's off:

- Keypoints jumping around or disappearing in the annotated video usually means a lighting or contrast problem, not a software bug. See optimize your capture space.

- A skeleton that's lying down, mirrored, or wildly out of scale in Blender (multi-camera recordings only) usually points to the calibration, not the recording itself. See get a calibration you can trust.

A single-camera recording won't give you reliable 3D positions no matter how clean the tracking looks, that's expected, see cameras and synchronization for why. If 2D tracking looked clean and you're ready for real 3D data, that's the cue to move on to multiple cameras.

## Next steps​

- Where to go next

- Find and read your output

- Record with multiple cameras

- The fastest check: did Blender open

- If you want to check without Blender

- What "worked" looks like, and what didn't

- Next steps
