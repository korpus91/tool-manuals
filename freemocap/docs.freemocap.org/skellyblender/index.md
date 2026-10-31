# SkellyBlender | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

GitHub API and raw files checked 2026-10-14 (repo metadata, releases, branch comparisons), PyPI/npm metadata, and freemocap uv.lock at v2.0.0-alpha.25 for pinned commits. Added the At a glance section (role in the app, links, pinned version, install note).

2026-08-26

Re-read freemocap_blender_addon (ref main): pyproject.toml (bumpver pattern vYYYY.0M.BUILD[-TAG], current_version v2026.04.1041, dependencies=[], requires-python >=3.10), package __init__.py (bl_info author ajc27, addon version (1, 1, 7), minimum Blender (3, 0, 0)), README.md (ajc27-git credit, Zenodo DOI badge, AGPLv3), core_functions/main_controller.py load_data() stage order and outputs (empties, rig, rigid body meshes, Skelly mesh, center of mass mesh, video planes, capture cameras, checkerboard ground plane, FBX/BVH export, saved .blend), create_freemocap_empties.py, add_capture_cameras.py (reads the recording's .toml calibration), export_3d_model.py default formats ['fbx', 'bvh'], export_video.py composited render pipeline, blender_ui/operators/__init__.py operator registry, .github/workflows, and confirmed there is no test suite; pantheon tier confirmed against the site's data/repos.yml

2026-08-24

freemocap_blender_addon source read directly (package v2026.04.1041); integration verified against the FreeMoCap clone (the core Blender export module)

More about how these docs are written

# SkellyBlender

SkellyBlender is the Blender addon of the FreeMoCap polyrepo. On disk and on GitHub it is freemocap_blender_addon (github.com/freemocap/freemocap_blender_addon, Python package freemocap_blender_addon); the site calls it SkellyBlender. It sits in the pantheon tier and owns the last stage of the pipeline. It turns a processed FreeMoCap recording into an animated Blender scene, saving a .blend file and exporting FBX and BVH. The original addon was developed by ajc27 (ajc27-git on GitHub), who is still credited as the addon author in bl_info.

What a completed load produces: keyframed empties for every tracked point, an armature rig with a TPose rest pose (for easier retargeting), rigid body meshes, a skinned Skelly mesh, center of mass visualization, capture videos as image planes, cameras rebuilt from the recording's calibration file, a checkerboard ground plane, and a saved .blend next to the recording's data. A second pass exports the rigged animation as FBX or BVH, and a third renders composited videos from the scene.

Packaging facts, from pyproject.toml and __init__.py: the version is managed by bumpver on a vYYYY.0M.BUILD pattern (currently v2026.04.1041, while bl_info separately declares addon version (1, 1, 7)), the minimum Blender is (3, 0, 0), and development requires Python >= 3.10. Runtime dependencies are declared as an empty list because the addon runs inside Blender's bundled interpreter. Licensed AGPLv3, with a Zenodo DOI badge in the README. There are no tests in the repository.

## At a glance​

In the FreeMoCap app. Makes the Blender scene. When you export a MediaPipe recording to Blender, FreeMoCap runs this add-on inside Blender to build the animated skeleton, save the .blend file, and write FBX and BVH files. Inside Blender, the same add-on adds a FreeMoCap tab to the 3D view sidebar. See open your recording in Blender.

Codefreemocap/freemocap_blender_addon

IssuesOpen issues

DownloadLatest release (freemocap_blender_addon_<version>.zip)

Version in FreeMoCap alpha.25549b0fd on main (v2026.04.1041)

LicenseAGPL-3.0

You don't need to install the add-on for FreeMoCap's own export; the app brings its own copy. To use it directly in Blender, download the release .zip and install it from Edit > Preferences > Add-ons.

## Contents​

- How it runs

- The Load Data pipeline

- Exports

- Animation tools

- In-viewport analysis tools

- The data handler and saved outputs

- Configuration

- Utilities

- Packaging and CI

- Caveats

- At a glance

- Contents
