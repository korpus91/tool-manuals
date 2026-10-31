# Cameras and synchronization | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): ImportVideosModal.tsx (audio and brightness-flash sync on import, added in alpha.23). Replaced the claim that there's no built-in sync for external cameras; rest unchanged.

2026-08-26

polyrepo-clones pulled 2026-08-26: skellycam README and package description (synchronized acquisition from cheap USB webcams, frame-perfect two-phase grab/retrieve orchestration); searched skellycam and freemocap clones for any built-in light-based or audio-based synchronization of external cameras and found none, so that attribution was corrected to the self-sync then import workflow documented in guides/posthoc-mocap and faq; posthoc synchronized_videos import path confirmed in freemocap-docs guides/posthoc-mocap.mdx and skellycam playback_router.py; single-camera support consistent with tutorials/single-camera and tutorials/hardware; dissertation-sourced numbers (six roughly $20 webcams at 1280x720 and 30 FPS, OpenCap iPhone pricing, Theia3D hardware cost) are not verifiable locally and were left as written

2026-08-20

not checked against a specific version

More about how these docs are written

# Cameras and synchronization

For 3D reconstruction to work, every camera's frames need to correspond to the same moment in time. Without that, a time lag between cameras shows up as inaccurate 3D data: the triangulation math assumes it's looking at the same instant from multiple angles, and a few milliseconds of drift breaks that assumption.

## SkellyCam​

SkellyCam is FreeMoCap's synchronized video acquisition component, and its core directive is to make high-quality synchronized recording work with low-cost, consumer-grade hardware. The validation data behind Accuracy, validity, and limits was collected entirely on six USB webcams, about 20each,recordingat1280x720and30FPS,foratotalcameracostofroughly20 each, recording at 1280x720 and 30 FPS, for a total camera cost of roughly 20each,recordingat1280x720and30FPS,foratotalcameracostofroughly120.

That matters beyond the sticker price. A comparably sized OpenCap setup needs six iOS devices, roughly 1,000to1,000 to 1,000to1,500 even with the cheapest available iPhones, and Theia3D's dedicated hardware costs more still. Since the same architecture that keeps SkellyCam's per-camera cost low also makes it cheap to add more cameras, and more cameras generally means more accurate 3D reconstruction (see triangulation and 3D reconstruction), accessibility and accuracy end up reinforcing each other here rather than trading off.

## Beyond USB webcams​

$20 webcams aren't a requirement; they're what the validation study happened to use. You can also record with cameras that aren't connected to the computer, like GoPros or phones, and bring the videos in afterwards with Playback > Import Videos. FreeMoCap can line them up using their audio, or a light flash that every camera saw. See process a recording after the fact. That keeps the door open for higher frame rate cameras for athletic movement, or non-USB cameras outdoors.

## Single camera versus multi-camera​

FreeMoCap can reconstruct 3D data from a single camera, but monocular reconstruction falls well short of what multiple cameras can provide. A second viewpoint adds real information about where a joint sits in space, rather than requiring the system to infer depth from one image, and it substantially reduces the impact of occlusion, a major failure point for single-camera systems. Multi-camera setups are recommended for anything beyond a quick test.

## Next steps​

- Get a multi-camera setup

- Optimize your capture space

- Why calibration matters

- Accuracy, validity, and limits

- SkellyCam

- Beyond USB webcams

- Single camera versus multi-camera

- Next steps
