# Filter and fill your data | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationnot yet checked against current software

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-20

not checked against a specific version

More about how these docs are written

# Filter and fill your data

By the time a recording reaches you as output, it's already been through SkellyForge, FreeMoCap's post-processing package. This page explains what it does, so you know what you're actually looking at when you inspect your data. SkellyForge is architecturally separate from the reconstruction step itself: a modular post-processing component, not something baked into triangulation, which is what makes both of the following steps possible.

## Filling Gaps​

Not every frame produces a usable 3D point for every keypoint. If too few cameras had a confident detection, or every tested camera subset had too much reprojection error, reconstruction leaves that point out rather than guessing. SkellyForge fills those gaps by interpolation. How many gaps you get in the first place comes down to capture quality: more occlusion, more cameras losing track of a keypoint, more gaps to fill. See optimize your capture space to reduce how often this happens.

## Smoothing Noise​

After gaps are filled, SkellyForge applies a low-pass Butterworth filter to the trajectories. In plain terms: real human movement changes relatively smoothly from one frame to the next, while a lot of the noise in raw triangulated data is fast, small, frame-to-frame jitter. A low-pass filter reduces the fast jitter while leaving the slower, real movement mostly intact.

That tradeoff runs in both directions. Filtering that's well-matched to your movement makes for cleaner-looking, easier-to-analyze data. Filtering that's too aggressive for a genuinely fast movement (a strike, a jump, anything ballistic) can smooth away real signal along with the noise. If your analysis depends on high-frequency detail, it's worth knowing that this smoothing step happened, rather than assuming the trajectories you're looking at are the raw triangulated output.

## Why This Matters for Your Analysis​

Both steps happen automatically, which is usually what you want. But "automatically" isn't the same as "invisibly": knowing that your data has been gap-filled and filtered helps you interpret it correctly, especially alongside the per-keypoint reprojection error that travels with your data as a separate quality signal. A keypoint with a lot of interpolated frames and high reprojection error deserves more scrutiny than one that was cleanly tracked throughout.

## Next steps​

- The FreeMoCap output data model

- Triangulation and 3D reconstruction

- Accuracy, validity, and limits

- Filling Gaps

- Smoothing Noise

- Why This Matters for Your Analysis

- Next steps
