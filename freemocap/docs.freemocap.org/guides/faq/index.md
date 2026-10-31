# Frequently asked questions | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): en-english.json tour text (realtime lightning toggle; recordings keep full frame rate), ImportVideosModal.tsx (Audio and Brightness flash sync), blender_export_config.py (FBX/BVH only), freemocap_blender_addon bl_info (Blender 3.0 minimum), alpha.23 release notes (Blender 5 compatible). Rewritten without the Discussions-era history; multi-person internals trimmed; accuracy figure carried over from /concepts/accuracy-and-limits.

2026-08-25

live polyrepo code: freemocap v2.0.0-alpha.21 realtime pipeline (realtime_aggregator_node.py, realtime_skeleton_inference_node.py, realtime_pipeline_config.py, camera_node_config.py), skellytracker MultiPersonTracker plus its 12-multi-person-tracking design doc, charuco_board_definition.py, freemocap_blender_addon __init__.py bl_info, skellysync README, absence of glTF/grayscale handling in cloned source, and this site's linked pages

2026-08-24

research/github-discussions-qa-raw.md (FreeMoCap/FreeMoCap Discussions Q&A) cross-checked against FreeMoCap and SkellyTracker source, main branches

More about how these docs are written

# Frequently asked questions

## Can FreeMoCap capture more than one person at a time?​

Not yet. FreeMoCap tracks one person per recording. If you need two people today, you can mask each person out in a video editor and process them as separate recordings.

## Does FreeMoCap work in realtime?​

Yes. While cameras are streaming, FreeMoCap can track, triangulate, and display a 3D skeleton live. Turn the live pipeline on with the lightning toggle. Recordings are always saved at the full frame rate, even if the live view can't keep up, and you get the most accurate data by processing the recording afterwards.

## How many cameras can I use? Do USB hubs work?​

USB bandwidth is usually the limit. Plug cameras straight into the computer, spread them across USB controllers, and lower the resolution if you need more of them. See connect and configure cameras.

## What size should I print the ChArUco board?​

Any size works if the cameras can see it clearly. Bigger boards are easier to see from far away. Mount it on something rigid, and enter the measured square length in the calibration settings. See calibrate your cameras.

## Do black-and-white or infrared cameras work?​

Untested. If the camera works with FreeMoCap, check the live tracking view early. If the skeleton shows up reliably in every camera, you're fine.

## Can I export to glTF or GLB?​

No. FreeMoCap exports FBX and BVH files. See export to FBX and BVH. To ask for glTF, request a feature.

## Which Blender versions work?​

Use a current version of Blender. Blender 5 is supported, and the FreeMoCap add-on needs at least Blender 3.0.

## Can I use GoPros, phones, or other cameras that aren't connected to my computer?​

Yes. Record with them however you like, then bring the videos in with Playback > Import Videos. FreeMoCap can line them up using their audio, or a light flash that every camera saw. See process a recording after the fact.

## My installation fails, or my recording is empty​

See fix an installation problem or fix a calibration problem. If neither helps, report a bug or ask on Discord.

## Is FreeMoCap accurate enough for research?​

In FreeMoCap's validation against marker-based motion capture, joint position errors were generally under 30 mm for walking. Accuracy depends on the tracker and your setup. See accuracy, validity, and limits.

- Can FreeMoCap capture more than one person at a time?

- Does FreeMoCap work in realtime?

- How many cameras can I use? Do USB hubs work?

- What size should I print the ChArUco board?

- Do black-and-white or infrared cameras work?

- Can I export to glTF or GLB?

- Which Blender versions work?

- Can I use GoPros, phones, or other cameras that aren't connected to my computer?

- My installation fails, or my recording is empty

- Is FreeMoCap accurate enough for research?
