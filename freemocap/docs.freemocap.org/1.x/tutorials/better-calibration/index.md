# Get a calibration you can trust | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationnot yet checked against current software

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-20

not checked against a specific version

More about how these docs are written

# Get a calibration you can trust

Fix a calibration problem is there for when something's already gone wrong. This page is the other side of that: habits that make a bad calibration less likely in the first place, and how to tell whether a calibration that completed without an error actually produced something trustworthy.

## Give the Board Real Variety​

It's tempting to hold the ChArUco board still, or move it in one simple sweep, and call the calibration done. Don't. Deliberately varying the board's position and its depth and tilt, not just sliding it side to side, is what improves the robustness of the camera parameters calibration solves for. A board held at a single distance and angle gives the optimization far less to work with than one that's been shown near, far, tilted, and rotated throughout the capture volume.

## Check Your Reprojection Error, Don't Just Trust That It Ran​

A calibration can finish without throwing an error and still be a poor one. The number that actually tells you whether to trust it is reprojection error: the gap between where a calibration point was detected and where the resulting camera parameters predict it should be. Lower is better. See Why calibration matters for what this number means, and Triangulation and 3D reconstruction for how the same error signal gets used again downstream, during reconstruction itself. If your calibration's reprojection error is high, that's the signal to go collect more, and more varied, board views rather than proceeding and hoping the downstream data is fine.

## Recalibrate When Anything Physical Changes​

A calibration describes exactly where your cameras are and how they're each aimed. That means it goes stale the moment anything physical changes: a camera gets bumped, refocused, or repositioned; a lens is swapped; a camera is added to or removed from the rig. There's no way for the software to detect this on its own, an old calibration will keep being used until you replace it, so treat any physical change to the camera setup as a reason to calibrate again before your next recording.

## Next steps​

- Calibrate your cameras

- Fix a calibration problem

- Set the ground plane

- Why calibration matters

- Give the Board Real Variety

- Check Your Reprojection Error, Don't Just Trust That It Ran

- Recalibrate When Anything Physical Changes

- Next steps
