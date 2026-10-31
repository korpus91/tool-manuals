# Coordinate conventions | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationnot yet checked against current software

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-19

not checked against a specific version

More about how these docs are written

# Coordinate conventions

FreeMoCap's 3D data is millimetres, right-handed, with +Z up once a recording has been through ground-plane calibration. This matches the axis convention used across robotics tooling and most 3D and biomechanics software, rather than the left-handed, Y-up convention common in some game engines. For the reasoning behind these choices, see Coordinate systems and units.

PropertyValue

Unitsmillimetres (mm)

Handednessright-handed, always

Up axis+Z, after ground-plane calibration (see below)

Rotation encodingquaternion, w, x, y, z (scalar-first)

Identity rotationthe T-pose

## World origin and orientation​

Where (0, 0, 0) sits, and which way is up, depends on how the recording was calibrated.

Ground-plane calibration (recommended). The origin is corner 0 of the ChArUco board, and +Z is the board's own upward-facing normal, computed with the right-hand rule. The subject comes in standing upright, feet at Z = 0. The board's placement on the floor sets the horizontal (X and Y) orientation of the scene: FreeMoCap does not tie X or Y to the subject's facing direction, so two recordings calibrated with the board turned 90° apart differ by a rotation about Z. See Set the ground plane for exactly how the origin and axes are built from the board.

Default calibration (no ground-plane board). The origin is the optical center of camera 0, and the world axes are camera 0's own: +Z outward from the lens, +X right, +Y down the image. This is right-handed, but it is not Z-up. Reconstructed subjects typically come in lying on their side rather than standing upright.

## Segment and rotation data​

Joint and segment rotations are independent of the world's horizontal orientation. They are built from the subject's own landmarks (an "up" direction from hips to neck, a "lateral" direction across the shoulders), so they resolve to the same anatomical meaning regardless of which way the calibration board was facing:

- +Z up, +X anterior (the direction the subject faces), +Y the subject's own left.

- Right-handed, same as the world frame.

- Quaternions are wxyz (scalar-first). Identity, (1, 0, 0, 0), is the T-pose: a segment whose current orientation matches its T-pose reference resolves to no rotation at all.

## Exporting to other tools​

Most 3D and game-engine tools do not share this convention. Unity is left-handed and Y-up. Unreal is left-handed, Z-up, and scaled in centimetres rather than millimetres. Blender's default world is Z-up, matching FreeMoCap's own up axis. Check the target application's convention before assuming an export carries over unchanged.

## Further detail​

This page states FreeMoCap's declared convention, not the full specification. For how the world transform is derived from each calibration method, and how segment rotations compose parent to child, see the current-work-plans directory in the core repo, particularly 00-foundation/conventions.md.

- World origin and orientation

- Segment and rotation data

- Exporting to other tools

- Further detail
