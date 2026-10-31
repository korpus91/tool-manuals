# Configuration | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-checked every claim against polyrepo-clones/freemocap_blender_addon at main (package v2026.04.1041): parameter_models.py dataclass defaults, default_parameters.json, load_parameters_config.py JSON loading path, MainController config reads (reduce_shakiness.recording_fps override from get_recording_framerate, add_rig.keep_symmetry/add_fingers_constraints/use_limit_rotation), and repo-wide search of all three MainController construction sites confirming no other config section is read anywhere

2026-08-24

freemocap_blender_addon source read directly (package v2026.04.1041); integration verified against the FreeMoCap clone (the core Blender export module)

More about how these docs are written

# Configuration

Config (dataclasses in parameter_models.py) is constructed from hardcoded defaults by load_default_parameters_config(), which can alternatively read a JSON file. Defaults include reduce_shakiness.recording_fps = 30.0 (overridden whenever the timestamps CSV yields a real framerate), add_rig.keep_symmetry = False, add_rig.add_fingers_constraints = True, add_rig.use_limit_rotation = False, and alignment reference points (left_knee, left_foot_index) in AdjustEmpties. Only the reduce_shakiness and add_rig sections are consulted by the current MainController pipeline; the other sections are carried but unused there.
